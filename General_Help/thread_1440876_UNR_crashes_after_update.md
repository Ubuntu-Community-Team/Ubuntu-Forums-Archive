---
title: "UNR crashes after update?"
date: 2010-03-28
forum: General Help
---

### Post by Slonda828 on 2010-03-28
Hi everyone,

 I run two UNR 9.10 (kernel is minor revision 20) boxes for my job, one for myself and one for another guy with whom I work. I have seen both of our netbooks crash at various times after installing updated software packages with apt. Everything will work fine once apt installs updated packages, and upon reboot everything looks normal. I can pick any of the available menu options from my Grub2 menu, and windows 7 boots fine. When I try to boot to UNR, the kernel panics after telling me that it has failed to mount the root file system because it cannot be found. Single user mode also fails once this happens. If I run any live cd that tries to mount the partition in question, it will panic the kernel and crash as well. I have to use my bootable USB stick (no CD drive on these netbooks), run a stripped down version of knoppix, skip attempting to automatically mount the bad partition, manually mount the partition on which linux resides, and run grub-install. Then once I reboot everything works fine. I have run fsck every time that this has happened, on my friend's netbook and mine, and everything checks out fine. If the partition were truly bad, I wouldn't think that I could mount it manually in knoppix. Plus, fsck never has to fix anything. This leads me to believe that it has something to do with grub 2, because running grub-install (which is just a bunch of scripts) fixes it. That makes me think it could be one of the stages of the boot loader somehow going bad. I am not sure how it works in UNR, but could the boot.img or core.img files  for grub get corrupted some how?

What in the world could be happening to cause this? Normally I run version 10 SUSE enterprise servers, and they run sysvinit and grub 1 so my knowledge here is a bit limited. It is a huge pain in the butt, because it has happened 3 times now between my EEE pc 1005HA and his aspireone ZG5. We are using these for work, so if they keep doing this I am going to have to switch them back to windows 7 because it is killing our ability to handle stuff on travel. I know there are bugs out there that mention similar things, and I have found some threads on here about similar happenings, but nothing looked remotely conclusive.

Has anyone seen this? Does anyone have and idea what causes it? Thanks in advance.

---

### Post by john newbuntu on 2010-03-28
Does UNR present you with other kernels that you could choose? If so, are you able to boot from an older kernel?

---

### Post by Slonda828 on 2010-03-28
It does, for example on my machine I could pick -14, -19, or -20. It fails to mount the root filesystem on all. This is what makes me think it is grub related, plus the fact that grub-install fixes it.

---

### Post by Slonda828 on 2010-03-28
Bump, does anyone know anything about this? Should I generate a bug report?

---

### Post by john newbuntu on 2010-03-29
Can you try booting from the grub prompt if you haven't already tried it before?

When you get your grub prompt, interrupt it by pressing any key and follow step 15 from the post below:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Note: Hitting the key C will get you into the CLI mode.

---

### Post by Slonda828 on 2010-03-29
If you are talking about specifying the root, pointing to a kernel manually from within the grub shell, and loading an init ram disk then I have already done this and it nets the same thing. If you read my post above, you can also note that when the box is in this state running UNR as a live CD produces the same effect (it crashes when it attempts to mount my linux partition). The only way I can get the system to boot at all is to use system rescue CD whilst setting it to NOT attempt to mount the partition that has linux on it (/dev/sda1). Then once I actually get in, I run fsck (which is clean), then mount the hard drive, jump into it, and run grub2-install --root-directory=/tmp/ /dev/sda and it runs the scripts. After that the machine runs fine. This only happens every once in a while when I install updates. 

I've done most of the simple stuff.

It just did it again last night on my friend's aspireone ZG5. I ended up having to run DBAN because this time his disk failed fsck (bad superblock) and I could not get it to pass or to mount even from system rescue CD. I nuked the hard drive, then reinstalled UNR and it is working again. It's an SSD (which I have never seen go bad), so I figured once I nuked it that everything would work. It works again now. If one of you developer types want me to try and snag some log files the next time this happens, let me know and I will try to do it. Of course, getting internet access is a problem when your machine is a paperweight. I do need to resolve this sooner rather than later, or I am going to have to find a more reliable distro. I can't keep messing with this stuff on travel.

