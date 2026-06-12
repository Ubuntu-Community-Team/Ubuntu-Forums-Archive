---
title: "USB Mouse freezes!!!"
date: 2009-07-25
forum: General Help
---

### Post by nabokov on 2009-07-25
hi guys, amongst all the problems im having with ubuntu 9.04, the most annoying
one is my USB mouse. Heres how it goes.
I start ubuntu up, its fine at first, but after a while my mouse freezes, everything else works fine, my keyboard my USB drives it all works fine.
now if i plug my second USB mouse in it starts working.....for a while then that freezes to. if i try to replug any of the mouses nothing works.
 
the mouses im using...
Main mouse is ---Razer DeathAdder
Second mouse --- A logitech track ball mouse 
bouth mouses are USB
Keyboard is USB but that works.
 
im running 2 Nvidia 8800 GT SLI
dual core 6600 intell
2gig ram
and a Asus P5NSLI board
 
Iv been scouring the internet for 3 days now, theres plenty of ppl with the isue 
but cant seem to find a fix....please help me out 
 
im shore you can tell im new to Ubuntu linux..im liking it ](*,)

---

### Post by nabokov on 2009-07-25
Bump......no one??

---

### Post by gastly on 2009-07-25
hmmm I have a Amkette USB mouse, it works fine.
Try this post:
[http://ubuntuforums.org/showthread.php?p=2398239](http://ubuntuforums.org/showthread.php?p=2398239)

and also, there's a tool to configure razer mouse:
[http://razertool.sourceforge.net/](http://razertool.sourceforge.net/)

Good luck :)

---

### Post by nabokov on 2009-07-25
ya none of that worked becouse the first thing i did was try using rzrtool but no luck
. im installin a 64 bit Ubuntu now since i was using a 32 on my  dualcore wee will c

---

### Post by nabokov on 2009-07-25
Nope that didnt help....im getn mad now.  >> it does it on 8.10 9.04 and 9.04 64bit
this time it did it no more than  a minute after i booted. some times it takes up to 10 mins. :mad:

---

### Post by gastly on 2009-07-25
Maybe it could be that your USB port is bad? Just my guess...
Try putting your keyboard into the port where you put your mouse in, or try putting a USB drive in your mouse port and see if it works.

---

### Post by nabokov on 2009-07-25
k trying it now

---

### Post by nabokov on 2009-07-25
yup nothing ... nothing works   why meee !!!!

---

### Post by gastly on 2009-07-25
don't give up...maybe someone else would give any suggestions...

---

### Post by nabokov on 2009-07-25
but 3 daays iv been wiout my desktop, its just a frekin mouse how hard can it be to get it to work,.

---

### Post by gastly on 2009-07-25
If it doesn't work...then there's no choice I think...just buy a PS/2 mouse. Quit using the USB one...

---

### Post by nabokov on 2009-07-25
> **gastly said:**
> If it doesn't work...then there's no choice I think...just buy a PS/2 mouse. Quit using the USB one...
 
U fkn kidding me i did not spend 50 buks on a mouse just to go buy another one 
 
ppl use USB mice with ubuntu why cant i ....

---

### Post by gastly on 2009-07-25
dude, do this, when the mouse freezes, open up a terminal and type
```
 dmesg | tail
```
and paste the output here.

EDIT: Press Alt+F2 and enter 'gnome-terminal' (without quotes) and press Enter.

---

### Post by abhi90 on 2009-07-25
For in that case you have to check your USB connection .....
Check if it is [B]Properly working or not.
Actually I am using_ Microsoft_  mouse and it work fine now....
The problem you have ,,,, the same problem I had too before....
But in that case I unplugged the USB and connect it again.....
Besides that install some packages for mouse.  
[/B]

---

### Post by nabokov on 2009-07-25
k it hasent frozen yet but thi sis what it is now 

russia@russia-desktop:~$ dmesg | tail
[   13.144113] type=1505 audit(1248508192.481:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2298
[   14.772986] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.772989] Bluetooth: BNEP filters: protocol multicast
[   14.783351] Bridge firewalling registered
[   19.659668] skge eth0: enabling interface
[   19.663033] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.351526] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.351860] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.208006] eth0: no IPv6 routers present
[ 2711.068576] usb 2-3.2: USB disconnect, address 5
russia@russia-desktop:~$

