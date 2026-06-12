---
title: "Strange appearance of text(all programs)"
date: 2010-12-18
forum: General Help
---

### Post by grey1beard on 2010-12-18
This evening, my iPower desktop AMD64, running 10.10, is suddenly inflicted with blanked out letters, like some spotty plague.
I'm attaching a screen shot (I hope).
Any opinions/advice/cures greatly appreciated.
John

---

### Post by lmarmisa on 2010-12-18
This seems the standard Clearlooks theme appearance. Maybe I am not able to see the details of letters. 

Please, check if everything in System -> Preferences -> Appearance is correctly defined.

---

### Post by AlphaLexman on 2010-12-18
Is the problem only in firefox or all applications?

If only firefox, click: Edit -> Preferences -> Content -> Fonts & Colors -> Advanced -> Allow pages to choose their own fonts... [and make the checkbox -> checked]

---

### Post by grey1beard on 2010-12-19
Thanks for the replies.
This morning, having cold booted up, nothing seems amiss, except my memory !
I can't remeber where else I might have been experiencing the problem - it may have only been in Firefox, but I have a feeling it was after an attempt to re-load Rhonda 3d drawing program.
A warm boot last night didn't clear it, but if it happens again, I'll post once more, with more details,
John

EDIT
Opened Firefox - no problems there. Then needed to open a text file I have on the desktop, and there was the same odd appearance. When I clicked on the file to scroll down, the problem disappeared.
If any more instances occur, I'll add them.

---

### Post by grey1beard on 2010-12-29
> **lmarmisa said:**
> ...... Please, check if everything in System -> Preferences -> Appearance is correctly defined.

I've looked here, but I can't tell if anything is amiss. 
In the Font preferences it reads Ubuntu, Sans, Ubuntu, Ubuntu Bold, Monospace, and all the point sizes are 12 point.
The rendering is Subpixel smoothing as I am using an lcd screen and the resolution is set at 96 dots per inch.

AAhh - the resolution figure was highlighted(selected) so I changed it to 95 then back to 96. The highlighting vanished, and so did the effect on the desktop labels.
However, as I write this, the black squares still appear in this thread page.

John

EDIT the last paragraph was a red herring.
The colored squares instead of text still exists in Firefox, and checking back to preferences shows that the resolution always appears highlighted when that window is opened.

---

### Post by grey1beard on 2010-12-30
As I have a dual boot system, I booted into windows xp, but there is no sign of the effect there.
Back now into 10.10, it seems to be getting worse, though that may just be paranoia !
The effect is present on the title bar, and the status bar of the Desktop, though not always, but is most obvious in paragraphs of text.
You can assume that it appears anywhere that there are letters.
At this instant as I type, I looked up from the keyboard, and the black squares have vanished from the body of the text, but are still in the url line!!!
I'll post another screen grab when I've enlarged it to a visible level.

John

---

### Post by grey1beard on 2010-12-30
Lets see if this works.
This is just the url, but I hope it's clear that the black rectangles don't line up exactly with the edges of the letters, but often overlap them

---

### Post by grey1beard on 2010-12-30
Yes, it's definitely getting worse.(see attached)
Now very keen to get some help before I can no longer read the suggestions!
John

---

### Post by grey1beard on 2010-12-30
I've just switched the Fonts rendering to "best shapes" instead of "sub-pixel smoothing, and all the blackrectangles have vanished !
Fingers crossed, this may be it.

---

### Post by lmarmisa on 2010-12-30
Check the fonts configured in Firefox (Edit -> Preferences -> Contents and Advanced). I attach two images showing my configuration. Try to untic the option "Allow pages to choose their own fonts, instead of my selections above" and check if the problem continues.

---

### Post by grey1beard on 2010-12-30
Good Evening Imarmisa, and thank you for the suggestion.
We posted at the same time so you may not have seen mine.
I'll give my trial till tomorrow, then try yours if it re-appears.

Regards
John
No need for me to wait, it's already re-appeared.
So I'll give your method a try.

---

### Post by grey1beard on 2010-12-30
For a moment there it worked, but as soon as I opened the system folder to see what the font setting was for the applications, the problem has re-appeared once again.
Ho hum.
Every time I change a setting of the fonts in System/Preferences/Appearances/Fonts the problem changes, disappears for a couple of minutes, then re-appears as soon as I cause a refresh, open another window, or anything.

---

### Post by lmarmisa on 2010-12-30
Try to disable the visual effects (System -> Preferences -> Appearance -> Visual Effects).

Regards,

Luis

---

### Post by grey1beard on 2010-12-31
Good Morning Luis.
I've switched the effects from Normal to None, restarted Firefox, and await with interest.
John

---

