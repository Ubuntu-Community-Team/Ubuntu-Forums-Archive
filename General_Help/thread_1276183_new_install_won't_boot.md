---
title: "new install won't boot"
date: 2009-09-26
forum: General Help
---

### Post by shawnisalk on 2009-09-26
Hi, there.


Here's what happens:
When I startup the machine, the Grub menu displays, but doesn't do anything. It is totally non-responsive. Hitting keys on the keyboard only causes the computer to beep.

I am trying to setup an IBM Thinkpad I Series 1400 with Linux. It worked fine with Windows on it.

I initially installed Puppy and struggled with it. Thinking a different distro might work where Puppy didn't, I installed Debian, with the same result.

Grub was the bootloader for both installs. Grub was installed in the MBR, in both cases. 

Debian liked the partitions I set up for the Puppy install, so I kept them.

So, the problem is not a hardware failure and it is not distro specific, nor is it Grub (a different version for each install), but I don't know what it is.

Could there be some problem with the MBR (even though the Windows install that was on it before was working)?

Anyone have any ideas?

---

### Post by blueridgedog on 2009-09-26
Since you can boot from the LiveCD, thinks must work at a basic level.  can you post the ouput of 

```
sudo fdisk -l
```

Also, you may want to try and reinstall grub.  Here are the standard instructions:

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by shawnisalk on 2009-09-26
Thank you for the quick response. I will post those things later today, for sure.

I've had a new discovery, though. When I ran fdisk, it said that the number of cylinders on the drive was 2432 and that anything over 1024 could cause problems with older boot software.

& I noticed that the Grub version was .97...

---

### Post by shawnisalk on 2009-09-27
I upgraded successfully to Grub2 and now the only problem is the CMOS battery is dead, so the system goes into FSCK automatically at the tail end of the boot process and wants to reboot every time.

But that's another issue.

Thanks for the help!

Shawn

---

