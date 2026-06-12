---
title: "webcam"
date: 2006-04-18
forum: General Help
---

### Post by Masterillusionist on 2006-04-18
could someone help me to install my usb webcam, it isn't a famous one. But i would like to get my cam going.
Amsn says there no cams installed so that's one problem. and it says that i'm behind a NAT. But i've followed the instructions on the amsnsite and opend the requird ports. 

Can somebody help me please

---

### Post by ebash on 2006-04-18
[QUOTE=Masterillusionist]could someone help me to install my usb webcam, it isn't a famous one. But i would like to get my cam going.
Amsn says there no cams installed so that's one problem. and it says that i'm behind a NAT. But i've followed the instructions on the amsnsite and opend the requird ports. 

Can somebody help me please[/QUOTE]
What kind of webcam do you have? To find out execute the following command in a terminal:
```
lsusb
```

Or unplug your camera and run the following command in a terminal:
```
tail -f /var/log/syslog
```

Once you/we know what kind of camera you have it will be easier to help.

---

### Post by Masterillusionist on 2006-04-18
glenn@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0c45:60fe Microdia
Bus 001 Device 001: ID 0000:0000
glenn@ubuntu:~$

---

### Post by Masterillusionist on 2006-04-18
glenn@ubuntu:~$ tail -f /var/log/syslog
Apr 18 20:49:59 localhost gconfd (glenn-11659): Adres "xml:readonly:/var/lib/gco nf/defaults" getraceerd naar een alleen-lezen configuratiebron op positie 7
Apr 18 20:50:03 localhost gconfd (glenn-11659): Adres "xml:readwrite:/home/glenn /.gconf" getraceerd naar een schrijfbare configuratiebron op positie 0
Apr 18 20:51:11 localhost kernel: [4300400.993000] rx: DUP pkt (seq 23856)!
Apr 18 20:53:53 localhost kernel: [4300562.623000] atkbd.c: Unknown key released  (translated set 2, code 0xaa on isa0060/serio0).
Apr 18 20:53:53 localhost kernel: [4300562.623000] atkbd.c: Use 'setkeycodes e02 a <keycode>' to make it known.
Apr 18 20:53:53 localhost kernel: [4300562.695000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Apr 18 20:53:53 localhost kernel: [4300562.695000] atkbd.c: Use 'setkeycodes e02 a <keycode>' to make it known.
Apr 18 20:53:57 localhost kernel: [4300567.250000] rx: DUP pkt (seq 59184)!
Apr 18 20:54:00 localhost kernel: [4300570.322000] rx: DUP pkt (seq 61824)!
Apr 18 20:54:31 localhost kernel: [4300600.844000] rx: DUP pkt (seq 8512)!

glenn@ubuntu:~$ tail -f /var/log/syslog
Apr 18 20:59:29 localhost kernel: [4300899.461000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Apr 18 20:59:29 localhost kernel: [4300899.549000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Apr 18 20:59:29 localhost kernel: [4300899.549000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Apr 18 21:00:54 localhost kernel: [4300984.303000] Inbound IN=wlan0 OUT= MAC=00:c0:49:56:e7:3c:00:11:50:36:ab:90:08:00 SRC=213.119.202.6 DST=192.168.2.4 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1636 DF PROTO=TCP SPT=1465 DPT=6891 WINDOW=65535 RES=0x00 SYN URGP=0
Apr 18 21:00:54 localhost kernel: [4300984.309000] Inbound IN=wlan0 OUT= MAC=00:c0:49:56:e7:3c:00:11:50:36:ab:90:08:00 SRC=213.119.202.6 DST=192.168.2.4 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1637 DF PROTO=TCP SPT=1466 DPT=6891 WINDOW=65535 RES=0x00 SYN URGP=0
Apr 18 21:00:57 localhost kernel: [4300987.328000] Inbound IN=wlan0 OUT= MAC=00:c0:49:56:e7:3c:00:11:50:36:ab:90:08:00 SRC=213.119.202.6 DST=192.168.2.4 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1714 DF PROTO=TCP SPT=1465 DPT=6891 WINDOW=65535 RES=0x00 SYN URGP=0
Apr 18 21:00:57 localhost kernel: [4300987.329000] Inbound IN=wlan0 OUT= MAC=00:c0:49:56:e7:3c:00:11:50:36:ab:90:08:00 SRC=213.119.202.6 DST=192.168.2.4 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1715 DF PROTO=TCP SPT=1466 DPT=6891 WINDOW=65535 RES=0x00 SYN URGP=0
Apr 18 21:01:03 localhost kernel: [4300993.232000] Inbound IN=wlan0 OUT= MAC=00:c0:49:56:e7:3c:00:11:50:36:ab:90:08:00 SRC=213.119.202.6 DST=192.168.2.4 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1862 DF PROTO=TCP SPT=1465 DPT=6891 WINDOW=65535 RES=0x00 SYN URGP=0
Apr 18 21:01:03 localhost kernel: [4300993.233000] Inbound IN=wlan0 OUT= MAC=00:c0:49:56:e7:3c:00:11:50:36:ab:90:08:00 SRC=213.119.202.6 DST=192.168.2.4 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1863 DF PROTO=TCP SPT=1466 DPT=6891 WINDOW=65535 RES=0x00 SYN URGP=0
Apr 18 21:01:34 localhost kernel: [4301024.475000] usb 1-8: USB disconnect, address 2

---

### Post by arrizaba on 2006-04-18
Have you tried easycam2?
It installs drivers for your webcam using a nice user interface. It is compatible for the moment with the drivers according to: Spca, Ov511, Pwc, Qce and drivers for Eyes Toy, so you might have luck and your camera might use one of these drivers. 
To download easycam2 you have to add to your repository list in /etc/apt/sources.list the line:

```
[COLOR="Blue"][FONT="Courier New"]deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main[/FONT][/COLOR]
```

Then

```
[FONT="Courier New"][COLOR="Blue"]sudo apt-get install easycam2 [/COLOR][/FONT]

```
should do.

---

### Post by Masterillusionist on 2006-04-18
could not connect to video device (/dev/video0)

that's the message i get with easycam2

---

### Post by Masterillusionist on 2006-04-18
i've tried spca5xx driver but when i try make it says

glenn@ubuntu:~/Desktop/ikke$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/glenn/Desktop/ikke CC=cc modules
make: *** /lib/modules/2.6.12-10-386/build: Onbekend bestand of map.  Stop.
make: *** [default] Fout 2
glenn@ubuntu:~/Desktop/ikke$ sudo make
Password:
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/glenn/Desktop/ikke CC=cc modules
make: *** /lib/modules/2.6.12-10-386/build: Onbekend bestand of map.  Stop.
make: *** [default] Fout 2
glenn@ubuntu:~/Desktop/ikke$
glenn@ubuntu:~/Desktop/ikke$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': Onbekend bestand of map
make: *** [install] Fout 1
glenn@ubuntu:~/Desktop/ikke$ sudo make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/glenn/Desktop/ikke CC=cc modules
make: *** /lib/modules/2.6.12-10-386/build: Onbekend bestand of map.  Stop.
make: *** [default] Fout 2
glenn@ubuntu:~/Desktop/ikke$ su
Password:

---

### Post by Masterillusionist on 2006-04-23
up

---

### Post by waster on 2006-07-01
So did you get it working? Did you have to edit the source code?

---

### Post by jitesh on 2006-07-04
I am having the same problem with my web camera

when I do lsusb I get:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 006: ID 0c45:612f Microdia
Bus 002 Device 003: ID 03f0:3f11 Hewlett-Packard PSC-1315
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I have tried by installing QCAM, GQCAM, V4L & also easycam2.

Im not sure what else to try & also best way to test the feed of the web camera.

The packaging of the webcam states a QCAM 330, uses USB port & I am working with Ubuntu Breezy 1.10

Any help appreciated.

---

### Post by moaxey on 2006-07-26
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0c45:613a Microdia
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

almost the same cam as start of thread
would have been great if masterillusionist had said how he did it!

---

### Post by jpmorelli on 2006-08-06
I think masterillusionist can't make it work at the moment, the post says "up" what it means he post that to make the post have score and not going lost at the bottom.
Sory about my english, it was difficult for me to explain this, hope you understand, and of course, I have a Genius Webcam Videocam Trek and having the same problem:
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 004: ID 045e:009d Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0c45:6007 Microdia
Bus 002 Device 002: ID 0506:0a01 3Com Corp.
Bus 002 Device 001: ID 0000:0000

A wireless keyboard and mouse from MS, a 3com external wireless lan adapter, and the webcam obviusly not working...:confused:

---

### Post by Icarosaurus on 2006-12-09
Moaxey said:
> Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0c45:613a Microdia
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

almost the same cam as start of thread
would have been great if masterillusionist had said how he did it!
Well, this is my webcam...the output of lsusb gives the same ids.
Someone in the world had the same issues:

[http://www.linuxquestions.org/questions/showthread.php?t=458968&highlight=613a]("http://www.linuxquestions.org/questions/showthread.php?t=458968&highlight=613a")

The juyce of all is that, if you control the list of cams supported by SPCA5XX:
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

..you'll find a camera with **0c45:613c**, not **0c45:613a**.
So it seems our camera is not supported (maybe it's a newer model), but I'm sure it needs only a slight correction in the drivers.
I'm not an expert programmer, but people is working on it:
[http://lists.zerezo.com/spca50x-devs/msg00824.html]("http://lists.zerezo.com/spca50x-devs/msg00824.html").
So I hope the problem will be soon solved...
I don't like swithcing to Windoz everytime I have to use cam [-(

---

### Post by budgie9 on 2006-12-09
use camorama I think it is called, it will see the camera if loaded.

---

### Post by Icarosaurus on 2006-12-09
It really seems that someone is working on a new kernel module for **sn9c120**, that's (maybe) the "bridge" of our "Microdia 613a":
[http://www.linux-projects.org/modules/news/index.php?storytopic=0&start=10]("http://www.linux-projects.org/modules/news/index.php?storytopic=0&start=10")

Hope to see the solution, soon. :)

There's only a little problem:
[http://www.linux-projects.org/modules/news/article.php?storyid=102]("http://www.linux-projects.org/modules/news/article.php?storyid=102")
:(

---

### Post by Icarosaurus on 2006-12-17
Well... webcam drivers have just been updated, now **Sonix 0x612c** and **Sonix 0x613b** should work...
[See here]("http://mxhaard.free.fr/news.html")
I think we have to wait few days before **0x613a** will work: I sent the drivers' author some "Snoop" of my webcam and he said they're really good...
So...don't give up...we'll soon have our little cheap cam working :D

---

### Post by Icarosaurus on 2007-01-22
Well, noone seems to write something here...
Anyway I continue posting here, hoping that this will help ...
Someone made a new driver for Sonix based cameras:
[http://www.linux-projects.org/modules/news/]("http://www.linux-projects.org/modules/news/")
But the minimum kernel version required is 2.6.19.
The Edgy default kernel version is 2.6.17...so I should update my kernel...and I'm really afraid of this :roll:
Moreover I'm soo lazy :roll: 
So I'm planning to install Feisty and I'm already downloading [the dvd for testing it]("http://cdimage.ubuntu.com/dvd/current/") (it will be released in April 2007).
I suppose the module will be present in the new kernel so...the camera should be recognized, I hope! 
I'll let you know!

---

### Post by Icarosaurus on 2007-01-23
Sensor 0V7648 is not supported by the spca102 module, version 1.34
Managed to compile it under Feisty...nothing to do :(

---

### Post by Masterillusionist on 2007-05-16
srry but i didn't botherd to make it work because nobody could give me a good solution. Maybe i will try again

---

### Post by hardyn on 2007-05-16
you say its behind a NAT... 

you must open some ports on your router... i believe amsn 6891.
i cant tell you how to forward ports on your router, as each router does it a little differently, you will have to get that manual out and start reading.

if there is no /dev/video0 there prolly isn't a driver for you camera, this is typical of cheap cameras, sometimes there wast even windows drivers... save he headache and buy a new one that is known to be supported, i don't think they are very much anymore

---

### Post by Icarosaurus on 2007-05-18
People is working on supporting as many webcams as possible....
My webcam is still not supported.
We should consider donating very cheap cams to these people.

Try this site for configuring your router port forwarding (anyway I think it has nothing to do with your webcam problem):
[http://portforward.com/english/routers/port_forwarding/routerindex.htm]("http://portforward.com/english/routers/port_forwarding/routerindex.htm")
Just choose your router model and pick MSN messenger from the list of applications.
It's normal that Amsn tells you are behind a NAT.... I'm behind a NAT too and everything works nice.
Bye

---

### Post by Icarosaurus on 2007-06-12
MICRODIA 0c45:613a FINALLY SUPPORTED!
Check:
[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")
:-D

---

