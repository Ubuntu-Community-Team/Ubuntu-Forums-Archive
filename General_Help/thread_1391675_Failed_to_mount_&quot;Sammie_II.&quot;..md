---
title: "Failed to mount &quot;Sammie II.&quot;."
date: 2010-01-27
forum: General Help
---

### Post by Martin McFly on 2010-01-27
[quote=Xubuntu 9.10]Error reading bootsector: Input/output error Failed to mount '/dev/sde1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details. .[/quote]

Sammie II. is my second external drive (there's also Sammie III., both 1 TB drives, but there are even bigger problems with III.)

I have Xubuntu 9.10, but if this is problem, mine, drives, or Linux's, I think it will be present in Ubuntu as well. Using netbook Asus EEE 904 (1024 MB RAM, 900MHz Celeron M CPU, 80 GB disc), I've had moderate problems with them on Windows XP. 

Let me explain: I plugged it through USB cable and it worked (in XP), but when I was moving notebook, it suddenly switched off (unmounted? simply, I wasn't  able to use it [it wasn't in This Computer]), till I stopped moving whole machine and/or pulled and plugged again USB connector. Seems like it was prone to moving, so when left on table, it was OK.

Now I switched to Linux and had more severe problems with it. It's NTFS you know, both 1 TB drives. Maybe I'll change future drives directly into ext4, but these have to stay in NTFS state.


The problem is that I connect the cables and, either nothing happens (nothing visible, like I have access to these drives through "MEDIA"), or they like connects, appear, but within second, they're gone. Are there some precautions I should take, or problems I should be aware when using these drives under Linux ? 

+ additional question, if I could automount these drives every time after system start, that would be great.



P.S. drive is Samsung, therefore Sammie

---

### Post by lordskid on 2010-01-27
You might have a lose usb cable

and yes you can automount it but I don't really know how, all I know is it has something to do with fstab. try googling for fstab.

---

### Post by Martin McFly on 2010-01-27
> **lordskid said:**
> You might have a lose usb cable

and yes you can automount it but I don't really know how, all I know is it has something to do with fstab. try googling for fstab.

First I added (manually) SWAP drive, now automount. I'm beginning to love fstab :-)

Actually, it's more complex

[img]http://img687.imageshack.us/img687/9729/schemedrives.png[/img]

While magnified section is one USB cable plugged into another (you know, to extend them), this "devide" into two cables are plugged is USB HUB.

I've been doing some research now and am quite worried, if I haven't crossed the line here:
[http://en.wikipedia.org/wiki/Universal_Serial_Bus#Maximum_useful_distance](http://en.wikipedia.org/wiki/Universal_Serial_Bus#Maximum_useful_distance)

The cables given with the discs are terrible. They're 0.5 meters long ! How can anybody plug it somewhere, that's impossible. 

When I said that there are plugged cables, I meant it. I'm sure they fit and aren't loose, as I plugged them as far as I could and bound with duct tape.


But there's lot of things that could went wrong. Do you see something like that here ?

---

### Post by Martin McFly on 2010-01-27
I've reduced cables, so instead of five I have just three now

1)from drives to USB HUB
2)from HUB (it's short, 15cm long cable) to long USB cable
3)long USB cable, connected to HUB output on one side and to netbook on other side.

Oh, these drives are 3.5'' (so they have external power source, I didn't wanted to risk USB power source when I have so low power consuming notebook)



One drive (II.) is connected, but it keeps writing Failed to connect Sammie III.

Who knows for how long will II. be connected, maybe something will happen.

---

### Post by Martin McFly on 2010-01-27
[quote=Xubuntu 9.10]
Failed to mount "Sammie III.".
...
Failed to create mount directory
[/quote]

Seems like Sammie III. is doomed. I've already managed to stabilize the second one.

Any suggestions how to help third drive ?

---

### Post by Martin McFly on 2010-01-30
Solved guys, I've replaced cables. Even slow speeds when copying on NTFS remains.

---

