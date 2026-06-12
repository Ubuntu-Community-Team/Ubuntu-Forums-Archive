---
title: "setting up a touch screen"
date: 2010-10-21
forum: General Help
---

### Post by evanm457 on 2010-10-21
I must say I've spent many nights trying to get this touch screen going on ubuntu but with no luck. Does anyone have any general step by step instructions or is there any sites I can go on. I have a Acer t230h and the furthest Ive got with it is typing something into the terminal and getting out aload of strange looking symbols and stuff. I presume that was in the right direction but i forget what I pressed... something like 'lbus' but longer I think. I have the touchscreen info plugged in with a usb lead so what ever their called in ubuntu might be a help. another thing I did find something related to the screen in the /dev/ folder by plugin it in and out a couple of times and spotting what file was missing and coming back but when I run it in terminal this is what happens -
 evan@ubuntu:~$ cat /dev/hidraw0
cat: /dev/hidraw0: Permission denied

any help in the right direction is appreciated.
Thanks, Evan.

---

### Post by evanm457 on 2010-10-21
just bumping this to the top before I head to bed again please help me. :)

---

### Post by Ayuthia on 2010-10-21
We can probably start off by checking to see if we can find the devices through one of the following:
```

lspci -nn
lsusb

```

If you are looking to see if you are getting any output you will need to be in admin mode to look at the /dev:
```

sudo cat /dev/hidraw0

```

I want to say that you might have a Quanta device.  You might check out this [thread]("http://ubuntuforums.org/showthread.php?t=1375047").

---

### Post by evanm457 on 2010-10-22
Thanks v much for the reply. I found a device at 'Bus 005 Device 002: ID 0408:3000 Quanta Computer, Inc.' which I presume is the touchscreen.  Which also means it runs on quanta. I was looking at the page you sent me before aright ( [B] 	 [Howto] Get Touchscreen working with Acer T230H on Karmic (Ubuntu 9.10)) but gave up because I didn't understand some of it but I will try harder. Another thing is I want Multitouch gestures so would this work with it and does it matter if it is only 9.10 and I'm on ubuntu 10.10
[/B]

---

### Post by evanm457 on 2010-10-22
Im after trying almost all of that post on how to get acer on karmic but when I get to changing the xorg.conf script it tells me that it is a read only file and that I dont have the permissions to edit it. I found the xorg.conf in the cd under etc/x11/. Does anyone know how to make the script editable. I sould be able to because I am the administrator???

---

### Post by Ayuthia on 2010-10-22
You can try:
```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by Ayuthia on 2010-10-22
> **evanm457 said:**
> Another thing is I want Multitouch gestures so would this work with it and does it matter if it is only 9.10 and I'm on ubuntu 10.10
[/B]

I am not for sure.  I would think that it will work because it should be reporting MT events.  You can check out this link about [multitouch]("https://wiki.ubuntu.com/Multitouch").  Your device is found at the ENAC site under the Hardware Support section.

Just to let you know though, right now there are no gestures being used in Ubuntu as of yet.  It can be found with the Unity desktop (which comes with Ubuntu Netbook Edition) and can be installed, but of course, your desktop would then look like the netbook edition.  However, you are able to test out the gestures by installing utouch and running:
```
gesturetest 0 0 0xffffffff
```

---

### Post by evanm457 on 2010-10-22
I was trying unity there for a couple of days cause I thought I'd have the screen working by now. Ya I thought it should have worked like plug and play but turns out not. Thanks for the gesture support but ill hafta try get it going first. I just don't have a clue what I'm doing wrong. Is there much of a difference from ubuntu netbook and the normal ubuntu because there could be a better driver in netbook. I was thinking of uninstalling ubuntu and installing ubuntu netbook but that might be just too much hassle if it doesn't work out.  Aww I dunno whats wrong I really don't think I'm getting anywhere and I don't have a clue whats wrong :'( lol :L Ano I'm sure its just something small to overcome but I dunno how to go about it?

---

