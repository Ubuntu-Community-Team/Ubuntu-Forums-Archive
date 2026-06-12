---
title: "Instalation issues"
date: 2011-03-18
forum: General Help
---

### Post by kimb on 2011-03-18
Hello, i've been trying to install Ubuntu on my computer for the last 2 days now but it refuese to work. The computer i uses is build and has the following stats:

6 Gb Ram
Intel Core 2 Quad 2.66 Ghz
500gb harddrive
and some nvidia card, will check later

Anynwya, the issue is that it refuses to install. I've tryed USb, CD and Windows installation but nothing work. 

when i try to install using usb this happes; 

First i select to install Ubuntu
[http://i56.tinypic.com/2r53vdl.jpg](http://i56.tinypic.com/2r53vdl.jpg)

Then it loads for a few secound and then the desktop popsup: 
[http://i51.tinypic.com/9fpj69.jpg](http://i51.tinypic.com/9fpj69.jpg)
Its the desktop background with the sound icon, interneticon and power icon
But none is clickable, i i can't do anything, no F buttons work, can't right click, only move my mouse around.


Using disk it goes fine at the start
[http://i56.tinypic.com/11hezhg.jpg](http://i56.tinypic.com/11hezhg.jpg)

And after selecting language and clicking install it start to loads and suddently stopps [http://i53.tinypic.com/24d0i2v.jpg](http://i53.tinypic.com/24d0i2v.jpg)
And stays like this for ever. nothing else happens


Using the windos installer this happens after the instalation and selecting the Ubuntu during boot up
[http://i52.tinypic.com/qyhg5f.jpg](http://i52.tinypic.com/qyhg5f.jpg)

Same as with USb except it manages to comprehend that i got internet connection before freezing



Any solutions to this?

Sorry for shitty images and shitty language, quite frustatrated that i can't make it work...


Thanks in advance for any help you might have!

---

### Post by sikander3786 on 2011-03-18
Welcome to Ubuntu and the forums :-)

No need to panic or get frustrated. I believe we will solve the issue soon. But you need to be patient throughout.

Which version of Ubuntu are you trying to install? From the Desktop image, it seems like Maverick?

So what we need you to do first is to check the MD5SUM of the downloaded image.

Then check the disc for defects. If necessary, burn a new disc at the lowest possible speeds or use a USB drive.

Then you might need to put in some boot parameters like acpi=off or nomodeset.

You can find step-by-step instructions here.

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

Let us know if none of those solves the issues so we can try some thing else.

---

### Post by kimb on 2011-03-18
Hello! 

Yes, i'm trying to install the 10.10 Maverick version


Found no error with diskcheck.


MD5Sum
1b9df87e588451d2ca4643a036020410
ubuntu-10.10-desktop-amd64.iso

*acpi=off*, *noapic* and [I]nomodeset seem to have fixed it!

thanks for your patience!
[/I][]("http://i51.tinypic.com/dg09sj.jpg")

---

### Post by kimb on 2011-03-18
New isssue, i have made a 30 GB partiton on my harddrive, how do i do this during instalion?

Read som guide but he gave 4gb to each of the "/" and the partition isn't big enough for this...

---

### Post by sikander3786 on 2011-03-18
[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

You can create partitions from the installer or use GParted from System > Administration menu.

---

