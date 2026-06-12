---
title: "Ubuntu on Thinkpad x200 Tablet...?"
date: 2010-10-16
forum: General Help
---

### Post by vickoxy on 2010-10-16
Hi,
i woul like to buy thinkpad x200 tablet. I wan to know how good does Ubuntu works on it. Especially these things:

1) Screen Rotation (auto or manually?)
2) Finger Gestures (not interested in Multitouch, just simple finger input)
3) Handwriting recognition software (not so important now, because in this thread i found there is nothing similar to the Windows 7 Recognition: [http://ubuntuforums.org/showthread.php?t=1586799](http://ubuntuforums.org/showthread.php?t=1586799)
4) any useful virtual keyboard for Tablet-Display Mode?
5) add other things :) i should know...

---

### Post by imraj on 2010-10-16
I have Lenovo X200 Tablet and recently installed Ubuntu 10.10 on exactly 10-Oct.

Everything seems to be working fine EXCEPT the following:
1. The screen rotation is Manual.
2. The PEN is not working except the normal click function; right-click does not work.

Since I m not good at unix; eventhough I tried MouseGesture utility but 'am unable to configure that to make pen working.
 
Let me also know if u find some solution to the above issues.

---

### Post by vickoxy on 2010-10-16
What do you mean by "Manual rotation"-button or something else?
E.G by Web Surfing-can you open a site with finger clicking on it, or not?

---

### Post by luisito on 2010-10-16
I have the X201 that is pretty much the same.

The touchscreen and stylus worked out of the box on 10.04, but without multitouch. I've just upgraded to 10.10 and nothing seems to have changed.

The screen rotation button on the screen doesn't do anything. I set up a launcher on the desktop to a script from here
[http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)

There is a program called cellwritter that does handwriting recognition. But it is not as effective as its Windows counterpart. it also includes an complete on screen keyboard.

There is also an on screen keyboard with larger keys but missing a few (PgDn, Home, and such) called onboard. Both on screen keyboards work well as you would expect.

There is a great program called Xournal to take notes with the stylus. You can even write notes on top of a PDF file, which makes it very very useful for proofreading your own articles.

Everything else just works out of the box.

---

### Post by vickoxy on 2010-10-16
Thanks for answer. I will probably make dual boot installation of 10.04 LTS.
Ok, so how does you rotation script work? I mean, how do you rotate the screen then?
Another question would be-for browsing, is there right-mice click possible to open new tab? (or something like that)?

Thanks again-....

---

### Post by luisito on 2010-10-16
To rotate the screen I press (with the mouse, stylus or my finger) the launcher that is on my desktop that runs the script from the howto page. It should be possible to map the button on the screen to that same screen, but I haven't investigated how to do it yet.

To open another tab when browsing you just click the button with the "+". In Firefox it's large and easy. In Chromium it's smaller and not hard to miss your clumsy fingers. I think it has a better precision after the upgrade to 10.10. It's hard to say though. I used to have more trouble hitting small buttons with my fingers or even scrolling. I don't see a reason not to go for the 10.10 release. Supposedly, it should be possible to enable multitouch gestures in 10.10, but I couldn't figure out how yet (it didn't work out of the box with the upgrade at least).

---

### Post by vickoxy on 2010-10-16
So, it seems that i should install Ubuntu on X200t if i buy it. For the missing handwriting recognition i should probably use windows 7 - hopefully there will be some useful solution in the near future in ubuntu world.

One question more, not only for you luisito :popcorn:, - i can not decide should i go with x200 or x200t. Tablet seems to be bulkier and havier, but on a daily use, is it so portable and nice to use as regular x200/x201. I mean, should i go for tablet (x200t) or "normal" notebook (x200t)?

Thanks

---

### Post by vickoxy on 2010-10-30
Hi,
i bought x200t. I can rotate screen with one button on the screen, but my stylus/pen is useless-the cursor is about 10 cm away from the pointing direction. Does anyone knows how to fix this. So, i would like to use xournal to make simple notes, rotate screen and use a pen...
Thanks

---

### Post by supr0 on 2010-12-01
Hi Vickoxy,

I got the X201T and have no problems with 10.10 with cursor pointing, it worked out of the box. Maybe distupgrade to 10.10?

How did you get screen rotation to work? You say a button on the screen, do you mean you use display drop-down on the panel bar at the top of the screen?

