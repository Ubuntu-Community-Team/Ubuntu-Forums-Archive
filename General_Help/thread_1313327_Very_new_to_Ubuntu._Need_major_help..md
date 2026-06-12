---
title: "Very new to Ubuntu. Need major help."
date: 2009-11-03
forum: General Help
---

### Post by end0citizen on 2009-11-03
I had been running Ubuntu 9.04 and Windows Vista (dual boot). I then upgraded to 9.10. When I'd go to 9.10, my cursor would not respond to movements of the mouse and I could not connect to any network.

I restarted to my Windows side, removed the Ubuntu partition, downloaded the 9.10 iso, and restarted with the 9.10 disc. It got 60% of the way through installing when I got an error message. It then kicked me over to the Ubuntu CD environment (or whatever it's called).

I restarted without the disk. I am now unable to boot to either my Windows side or Ubuntu side, despite both being present on the hard drive.

I get the following message:
```

Loading Grub (I forget the number here)

Error 15

```I can now only boot with the CD.

I'd appreciate any help, but I am very new to Ubuntu or Linux at all. I looked at this thread:

[http://ubuntuforums.org/showthread.php?t=43591](http://ubuntuforums.org/showthread.php?t=43591)

I don't understand what most of it means, though.

Thank you for any help.

---

### Post by snowpine on 2009-11-03
Hi end0citizen, welcome to the forums!

You have a decision to make... do you want to 1) get 9.10 working right away? or 2) get your computer fixed as soon as possible?

I can't really help you with #1... 9.10 has problems on my computer, so I'm sticking with 9.04 for a while. 9.04 works fine for my needs, and will be fully supported through Oct. 2010. If you decide to proceed with 9.10, you should spend some time with the Live CD... can you get the mouse/cursor and networking to work using the Live CD? If they don't work with the Live CD, they probably won't work after you install either. :)

The immediate problem is that your install failed and your system is unbootable. (But hopefully, your Windows install is still there... you just can't boot it because of the aborted Ubuntu install.) The solution is to reinstall Ubuntu... I am assuming you know how to do this from when you set up 9.04 dual boot with Windows? Good. Well, you can reinstall 9.04 and get back to work right away... or you can try again with 9.10 if you want. Good luck!

---

### Post by end0citizen on 2009-11-03
Thank you. I'd like to be able to run 9.10, but I guess I'll try that and let you know.

BTW- I am currently using the computer that has the problem. So, yes my cursor and networking work on here. 

Once everything is working again, I'll be back.

or (the bad alternative)

I'll return on Live CD.

---

### Post by snowpine on 2009-11-03
9.10 Live CD is working okay? That's a good sign. :)

I suggest checking the CD for errors... you can do this from the very first screen after you boot with the CD in the drive. (A burn error on the CD might explain why the install failed at 60%.)

Assuming the CD is okay, it's worth trying the install again. :) Make sure you pay attention during the Partitioning step so that you replace the (failed) Ubuntu install, but keep the Windows partition for the dual boot.

---

### Post by coffeecat on 2009-11-03
I'll explain the grub business first.

When you upgraded from 9.04 to 9.10, you retained what is now called legacy grub. That has several parts, but the most important are:

stage 1 - about 400 bytes which resides in the first part of the MBR (master boot record).

stage 1.5 - which is a few kilobytes in size and resides in an otherwise unused part of the hard disc immediately after the partition table.

stage 2 - which can be found in /boot/grub of you root partition.

/boot/grub/menu.lst - this is the configuration file.

When you tried to do a fresh install of 9.10, it first of all reformatted your root partition (so that you lost stage 2 and menu.lst), wrote about 60% of the installation, but then failed before it could install grub2 (which is what comes with a fresh install of Karmic) and write grub2's stage 1 and stage 1.5 to the HD.

So now when you try and boot up, legacy stage 1 (which is still there) calls stage 1.5 which has nowhere to go because there is no stage 2 nor menu.lst for it. Hence the error message, which is terse because legacy grub has to squeeze into a small space -  no room for much code.

So - if you manage to do a fresh re-install of Ubuntu, grub (in some form or another) will get reinstalled and you'll be able to boot into Vista again.

Options:

You could try reinstalling 9.10 again, preferably with a freshly burnt CD in case the one you used was faulty - although that's unlikely if you can boot up with it. Disadvantage - you may get a failed install again. Advantage - you might get lucky a second time.

Or you could try reinstalling 9.04 as you know this works.

If you need some thinking time, but want to get into Vista in the meantime, download yourself [SuperGrubDisk]("http://www.supergrubdisk.org/"), burn it to CD and start up with it. There are two options in the highly user-hostile menu. One to simply boot Windows, the other to repair the Windows MBR and then boot up. That at least will restore you to a single-booting Windows environment for the time being.

If I were you, I'm not sure what I would choose between 9.10 and 9.04. Since 9.10 runs off the CD it *ought* to install, and perhaps this was a one-off mishap. On the other hand, 9.04/Jaunty is a damn good version and will be supported for another year.

---

### Post by end0citizen on 2009-11-03
Thanks everyone for the help, especially the explanation about grub.

I'm now on 9.10 and it is working fine :)

---

