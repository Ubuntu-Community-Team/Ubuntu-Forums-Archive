---
title: "Can I honestly get some help?"
date: 2009-11-04
forum: General Help
---

### Post by terrorhawk on 2009-11-04
Honestly... I have scoured. I have searched. I have looked elsewhere. I'm the ******* Christopher Columbus of the Linux users of 9.10 right now. I just... want... someone... to directly help lol.

You may have heard it before. You may have helped someone before. If you have, HELP ME, TOO. I'd really appreciate it if someone could do this for me, because this is getting a bit out of hand.

Now... to my point: I cannot get my graphics on Ubuntu 9.10 to go above 1024x768. I have a Dell Dimension 2400 with an Intel 82845G graphics card. Nothing fancy, obviously. I'm not even concerned about Compiz... all I want is my resolution back. With 9.04 it was fine at 1280x1024 (the highest it can go, due to my crappy monitor and limiting graphics card) but now, all of a sudden, it no longer finds the ability to go that high.

I did a clean install -- ext4 filesystem, etc, etc -- if that's worth noting.

If someone can give me a straightforward answer on how to go ahead and do this, and actually help guide me (I'm not handicapped... just nearly blinded by frustration at this point, kinda) that would be SO damn appreciated lol.

Please, guys, I thought the Linux community was about help. I never had issues when in need before... I don't see why things change now.

Hell... if I had the money, I'd pay someone to fix this. I want to learn to do this firsthand though, so I need someone with more know-how than I have at this point to help me.

So... yeh... there's my plea.

Thank you.

---

### Post by P4man on 2009-11-04
I dont think there is a need for such a plea, most people get helped when just asking the question :)

But anyway, lets start by getting some info. What monitor do you have?
Can you post the contents of /etc/X11/xorg.conf?

Did you already try using xrandr or grandr or not? open a terminal and type
```
xrandr
``` 

and post the output here.

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> I dont think there is a need for such a plea, most people get helped when just asking the question :)

But anyway, lets start by getting some info. What monitor do you have?
Can you post the contents of /etc/X11/xorg.conf?

Did you already try using xrandr or grandr or not? open a terminal and type
```
xrandr
``` 

and post the output here.



Okay. When I go look in the /etc/X11 folder, there is no actual xorg.conf file anywhere. I don't see it... literally. My monitor is also just a simplistic Dell CRT monitor. I think it's 15 or 16 inches total, but it used to display 1280x1024 perfectly.

Also, this is what I got when I typed the command in terminal:

[B]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       75.0*+   75.1  
   800x600        75.0  
   640x480        75.0     60.0  
   720x400        70.1  [/B]

---

### Post by Peter09 on 2009-11-04
There is no real configuration in xorg any more for Karmic, it is now virtually obsolete.

---

### Post by Peter09 on 2009-11-04
Follow through this link it may help