What about the button on the screen itself? Does anyone know how to map this to screen rotate?

---

### Post by vickoxy on 2010-12-01
Hi,
thanks for replying-i forgot this thread. Well i found solution by adding to startup stylus.sh:

```
#!/bin/bash
# Remap the side button to bring up context menu.
xsetwacom set "Serial Wacom Tablet" Button1 "button 1"
xsetwacom set "Serial Wacom Tablet" Button2 "button 3"
# Fix the "Serial Wacom Tablet eraser" button to paste
xsetwacom set "Serial Wacom Tablet eraser" Button1 "button 2"
```

and appointed to rotate button on display this .sh:

> #!/bin/bash
# Won't work if the display is something other than 1024x768
# Won't rotate if external monitor is connected

killall conky  
sleep 20 && conky &

orientation=`xrandr -q | grep -c 1280x800`
if [ $orientation -eq 2 ]; then
   /usr/bin/X11/xrandr --orientation right
   xsetwacom set "Serial Wacom Tablet" Rotate CW
   xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
else
   /usr/bin/X11/xrandr --orientation normal
   xsetwacom set "Serial Wacom Tablet" Rotate NONE
   xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
fi
killall conky


So, i am happy now with note taking. Just hoping that we will see soon some good handwriting recognition app...

---

### Post by TheJackal12 on 2011-01-01
I just purchased a Thinkpad x200t. Everything is working right now, except the rotate function. Pressing the rotate button on the display rotated the display, but did not rotate the stylus.

After using the script from above:
```
#!/bin/bash
# Won't work if the display is something other than 1024x768
# Won't rotate if external monitor is connected

killall conky
sleep 20 && conky &

orientation=`xrandr -q | grep -c 1280x800`
if [ $orientation -eq 2 ]; then
/usr/bin/X11/xrandr --orientation right
xsetwacom set "Serial Wacom Tablet" Rotate CW
xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
else
/usr/bin/X11/xrandr --orientation normal
xsetwacom set "Serial Wacom Tablet" Rotate NONE
xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
fi
killall conky 
```

```
#!/bin/bash
# Won't work if the display is something other than 1024x768
# Won't rotate if external monitor is connected

killall conky
sleep 20 && conky &

orientation=`xrandr -q | grep -c 1280x800`
if [ $orientation -eq 2 ]; then
left
xsetwacom set "Serial Wacom Tablet" Rotate CCW
xsetwacom set "Serial Wacom Tablet eraser" Rotate CCW
else
/usr/bin/X11/xrandr --orientation normal
xsetwacom set "Serial Wacom Tablet" Rotate NONE
xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
fi
killall conky 
```

```
#!/bin/bash
# Won't work if the display is something other than 1024x768
# Won't rotate if external monitor is connected

killall conky
sleep 20 && conky &

orientation=`xrandr -q | grep -c 1280x800`
if [ $orientation -eq 2 ]; then
/usr/bin/X11/xrandr --orientation inverted
xsetwacom set "Serial Wacom Tablet" Rotate HALF
xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
else
/usr/bin/X11/xrandr --orientation normal
xsetwacom set "Serial Wacom Tablet" Rotate normal
xsetwacom set "Serial Wacom Tablet eraser" Rotate normal
fi
killall conky 
```
It worked. To have it rotate counter clockwise and inverted, I changed the appropriate values.

I saved the three files (made executable) into my documents folder. To launch them, I mapped two of the buttons on the tablet display by going to System -> Preferences -> Keyboard Shortcuts and clicking "Add" (The "command" is the location of the file, i.e. /home/user/Documents/CW.sh). For some reason, it won't let me map the first button (rotate by default) or the last one (lock screen). To map the third script, I used "Control + one of the two tablet buttons". 

I thought I would post this here for future reference and people searching x200t or x200 tablet because I didn't find a "How To Guide" for the x200t. Thank you very much for the above scripts (I didn't use the first script provided though).

---

### Post by anthony_barker on 2011-01-11
New x200 tablet user - rotation working, touch working... stylus buttons don't click..
> 
xsetwacom -v --list dev
... Display is '(null)'.
... 'list' requested.
...