---

### Post by nabokov on 2009-07-25
ok now when the mouse froze the whole system froze, so i couldnt open up a terminal . this is just funny now

---

### Post by nabokov on 2009-07-25
here is the report after the mouse froze i couldnt copy the text off the terminal so ..
I HAD TO TAKE of pic of it lol
 
hers a link to it [http://s185.photobucket.com/albums/x34/alexnabokov/Work/?action=view&current=DSC045781.jpg](http://s185.photobucket.com/albums/x34/alexnabokov/Work/?action=view&current=DSC045781.jpg)
 
NOTE: after my mouse froze I pluged in my other mouse to navigate to the terminal becouse alt+tab was not working 
 
[IMG]http://i185.photobucket.com/albums/x34/alexnabokov/Work/DSC045781.jpg[/IMG]

---

### Post by nabokov on 2009-07-25
ok i managed to get a report without having to blugin another mouse hence screing up 
the result so here it is 
 
this is right after it froze on me 
 
[IMG]http://i185.photobucket.com/albums/x34/alexnabokov/Work/mm.jpg[/IMG]

---

### Post by nabokov on 2009-07-25
no one has nothin ...??

---

### Post by gastly on 2009-07-25
hmmm...I don't see any errors in the output...
Do you have any other OS in the machine? If yes, then does the mouse work in it?
If it doesn't work in the other OS, then your USB port is fried or the mouse is faulty, if it does work in another OS...then...something's wrong with Ubuntu. 

Also check if you have the package 'xserver-xorg-input-mouse' installed. You can check it from the terminal:
```
aptitude show xserver-xorg-input-mouse
```

if it says **State: Installed** then it's installed.

---

### Post by nabokov on 2009-07-25
> **gastly said:**
> hmmm...I don't see any errors in the output...
Do you have any other OS in the machine? If yes, then does the mouse work in it?
If it doesn't work in the other OS, then your USB port is fried or the mouse is faulty, if it does work in another OS...then...something's wrong with Ubuntu. 
 
Also check if you have the package 'xserver-xorg-input-mouse' installed. You can check it from the terminal:
```
aptitude show xserver-xorg-input-mouse
```if it says **State: Installed** then it's installed.
 
k this is what it gave me 
 
 
Package: xserver-xorg-input-mouse
State: installed
Automatically installed: no
Version: 1:1.4.0-1
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 164k
Depends: libc6 (>= 2.4), xserver-xorg-core (>= 2:1.5.99.901)
Replaces: xserver-xorg (< 6.8.2-35)
Provides: xserver-xorg-input-4
Description: X.Org X server -- mouse input driver
This package provides the driver for mouse input devices. 
 
More information about X.Org can be found at: <URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
This package is built from the X.org xf86-input-mouse driver module.
 
ohh ya and yes the Usb ports work tested them in vista on the same machine, and the mice workt fine
 
 
 
 
soo what now???:)

---

### Post by gastly on 2009-07-25
ok, I googled it a bit, and I found a little how-to. It tells you how to configure USB mice:
[http://linuxreviews.org/howtos/xfree/mouse/](http://linuxreviews.org/howtos/xfree/mouse/)

Let's see if that works...

---

### Post by nabokov on 2009-07-25
> **gastly said:**
> ok, I googled it a bit, and I found a little how-to. It tells you how to configure USB mice:
[http://linuxreviews.org/howtos/xfree/mouse/](http://linuxreviews.org/howtos/xfree/mouse/)
 
Let's see if that works...
 oOk so im tryin a few things on that how too.. loooks promesing
but im having a few problems along the way 
 
when i input  " cat /dev/input/mouse1" or mice or mouse 1 through 3
it comes back with" Permission denide 
 
is this supose to happen ??

---

### Post by gastly on 2009-07-26
you should add a 'sudo' before the command.

```
sudo cat /dev/input/mouse1
```

---

