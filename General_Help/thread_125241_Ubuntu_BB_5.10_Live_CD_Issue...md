---
title: "Ubuntu BB 5.10 Live CD Issue.."
date: 2006-02-03
forum: General Help
---

### Post by Breaks on 2006-02-03
Well, i stuck the Live CD into the drive and booted from it just to make sure that my new hardware is picked up before actually installing the OS and as it tried to boot up the Xserver all i got was a bunch of green, gray and what not lines going vertically down the monitor, so i pressed ctrl + alt + backspace and then i got a bunch of colourful squares all over the screen and it wouldnt do anything. Any advice or information on this and why its doing this? :-|

---

### Post by christhemonkey on 2006-02-03
Sounds like the Xserver is set up incorrectly, with the vertical sync rate set too high (or something...!),
On an install, you would edit the xorg config file,
either by editing manually the xorg.conf file
Or by running from prompt:
> sudo dpkg-reconfigure xserver-xorg
To get into a terminal type:
Ctrl+Alt+F1

EDIT: Though this is only for full install, not sure about if its a live cd!

---

### Post by confused57 on 2006-02-04
Had the same problem, my home built pc had a XGI Volari V3 video card, which doesn't have any Linux drivers.  Ordered and installed a GeForceFX 5500 Nvidia card and the BB 5.10 live CD works great.  May or may not be related to your problem.

---

### Post by Breaks on 2006-02-04
I think it most likely is, or appears to be from what i see, a driver issue. I have a  Geforce MSI 6800GS 256mb. Anyone else got this card and got ubuntu 5.10 working with it?

---

### Post by funkylydia on 2006-02-04
I also have this problem, I have tried various different settings in xserver including correcting the vertical sync rate as you recommend, I have also tried changing resolution and colour depth, the display has changed but was no easier to read, any ideas?

---

### Post by christhemonkey on 2006-02-05
Still with sort of scrolling lines of colours?
If so, its either your vertical or horizontal sync rate things.
Try changing them in your xorg.conf to really reserved values.
like 50 for both values.

---

### Post by funkylydia on 2006-02-05
What I see when it starts is the line consists of alternating blue and white vertical lines. 
I tried lowering the sync rates and then the display refused to start.
I also tried chaning the colour depth to 16 this just changed the blue to pink.
Changing the screen resolution to the minimum had almost no effect at all as well.
Any other ideas anyone? :-k 
btw I know this is a dumb question but how do I shut down the system from the command prompt?

---

### Post by christhemonkey on 2006-02-05
```
sudo shutdown -h now
```
That shuts it down.

Post us your xorg error log (i forget where it is, probably the same place as your xorg.conf)

---

### Post by funkylydia on 2006-02-05
how would I get that considering I am using the live CD (I am using the XP installation on the same comp to post this)

---

### Post by christhemonkey on 2006-02-05
oh, hmm yes, the live CD creates a filesystem in your RAM does it not?
So from a command prompt you can navigate to the directory
```
cd /var/log/
```
and then
```
vi Xorg.0.log
```
press ZZ to exit

---

### Post by funkylydia on 2006-02-05
Ok, how do I then access it to post it here?

---

### Post by christhemonkey on 2006-02-05
the second command i said opens the file
vi xorg.0.log
Or whatever your log is called.

---

### Post by funkylydia on 2006-02-07
Ok I can view the file but I'm afraid I can't see how to post it here :-k

---

### Post by christhemonkey on 2006-02-08
Write it down? On paper?
Or save it to a floppy or somat?
(to do that, insert a floppy, make sure you mount it)
```
cd /media/floppy0/
vi /etc/X11/xorg.log
```
type
```
:s xorg.log
Then ZZ to quit
```

---

### Post by funkylydia on 2006-02-08
well its about 20 pages as far as I can see, so I don't think writing it down is an option and I don't have a floppy drive. Could I use a USB Disk on key?

---

### Post by christhemonkey on 2006-02-08
Yes. just replace the floppy0 part with usb-disk

---

### Post by funkylydia on 2006-02-09
I tried with the usb-disk but when I typed cd /media/usb-disk/ it said it could not be found.
And I assume for the second command you meant vi /etc/X11/xorg.conf as .log doesn't exist.
And :s xorg.log didn't work either I am afraid. So I'm not sure if I am being dumb or what, is there anything on the file which I should look out for as possible causes of the problem?

---