---

### Post by spiderbatdad on 2010-03-29
Why not install legacy grub?
The end of this article:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Slonda828 on 2010-03-29
Is there any particular reason for *why* I should revert to grub legacy? I understand that the simple answer is because it is giving us grief, but I suppose as a thinking guy I kind of want to examine why it isn't working like it should. I hate to sound like a refusenik, but I would like a distro that functions like it should when you download it(with the exception of adding backports and such). Having a distro in my line of work that functions as it should out of the box makes it easy to deploy similarly configured systems for other people. If I have to walk everyone through installation, then install grub as well, that just means more time and more potential for the end user to screw it up and bring it back to me ;) Another thing to look at is that we are doing this so that we do not have to support windows on these machines (and pay for doing so). I cannot justify this as cost effective if I have to spend man hours on it that cost more than the cost of just buying windows 7. I know this is really neither here nor there, but a lot of non-linux types (the people for whom I am making these boxes) just want their stuff to "work".

My EEE pc 1005HA is tier 1, and so far this has only happened once. That I can deal with. My friend's aspire one, on the other hand, has done this three times now in a period of a month. I am thinking Jolicloud may be a better choice for that box, as it is tier 1 compatible with that distro. It may just be that UNR just doesn't work very well on the apsire one 110. 

Still, before we scrap it, I am open to ideas as to what is causing this. When I got it to crash last night, the only thing I did was open a terminal window, update apt, then install upgrades with it. It installed some upgrades, I rebooted, and it failed to mount the root filesystem again. Meh.

---

### Post by spiderbatdad on 2010-03-29
My understanding is that Ubuntu is based on Debian-Unstable.
It is a testing ground...hence a new release every 6 months, with things like grub2, gconf2, gdm2.28, etc...

BTW I'm running UNR on the Acer Aspire One...and it runs perfectly. I did have some issues with grub2 after adding Debian to another partition...I resolved the problem by installing legacy grub.

Lucid LTS is very close. Probably a clean install of the relased version will solve all problems.

---

### Post by Slonda828 on 2010-03-29
I'm dropping jolicloud on my buddy's aspireone 110 in the morning. I will let everyone know how it goes just so we do not leave this thing hanging ;)

---

### Post by Slonda828 on 2010-03-30
Dude, JolieCloud rocks on the Acer AspireOne 110 (or ZG5). I have installed sysv-rc-conf and turned off all extra services and this thing boots QUICK, even with a first generation SSD. So far I have zero issues to report. The WIFI LEDs work, you can hot swap SD cards, it can actually connect to hidden wireless networks, and it doesn't crash when you close the lid. I couldn't do any of those things with UNR 9.10 on this machine. Kudos to the JolieCloud people!

In defense of UNR I still have zero issues with it on my EEE pc 1005HA, and have no plans of removing it :) I still love UNR too.

---

### Post by spiderbatdad on 2010-03-30
I looked at jolicloud, thanks for making me aware of it. I'm interested, and downloading now to give it a test run.

Gave Jolicloud a try out. It's ok. Seems a little buggy. Anytime I tried to edit preferences of the file browser...the application crashed. All windows are maximized with no buttons, and unlike Ubuntu, I couldn't find Maximus to disable in startup applications. I'm sure with some work I could have found a way, but it wasn't intuitive, and since it's built from Ubuntu, one would think something like that would behave the same. There were too few media applications for my taste. Instead more of a focus on social networks.

I did like the animation of icons a la KDE. But overall it isn't for me. UNR is more polished, behaves as expected, and feels more like a computer. Chromium and Facebook pre-installed on Jolicloud raised an eyebrow...um

---

### Post by Slonda828 on 2010-03-31
Isn't it crazy how some distros work so much better on different hardware? UNR on the aspireone ate icons, crashed, wouldn't mount SD cards, etc. Jolicloud on that same machine works flawlessly. For your machine it is the opposite. I would like to see a better hardware compatibility list out of the end user desktop distros. The nice thing about the enterprise distros is that you can literally check the HCL for everything you have and then be fairly certain that the distro will perform as advertised. I wish we had that in the desktop world sometimes :/

---

