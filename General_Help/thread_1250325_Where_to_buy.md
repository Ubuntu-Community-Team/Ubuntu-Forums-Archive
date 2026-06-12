---
title: "Where to buy?"
date: 2009-08-26
forum: General Help
---

### Post by Silvernail on 2009-08-26
Suggestions please, where to go to buy the latest stable version of Ubuntu?

---

### Post by Bucky Ball on 2009-08-26
Can't you download the ISO? And I recommend 8.04 LTS (Long Term Support). It is the most stable around at the moment as is the oldest version currently supported.

---

### Post by M!K3_$ on 2009-08-26
Either download the .iso file from [www.ubuntu.com](www.ubuntu.com) and burn it.
or 
you can request a free cd from that site.

---

### Post by FeTTo on 2009-08-26
go to ubuntu.com and request a cd from them...i did and got it in less than 1 week. its 9.04, jaunty , the best version IMO. 10x better then hardy and its free, or you can just dl the iso like Bucky said from ubuntu.com and rip it to a cd. however i had many problems with disk errors that way.

---

### Post by Bucky Ball on 2009-08-26
> **FeTTo said:**
> ... you can just dl the iso like Bucky said from ubuntu.com and rip it to a cd. however i had many problems with disk errors that way.

Always use the torrent version. Checks md5 on way down and is quickest and safest way. The option for the torrent file is toward the bottom of the download page. 

And ALWAYS hit the 'Check disk for defects' option in the install menu before installing. :)

---

### Post by boof1988 on 2009-08-26
> **Silvernail said:**
> Suggestions please, where to go to buy the latest stable version of Ubuntu?

All of the previous suggestions are good...

If you really want to go to a brick-and-mortar store to buy an Ubuntu disk...

[LIST=1]
[*]Maybe try Best Buy, Microcenter etc.  There's usually a section that has various linux's as well as other software.  I've seen them around $3-$6 USD.
[*]One other option... is to buy a Linux or Ubuntu magazine at a local bookstore... Just make sure to pick one that comes with an installation disk in it.  I've seen them around $10-$15 USD.
[/LIST]

---

### Post by scouser73 on 2009-08-26
Look in my signature for getting Ubuntu.

---

### Post by jmszr on 2009-08-26
Silvernail,

Ubuntu (and other GNU/Linux distributions) can be found through here:[http://distrowatch.com/](http://distrowatch.com/)

Ubuntu is US$1.68 plus shipping (?).

---

### Post by Silvernail on 2009-08-27
First, THANKS for all the replies.
Long story short, I screwed up royally on an installation on a new computer.

Could not get my CD 8.04 to install.
Finally got a flash drive 7.10 to install.

Dropped my 8.04 back in and it started to upgrade/install.
After several attempts I'm getting "Hash Sums Mismatch".

I know what Hash Sums are but thats it.
What should I trouble shoot for?

PS
I now have 6 flavors of 2 different kernels on the HD. I would like to wipe everything clean. HOW?

Thanks.
d

---

### Post by scouser73 on 2009-08-27
Here is a tutorial for removing old kernels from the Grub menu: [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by Silvernail on 2009-08-27
> **scouser73 said:**
> Here is a tutorial for removing old kernels from the Grub menu: [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

Sound like just what I need. But I can not get it to load. Is this the complete path?
```
http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/
```

Thanks
Dave

---

### Post by cariboo on 2009-08-27
Try [this]("http:///www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/") link, it works.

---

### Post by Bucky Ball on 2009-08-27
I personally suggest you download the alternate ISO of 8.04 LTS via a torrent, boot from that and see how you go. Run 'Check disc for defects' from the options before you install.

---

### Post by Silvernail on 2009-08-27
I am not sure I understand what is happening.

I insert the Hardy 8.04 CD in the cdrom drive
It mounts and puts an icon on the desktop
The fill bowser comes on the screen and shows me the content of the CD

Several different places I have seen the 'xclient-base' is broken
the install procedure shows this
'sudo dpkg --configure -a' shows 'xclient-base' broken.

Go to synaptic-manager and under broken shows 'xclient-base'.
Down at the bottom it says xxx to install 0 broken.

Flag xclient-base  to install on synaptic-manager.
It can not find the CDrom.

---

### Post by Silvernail on 2009-08-27
> **Bucky Ball said:**
> I personally suggest you download the alternate ISO of 8.04 LTS via a torrent, boot from that and see how you go. Run 'Check disc for defects' from the options before you install.

Sorry I did not mention this before. I have a copy of 8.04. I tthink I am going have to admit its corrupt.

---

### Post by Silvernail on 2009-08-27
Where/How do I get to 'multiverse' and 'universe' for Gutsy 7.10?

Thats the only OS I can get to boot on that new machine. And it is the  only DVD burner I have. None on this laptop.

Then where is the torrent howto. Not the manual that just says this does this.

---

### Post by ubudog on 2009-08-27
> **Bucky Ball said:**
> Can't you download the ISO? And I recommend 8.04 LTS (Long Term Support). It is the most stable around at the moment as is the oldest version currently supported.

Yeah just do that, although I like the Jaunty Jackalope, much faster, but Hardy is pretty cool too. :P

---

### Post by Bucky Ball on 2009-08-28
Um, you need to boot from the CD, not just insert it. Get into your BIOS and change the boot order to kick off from your CD first, not the hard drive. You probably need to hit Delete, escape or F1 to get in there (it can vary, F2 on my desktop which is unusual).

For torrents you use Transmission (Applications->Internet). Download the torrent file from the download page, open Transmission and then add the torrent file. That should start to come on down the line pretty quickly. 

You'll find the torrent files if you scroll down the page a bit here (ends with .iso.torrent):

[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

Choose the appropriate one for your machine (Alternate, i386 if 32 bit, AMD64 if 64 bit) and download.

---

### Post by Silvernail on 2009-08-28
As if 2:30 this Friday morning everything is as it should be.

A first for me. Having used Linux since '99, this is the 1st time I have downloaded and burned an ISO image. It went smoothly and worked.

Let me say thank you to all of you for putting up with me and giving me good feedback.

Thanks guys
Dave

ps will someone marked this solved

---

### Post by Bucky Ball on 2009-08-28
A pleasure, good news and welcome to the fold. Post back with any further issues. :)

---

