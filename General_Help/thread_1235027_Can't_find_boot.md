---
title: "Can't find boot?"
date: 2009-08-08
forum: General Help
---

### Post by Pete Zafase on 2009-08-08
Hi I have used Ubuntu a couple of month, so I am pretty much a noob when it comes to Linux.
I think what have happened is that the grub won't find my original boot anymore.
I was using Spotify trough Wine, when suddenly Spotify crashed, and made this horible noise (like a chainsaw).
And the whole computer froze, so I just turned the computer off with the off-button.

(I am btw using Ubuntu Jaunty, on a Packard Bell laptop)

When I turned the computer on again I got a black screen with following message:


Kinit: Name_to_dev_t(/dev/disk/by-uuid/dd3180d2-3fe4-45be-816b-30bd5a5a8648 ) = dev(8,5)
Kinit: Trying to resume from //dev/disk/by-uuid/dd3180d2-3fe4-45be-816b-30bd5a5a8648
Kinit: No resume image, doing normal boot....

Mount: Mounting /dev/disk/by-uuid/d849cf8a-7ba3-44fd-8830-843c8fbf6678 on /root
Failed: Invalid argument
Mount: Mounting /dev on /root/dev failed: No such file or directory
Mount: Mounting /sys on /root/sys failed: No such file or directory
Mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootarg

This happened first once, but suddenly the computer worked as normal again. But after a couple of days the same problem occured, with the same message.

I have looked for help in a Norwegian Ubuntu-forum, where they wanted me to boot from live-cd, and write this in the terminal:

mkdir ~/Desktop/harddrive
sudo mount -rw /dev/sda1 ~/Desktop/harddrive
sudo chroot ~/Desktop/harddrive
sudo aptitude reinstall ubuntu-minimal

But it didn't help. 

So I hope someone can help me with my problem. Also, I am not steady on Ubuntu/Linux so please be patient with me. I need an easy step-by-step guide.
In advance, thanks.
-Pete Zafase

---

### Post by Pete Zafase on 2009-08-08
Also:
When I wrote the code in the terminal window I got this back:

ubuntu@ubuntu:~$ mkdir ~/Desktop/harddrive
ubuntu@ubuntu:~$ sudo mount -rw /dev/sda1 ~/Desktop/harddrive

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo chroot ~/Desktop/harddrive
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo aptitude reinstall ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  ubuntu-minimal 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 28.0kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main ubuntu-minimal 1.140 [28.0kB]
Fetched 28.0kB in 0s (97.8kB/s)     
(Reading database ... 105940 files and directories currently installed.)
Preparing to replace ubuntu-minimal 1.140 (using .../ubuntu-minimal_1.140_i386.deb) ...
Unpacking replacement ubuntu-minimal ...
Setting up ubuntu-minimal (1.140) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


And yeah, my harddrive is sda1 as far as I know.
-Pete Zafase

---

### Post by Pete Zafase on 2009-08-08
I did also run memtest, but I got no errors.

Do anyone know how to fix this problem? I have searched many sites, but no one can help me!

---

### Post by Pete Zafase on 2009-08-09
*bump*

---

### Post by gabry79Italy on 2009-08-09
Boot from a live cd
terminal:
sudo -s
fsck -r /dev/sda1
fsck -p /dev/sda1
exit
reboot pc
if those don't work boot again from live and :
sudo fdisk -l

---

### Post by martinbaselier on 2009-08-09
The sound and the randomness of the problem suggest a defect hdd. It would suggest you to follow Gabry's tips though and maybe this will help. It can at least show you the hdd problems.

---

### Post by Pete Zafase on 2009-08-09
Dude, it worked!
Thank you very much!

But I didn't think of copying the terminal window, so I can't remember what it said. At least my computer work again.
Should I stop using Spotify through Wine? And is it a native Spotify for Linux yet?

And also, is it usual for Ubuntu Jaunty to crash, or have errors? Should I change my distro?

Thanks for the help!

---

### Post by Pete Zafase on 2009-08-09
And now I got another problem. This is slightly easier to fix though.
When my original Ubuntu boot was f*cked, I made a new Ubuntu boot side by side with my original. How do I remove that one now?

---

### Post by gabry79Italy on 2009-08-10
Boot from your ' original ' ubuntu , open 'gparted' or 'partitions editor ' umount the partition of the 'new' ubuntu you wanna remove and then delete such partition and format this into fat32 
I'm sorry for my bad English

---

### Post by P4man on 2009-08-10
> **Pete Zafase said:**
> 
Should I stop using Spotify through Wine? And is it a native Spotify for Linux yet?

didnt know spotify, but their download page suggests using wine, which both means there is no native client, but also that is will probably work.

Either way, its highly unlikely spotify caused your problems. It might crash, but even then it wouldn't render ubuntu in an unbootable state. The "chainsaw" sound you heard, did it come from your speakers, or from the machine itselve?

