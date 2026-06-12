---
title: "Use pen tablet to draw on the top of the screen"
date: 2011-07-28
forum: General Help
---

### Post by Macrotus on 2011-07-28
Hi

I have Wacom Bamboo Fun Pen & Touch pen tablet and I'd like to use it to draw on the top of the screen.. For example if I have Evolution opened on the screen, I want use my pen tabled to draw with freehand on the top of Evolution. Did you understand?

Is there any small application which allows to do that?

---

### Post by Mark Phelps on 2011-07-28
I used to use my tablet PC with Ubuntu, and the answer was NO.

Drawing on screen is similar to typing on screen -- the app must support that activity.  You can't simply type onto the desktop, so it makes sense that you can't draw onto it, either.

---

### Post by turtle153 on 2011-07-28
I'm not sure what you mean by top. The **top half of the screen** or **above all applications**. If you mean the latter then I made a quick tutorial: [http://ubuntudaily.blogspot.com/2011/07/use-compiz-to-annotate-your-screen.html](http://ubuntudaily.blogspot.com/2011/07/use-compiz-to-annotate-your-screen.html)

---

### Post by Favux on 2011-07-28
You also might want to check out Ardesia:  [http://code.google.com/p/ardesia/](http://code.google.com/p/ardesia/)

---

### Post by Macrotus on 2011-07-28
Tanks turtle153, that's what I wanted.

I'm having troubles with my Wacom Bamboo Fun Pen & Touch and Ubuntu 10.04 LTS. How I can get them work?

---

### Post by Favux on 2011-07-28
See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Macrotus on 2011-07-28
Thanks

I got the tablet working, but the pen doesn't. When I take the pen close to the tablet, the cursor disappears. I didn't get the step 2 working.

---

### Post by Favux on 2011-07-28
Since you're using Lucid did you update the xorg-macros before compiling xf86-input-wacom?

---

### Post by Macrotus on 2011-07-28
I ran the command "sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak", and it says that /usr/share/aclocal/xorg-macros.m4 doesn't exists.

---

### Post by Favux on 2011-07-28
That's just to make a back up of the default version.  I put that in early.  Should probably remove it since there hasn't been any problem with updating the macros and so no need to restore the default version.  So ignore it.

---

### Post by Macrotus on 2011-07-28
Thanks.

> ./autogen.sh --prefix=/usr

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:45: error: xorg-macros version 1.8 or higher is required but 1.5.0 found
/usr/share/aclocal/xorg-macros.m4:39: XORG_MACROS_VERSION is expanded from...
configure.ac:45: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1

What's this?

---

### Post by Favux on 2011-07-28
It's saying your update of xorg-macros from version 1.5 to 1.8 didn't work.  So you need to redo that.  Let me know if you're seeing errors other than the copy one.  You can show me your output.

---

### Post by Macrotus on 2011-07-28
All the previous commands were performed successfully without any errors.

Is there any alternative way to update xorg-macros?

---

### Post by Favux on 2011-07-28
Maybe someone has made a PPA for it, say on the Xorg edgers launchpad site or something.  I don't know.

It shouldn't be this hard.  The instructions do work.  But you're not giving me enough information to spot where you are having your problem.  Give me everything in the terminal from start to where you are having your problem.

---

### Post by Macrotus on 2011-07-29
I don't have the results saved so I can't give them to you.

I'm 100% sure I did exactly what you said in your tutorial and there wasn't any errors before that (except that copy error which you said I can skip).

I remember it said that some of those packages was already installed, because I tried another tutorials to get it work.

---

### Post by Favux on 2011-07-29
Alright, but it is easy enough to check.  Look in /usr/share/aclocal for xorg-macros.m4.  Right click on and check Properties.  Is the date the same as the date when you compiled it?  Is it the same size and date as the one in the util-macros-1.8.0 folder?

---

### Post by Macrotus on 2011-07-29
No. /usr/share/aclocal/xorg-macros.m4 is smaller and older than the util-macros-1.8-0's file. Should I copy the file from util-macros-1.8-0 to the aclocal folder or what?

---

### Post by Favux on 2011-07-29
Yes.  Something went wrong so just manually copy the macros into place.  Then the compile of xf86-input-wacom should go OK for you.

---

### Post by Macrotus on 2011-07-29
Now the tablet and the pen are working, but I'm wondering how to change the physical button's commands in the tablet and in the pen.

Because when I want to draw on the top of the screen (over the applications), I always need to press CTRL + Windows-logo + ALT and mouse button 1 (It's enough to press the table with the pen) and move the pen/mouse. How I can change the settings so that I can draw when I press the table's button 1 and move the pen on it? Eraser should work with button 2 and pen and erasing the full screen happens when pressing button 3.

Edit. How about the pressure levels? Should they work?

---

### Post by Favux on 2011-07-29
Great!  Nice job.

If you are using the Compiz plug-in annotate isn't it just alt+Super?

So you determine the "device name" for the pad using *xinput list* in a terminal.  Then it would be something like:
```
xsetwacom set "device name" Button 1 "key alt Super_R"
```

Yes pressure should be working.  Have you configured the extended input devices in Gimp etc.  See the screen shots on the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by Macrotus on 2011-07-29
I changed the keys to CTRL + Windows-logo + ALT but I took CTRL away. 

I ran xinput list and I got this

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech Illuminated Keyboard  	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Pen stylus      	id=18	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Pen eraser      	id=19	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Finger touch    	id=20	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Finger pad      	id=21	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech Logitech Illuminated Keyboard  	id=8	[slave  keyboard (3)]
    &#8627; HID 0a5c:4502                           	id=11	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0	id=13	[slave  keyboard (3)]
    &#8627; UVC Camera (046d:0821)                  	id=16	[slave  keyboard (3)]

```

The I ran

> xsetwacom set "Wacom BambooFun 2FG 6x8 Finger pad" Button 1 "key alt Super_R"

Nothing happens. 

Button 1 is left click, button 3 is right click, button 4 is back and button 2 doesn't do anything that I could recognize.

---

### Post by Favux on 2011-07-29
Try Super_L instead of _R.  You installed the wacom.ko from input-wacom, correct?

---

### Post by Macrotus on 2011-07-29
I tried also _L, no difference. /lib/modules/2.6.32-33-generic/kernel/drivers/input/tablet contains wacom.ko so yes I, installed it.

---

### Post by Favux on 2011-07-29
Shoot.  I think with input-wacom the button assignments for 1 through 4 are 1,2,3,8 so that isn't the problem.

It's probably just using the key name is causing a press and release (+/-) by default.  And we want to keep a press.  Hmmm.  Let's try changing it to:
```
"key +alt +Super_L"
```

---

### Post by Macrotus on 2011-07-29
It doesn't change anything. I'm wondering why the button works as it worked before those changes. Should it break and stop working?

---

### Post by Favux on 2011-07-29
Not sure what you are asking.

This is bringing up vague memories about the tablet buttons (their xsetwacom implementation) not holding a press like the keyboard can.  There was a discussion about this somewhere.  I can't remember if they figured it out.  I'll have to see if I bookmarked it somewhere. Finding it could take quite a while.

---

### Post by Favux on 2011-07-29
Got lucky and found it fairly quickly.

According to this discussion:  [http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTimw_EbMcV%2B3Kw15BwWUG9OyJRwSY_b81t%3D2Aiyo%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTimw_EbMcV%2B3Kw15BwWUG9OyJRwSY_b81t%3D2Aiyo%40mail.gmail.com&forum_name=linuxwacom-discuss)  we should have it right or close to right anyway.  So I'm not sure what's wrong.

---

### Post by Macrotus on 2011-07-29
I don't know how that should help me with my issue. Thanks for reply anyway.

No luck with using id instead of the device name. Do you know any way to test which keys the user (in this case me) is pressing? It could help me to find out what's wrong.

---

### Post by Favux on 2011-07-29
No that's a major pain.  If you don't recognize what the button is doing on default you can't guess what number it has and you have to test them one by one.  They wrote over my little section on that on the mediawiki, but I still have a little bit on it on the BambooPT HOW TO in part V.  That gives you the button numbers and what the corresponding X numbers do, at least the ones I know about.

---

### Post by Macrotus on 2011-08-01
I didn't get the buttons work like I wanted, but I don't care. It's not so highly needed that I'd spend the whole year for this.

Can I now delete the folders from desktop, or is there something which is needed? I hope those commands didn't install the functionality on the desktop!

---

### Post by Favux on 2011-08-01
Nope, just used the Desktop as a working directory so you could see and find things easily.  You can delete them or move them elsewhere.  With a kernel update you'll need to run the input-wacom one again to compile a wacom.ko for the new kernel so you might want to keep that one around, at least until it is replaced by a new version.

---