### Post by lidex on 2010-12-31
Try removing your ~/.fontconfig folder, or the contents of. Then reconfigure:
```
sudo dpkg-reconfigure fontconfig
sudo fc-cache -f -v
```
Logout/in

---

### Post by grey1beard on 2010-12-31
Thanks lidex. Looks neat idea, and though not familiar enough yet with what happens at that level, I can see from "what it says on the tin" the logic.

I'll give Luis idea a trial run for today, then if necessary go your suggested route. 
But so far ,so good. It seems to be behaving normally ! 
John

---

### Post by grey1beard on 2010-12-31
I've just done a search for fontconfig folder and found two instances of it.
(I'll post a screen grag of the results if it is any help.)

I also sorted the dates to see if anything corresponded with the time the effect appeared, but nothing is obvious. The last file modification date seems to be at least 7-10 days before I noticed it.

I've added another screen grab showing a different effect which is also occurring, that of lines or blacked out areas of a window.
So I conclude from this that it isn't confined to the rendering of the fonts.
On some pages when it occurs it might be only instances of a single letter, but on some it might be 2 or 3 letters, but every instance on the page.

I now hesitate to try the fontconfig route unless I'm given very precise lines of code for each action. I'm sure you'll understand.

Regards
John

---

### Post by grey1beard on 2010-12-31
Have I got a virus ?
AAAAAAAAAAAAAAAAAAAGGGGGGGGGGGGGGGGGGHHHHHHHHHHHHHHH

---

### Post by lidex on 2010-12-31
Looks to me like a graphics issue. Made any changes in drivers recently? What is this output:
```
sudo lshw -C display
```
```
cat /var/log/Xorg.0.log
```

It resembles this bug report:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532111](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532111)

---

### Post by grey1beard on 2010-12-31
The result of the first line -

john@dragon:~$ sudo lshw -C display

 >  *-display:0             
       description: VGA compatible controller
       product: RV410 [Radeon X700]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:e0000000-efffffff memory:f1000000-f100ffff ioport:a000(size=256) memory:f0000000-f001ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:05:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1010000-f101ffff

The second command produces reams of lines.
Is there a particular set of lines I should look for, rather than post the whole lot ?
I've followed your link to the bug report and there certainly are similarities.
I'll go back and look at in detail.
About to leave house !
John

---

### Post by lmarmisa on 2010-12-31
> **grey1beard said:**
> The result of the first line -

john@dragon:~$ sudo lshw -C display

 

The second command produces reams of lines.
Is there a particular set of lines I should look for, rather than post the whole lot ?
I've followed your link to the bug report and there certainly are similarities.
I'll go back and look at in detail.
About to leave house !
John

This command shows the last 50 lines of the file /var/log/Xorg.0.log:
```

tail -50 /var/log/Xorg.0.log

```

---

### Post by grey1beard on 2010-12-31
Herewith last 50 lines 
> 
[    22.961] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.961] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.961] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.961] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.961] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    22.961] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    22.961] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.961] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.062] (II) RADEON(0): EDID vendor "GSM", prod id 22114
[    23.070] (II) RADEON(0): Using hsync ranges from config file
[    23.070] (II) RADEON(0): Using vrefresh ranges from config file
[    23.070] (II) RADEON(0): Printing DDC gathered Modelines:
[    23.070] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    23.070] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    23.070] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.070] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.070] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.070] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.070] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.070] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    23.070] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.070] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.070] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.070] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.070] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.070] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    23.070] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    23.070] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.070] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    28.793] (II) RADEON(0): EDID vendor "GSM", prod id 22114
[    28.793] (II) RADEON(0): Using hsync ranges from config file
[    28.793] (II) RADEON(0): Using vrefresh ranges from config file
[    28.793] (II) RADEON(0): Printing DDC gathered Modelines:
[    28.793] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    28.793] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    28.793] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.794] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.794] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.794] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.794] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.794] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.794] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.794] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.794] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.794] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.794] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.794] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    28.794] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    28.794] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.794] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)

Does this convey anything useful towards diagnosis ?

John

---

### Post by grey1beard on 2010-12-31
> **lidex said:**
> Looks to me like a graphics issue. Made any changes in drivers recently? What is this output:
```
sudo lshw -C display
```
```
cat /var/log/Xorg.0.log
```

It resembles this bug report:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532111](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532111)

Re the bug report, I followed the link and read other posts for that bug and what was posted as a duplicate. I noticed that they both referred to nvidia graphics, but as you can see, mine is a Radeon card.
As I type this there is no evidence of the garbage. I've just spend about 20 minutes looking at videos of New Year celebrations via the BBC web site, and realised that there were no signs of the problem.
I'll wait to see how long it takes to reappear.
Re new drivers - none that I can think of, but then short term memory ???
Where/how do I find a log of what I might have installed in the last 15 days ?

