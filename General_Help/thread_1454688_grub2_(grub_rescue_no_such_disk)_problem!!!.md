---
title: "grub2 (grub rescue no such disk) problem!!!"
date: 2010-04-15
forum: General Help
---

### Post by sjnovick on 2010-04-15
Hi all.  I just installed Ubuntu 10.4 beta.  The installation is fine, but grub2 isn't loading Linux.

Instead of booting into the OS, I get the message:

No such disk
grub rescue >


I have two hard drives:  /dev/sda and /dev/sdb.
Ubuntu is the only OS and is located on /dev/sda1.

I ran the "boot info" script and include the results here.

One problem I see is that I have grub2 on the MDRs of both /dev/sda and /dev/sdb.  

BTW:  From the Live CD, I can select boot into hard drive and Ubuntu will start up just fine.  I can also use "Super Grub" CD and everything loads fine.

Help???

---

### Post by john newbuntu on 2010-04-15
Somehow Grub is finding problems with grub.cfg.  Once you get to the rescue mode, type the following commands one after the other:

```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img
boot

```

If this gets you to boot into Ubuntu, run:
```
sudo update-grub2
```
Hopefully the next reboot should get you straight to Ubuntu

For more details, you can refer:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by sjnovick on 2010-04-15
Thank you for your reply!  I wished that worked, but it didn't.

I did this:
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro quiet splash

File not found.

Then I tried:
set root=(hd0,1)
set prefix=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro quiet splash

Still file not found.
In both cases above, I it would not find anything with
ls /boot/grub

Finally, I tried (not knowing if this is close to correct!):
set root=(UUID=632963c1-c35e-4adb-b39e-0a40eef51702)
set prefix=(UUID=632963c1-c35e-4adb-b39e-0a40eef51702)

Now, ls /boot/grub  shows me the grub directory contents.

But,

insmod /boot/grub/linux.mod

results in file not found.   :(


Help, help, help!!!

---

### Post by john newbuntu on 2010-04-15
Ok. Lets try re-installing grub2 by following step 13 in this post by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Immediately after you boot into Ubuntu, run "sudo update-grub2"

If that failed, read this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by oldfred on 2010-04-15
Are you booting sda and not sdb. The UUID in the grub from sdb does not exist so it will give errors. The grub in sda looks ok. Check BIOS or single boot with f12 or single boot key on BIOS screen.

---

### Post by sjnovick on 2010-04-15
Problem solved!  Thanks for all your help!  The issue was that I somehow have grub2 installed on both of my hard drives.  In my BIOS (CMOS?), I needed to change the boot order of those two drives and everything worked!

---

### Post by Mark Muhandiramge on 2011-01-15
I have ubuntu 10.4. It says "no such disk found" What shall i do now? I need immediate assistance...

---

### Post by Quackers on 2011-01-15
It would be better to start your own thread giving details of what has happened. Also if you can include the boot script output, it will help.

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

