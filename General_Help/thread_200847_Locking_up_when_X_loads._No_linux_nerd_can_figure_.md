---
title: "Locking up when X loads. No linux nerd can figure it out so far."
date: 2006-06-20
forum: General Help
---

### Post by JanHammer on 2006-06-20
OK, so, I've **never** been able to run ubuntu because of this error. Meaning I've never been able to get into the actual gui and edit any settings, just trying to get this across. I first tried ubuntu 5.10 (both the live CD and installing it) and I got this error, then in hopes they fixed it I tried ubuntu 6.06 (once again both installing and live CD) and I get the same problem. I'd like to think someone has enough knowledge of ubuntu to know what to do (like the ubuntu team :/) because I don't want this to be hopeless. 

Anyway try to find a way to get this fixed, and if you don't know try to find an uber linux geek. My PC specs are:

(eMachine T1221)
1.3GHZ celeron 100mhz FSB
512mb PC133 RAM
40gb IDE HDD
120gb IDE HDD
geforce 5500 PCI

And pickles are delicious, yum.

---

### Post by aysiu on 2006-06-20
Well, I have two eMachines, and they work flawlessly with Ubuntu (Hoary, Breezy, and Dapper), so it's not an eMachines thing.

It's also not a Ubuntu thing.

Which leaves us two possibilities:

1. Something's wrong with your hardware (let's hope not)
2. Something's wrong with the disks you're using

Take a look at this page and tell me if you did all these steps when you burnt the disk:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by Iandefor on 2006-06-20
What's the error, exactly? Or does it just lock up?

Have you verified that it isn't your video driver? I've had much the same problem when using the wrong driver.

---

### Post by JanHammer on 2006-06-20
aysiu you managed to link me to something I've never seen or tried before, you could be my savior ^_^. But I'm posting this to keep the thread updated and alive and will edit or make a new post if this does anything. 

And Iandefor it just locks up, and on the boot (well as much as it boots) it says OK when it gets to video. *shrugs*

---

### Post by aysiu on 2006-06-20
Keep us posted. We don't know everything here (we're just other users like you), but we'll help as best we can.

---

### Post by JanHammer on 2006-06-20
Bad news :/ the MD5 checker came out fine and I even tried that burning program. I don't know what hardware could be causing trouble, it's all normal common brand things.

---

### Post by aysiu on 2006-06-20
Have you tried other Linux CDs (Mepis, PCLinuxOS)? Maybe there's something going on with Ubuntu. You burnt at a slow speed, too...?

---

### Post by JanHammer on 2006-06-20
I tried PClinuxOS and it didn't even boot FROM the disc, and tried knoppix and that worked. Also I burnt ubuntu at 12x, I don't see how there can be a disc problem if it starts from the disc?

---

### Post by Iandefor on 2006-06-20
[quote=JanHammer]Bad news :/ the MD5 checker came out fine and I even tried that burning program. I don't know what hardware could be causing trouble, it's all normal common brand things.[/quote] The nv driver doesn't support your GeForce 5500. You need either the NVIDIA driver or the VESA driver.

---

### Post by JanHammer on 2006-06-20
Ooo, you give me new news. How do I do this?

---

### Post by Iandefor on 2006-06-20
[quote=JanHammer]Ooo, you give me new news. How do I do this?[/quote] It's possible that this isn't your problem, but follow the guide anyways.

1. Boot into Ubuntu recovery mode

2. open up the file /etc/X11/xorg.conf for editing, using the command ```
vi /etc/X11/xorg.conf
``` Make sure it says "insert" at the bottom of the screen- otherwise, you won't be able to input text. It'll probably look a little cryptic. What you want is a section talking about your video card. There should be a line that reads ```
Driver         "nv"
``` Somewhere. Change it to read  ```
Driver         "vesa"
``` 

3. Hit esc, enter :x (Make sure this is at the bottom of the screen), and hit enter. If you've done it right, you'll be back at the command line.

4. Reboot. It should work.

---

### Post by JanHammer on 2006-06-20
Well I'm in knoppix right now (much less complicated in editing that file ^_^. It turns out ubuntu chose the wrong video card (the onboard) and I'm having a linux geek help me out here in IRC on it. Any suggestions? What's in the xorg file is:

Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

---

### Post by Iandefor on 2006-06-20
[quote=JanHammer]Well I'm in knoppix right now (much less complicated in editing that file ^_^. It turns out ubuntu chose the wrong video card (the onboard) and I'm having a linux geek help me out here in IRC on it. Any suggestions? What's in the xorg file is:

Section "Device"
    Identifier    "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:1:0"
EndSection[/quote] Maybe. What's the output of > lspci

---

### Post by JanHammer on 2006-06-20
Got past that and it's no longer locking up. What I did was just change the driver to "vesa" to see if it would work. When it started it when past where it would lock then got to X and said there was a error. I ended up getting sent to just bare command line, fun :/.

---

### Post by Iandefor on 2006-06-20
[quote=JanHammer]Got past that and it's no longer locking up. What I did was just change the driver to "vesa" to see if it would work. When it started it when past where it would lock then got to X and said there was a error. I ended up getting sent to just bare command line, fun :/.[/quote]Okay, so it might not be the driver. Did you stop to see what kind of error it is? It'll make helping you easier if I get to know what the problem is :-D.

---

### Post by scxtt on 2006-06-20
2 quick questions:

1. is "geforce 5500 PCI" the video card you want to use, and that your monitor is plugged into?
2. does your motherboard have onboard video?  and if so, have you disabled it in order to use your "geforce 5500 PCI"?

---

### Post by JanHammer on 2006-06-21
Ubuntu works now, it wouldn't of worked if one of you didn't point out the driver issue since no one thought of it before. I changed the driver to vesa and had to point it to my FX5500, worked fineeee. Because like I said, the onboard was taking its place. 

Thanks.

---

### Post by Iandefor on 2006-06-21
[quote=JanHammer]Ubuntu works now, it wouldn't of worked if one of you didn't point out the driver issue since no one thought of it before. I changed the driver to vesa and had to point it to my FX5500, worked fineeee. Because like I said, the onboard was taking its place. 

Thanks.[/quote]Weird. Well, you're welcome!

---

