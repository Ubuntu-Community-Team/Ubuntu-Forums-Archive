---
title: "Editing boot list"
date: 2010-08-29
forum: General Help
---

### Post by Ozlanthos on 2010-08-29
I am new to Linux and am having a small issue. I've been using Ubuntu for a little while, but being primarily a windoze user, I'm not quite use to using programs like xterm. Seeing as I have had Ubuntu on my machine for a while, (over several versions of Ubuntu) I've had boot-loaders for the numerous iterations of Ubuntu accumulating in my boot list. Is there any way to get rid of the boot loaders for versions of Ubuntu that I'm no longer using? Also I'd like to change the order of the remaining boot loaders in my list.

-Oz

---

### Post by mikewhatever on 2010-08-29
All those entries you see at boot are old Linux kernels, and It would make sense to uninstall all but the latest version.
The following command will print all currently installed kernel versions, please run it and post the output.

dpkg -l | grep linux-image

---

### Post by Ozlanthos on 2010-08-29
ii  linux-image-2.6.31-17-generic        2.6.31-17.54                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-21-generic        2.6.31-21.59                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-22-generic        2.6.31-22.63                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                  2.6.31.22.35                             
    Generic Linux kernel image

---

### Post by Quackers on 2010-08-29
You can use Ubuntu-tweak for that. See this thread
[http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+entries+grub](http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+entries+grub)

---

### Post by mikewhatever on 2010-08-29
> **Ozlanthos said:**
> ii  linux-image-2.6.31-17-generic        2.6.31-17.54                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-21-generic        2.6.31-21.59                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-22-generic        2.6.31-22.63                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                  2.6.31.22.35                             
    Generic Linux kernel image

Run the command below to remove the older kernels.

```
sudo apt-get --purge autoremove linux-image-2.6.31-17-generic linux-image-2.6.31-21-generic
```

---

### Post by Ozlanthos on 2010-08-30
Ok so I ran that little ditty, and now when I "dpkg -l | grep linux-image"
I get
ii     linux-image-2.6.31-22-generic           2.6.31-22.63
     Linux kernel image for version 2.6.31 on x86
ii    linux-image-generic                                   2.6.31.22.35
     Generic Linux kernel image

and several kernels still showed up in grub when I restarted. Any suggestions?
I tried to address this issue in my LUG and several different things that we tried didn't seem to rectify the issue either....

-Oz

---

### Post by tardis0011 on 2010-09-02
I know a GUI way ;) :
Install Ubuntu Tweak and then open it up
Click on Package Cleaner on the left
Then click on Clean Kernels
Then click on Unlock
And now finally click on Select All and then Cleanup

I hope this helps!

---

### Post by mikewhatever on 2010-09-03
> **Ozlanthos said:**
> Ok so I ran that little ditty, and now when I "dpkg -l | grep linux-image"
I get
ii     linux-image-2.6.31-22-generic           2.6.31-22.63
     Linux kernel image for version 2.6.31 on x86
ii    linux-image-generic                                   2.6.31.22.35
     Generic Linux kernel image

and several kernels still showed up in grub when I restarted. Any suggestions?
I tried to address this issue in my LUG and several different things that we tried didn't seem to rectify the issue either....

-Oz

That looks alright. You only have one kernel now, 2.6.31-22-generic. Are you sure those are older kernels in the grub menu? There are several entries by default,
the kernel
the recovery mode
memtest
.

---

### Post by johnonfire on 2010-09-18
@ Ozianthos
Is your computer dual boot with more than one linux OS on it?  My system is dual boot with Lucid on one partition and Karmic on another, but they share a common /boot folder (as a separate partition, which is pretty standard).

Each OS has its own set of kernels installed, but the files for them are all stored in /boot and the update-grub command builds its menu based on those existing files.  When I run the "apt-get purge" command, it will only purge old kernels that are installed on the OS I'm running, so in order to really clean out the grub menu, I had to boot into Karmic (which I never use anymore, just keep around in case Lucid gives me stability problems) and run the purge command in there.  This will clean out the remaining "phantom" kernels in the /boot folder and the update-grub will then clean up grub.

Hope this helps.

By the way, even if your multi-boot system doesn't share a common /boot folder with all your OS partitions, update-grub will still find all your boot folders and build a grub menu based on all installed kernels.

---

