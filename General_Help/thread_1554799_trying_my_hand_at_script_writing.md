---
title: "trying my hand at script writing"
date: 2010-08-17
forum: General Help
---

### Post by jsriz on 2010-08-17
I have been trying things just to gain bragging rights....
I was wondering if i could somehow write a script to make the led of the internal web cam(of my lappi) turn on or flicker (without starting the camera),jus 4 fun, but it should be possible ain't it!!!!
I tried reading the source codes of cheese but i guess i make a bad programmer.
Could anyone help me out

---

### Post by KeyserSoze93 on 2010-08-17
I don't know about a camera light, but you can make the lights on your keyboard flash by themselves using the xset command.

From the man page:

```

       led     The led option controls the keyboard LEDs.  This controls the turning on or off of one or all of the LEDs.  It accepts an
               optional  integer,  a  preceding  dash(-)  or  an ’on/off’ flag.  If no parameter or the ’on’ flag is given, all LEDs are
               turned on.  If a preceding dash or the flag ’off’ is given, all LEDs are turned off.  If a value  between  1  and  32  is
               given,  that LED will be turned on or off depending on the existence of a preceding dash.  A common LED which can be con&#8208;
               trolled is the ‘‘Caps Lock’’ LED.  ‘‘xset led 3’’ would turn led #3 on.  ‘‘xset -led 3’’ would turn it off.  The particu&#8208;
               lar LED values may refer to different LEDs on different hardware.

```

---

### Post by kaivalagi on 2010-08-17
Sounds like you would need to rewrite the drivers for the webcam to provide the led thing you want...I would pick something else to try.

A lot of people here suggest learning something like Bash or even Python first off, I suggest taking on python, it can be used like any scripting language and and you can also do a lot more with it than bash/sh etc.

Bottom line, you need to find a way to learn that best suits you, some prefer reading lots first, others learn by example and problem to solve...your call.

Just dont expect anyone to write code for you :p

---

### Post by jsriz on 2010-08-18
> **kaivalagi said:**
> Sounds like you would need to rewrite the drivers for the webcam to provide the led thing you want

That would be the case if it were external cam but this one is on my laptop and it works "out of the box" on linux so I believe I could achieve it by changing some scripts in my present installation(well not sure which ones though) 
> 
Just dont expect anyone to write code for you :p
:lolflag: but i just need a clue about what to do.....

---

### Post by jsriz on 2010-08-18
> **KeyserSoze93 said:**
> I don't know about a camera light, but you can make the lights on your keyboard flash by themselves using the xset command.

From the man page:

```

       led     The led option controls the keyboard LEDs.  This controls the turning on or off of one or all of the LEDs.  It accepts an
               optional  integer,  a  preceding  dash(-)  or  an &#8217;on/off&#8217; flag.  If no parameter or the &#8217;on&#8217; flag is given, all LEDs are
               turned on.  If a preceding dash or the flag &#8217;off&#8217; is given, all LEDs are turned off.  If a value  between  1  and  32  is
               given,  that LED will be turned on or off depending on the existence of a preceding dash.  A common LED which can be con&#8208;
               trolled is the &#8216;&#8216;Caps Lock&#8217;&#8217; LED.  &#8216;&#8216;xset led 3&#8217;&#8217; would turn led #3 on.  &#8216;&#8216;xset -led 3&#8217;&#8217; would turn it off.  The particu&#8208;
               lar LED values may refer to different LEDs on different hardware.

```
That seems cool but can't try that out as some one at dell decided to remove all the leds for my model[:(].
In that case I can guess we'd be able to make a nice light show on the laptop with alternating light glowing up during boot up.
I never thought i'll miss the led's when i bought this one....:mad:

---

