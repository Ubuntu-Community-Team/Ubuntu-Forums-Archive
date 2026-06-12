---
title: "Most Ancientest Computer Ever"
date: 2009-12-31
forum: General Help
---

### Post by Dorrax on 2009-12-31
I have recently been given a 10 year computer. I need a computer to run my TV so I can TV over the internet because cable is too expensive. It has a video card with s-video output, which is what my TV uses. 

However, I have run up against some problems I don't know how to solve. I managed to get ubuntu 9.1 installed, but it doesn't recognize the TV. I know the card works because the screen comes up on the TV when I turn on the computer, but goes away when it starts to boot the OS. This also happened with my wireless USB keyboard and mouse. They worked when working with the BIOS, but stopped when ubuntu loaded. I tried with a wired USB mouse, it also failed. I had to search to find a mouse and keyboard with PS2 plugs, which is harder than you'd think.

How do I get ubuntu to recognize my s-video at least? Getting the USB keyboard and mouse to work would be nice too.

SOLVED: s-video instructions here: [http://ubuntuforums.org/showthread.php?t=1327437](http://ubuntuforums.org/showthread.php?t=1327437)

Fixed USB by searching through the BIOS.

---

### Post by Dorrax on 2009-12-31
Now that I look a little harder, I don't think any of the USB ports are being recognized. I plugged in a flash drive with a power light, and it doesn't get any power. Again, it works before the OS boots up, then stops after booting.

---

### Post by judge jankum on 2009-12-31
This old thing I'm on now is 12 years old,TV works great with 8.04 so I know it should work.

---

### Post by Dorrax on 2009-12-31
On what is probably an unrelated matter, my "sound system" just quit. By sound system I mean the FM transmitter I have plugged into what I think is the sound card that broadcasts to my radio.

I'm not working with much here.

---

### Post by judge jankum on 2009-12-31
Do you do live FM radio?

---

### Post by Dorrax on 2009-12-31
No, I just haven't had time to buy real computer speakers, so I was using the FM transmitter I use with my MP3 player in my car. It started working again when I unplugged and plugged it back in. I hate that because it probably means that it isn't really fixed.

---

### Post by dcstar on 2009-12-31
> **Dorrax said:**
> I have recently been given a 10 year computer. I need a computer to run my TV so I can TV over the internet because cable is too expensive. It has a video card with s-video output, which is what my TV uses. 

However, I have run up against some problems I don't know how to solve. I managed to get ubuntu 9.1 installed, but it doesn't recognize the TV. I know the card works because the screen comes up on the TV when I turn on the computer, but goes away when it starts to boot the OS. This also happened with my wireless USB keyboard and mouse. They worked when working with the BIOS, but stopped when ubuntu loaded. I tried with a wired USB mouse, it also failed. I had to search to find a mouse and keyboard with PS2 plugs, which is harder than you'd think.

How do I get ubuntu to recognize my s-video at least? Getting the USB keyboard and mouse to work would be nice too.

For USB devices your BIOS needs to support the modern options - check if there are any settings you can change.

---

### Post by judge jankum on 2009-12-31
Maybe someone here can help with those issues..
 We have to transmit through a radio station to the troops in Iraq/Afg....I got excited there for a minute lol!!!!

---

### Post by Dorrax on 2009-12-31
> **dcstar said:**
> For USB devices your BIOS needs to support the modern options - check if there are any settings you can change.

What are the modern options I should look for?

UPDATE:

The USB stuff works now. Checked the BIOS, for some reason the USB controller was set to all disabled.

Still no luck on s video output. Not sure what video card i have, other than an ATI.

---

### Post by mr clark25 on 2010-01-01
i know xrandr will show you what its capable of...
command:
xrandr

i know that probably wont help much, but it might help some. at the top (second line) it will show you what the current video output method is. at the bottom, it will show you what other output options you have.
here is my output from xrandr:

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 2480 x 1050
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
VGA-0 disconnected (normal left inverted right x axis y axis)


first line: min, current, and max resolution
second line(may carry over into 3rd line): current output method
lines 4-10: resolution options
last lines: other display output methods. 

somewhere near the end, you should have something about s-video.
ubuntu doesnt support older ati cards to well, so good luck

---

### Post by Dorrax on 2010-01-01
> **mr clark25 said:**
> i know xrandr will show you what its capable of...
command:
xrandr

i know that probably wont help much, but it might help some. at the top (second line) it will show you what the current video output method is. at the bottom, it will show you what other output options you have.
here is my output from xrandr:

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 2480 x 1050
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
VGA-0 disconnected (normal left inverted right x axis y axis)


first line: min, current, and max resolution
second line(may carry over into 3rd line): current output method
lines 4-10: resolution options
last lines: other display output methods. 

somewhere near the end, you should have something about s-video.
ubuntu doesnt support older ati cards to well, so good luck

Ok, i see my disconnected s-video in xrandr, what command do I need to make it work? Tried looking in the man pages, but I'm not good at understanding them...

---

### Post by northrup on 2010-01-01
Have you tried starting your computer with both a regular computer monitor and the TV connected?  In my experience, display settings will only be correctly applied to one video signal, not both.  Ubuntu will likely prioritize your standard monitor output over your S-Video output, and therefore only display to a "primary" display.  I had the same issue when connecting an HDTV to an Ubuntu PC, except the inverse happened: Ubuntu targeted my TV because it uses a DVI connection, and my monitor's VGA connection was considered "secondary".

---

### Post by Dorrax on 2010-01-01
> **northrup said:**
> Have you tried starting your computer with both a regular computer monitor and the TV connected?  In my experience, display settings will only be correctly applied to one video signal, not both.  Ubuntu will likely prioritize your standard monitor output over your S-Video output, and therefore only display to a "primary" display.  I had the same issue when connecting an HDTV to an Ubuntu PC, except the inverse happened: Ubuntu targeted my TV because it uses a DVI connection, and my monitor's VGA connection was considered "secondary".

It did not work. Thank you though.

---

### Post by mr clark25 on 2010-01-01
i was trying to do a similar thing with my graphics card. here is my post: [http://ubuntuforums.org/showthread.php?t=1327437](http://ubuntuforums.org/showthread.php?t=1327437)

that should help.

---

### Post by northrup on 2010-01-01
Not working as in no video on either display, or just still no S-Video output, but your regular monitor is working okay?

I don't know if you tried this already, but you can open up the Display dialog box (System > Preferences > Display) and see if the "Mirror screens" option is checked.

If all else fails, I'd enter the BIOS and see if there's a way to change the display settings so that your S-Video connection is your "primary" display.  I'd guess that the BIOS menu will show up on the TV if you're getting video signal up until the boot process starts.

---

### Post by Dorrax on 2010-01-01
It all works now, used the instructions found in [http://ubuntuforums.org/showthread.php?t=1327437](http://ubuntuforums.org/showthread.php?t=1327437), set up a shell script and put it into the startup applications list. 

Thank you very much!

---

