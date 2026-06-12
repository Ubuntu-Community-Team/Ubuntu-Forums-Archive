---
title: "Ubuntu 9.10 installation failure. Help please!"
date: 2009-10-29
forum: General Help
---

### Post by Gazzz7472 on 2009-10-29
Hi
I have an Advent 6552 laptop.  I upgraded to Ubuntu 9.10 from Ubuntu 9.04.  But unfortunately in 9.10 my trackpad does not work and neither does an external mouse.

Will probably go back to 9.04 as this worked fine for me, but have no idea how to do this without the use of a mouse.

Any help gratefully received.

---

### Post by philinux on 2009-10-29
Can you move the mouse at all with the trackpad?

---

### Post by P4man on 2009-10-29
you sure its "only" a mouse+trackpad issue and the OS is not frozen entirely? Can you log in ? Once logged in does alt+ F1 or alt+ f2 work ?

---

### Post by Gazzz7472 on 2009-10-29
No trackpad and external mouse are both dead and frozen 

If there is a way to use the keyboard to downgrade to 9.04 would be a help.

---

### Post by Gazzz7472 on 2009-10-29
I can use the keyboard.

---

### Post by philinux on 2009-10-29
Restart the machine using this.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

at grub press esc.

Choose recovery mode. Then at the menu choose resume normal boot.

---

### Post by P4man on 2009-10-29
Ive never heard of a trackpad and a mouse doing nothing. Find it hard to believe it would be something inherent to 9.10.

Can you boot a 9.10 live cd and confirm the issue there?

As for your question: no, there is no downgrade path Im afraid.

---

### Post by phillw on 2009-10-29
Sorry to hear the problems.. If nothing else works ...

 Boot with the 9.04 LiveCD, check it works, then select 'install' tell it to use the whole disk, that should over-write the 9.10.

Phill.

---

### Post by P4man on 2009-10-29
> **phillw said:**
> Sorry to hear the problems.. Boot with the 9.04 LiveCD, check it works, then select 'install' tell it to use the whole disk, that should over-write the 9.10.

Phill.

**Yes but it would also overwite / erase all documents and settings !!**

---

### Post by phillw on 2009-10-29
> **P4man said:**
> **Yes but it would also overwite / erase all documents and settings !!**


Erm, yeah ... I was assuming it was a new install.

If the OP does need a backup, I'll scribble down a tar script for the OP if I'm told the devices that are available to hold the backup on.

Phill.

---

### Post by Gazzz7472 on 2009-10-29
I ugraded through the Ugrade Manager so I am wondering if something got corrupted whilst downloading the files.

Am using Vista right now, which shows how desperate I am without Ubuntu.

I am going burn a LiveCD and try Ubuntu 9.10 from that.  Seems a shame to give up on it so soon.

---

### Post by phillw on 2009-10-29
> **Gazzz7472 said:**
> I ugraded through the Ugrade Manager so I am wondering if something got corrupted whilst downloading the files.

Am using Vista right now, which shows how desperate I am without Ubuntu.

I am going burn a LiveCD and try Ubuntu 9.10 from that.  Seems a shame to give up on it so soon.

As previously mentioned - do you have any data you want to save from your ubuntu area ?

Burn your CD at 4X speed (people have funnies at higher speeds)

Check the md5  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Phill.

---

### Post by Gazzz7472 on 2009-10-29
Great the LiveCD worked so my download through the Upgrade Manager must have got corrupted somehow.    :popcorn:

---

### Post by P4man on 2009-10-29
> **Gazzz7472 said:**
> I ugraded through the Ugrade Manager so I am wondering if something got corrupted whilst downloading the files.

Am using Vista right now, which shows how desperate I am without Ubuntu.

I am going burn a LiveCD and try Ubuntu 9.10 from that.  Seems a shame to give up on it so soon.

Its possible but unlikely. Unless Im horrible mistaken, downloads are also verified. There is only a very small chance of them being corrupted yet still passing md5 check. Im sure someone much smarter than me can even give you the exact odds, but Im guessing less than on in a million.

Anyway, you havent mentioned yet if your mouse is USB or PS2. If its USB and I assume your touchpad is internally connected through USB as well (though im not sure, do these things use ps2?), perhaps you're having a general USB or PS2 problem? Might be worth checking your bios if there is a setting set wrong somehow.

---

### Post by P4man on 2009-10-29
> **Gazzz7472 said:**
> Great the LiveCD worked so my download through the Upgrade Manager must have got corrupted somehow.    :popcorn:

ah our posts crossed. I still dont think so, more likely is something is wrong in the xorg.conf due to the upgrade. Try rebooting in recovery mode and recreate a default xorg.conf.

---

### Post by Gazzz7472 on 2009-10-29
Well seems touchpad is working ok after the install from the CD up to now.

I don't know much about the technical side of Ubuntu.  Perhaps I didn't click on an option correctly during the Upgrade Manager install.

Ext Mouse is USB no idea about trackpad though.

Thankyou for all your help so far.

---

### Post by P4man on 2009-10-29
> **Gazzz7472 said:**
> Well seems touchpad is working ok after the install from the CD up to now.

I don't know much about the technical side of Ubuntu.  Perhaps I didn't click on an option correctly during the Upgrade Manager install.

Ext Mouse is USB no idea about trackpad though.

Thankyou for all your help so far.

Oh if you're okay doing a fresh install than it no use figuring it out. Enjoy 9.10 and dont forget to mark this thread as solved :)

---

### Post by Gazzz7472 on 2009-10-29
Not sure how to mark the thread as solved.

---

### Post by phillw on 2009-10-29
> **Gazzz7472 said:**
> Not sure how to mark the thread as solved.

When everything is working, go back to your 1st posting, click on edit & you can then mark it solved.

(From memory !!!)

Regards,

Phill.

---

### Post by shadowlands on 2009-10-30
How do I enter in the line of information you provided? Everthing was working fine and then it asked me to update so I did and then after the up grade the screen was blue and my mouse is frozen my key board works.> **philinux said:**
> Restart the machine using this.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

at grub press esc.

Choose recovery mode. Then at the menu choose resume normal boot.

---

### Post by hatkirby on 2009-10-31
I'm having the same problem, and I don't want to reinstall the OS because I have a ton of data that would take a while to back up. The mouse does not move or click. Here is my xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I'm guessing the problem is the lack of a mouse InputDevice section, though the keyboard is lacking one too and it still works. I've tried automatically recreating the file, but nothing happens. What should I do?

---

### Post by P4man on 2009-10-31
Seems to be a bug on some machines:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/378818](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/378818)

If its indeed related to the kernel as ppl seem to suggest there, then you could try a few kernel boot options> Have a look here to see how:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

and here is list of options you could try:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

id start with the irqpoll option, and if that doesnt work the others relating to IRQs.

---

### Post by hatkirby on 2009-10-31
> **P4man said:**
> Seems to be a bug on some machines:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/378818](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/378818)

If its indeed related to the kernel as ppl seem to suggest there, then you could try a few kernel boot options> Have a look here to see how:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

and here is list of options you could try:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

id start with the irqpoll option, and if that doesnt work the others relating to IRQs.Thank you. I'll try that right away.

---

### Post by hatkirby on 2009-10-31
I tried that and some other kernel options but none worked. However, I finally realized that my GRUB menu was listing the wrong kernel version, it was booting into 28.15 instead of 31.14, so I modified my menu.lst and now my mouse (and other things) work. :)

---