... Found device 'Serial Wacom Tablet stylus' (15).
Serial Wacom Tablet stylus STYLUS    
... Found device 'Serial Wacom Tablet eraser' (13).
Serial Wacom Tablet eraser ERASER    
... Found device 'Serial Wacom Tablet touch' (14).
Serial Wacom Tablet touch TOUCH    

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=14	[slave  pointer  (2)]
.

tried xsetwacom set "Serial Wacom Tablet stylus" Button1 "button 1"

.... didnt seem to work...

Any ideas?

---

### Post by Favux on 2011-01-11
Hi anthony_barker,

Button1 is by default the stylust tip and is set to 1 or Button 1.  Button2 and Button3 are the stylus buttons and they can be set to either 2 - middle click or 3 - right click.

---

### Post by noah++ on 2011-01-11
If your tablet supports multitouch, then multitouch does work with it, just not very well. It's very aggravating -- so hard to get the gestures right that it robs them of all their convenience. But that it works at all shows that there is hope. I've been in touch with the developers too on this forum. They seem active and responsive.

---

### Post by anthony_barker on 2011-01-12
Thanks - figured it out...

this page was helpful

[http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus]("http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus")

I have to say the main thing I am missing from a meego or a windows 7 style browsing experience now is gestures - or "flicks in Win7".

Xournal works fine for basic pdf annotation (like on the n900).

Although the win7 handwriting recognition is impressive I find it easier to simply type. Win7 integrates the tablet features badly - especially the floating keyboard thing.


One last question - my finger touch seems to be off by a bit - is there anyway to easily fix?

---

### Post by Favux on 2011-01-12
Hi anthony_barker,

Good!
> I have to say the main thing I am missing from a meego or a windows 7 style browsing experience now is gestures - or "flicks in Win7".

Use Tom Jaeger's EasyStoke.

> Win7 integrates the tablet features badly - especially the floating keyboard thing.
You could try CellWriter.  In addition to letter recognition it offers a keyboard.

> One last question - my finger touch seems to be off by a bit - is there anyway to easily fix? 
You could use xinput_calibrator.  I don't know if the PPA includes your release so you might have to compile it.  Then when you get the touch coordinates from it place them in a xsetwacom startup script using the xsetwacom commands for TopX & Y and BottomX & Y.

---

### Post by anthony_barker on 2011-01-12
Thanks - and the grab and drag firefox plugin works well too

[http://grabanddrag.mozdev.org/]("http://grabanddrag.mozdev.org/")

---

### Post by Favux on 2011-01-20
Hi guys,

I just added the ThinkPad X201t's to [Magick Rotation]("http://ubuntuforums.org/showpost.php?p=10376535&postcount=37").  I'd love to have an X200t confirm it works for them.  Or any ThinkPad X for that matter.

The link takes you to a preview version of 1.3.  Magick also let's you toggle touch on and off, choose screen orientation in tablet mode, and run shell commands before and after changing to tablet mode.  The shell commands can show CellWriter, or whatever onscreen keyboard you use, in tablet, enlarge panel size to make them more touch friendly, etc.

Magick Rotation is at:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by nikosm on 2011-03-12
Hi Favux!

I can confirm that magick-rotation works well with a Lenovo X200t and 10.10 . In fact, it fixed a problem that was bugging me for a while (see [this post]("http://ubuntuforums.org/showpost.php?p=9996058&postcount=1")). This problem seems to have broken my suspend at some point, which is also fixed by your code - yay! :)

Only two remarks:
 - first time I ran the script, it broke the left-click, i.e. I could only right click by tapping with the stylus button pressed. That was also the case for the trackpoint, only right-click worked. After restarting everything was normal though, and later when I suspended everything was still fine.
 - the tooltip on the green arrow says "Loading..." . Is that normal/intended?

Thanks again for your dedication and excellent work!!

Nikos

P.S. Btw, any news on calibration? I read somewhere that wacompl is not available for 10.10 . My stylus loses accuracy on the edges (but works fine in the middle of the screen).

---

### Post by Favux on 2011-03-12
Good!
> the tooltip on the green arrow says "Loading..." . Is that normal/intended?
No, it should say "Normal mode" or "Tablet mode" depending on whether you are rotated or not.  See if that shakes out after a few restarts, etc.
> Btw, any news on calibration? I read somewhere that wacompl is not available for 10.10 . My stylus loses accuracy on the edges
No not yet.  jayhawk's concern is the python module we'd need to use for it might not be getting the needed support into the future and he doesn't really want to write it in C.  You could try [xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator") in the meantime.

