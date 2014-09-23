#ijeomamotion.js
 
A Javascript library (which supports p5.js) for sketching animations. Ijeoma (ee-JOH-mah) means safe journey in Igbo, the language of my family from Nigeria. I started writing this a while back in Java for Processing then ported it to JS for processing.js and recently I've rewrote it for JS and  .js. You can find the p5.js addon p5.ijeomamotion.js [here](https://github.com/ekeneijeoma/p5.ijeomamotion.js).

#Download 
Developement: 
https://raw.githubusercontent.com/ekeneijeoma/ijeomamotion.js/master/build/ijeomamotion.js

Production: 
https://raw.githubusercontent.com/ekeneijeoma/ijeomamotion.js/master/build/ijeomamotion.min.js

#Examples  
Circular Networks [1](http://ekeneijeoma.github.io/ijeomamotion.js/examples/CircularNetwork.html) and [2](http://ekeneijeoma.github.io/ijeomamotion.js/examples/CircularNetwork2.html)

[Pie Chart](http://ekeneijeoma.github.io/ijeomamotion.js/examples/PieChart2.html)

[Sequence](http://ekeneijeoma.github.io/ijeomamotion.js/examples/Sequence.html)

[Timeline](http://ekeneijeoma.github.io/ijeomamotion.js/examples/Timeline.html)

#Getting Started 
##How to create Tweens

###Numbers  
There are 4 ways to setup Tweens.
```javascript
new MOTION.Tween(duration,delay,easing) //object defaults to window
new MOTION.Tween(object, duration, delay, easing) 
new MOTION.Tween(object, property, end, duration, delay, easing)
new MOTION.Tween(property, end, duration, delay, easing) //object defaults to window
```

Say you want to tween x from 0 to 100 in 100 frames. 
```javascript
var x = 0;
var t = new MOTION.Tween(100).add("x", 100, 100).play();
```
or
```javascript
var x = 0;
var t = new MOTION.Tween(this,100).add("x", 100).play();
```

or
```javascript
var x = 0;
var t = new MOTION.Tween(this, "x", 100, 100).play();
```

The 2nd way lets you chain/add more properties to the Tween. Say we want to tween a var x from 0 to 100 and var y from 0 to 100 in 100 frames.
```javascript
var t = new MOTION.Tween(this).add("x", 100).add("y", 100).play();
```

###All in 1!
You can also tween multiples properties of any type in 1 Tween.
```javascript
var t = new MOTION.Tween(100).add("x", 100).add("c", color(255)).add("v", createVector(100, 100)).play();
```

###Callbacks 
```javascript
t = new MOTION.Tween(100).onStart(func).onUpdate(func).onEnd(func).play(); 
```

##How to playback Tweens 
###Delaying
```javascript
var t = new MOTION.Tween("w", width, 50, 50).play(); //delay for 50 frames
```
or
```javascript
var t = new MOTION.Tween(this,50,50).add("w", width).delay(50).play();
```
###Pausing, Resuming  
```javascript  
t.pause(); 
t.resume(); 
t.seek(time); 
```
###Repeating
```javascript
var t = new MOTION.Tween("w", width, 100).repeat().play();
```
###Reversing
```javascript 
var t = new MOTION.Tween("w", width, 100).repeat().reverse().play();
```

##How to playback tweens in parallel
```javascript
var p = new MOTION.Parallel()
  .add(new MOTION.Tween(...)) 
  .add(new MOTION.Tween(...)) 
  .play(); 
``` 

##How to playback tweens in a sequence
```javascript
var s = new MOTION.Sequence() 
  .add(new MOTION.Tween(...)) 
  .add(new MOTION.Tween(...))  
  .repeat()
  .play();
``` 

##How to playback tweens in a timeline
```javascript
var t = new MOTION.Timeline()
  .add(new MOTION.Tween(...), 100) //creates a keyframe at 100 frames and adds that tween object
  .add(new MOTION.Tween(...), 200)
  .repeat()
  .play();

//or

var t = new MOTION.Timeline();
var k1 = new MOTION.Keyframe(100).add(new MOTION.Tween(...))
var k2 = new MOTION.Keyframe(200).add(new MOTION.Tween(...))
t.add(k1).add(k2).play();
``` 