[http://ubuntuforums.org/showthread.php?t=493082](http://ubuntuforums.org/showthread.php?t=493082)

---

### Post by P4man on 2009-11-04
It looks like your monitor claims it cant handle more than 1024. We can try and force higher resolution at your own risk. Do you know what refresh rate it can do at 1280x1024? Im gonna assume 60Hz to be safe

Create the new mode:

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

then try switching to it:
```
xrandr --output [COLOR="Red"]VGA1[/COLOR] --mode 1280x1024

```

**edit**: not sure if that should be [COLOR="Red"]VGA1[/COLOR] or [COLOR="Red"]VGA[/COLOR]. If one fails try the other

---

### Post by bradleypariah on 2009-11-04
I'll bite.  I'm having the exact same issue and I too have been looking all over the Earth for an answer.  Every time I have found "an" answer, it has never been "the" answer.  I have, in fact, been down the xrandr path, and the xorg.conf path, and the choosing different adapters path... I'm close to the "try a different operating system" path.  

God bless you, and here's my ***xrandr*** output

```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 354mm x 265mm
   1280x1024      75.0*+   60.0  
   1152x864       75.0  
   1024x768       85.0     75.0     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     66.7     59.9  
   720x400        87.8     70.1  
DVI-0 connected (normal left inverted right x axis y axis)
   1280x720       60.0 +
   1920x540       60.1  
S-video disconnected (normal left inverted right x axis y axis)
```The resolution I want is 1360x768.  I typed
```
cvt 1360 768
```it spit out
```
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```so i typed
```
xrandr --newmode Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```and it spit out
```
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
```Then nothing happened.  I logged out.  I restarted.  Nothing.
So, I input
```
xrandr --output DVI-0 --mode 1360x768
```It spit out
```
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

```Nothing.  I logged out, I re-started, nada.

I am quite sad.  Ubuntu and I are on the outs.

Before you ask; Yes,  I have pasted the modelines I created into the xorg.conf file.  This made no difference at all.

I have tried every suggestion in all of the following locations:
[COLOR=Blue][https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://ubuntuforums.org/showthread.php?t=306663](http://ubuntuforums.org/showthread.php?t=306663)
[https://wiki.ubuntu.com/Specs/UNRKarmicApplicationResolution](https://wiki.ubuntu.com/Specs/UNRKarmicApplicationResolution)
[http://ubuntuforums.org/showthread.php?t=790301](http://ubuntuforums.org/showthread.php?t=790301)
[http://ubuntuforums.org/showthread.php?t=970095](http://ubuntuforums.org/showthread.php?t=970095)
[http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)[/COLOR]      
(just to name a few)
I've been at this for ***a week***.  I'm losing much needed sleep.  I'm seriously close to putting a fist through a wall.  If you have some advice; please help - and thank you.

---

### Post by P4man on 2009-11-04
bradleypariah, this line seems wrong:
```

xrandr --newmode [COLOR="Red"]Modeline[/COLOR] "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

```

Try
```
xrandr --newmode  "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```

If you got xrandr help options then that means the command you gave was not correct.

---

### Post by P4man on 2009-11-04
BTW, those changes are not persistent. If you reboot they will get lost, but if they work Ill explain how to make them persistent.

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> BTW, those changes are not persistent. If you reboot they will get lost, but if they work Ill explain how to make them persistent.

This is all I get when I try that first command you told me:

[B]X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18[/B]

---

### Post by bradleypariah on 2009-11-04
Thank you for helping.

I pasted
```
xrandr --newmode  "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```It spit out nothing.  Just went back to prompt.
So I typed
```
xrandr --output DVI-0 --mode 1360x768
```It said
```
xrandr: cannot find mode 1360x768
```So I tried
```
xrandr --output DVI --mode 1360x768
```It did nothing

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> This is all I get when I try that first command you told me:

[B]X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18[/B]

Did you run it twice? It would give "badname: if that mode line already exists. Check by running xrandr. If you see the 1280x1024 line in there, try using it with the second command.

---

### Post by P4man on 2009-11-04
> **bradleypariah said:**
> Thank you for helping.

I pasted It spit out nothing.  Just went back to prompt.
As it should. You can check if the modeline is added by running xrandr again.

As for changing to the new mode try this:
```
xrandr --output DVI[COLOR="Red"]-0 [/COLOR]--mode 1360x768
```

---

### Post by bradleypariah on 2009-11-04
I wound up getting his same error.
So I re-typed xrandr
Check this out!
```
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 354mm x 265mm
   1280x1024      75.0*+   60.0  
   1152x864       75.0  
   1024x768       85.0     75.0     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     66.7     59.9  
   720x400        87.8     70.1  
DVI-0 connected 1280x720+1280+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1280x720       60.0*+
   1920x540       60.1  
S-video disconnected (normal left inverted right x axis y axis)
  1360x768_60.00 (0x80)   84.8MHz
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8H
```

Dude!  The 1360 x 768 exists!  :-D  But it's on the S-Video output?!  lol  How the heck did I do that?? How do I move it to DVI?

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Did you run it twice? It would give "badname: if that mode line already exists. Check by running xrandr. If you see the 1280x1024 line in there, try using it with the second command.

Now all I'm getting is "Cannot find mode 1280x1024"

---

### Post by P4man on 2009-11-04
> **bradleypariah said:**
> 

Dude!  The 1360 x 768 exists!  :-D  But it's on the S-Video output?!  lol  How the heck did I do that?? How do I move it to DVI?

ah.. good point and question. Not entirely sure. Try this

```
xrandr --newmode [COLOR="DarkRed"]DVI-0[/COLOR] "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```

If that fails try
```

xrandr --addmode [COLOR="DarkRed"]DVI-0[/COLOR] 1360x768
```

Not sure if it should should be [COLOR="DarkRed"]DVI-0[/COLOR] or [COLOR="DarkRed"]DVI[/COLOR]

---

### Post by terrorhawk on 2009-11-04
> **terrorhawk said:**
> Now all I'm getting is "Cannot find mode 1280x1024"

And, now, when I open a terminal and type "xrandr" this is all I get:

[B]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       75.0*+   75.1  
   800x600        75.0  
   640x480        75.0     60.0  
   720x400        70.1  
  1280x1024_60.00 (0x125)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz[/B]

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> Now all I'm getting is "Cannot find mode 1280x1024"

Did you try for both VGA and VGA1? 

More things to try (keep in mind I cant test this stuff here, xrandr doesnt work with my nvidia drivers):

```
xrandr --output VGA1 --mode 1280x1024_60.00
```
```
xrandr --output VGA1 --mode 1280x1024 --rate 60
```

---

### Post by bradleypariah on 2009-11-04
Thank you so much again for helping the two of us!

The first code got a response of
```
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
```The second code gave a response of
```
xrandr: cannot find mode "1360x768"
```:-s

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Did you try for both VGA and VGA1? 

More things to try (keep in mind I cant test this stuff here, xrandr doesnt work with my nvidia drivers):

```
xrandr --output VGA1 --mode 1280x1024_60.00
```
```
xrandr --output VGA1 --mode 1280x1024 --rate 60
```

I don't get what I'm supposed to be doing at this point... when I enter those two codes you just sent, they don't even do a thing. Where am I supposed to be entering this stuff if not in the Terminal?

It's late at night... I'm tired... and getting more annoyed. I don't wanna just give up though.

What exactly do I do?

---

### Post by P4man on 2009-11-04
> **bradleypariah said:**
> 
]The second code gave a response of
```
xrandr: cannot find mode "1360x768"[-s

Maybe:
[CODE]xrandr --addmode DVI-0 1360x768_60.00
```
?

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> I don't get what I'm supposed to be doing at this point... when I enter those two codes you just sent, they don't even do a thing. 



Sure they do. compare the output of xrandr in your first post the last one you posted. At the bottom you will see a new mode was created for 1280x1024. Now all you have to do is switch to it ;)

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Sure they do. compare the output of xrandr in your first post the last one you posted. At the bottom you will see a new mode was created for 1280x1024. Now all you have to do is switch to it ;)

When I open System>Preferences>Display, 1280x1024 is still not displayed there lol.

---

### Post by P4man on 2009-11-04
No but with some luck
```

xrandr --output VGA1 --mode 1280x1024_60.00
```

or

```
xrandr --output VGA --mode 1280x1024_60.00
```

should switch to it

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> No but with some luck
```

xrandr --output VGA1 --mode 1280x1024_60.00
```

or

```
xrandr --output VGA --mode 1280x1024_60.00
```

should switch to it

The first code spits me the error: "Cannot find mode 1280x1024_60.00"
The second code just goes to a ready Terminal line, doing nothing.

I'm so frustrated lol. I don't want to downgrade back to 9.04 though. I'd really rather not have to do that.

---

### Post by bradleypariah on 2009-11-04
Okay, the goods:  :-D
```
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```Has the pleasing effect of adding the correct resolution to S-Video
Your new suggestion of 
```
xrandr --addmode DVI-0 1360x768_60.00
```Moved it to my possible resolutions in the Displays window!  Bravo!  :-D

Now... how do I make it stick?  I logged out, and as you mentioned, when logging back in, all of the work is gone.  How can I make this default?

Thank you thank you thank you!  :-D

---

### Post by P4man on 2009-11-04
Ah, at least someone is having some success :D

Before making it stick, can you confirm you can also change the resolution by using 

```
xrandr --output DVI-0 --mode 1360x768_60.00
```

?

As for making it stick, there are a few ways apparently. Adding the right stuff to your xorg.conf being the preferred one, but since you already seem to have tried that, lets try a somewhat less beautiful solution

create a new file called ~/.xprofile
And paste all 3 xrandr commands in there to create the mode (im assuming upon reboot those modes are gone too), assign them to DVI-0 and switch to it. That will only work for your user and it will cause some resizing when you log in. If you dont want that lets try your xorg.conf, but I must warn you Im no authority in that (or any other) field.

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> The first code spits me the error: "Cannot find mode 1280x1024_60.00"
The second code just goes to a ready Terminal line, doing nothing.

.

Can you post the output of 

```
xrandr
```

again?

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Can you post the output of 

```
xrandr
```

again?

Here it is...

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       75.0*+   75.1  
   800x600        75.0  
   640x480        75.0     60.0  
   720x400        70.1  
  1280x1024_60.00 (0x125)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
```

---

### Post by bradleypariah on 2009-11-04
oooh... :-(

I've got a problem.. either the color bit-depth and/or the frequency are wrong.  The new screen resolution of 1360x768 ***works***, but everything is tinted purple.  I think I need to re-trace all the previous steps trying out different resolutions.  I've got the method now, plus this thread will exist for a great reference.  I've already tried a 1920x1080, but I got errors... (Duh!) I'm almost certain my 5-year-old ATI 9550 can't hang with that.  Poor Linux :-(  It gets all the hand-me-downs... for now. ;-)   I'll keep trying to find a compatible resolution.  Once I've accomplished that (tomorrow) I'll come back to this thread and follow your advice to "make it stick."  

Oh! and yes, the code you just gave me ***does*** immediately change the resolution on my DVI output.  :-)  Just the wrong parameters - which is totally my fault.  I'm feeling so much better about this.  If I have any further issues tomorrow night, I'll post here again.  If I figure it out on my own, I'll see you in the other threads!  Thanks so much.  You rock!
  :guitar:

---

### Post by P4man on 2009-11-04
Ok I think I understand now. You have to add that mode to vga first.

```
xrandr --addmode VGA1 1280x1024_60.00
```

If you run xrandr again it should look neater and have a line like 
 1280x1024_60.00   59.9 

If it does, try changing to the new mode again, or check your change resolution app if it doesnt show up there now.  The other poster did this because he has more than one monitor, but it seems you have to do with also with just one.

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Ok I think I understand now. You have to add that mode to vga first.

```
xrandr --addmode VGA1 1280x1024_60.00
```

If you run xrandr again it should look neater and have a line like 
 1280x1024_60.00   59.9 

If it does, try changing to the new mode again, or check your change resolution app if it doesnt show up there now.  The other poster did this because he has more than one monitor, but it seems you have to do with also with just one.

HOLY **** IT WORKED.

**Now... what've I gotta do to make sure this doesn't go away after I restart?** Also, I'm going to completely wipe my computer free and reinstall 9.10 because I was dual-booting 9.04 with it, just in case this problem persisted. If I follow your directions, will I be able to do this all over again?

BY THE WAY... THANK YOU!!

---

### Post by P4man on 2009-11-04
Bradley, while reading the man page for cvt (the utility to generate those modelines) I saw this:

> -r|--reduced
               Create  a  mode  with reduced blanking.  This allows for higher
               frequency signals, with a lower  or  equal  dotclock.  Not  for
               Cathode Ray Tube based displays though.

I have no idea, but perhaps that is something you could try for your LCD. It would change the modeline to:
```

"1360x768R"   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync
```
Maybe your videocard can handle that ?

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> HOLY **** IT WORKED.

**Now... what've I gotta do to make sure this doesn't go away after I restart?** Also, I'm going to completely wipe my computer free and reinstall 9.10 because I was dual-booting 9.04 with it, just in case this problem persisted. If I follow your directions, will I be able to do this all over again?

BY THE WAY... THANK YOU!!

Yes you will be able to "do it all over again". You will have to next boot anyway.

To  make it stick, see my post #27 ( I think). 

If you want to do it through xorg, I suggest you start a new thread requesting xorg.conf help and specifying the 3 commands you need to make it work with xrandr (one to create the mode, one to add it to VGA, and then to set it). That might also help other users. This thread is becoming quite a mess :)

---

### Post by dylan_newb on 2009-11-04
Ive been following this threadand tried to get ubuntu 9.10 to go to 1024x768 but I'm stuck on 800x 600. I got the option to go to 1024x768 when i did what you said but screen went blank and moniter said unsupported mode. I switched the hard drive to the one i have 9.04 on and booted and its at1024x768 right now. So i know my moniter supports it but 910 wont let me do it.

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Yes you will be able to "do it all over again". You will have to next boot anyway.

To  make it stick, see my post #27 ( I think). 

If you want to do it through xorg, I suggest you start a new thread requesting xorg.conf help and specifying the 3 commands you need to make it work with xrandr (one to create the mode, one to add it to VGA, and then to set it). That might also help other users. This thread is becoming quite a mess :)

So I've gotta create an X folder (as you said in post #27 you think) but where at? And what do I do, just make a .txt file of it?

---

### Post by P4man on 2009-11-04
> **dylan_newb said:**
> Ive been following this threadand tried to get ubuntu 9.10 to go to 1024x768 but I'm stuck on 800x 600. I got the option to go to 1024x768 when i did what you said but screen went blank and moniter said unsupported mode. I switched the hard drive to the one i have 9.04 on and booted and its at1024x768 right now. So i know my moniter supports it but 910 wont let me do it.

Well Im not sure what exactly you did heh. but each monitor is different, what works for posters here may not work for you. Did you create the proper modeline with cvt or only copy pasted the lines from here and changed the resolution? Im guessing the latter and that wont work,

Anyway a sinple reboot would have reverted your settings to what they were. so boot 9.10 again and use a proper modeline for your monitor. You can generate such a line using cvt. Run

```
cvt 1024 768 60
```

Change 60 for whatever refresh rate it can do.

Then you can use the commands I wrote in this thread, but do change the entire modeline!

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> So I've gotta create an X folder (as you said in post #27 you think) but where at? And what do I do, just make a .txt file of it?

No folder. A file. Just create an empty file in your home folder called
.xprofile

and put those commands in there.

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> No folder. A file. Just create an empty file in your home folder called
.xprofile

and put those commands in there.

Sorry to ask but I'm just making sure I've got this right...

So, I need to go to my Home folder, and create a blank FILE and paste those 3 major commands in there? So, I take it I'll have to run that every time I sign back on right?

---

### Post by P4man on 2009-11-04
> **terrorhawk said:**
> Sorry to ask but I'm just making sure I've got this right...

So, I need to go to my Home folder, and create a blank FILE and paste those 3 major commands in there? So, I take it I'll have to run that every time I sign back on right?

Yep. Do rename the file to .xprofile though. The '.' dot at the beginning makes it a hidden file.

Then again, i never tried any of this, so do let me know if it works :) And make sure to test the commands first in a terminal after a fresh boot.

---

### Post by terrorhawk on 2009-11-04
> **P4man said:**
> Yep. Do rename the file to .xprofile though. The '.' dot at the beginning makes it a hidden file.

Then again, i never tried any of this, so do let me know if it works :) And make sure to test the commands first in a terminal after a fresh boot.

I'm definitely going to! Thank you, I appreciate it a lot. I'll reply back to this tomorrow -- for now, I've gotta get some damn sleep lol. If I don't reply back to here, I will PM you instead so that this doesn't get all jumbled again. -__-

THANKS AGAIN!

---

### Post by dylan_newb on 2009-11-04
i think i might be out of screen 
here is my cvt output
```
"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync 
```

---

### Post by P4man on 2009-11-04
> **dylan_newb said:**
> i think i might be out of screen 
here is my cvt output
```
"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync 
```

Out of screen? What does that mean?
anyway I have no clue if what you are trying is correct or not, you havent specified yet what monitor, what videocard and what (if any) drivers you are using.  Start by saying that, and the ouput of xrandr and lets take it from there.

---

### Post by dylan_newb on 2009-11-04
sorry 
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```
```
xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
dylan@dylan-desktop:~$ 

```

---

### Post by t0p on 2009-11-04
Can I make a suggestion?  I think it'd be a good idea if anyone else needs help with this kind of problem, they should start a new thread.  This one has become very unwieldy.

Just a thought.

---

### Post by P4man on 2009-11-04
> **dylan_newb said:**
> 
snip
What monitor do you have?

Anyway if you are sure it can do 1024x768x60 try this:

```
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode 1024x768_60.00
```

If that fails, post the new output for
```
xrandr
```

If that gives an "out of range" error on your monitor, then your monitor doesnt support 1024x768 60Hz, or not without interlacing and I doubt you want that unless you love headaches.

---

### Post by dylan_newb on 2009-11-04
i know its not my monitor because i was running 9.04 at 1024x768 60hz on the same one and its a 32" hdtv but it goes out of range on 9.10. i dont know what to to. maybe   the modeline it gives me is wrong idk but thinking of going back to 9.04 now  thanks for your help

---

### Post by dylan_newb on 2009-11-04
oh ya 
```

xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
   1024x768_60.00   59.9   

```
if you cant help its ok not good at this. new to ubuntu

---

### Post by P4man on 2009-11-04
aaah its for a tv. 
In that case perhaps dont use cvt but gtf to generate the modelines. I cant honestly say I know what the difference is but they produce slightly different modelines. You could also try 50Hz instead of 60.

```
bob3@bob3-desktop:~$ gtf 1024 768 60

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

bob3@bob3-desktop:~$ gtf 1024 768 50

  # 1024x768 @ 50.00 Hz (GTF) hsync: 39.55 kHz; pclk: 51.89 MHz
  Modeline "1024x768_50.00"  51.89  1024 1064 1168 1312  768 769 772 791  -HSync +Vsync






```

but there is probably a far better resolution for that tv.. what tv is it exactly?

---

### Post by HiImTye on 2009-11-04
[LIST=1]
[*]install the proprietary drivers (administration>hardware drivers)
[*]```
sudo nvidia-xconfig
```
[*]```
gksudo nvidia-settings
```
[*]xserver display configuration
[*]change the 'resolution' field to 1280x1024
[*]click on 'save to x configuration file'
[*]uncheck 'merge with existing file'
[/LIST]
if you have issues getting your resolution to 1280x1024 then keep asking here

if you have issues *keeping* your resolution at 1280x1024 then try to finger it out on [my post]("http://ubuntuforums.org/showthread.php?t=1311152")

---

### Post by HiImTye on 2009-11-04
sorry if my instructions don't make sense, I've been drinking

---

### Post by P4man on 2009-11-04
> **HiImTye said:**
> sorry if my instructions don't make sense, I've been drinking

They dont make sense since the posters here all use intel onboard video, not nvidia cards. But cheers :p

---

### Post by HiImTye on 2009-11-04
haha I read 'intel' but my brain was saying 'nvidia'

at least someone knows that I Was an eejiot (too bad it wasnt me :P)

---

### Post by HiImTye on 2009-11-04
> **P4man said:**
> aaah its for a tv. 
In that case perhaps dont use cvt but gtf to generate the modelines. I cant honestly say I know what the difference is but they produce slightly different modelines. You could also try 50Hz instead of 60.

```
bob3@bob3-desktop:~$ gtf 1024 768 60

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

bob3@bob3-desktop:~$ gtf 1024 768 50

  # 1024x768 @ 50.00 Hz (GTF) hsync: 39.55 kHz; pclk: 51.89 MHz
  Modeline "1024x768_50.00"  51.89  1024 1064 1168 1312  768 769 772 791  -HSync +Vsync






```but there is probably a far better resolution for that tv.. what tv is it exactly?
the resolution is generally limited by the resolution of the TV-Out correct? (unless it is using a non-generalized SVideo/RCA/RG6 connection)

---

### Post by P4man on 2009-11-04
> **HiImTye said:**
> the resolution is generally limited by the resolution of the TV-Out correct? (unless it is using a non-generalized SVideo/RCA/RG6 connection)

his xrandr output suggests he is using a VGA cable, not videoout.

---

### Post by HiImTye on 2009-11-04
> **dylan_newb said:**
> oh ya 
```

xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
   1024x768_60.00   59.9   

```if you cant help its ok not good at this. new to ubuntu
does 9.10 use top or bottom for 60hz (i.e. does it use 59+ or 60+ for _60") might be the issue

---

### Post by praveenthivari on 2009-11-04
Can't we solve it with just installing Intel graphic card drivers. 

I have 1440x900 monitor and Karmic could identify the default resolution even without drivers. I have NVIDIA drivers though.

---

### Post by The Cog on 2009-11-04
This thread did get a little unwieldy. Very interesting though.

A script like this might be useful:

```

#!/bin/sh

horiz=1360
vert=768
rate=60
screen=VGA1
modename="$horiz"x"$vert"_"$rate"


mode=$(cvt $horiz $vert $rate | grep Modeline | cut -d ' ' -f 3-)
#mode=$(gtf $horiz $vert $rate | grep Modeline | cut -d ' ' -f 5-)

xrandr --newmode $modename $mode
xrandr --addmode $screen $modename
xrandr --output $screen --mode $modename

```

---

### Post by P4man on 2009-11-04
> **The Cog said:**
> This thread did get a little unwieldy. Very interesting though.

A script like this might be useful: 

Nice idea, I like it  :)

Can you make it smarter by having it discover the screen name(s) from xrander output?

Then again, no one wants to run this script on each boot after getting to the desktop, so it would be nice to test,  but it should actually produce a .xsession script or better yet, a xorg.conf. Are you up to that ? :p

---

### Post by dylan_newb on 2009-11-04
sorry i was watching a movie (jennifer's body) 
i dont know how to test that code
what to save as and how to run
sorry newb here

---

### Post by mbeach on 2009-11-04
> **P4man said:**
> aaah its for a tv. 
In that case perhaps dont use cvt but gtf to generate the modelines. 

Thanks for that tidbit P4Man! Great job assisting here by the way.

---

### Post by The Cog on 2009-11-04
> **P4man said:**
> Nice idea, I like it  :)

Can you make it smarter by having it discover the screen name(s) from xrander output?

Then again, no one wants to run this script on each boot after getting to the desktop, so it would be nice to test,  but it should actually produce a .xsession script or better yet, a xorg.conf. Are you up to that ? :p

The idea of this was that you configure the resolution and the screen you want it applied to at the top of the script, and the lines at the bottom then apply the stated resolution to the stated screen. 

You can leave it as a standalone script by puting it in a file and then marking the file executable (chmod +x *filename*). Then you can just run the script whenver you want that resolution. Make several, with different names, to quickly switch resolutions. Even add one of them to ~/.xprofile so it gets run every time X starts.

Or you can just add it all to the end of .xprofile if you know you will always want that one resolution.

Warning:
I haven't actually tried the script, I just made it up from other posts in this thread.

---

### Post by P4man on 2009-11-04
> **dylan_newb said:**
> sorry i was watching a movie (jennifer's body) 
i dont know how to test that code
what to save as and how to run
sorry newb here

What code?

Before I type it all again, can you tell us the exact type and brand of tv, and confirm if you are using a 15 pin VGA cable (typically blue connectors) straight from the PC to the tv ? This is a VGA cable:
[http://www.unistarcomputer.com/attachedimages/d_2009-10-14-13-3-0f_vga.jpg](http://www.unistarcomputer.com/attachedimages/d_2009-10-14-13-3-0f_vga.jpg)

---

### Post by terrorhawk on 2009-11-04
LOL Booting up the computer today, it defaulted back to 1024, but I made it 1280 again. It screwed up my whole top GNOME panel ahaha. I had to reset everything back to how it was before. Kind of an annoyance, but at least I have 1280.

So... with that being said... where would I go or who would I ask if I were to want to find a way to make this permanent? What would I have to do to make it so that I don't have to manually do this, or will a future Ubuntu fix address this problem?

Anyone know?

---

### Post by The Cog on 2009-11-04
Well, the easiest thing to do would (I think) to add the commands to the end of the file ~/.xprofile so it runs whenever X is started.

---

### Post by terrorhawk on 2009-11-05
> **The Cog said:**
> Well, the easiest thing to do would (I think) to add the commands to the end of the file ~/.xprofile so it runs whenever X is started.

That worked, thank you! When I put it there, and restart, I saw that it flickered a little bit and make the wallpaper look like it was set to 'Tiled' bit it loaded after that.

I hope Ubuntu fixes Intel cards, or that I can at least get a couple bucks and get a decent PCI (I can't have PCI-E on this old computer lol) graphics card with like 256MB of RAM.

---

### Post by kixome on 2009-11-05
Help is here! use a .04 version and never a .10 version

---

### Post by jdier on 2009-11-23
> **bradleypariah said:**
> Okay, the goods:  :-D
```
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```Has the pleasing effect of adding the correct resolution to S-Video
Your new suggestion of 
```
xrandr --addmode DVI-0 1360x768_60.00
```Moved it to my possible resolutions in the Displays window!  Bravo!  :-D

Now... how do I make it stick?  I logged out, and as you mentioned, when logging back in, all of the work is gone.  How can I make this default?

Thank you thank you thank you!  :-D

Yeah baby.  This got me there too.  Still reading to get to the :make it stick part.

---

### Post by FXEF on 2009-11-23
> **jdier said:**
> Yeah baby.  This got me there too.  Still reading to get to the :make it stick part.

Read post# 65.
):P

---

### Post by jdier on 2009-11-25
OK, great.  I added my 3 lines to my ~/.profile (did not have ~/.xprofile) and everything works famously.

Given that .profile is in MY home directory, how can I set it up so any user (or new user) will also have this run?

Do I have to put something in everyone's .profile?

---

### Post by jdier on 2009-12-03
Just checking to see if anyone could give me a shove in the right direction here.

---

### Post by MalTOmeal3 on 2012-07-31
I followed a lot of the instructions on here about getting my xrandr settings correct for my external monitor on my laptop, and I got it to reset automatically at boot doing this:

find the desired modline settings in terminal (example of my settings)

cvt 1280 1024
make a text file as root in usr/share/applications with these xrandr prompts:

[LIST]
[*]xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
[*]xrandr --addmode VGA1 1280x1024_60.00
[*]xrandr --output VGA1 --mode 1280x1024_60.00
[/LIST]

Make it executable in its properties. 
Set as a startup application.

BTW, this was on my Ubuntu 12.04 x64 install.

---