John

---

### Post by lidex on 2010-12-31
In case you need it,
These versions probably more helpful:
```
cat /var/log/Xorg.0.log | grep EE
```
```
cat /var/log/Xorg.0.log | grep WW
```
Also running compiz-check, use the link in my sig.

More info on ati drivers here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by grey1beard on 2011-01-01
Happy New Year from this side of the pond.
I've had a quick look at the Compiz link and will follow that up later today.
I tried the lines of code, and got the following -

> john@dragon:~$ cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.236] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.279] (WW) Falling back to old probe method for vesa
[    18.279] (WW) Falling back to old probe method for fbdev

> john@dragon:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.251] (II) Loading extension MIT-SCREEN-SAVER

John

---

### Post by grey1beard on 2011-01-01
Lidex - I've run the compiz-check and got an OK on all counts(4).

John

---

### Post by lidex on 2011-01-01
Do you have an xorg.conf file:
```
cat /etc/X11/xorg.conf
```

---

### Post by grey1beard on 2011-01-01
> **lidex said:**
> Do you have an xorg.conf file:
```
cat /etc/X11/xorg.conf
```

> No such file or directory

Had to copy/paste your line of code, as half of it was blacked out !!
John

---

### Post by lidex on 2011-01-01
OK. Some have had success using the "nomodeset" kernel option. This link explains how:
[http://www.uluga.ubuntuforums.org/showpost.php?p=9642841&postcount=43](http://www.uluga.ubuntuforums.org/showpost.php?p=9642841&postcount=43)

---

### Post by grey1beard on 2011-01-01
I've followed the "nomodeset" instructions, and at this instant the screen is clean and looks normal.
I'll post again in a few hours to conform, or otherwise.
John

---

### Post by grey1beard on 2011-01-01
After a couple of hours there is still no sign of the black plague.
There is a residual effect, most visible in the background of small graphics, but also occaisionally in amongst text of small black dots.

Whatever this is, and I assume it's a separate issue, I can live with it.

Many thanks lidex for all your help, and I shall mark this thread as solved.
Regards
John

---

### Post by lidex on 2011-01-01
You're welcome. Happy New Year and good luck.

---

### Post by grey1beard on 2011-02-07
Well, it's now into February, and the problem has reappeared and seems to be getting worse, so I've "Unsolved" the thread as it contains the route I've taken so far.
However, I can now attach an updated sgreen grab of the effect, and hope that someone can give me more guidance.
Regards
John

---

### Post by grey1beard on 2011-02-10
I've now got to the stage where Ubuntu was virtualy unreadable, so I checked windows.
That now also shows signs, so I assume that it is the video card which is the source of the problem.
When I've found a replacement, I'll post the results.

---

### Post by grey1beard on 2011-02-10
Just to see what might happen, I went back to lidex #29, and tried the nomodeset instructions on that link.
However this time, after typing sudo gedit /etc/default/grub 
I got  (gedit:1605): Gtk-WARNING **: cannot open display:

---

### Post by grey1beard on 2011-02-12
Started to look for replacement cards on ebay, and noticed that most cards are now pci-e, and had fans on them.
So not knowing what my sockets were, I took the covers off.
Guess what. PCI-e card with fan, and with a couple of years' crud - dirt plus unidentified no-longer-flying objects.

Now have nice clean card, and screen with only small amount of spotting, which I can live with (see earlier post).

I suspect that this effect may be inefficient driving for my wide screen, so I'll wait to see if the spring clean has had a permanent effect.
I had seen a marked deterioration in the screen during a long session, till it decided not to go beyond a completely black screen with only the mouse icon showing.

If today's session produces no further worsening, I'll mark this solved. If not then it's off to buy a replacement.

John

---

### Post by grey1beard on 2011-02-12
A bit more info before I finally spend some cash.

The curious spottiness has a characteristic that might point to a cause, but which I can't decipher.
If you look carefully at my latest screen grab attached, you will see that the "spots" only appear in specific places.

In the opened Evolution window, all the graphics icons have a background of spots, and so do the frames(is that what they're called?) at the top of the right hand pane, and the bottom of the left hand pane.
The text itself doesn't seem to be affected, and this seems to be true in Firefox as well. The graphics have the spots, but the text doesn't.

If anyone reading this has any thought as to what is happening, please contribute.

John

---

### Post by grey1beard on 2011-02-13
I've now found a website [www.playtools](www.playtools) .com that shows examples of failing video cards, and sure enough, there are the same symptoms.
"Video ram failing".
Problem identified, and cash will solve problem.

John

---

