---
title: "Ubuntu won't start"
date: 2011-08-06
forum: General Help
---

### Post by ivanp on 2011-08-06
Hi,

I just run last night an update on my ubuntu 11.04 and asked for restart and won't start ever since. I don't even know what the update because I taught it was an usuall apdate as the many you get every week.

Now it shows gnu grub command line screen, minimal bash-like terminal, where yo can type a few commands. But boot command says error: no loaded kernel.

How to go back to previous state? 
Thanks in advance

---

### Post by garvinrick4 on 2011-08-06
Do you have a live Cd or Usb. (Install Cd using Try Ubuntu)?

---

### Post by sinbowden on 2011-08-06
I had the same problom and did not come to a favroble solution. i just reinstaled the previous version. 
   Did you receive an error Msg b4 the bash terminal log in screen?? also on a separate occasion not related to the same problem, my pc kept booting to bash log in. I rebooted my pc like 3 or 4 time and it finely booted normally (surprisingly) and i have found the same thing works After,  installing new video drivers and I initially boot to a blank screen... Can you become a root user? ```
 sudo -i 
``` or ```
 sudo -s 
``` or ```
  sudo su 
```

---

### Post by cdavid13 on 2011-08-06
I had a problem after an update on my desktop that it would boot to a blank screen unless I went into the boot manager and picked the which device I wished for it to boot from (weird). but it works for now.

---

### Post by ivanp on 2011-08-13
Thank you all for your replies.
I have Not gone any further, and here are some answers to your questions, but first I should mention my install is inside windows, so I can't (I believe) backup my files.

I do have now an USB with Ubuntu 11.04, but after restart and boot from it, the machine won't start and fail with Boot error.

Since I can't boot, sudo command is not recognized. Neither is su. All I have is a "gnu grub version -.99~rc1-13ubuntu3" terminal screen where boot command fails with No loaded kernel. Atually, the only command which is doing something apparently is reboot.

I really can't just reinstall without getting my files out of there. For two years I have only logged in into the ubuntu boot.

---

### Post by raja.genupula on 2011-08-13
what you are getting guys ? grub> or the problem is at grub with after selecting ubuntu to boot ?

---

### Post by Blasphemist on 2011-08-13
I really don't have any experience with wubi (ubuntu within windows) grub issues but I think the instructions for booting from the grub> or grub rescue> prompt should still work. Look at this document. [https://help.ubuntu.com/community/Grub2#GRUB](https://help.ubuntu.com/community/Grub2#GRUB) 2 Troubleshooting Preparation

Which of those prompts you are getting dumped to should guide you on what commands to use. This should allow you to get booted and when you do, copy your important files out. Then I'd reinstall or update grub but you should find documentation in the wiki on that and on converting to a non-wubi installation of ubuntu. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

In the wubiguide, there is this section on not being able to boot. [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

That section does point to this thread for further help. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by ivanp on 2011-08-14
Thank you for your replies, following the answers:

Yes, the prompt is grub>

Set returns the following list
?=0
color highlight=black white
Color normal= white black
Lang =
pager =
prefi = (memdisk)/boot/grub
Roto = memdisk
Show panic message = true

Trying to list the prefix folder returns an empty list. The same goes for (memdisk)/boot/. (memdisk)/ has one file: wubildr.cfg
Trying configfile (memdisk)/boot/grub/grub.cfg just cleans the screen
I never found any of the files the grub manual said I should...

None of the other file systems have a boot folder, neither does the one with the ubuntu folder inside (hd0,msdos4). (hd0,msdos4) has two files which might be of use wubildr and wubildr.cfg

---

### Post by bcbc on 2011-08-14
You need to find the root.disk file. If you can find it, you can copy data off it from windows. That seems to be priority #1, then trying to make it boot would be priority #2.

So, if you installed on C:, then it will be at C:\ubuntu\disks\root.disk

Report back if it's not there or there is no \disks folder.

If it is there, use this to copy data off it: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

---

### Post by ivanp on 2011-08-15
Awesome! I have recovered all my info with Ext2Read in the expected path.
Besides that, all files I was supposed to find when troubleshooting grub are inside this root.disk, initrd.img and a backup, vmlinuz file, the boot and grub folders.

So, priority #1 has been met. What's next?

---

### Post by bcbc on 2011-08-16
That's great! It is a bit strange that the root.disk was in the correct place, is accessible by ext2read - yet cannot boot.

I recommend trying to get your Ubuntu USB to work and then running the [bootinfoscript]("http://bootinfoscript.sourceforge.net"). But in the meantime, if you want to try this... boot Ubuntu and when you get to the grub prompt enter:

```
search -s -f -n /ubuntu/disks/root.disk
echo $root

```
That will tell you the partition that the root.disk is on, or give an error if it can't find it. Please post this info back.

Then you can try this:
```
loopback loop0 /ubuntu/disks/root.disk
```
That will create a loop device from the root.disk (or give an error).

If so far everything is working, try to load the grub menu:
```
configfile (loop0)/boot/grub/grub.cfg
```

See where that gets you and let us know what errors you find along the way.

---

### Post by ivanp on 2011-08-17
It's even weirder that after getting the files out I have started the machine to follow the new instructions and it booted as it never happened anything. It just checked the disks and is working like a charm.

Thank you all very much for your help!

Wait. Is there something I should do before claiming victory?

---

### Post by bcbc on 2011-08-18
That is a little weird. But also good that it's working again.

Maybe it's time to consider partitioning and [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi install (depending on how much you use Ubuntu). Wubi works great to try out Ubuntu, but at some point you're going to have to bite the bullet.

Or keep your backups current ;)

---

