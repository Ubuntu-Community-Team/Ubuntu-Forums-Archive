---
title: "ubuntu 10.04, touchpad stoped working"
date: 2010-05-16
forum: General Help
---

### Post by seniortaco on 2010-05-16
Hi all, so I've just recently upgraded from 8.04 to 10.04 and i am already impressed with the new features..
Ive run into an odd issue though that I can't seem to figure out.
My touchpad has just stopped working. The only way i can use a mouse now is if i plug one into the usb. But when I first installed 10.04 it was working perfectly.

Just so we are up to date on what was recently changed..
Right before this I was resizing my ubuntu partition to make room to install BT2 into the harddrive. Ive installed it now and BT2 works great.. But when i loaded back into my ubuntu partition, after finishing the install the touchpad decided to stop working??? It was working great before I installed BT2 to the hardrive, i made no changes to ubuntu when i was doing the install (only to the file system and GRUB), that i know of anyway. and now its out.. any ideas??  

I recently ran into this post [http://ubuntuforums.org/showthread.php?t=1479286](http://ubuntuforums.org/showthread.php?t=1479286) im not sure if the 2 are related. 

Anyways ive listed the xinput list.. if there is anything else I can post that will help let me know, Ive really gotta get this touchpad running agian bc the only mouse I have is off my desktop.. 

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Gaming Mouse                   id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

The laptop is a Satellite A105-S2716 with the 1.4 bios

Ive tried to use the touch pad on/off button, it does nothing. Also I've tried installing gsynaptics and the touchpad has been "enabled" thru it but still no avail.
 
Just to add on here it seems to be detected fine? I don't know if there is problems with the driver but ubuntu recognizes the device.. It just doesn't seem to want to use it.

---

### Post by battleship on 2012-09-06
Hi did you ever resolve your problem w/BT? I run bt 5.2r on 3 laptops and only one has this problem . It is an HP 9200 series, The pad has worked fine for months. Then all of the sudden it won't work Ive tried everything I could find. A usb mouse still works fine. BTW it is dual booted w vista But the pad still works under windows.
I get an identical message as you did

xinput list
&#9121; Virtual core pointer id=2 [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)]
&#9116; &#8627; Logitech USB Gaming Mouse id=9 [slave pointer (2)]
&#9116; &#8627; SynPS/2 Synaptics TouchPad id=11 [slave pointer (2)]
&#9116; &#8627; Macintosh mouse button emulation id=12 [slave pointer (2)]
&#9123; Virtual core keyboard id=3 [master keyboard (2)]
&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)]
&#8627; Power Button id=6 [slave keyboard (3)]
&#8627; Video Bus id=7 [slave keyboard (3)]
&#8627; Power Button id=8 [slave keyboard (3)]
&#8627; AT Translated Set 2 keyboard id=10 [slave keyboard (3)]

Anybody got any Ideas?
Any help much appreciated!
TIA

---

### Post by overdrank on 2012-09-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

