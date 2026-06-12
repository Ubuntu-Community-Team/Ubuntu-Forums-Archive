---
title: "Grub2 Boot Menu"
date: 2010-07-24
forum: General Help
---

### Post by TheSe7enth on 2010-07-24
I just installed Ubuntu recently (this morning, even), after having played around with it for a long time (several months) on VMWare. I decided since VMWare used more memory to run two OS at once (physical and virtual), I would install Ubuntu on a secondary drive to run it as a physical. All went well, considering I'm typing this from it now...except that I can't access Windows XP when I start up in the boot menu.

It lists two options, Windows 7 and Ubuntu. Windows 7 was the first one I installed, then I went back and installed XP (and yes, it's possible, using a few programs and the install CD of 7 to do a repair), and _then_ installed Ubuntu. Windows 7 is on it's own 250 GB (which would be "hdd0,1", I assume), while Ubuntu and XP are on the same drive (assuming as "hdd1,2" and "hdd1,1" respectively; XP was installed first, as noted earlier).

I've read online about several things such as editing the "40_custom", or creating your own file in the /etc/grub.d folder, but there's a problem. ... even using "sudo su" to give myself root/admin privileges, there's still a 'permission denied' error if I try to drag & drop a new file, and if I try to open 40_custom in gedit, it simply doesn't allow me to type anything in the program.

Forgive me if I seem unintelligent when it comes to Ubuntu, I'm a Windows person. I wouldn't be on a support forum if I knew anything about Ubuntu, but admittedly, I know nothing about Unix... I've only used Windows since the '95 days (which is scary, seeing as how I was born in '91). I'll appreciate any feedback I can get.


On another note, if anyone knows what causes a PS/2 ball mouse to start moving and clicking erratically on Ubuntu, or freezes up entirely on XP or other Windows OS, I could use the help with that too. The ball and rollers are clean, the PS/2 port and mouse are both fine as far as I can tell, but it may just be that I need a new mouse.

---

### Post by cj.surrusco on 2010-07-24
Are you sure that you are running the command properly? Just want to double-check, because I can't see any other reason why you would have this problem. In this case it would be:
```
sudo gedit /etc/grub.d/40_custom
```

---

### Post by amsterdamharu on 2010-07-24
gedit is a graphic program for that you can use gksu.

Press alt+F2 and type ```
gksu gedit
``` Not you have gedit open as root.

You could open nautilus (file browser) this way but it's a bit dangerous since you might accidentally delete things.

---

### Post by TheSe7enth on 2010-07-24
> **amsterdamharu said:**
> gedit is a graphic program for that you can use gksu.

Press alt+F2 and type ```
gksu gedit
``` Not you have gedit open as root.

Okay, that did work. Now gedit allows me to edit the file. Once again, forgive my lack of knowledge, I'm completely inexperienced with Ubuntu on even an intermediate level. I've only worked in support with Windows for years, this is my first venture into Unix, but not knowing what's right and wrong does make it a very confusing and scary experience so far. Haha.


Correct me if I'm wrong here, but the right command to add Windows XP as an option would be:

```
#!/bin/sh -e
echo "Adding Windows XP to GRUB 2"
cat << EOF
menuentry "Windows XP Professional" {
set root=(hd1,1)
chainloader +1
}
EOF
```

Right? I mostly relied on other pages and just saw how the code worked, and put it all together into one code that seemed about right to me; but while that might work with Javascript, C++, and other codes, I'm not sure about Unix, so I thought it was best to ask before I try anything stupid.

---

### Post by amsterdamharu on 2010-07-24
What you can try first is boot into ubuntu and do the following: Press alt+F2 and type "gnome-terminal" then run the following command:
```
sudo update-grub
```Restart and see if windows is in your menu. 

If not:
Here is the content of my /etc/grub.d/40_custom file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 78e8cac6e8ca823c
    drivemap -s (hd0) ${root}
    chainloader +1
}

```The uuid of the disk is probably different on your computer so you need to find out what the uuid of your windows partition is. (My XP is on the first partition of the first harddisk).

You can do that by running the boot info script and post the results here:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I can check not only the uuid but also the partition windows xp is on if it's found.

---

### Post by TheSe7enth on 2010-07-24
> **amsterdamharu said:**
> What you can try first is boot into ubuntu and do the following: Press alt+F2 and type "gnome-terminal" then run the following command:
```
sudo update-grub
```Restart and see if windows is in your menu. 

If not:
Here is the content of my /etc/grub.d/40_custom file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 78e8cac6e8ca823c
    drivemap -s (hd0) ${root}
    chainloader +1
}

```The uuid of the disk is probably different on your computer so you need to find out what the uuid of your windows partition is. (My XP is on the first partition of the first harddisk).

You can do that by running the boot info script and post the results here:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I can check not only the uuid but also the partition windows xp is on if it's found.

I did try updating grub, with no success. It simply refuses to find XP at all... I did find that XP installed on two partitions -- one "System Reserved" and one for XP's documents and settings, etcetera -- but the boot.ini is in System Reserved and still isn't detected by grub. And I have checked the boot.ini to check what partition it is, and it's listed as:

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP on D:\" /fastdetect
```

I assume that would mean hdd(1,1). That script you listed though says "sdb2", so I'm not entirely sure...

Out of curiousity though, what are the "drivemap" and "search --no-floppy" parameters for? Would they be necessary in my code, or no?


Edit: I looked a bit farther into the results file, it is indeed sdb1; sdb2 is the "swap partition", while sdb3 is Ubuntu. sdb5 apparently is unallocated space. Why it skipped sdb4, I don't know, but that is the order they were installed in. XP, swap partition, Ubuntu, and left the unallocated space alone.

Second edit: I figured out what that 'search' parameter was when I looked at it again. I found the UUID and everything, so I modified your code to suit mine, saved the file, and will update Grub then reboot to see if it worked. If so, I'll be sure to post and acknowledge it's solved, if not, I'll be back. Wish me luck~! Thanks for all the help.

---

### Post by TheSe7enth on 2010-07-25
Apologize for the necro (sort of) and double post, but I've solved the problem, and thought it was worth acknowledging because it may help other users encountering the same issue.

When you have Windows 7 installed as well as XP, you don't have to add XP to the grub boot menu for Ubuntu. In fact, even if you try, it usually won't work... When you have XP installed first, or even 7 installed, and add the other (and repair if you installed XP over 7), then they merge both into one format. If Ubuntu targets Windows 7, that's enough. Simply pick the Windows 7 bootloader from the Grub menu when you start up, and then it'll give you the open to choose Windows 7 or XP. So you'll go through two boot menus, but it's still the only way to do it from what I can see.

I do have one question though; how do I change the Grub menu to be on Windows 7 by default, so that I can restart my computer straight into 7 when I'm not at my computer? It's my most used OS, so it seems preferable to have it that way, I just don't know how to do it.

---