---

### Post by nikosm on 2011-03-14
> **Favux said:**
> 
No, it should say "Normal mode" or "Tablet mode" depending on whether you are rotated or not.  See if that shakes out after a few restarts, etc.

Yes, it's working fine now. Btw, I can reproduce the left-click crashing problem I mentioned - it occurs when I disable touch by touching the green arrow. Then, left click of stylus and trackpoint are disabled, but come back when touch is reenabled e.g. from the command line. Disabling touch by stylus/trackpoint doesn't cause this problem.

> **Favux said:**
> 
You could try [xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator") in the meantime.

Thanks for the tip. I have 64 bit 10.10, so I'd need to build by myself, I installed git-core but when I run ./autoconf.sh I get an error
```

...
checking for XINPUT... no
configure: error: Package requirements (x11 xext xi inputproto) were not met:

No package 'xi' found

```

Any ideas? 

thanks again,
Nikos

---

### Post by Favux on 2011-03-14
Hi Nikos,

I'm going to guess you need:
```
sudo apt-get install libx11-dev libxi-dev x11proto-input-dev
```
> Btw, I can reproduce the left-click crashing problem I mentioned - it occurs when I disable touch by touching the green arrow. Then, left click of stylus and trackpoint are disabled, but come back when touch is reenabled e.g. from the command line. Disabling touch by stylus/trackpoint doesn't cause this problem.
Hmm.  That one I don't get.  I'll look at that some more but I think I'll need to get the boss to take a gander.

---

### Post by Kate the Enthusiast on 2011-04-07
Hello everybody!

how can I get the scripts from the first post?
I can see their names underlined but there are not links for me.

---

### Post by vickoxy on 2011-04-07
What scripts do you need? I can copy here my scripts...

---

### Post by Kate the Enthusiast on 2011-04-08
> **vickoxy said:**
> What scripts do you need? I can copy here my scripts...

Thank you, at first I have not figured out that the scripts are at the end of the post. But now I have got the scripts.

I have the i-pod like screen, and as it has been mentioned, it looks like the scripts dont work for my model.

So I have upgraded myself to 11.04 beta and two of the screen buttons start to work out of box:

the one with "restart" picture (makes rotation, but without mouse again) and the last one with the lock (calls logout).

---

### Post by anthony_barker on 2011-04-18
Anyone try 11.04 yet?

---

### Post by OblongShape on 2011-05-03
Hi everybody,

I upgraded  from Ubuntu 10.10 to 11.04 on my Thinkpad X200 Tablet. Everything that used to work under the 10.10 still works.
 I had been struggling for two years to fix my screen rotation's issue and I was surprised to find out the scripts and the link to "Magic-rotation" cited above. However, after I installed the latter yesterday, I still have a problem with the pen rotation: the screen amazingly rotates automatically when I go to tablet mode, but the cursor goes far away from the stylus. 
I would appreciate if someone could help me fix out this.

Thanks in advance.

---

### Post by Favux on 2011-05-03
Hi OblongShape,

We are working on updating Magick Rotation for Natty.  There are several issues.  Hopefully we'll be able to release the fixes in a v. 1.4 fairly soon.

In the meantime you could try the fix suggested in this bug report:  [https://bugs.launchpad.net/magick-rotation/+bug/744274](https://bugs.launchpad.net/magick-rotation/+bug/744274)

---

### Post by OblongShape on 2011-05-03
Hi Favux,

Thank you for the reply. I already tried the solution suggested by "es128" (cf. the link you just mentioned above), everything is working now and I'm happy :-).
Maybe I should quote es128 here for the those who may have the same problem:

[I]1. Delete the magick-rotation folder in my home directory, then re-extract the archive to there in order to get a fresh start
2. In xrotate.py, changed lines 110, 111, and 200 to switch "cw" and "ccw"
3. Run magick-rotation in order to run the installer[/I]


thanks again!

---

### Post by anthony_barker on 2011-09-26
Interesting discussion of the linux table over here

[http://lwn.net/Articles/455891/]("http://lwn.net/Articles/455891/")

---

### Post by anthony_barker on 2011-09-26
Interesting discussion of the linux tablet over here

[http://lwn.net/Articles/455891/]("http://lwn.net/Articles/455891/")

---