> 
And also, is it usual for Ubuntu Jaunty to crash, or have errors? Should I change my distro?


Hehe.. well, i wouldn't go as far as saying that ubuntu is completely free of any issues, but what you are seeing is anything but normal. Without wanting to jump to conclusions, I would strongly suggest you make a backup of stuff you dont want to lose, because your harddisk might be dying.

---

### Post by Pete Zafase on 2009-08-10
> **gabry79Italy said:**
> Boot from your ' original ' ubuntu , open 'gparted' or 'partitions editor ' umount the partition of the 'new' ubuntu you wanna remove and then delete such partition and format this into fat32 
I'm sorry for my bad English

Don't worry about your English. I'm a Norwegian, so I ain't that steady myself.

Do you think you could explain more detailed? Where do I find 'gparted' or 'partitions editor'? 
And how do I format that into fat32?
Thanks for answering btw!

---

### Post by Pete Zafase on 2009-08-10
> **P4man said:**
> didnt know spotify, but their download page suggests using wine, which both means there is no native client, but also that is will probably work.

Either way, its highly unlikely spotify caused your problems. It might crash, but even then it wouldn't render ubuntu in an unbootable state. The "chainsaw" sound you heard, did it come from your speakers, or from the machine itselve?



Hehe.. well, i wouldn't go as far as saying that ubuntu is completely free of any issues, but what you are seeing is anything but normal. Without wanting to jump to conclusions, I would strongly suggest you make a backup of stuff you dont want to lose, because your harddisk might be dying.


Yeah, I use Spotify through Wine. It's ok, but it crashes from time to time. But they have realesed there codes and so on, so a third part can make a linux native client.

And the "chainsaw" sound came from the computer itself i think. But it did only happen when I had Spotify open, and Spotify crashed.

Yeah, but is the older versions of Ubuntu more stable than Jaunty? And I guess I have to see what happens.

---

### Post by P4man on 2009-08-10
> **Pete Zafase said:**
> Yeah, but is the older versions of Ubuntu more stable than Jaunty? 

Hard to tell. With every new release, old bugs get squashed, and new ones get introduced. But its only the bugs that bite you that.. well, matter

That said, I wouldn't call any ubuntu release since 6.x unstable. Unless you happen to run a machine that for some reason doesn't play nice with it. 

To give you an idea, my main computer runs jaunty, and I can't remember what boot splash I put on it. I hasn't been  rebooted in like.. well, lets check:

bob@bob-desktop:~$ uptime
 22:21:34 up 16 day,  4:56,  8 users,  load average: 0.45, 0.33, 0.23

16 days. Thought it was longer, I guess I must have gotten a new kernel then or something :) Anyway, I remember being impressed by the quick boot time, but on second thought.. who cares lol.

One of my secondary machines locks up like every 2 hours or so. But its a hardware issue I havent found yet, as since this morning I can't even get in the bios anymore;

---

### Post by Pete Zafase on 2009-08-10
Ahh, I see.

And I found the partitions editor, but I can't delete, or remove sda2. Can anoyone help?

---

### Post by P4man on 2009-08-11
you may have to unmount it first. In gparted just right click it, chose unmount.

edit: not sure why you want to delete it though. Can you say again what you intend to do?

---

### Post by ubudog on 2009-08-11
> **gabry79Italy said:**
> Boot from a live cd
terminal:
sudo -s
fsck -r /dev/sda1
fsck -p /dev/sda1
exit
reboot pc
if those don't work boot again from live and :
sudo fdisk -l

Should work.

---

### Post by Pete Zafase on 2009-08-11
Yes, id did work very well.

Because I made another boot when my original sda1 went to h*ll, so I could still use my computer. And now I don't need it since sda1 works again. And it's very annoying to have to choose which one I am going to boot every time I turn the computer on. I just want it to boot from sda1 from the start. And I don't need sda2 anymore, so I want to remove it.

---

### Post by gabry79Italy on 2009-08-11
Are you sure the partition is sda2? Check well before deleting a partition...open gparted and check it or run in terminal sudo fdisk -l 
and check it...

---

### Post by Pete Zafase on 2009-08-11
I have always used sda1, and I never had sda2 before, so yes.
And I got very low memory on sda2, and very much on sda1, so I guess it's sda2 I'm gonna remove.

Eitherway, if I should f*ck up, I do got backup on a memorystick.

---

### Post by Pete Zafase on 2009-08-11
Don't work to unmount it, nor delete it!

---

### Post by gabry79Italy on 2009-08-13
Try to do that after booting from a live cd

---

### Post by Pete Zafase on 2009-08-14
I deleted the other partition now, but when I try to boot I get this:
Grub loading... Please wait.
Error 22

Sda1 is fully intact though. But the computer wont boot.

---

### Post by gabry79Italy on 2009-08-15
You should reinstall grub, try to boot from live and run
sudo grub installa /dev/sda

---

