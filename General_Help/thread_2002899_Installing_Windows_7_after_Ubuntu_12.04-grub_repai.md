---
title: "Installing Windows 7 after Ubuntu 12.04-grub repair"
date: 2012-06-13
forum: General Help
---

### Post by GreatDanton on 2012-06-13
Hi!
I know my question was answered a lot of times, but I am still not sure how to do because there are a lot of old threads.

I have one hard disk drive on which is Ubuntu 12.04. Now I want to shrink partition (I know how to do it - with Gparted) and after that I want to install Windows 7 on it. The problem is I do not know how to repair Grub menu, after Windows installation. Can someone tell me how to repair Grub, so I can choose which operating system I would like to use.

2. Is it possible to view files of other operating system. For example when I am on Ubuntu is it possible to view Windows files or not (ex. Music folder).


Thanks in advance

---

### Post by GreatDanton on 2012-06-13
Hi,
I shrink my Ubuntu partition with Gparted, but unfortunately I was not able to use Gparted with Ubuntu live. I was lucky to have Fedora 17 on my Usb key and I used Gparted from there. Does anybody know why Gparted wasn't working on Ubuntu, but was working on Fedora. After that I have installed Windows 7.

Now I want to know how can I get grub menu back, so I can choose between operating systems. I found some old threads but I am not sure if I can follow them.

Can somebody point me to the right place.

---

### Post by GWBouge on 2012-06-13
Not sure about GParted, I haven't had any issues with it from a Live CD, but good that you found a way to get it to work.  As for getting GRUB back, these might help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Cavsfan on 2012-06-13
**sudo grub-install /dev/sdx** where x is the hard drive. sda if you only have one.
That might fix it.

---

### Post by drs305 on 2012-06-13
If the Grub files are intact what *Cavsfan* recommends should return control to Grub [edit: *from a working Ubuntu installation*]. If you don't see a Windows entry, after booting into Ubuntu run "sudo update-grub".

It's hard to say why the Ubuntu Gparted didn't work, but often it is because something was mounted. If it is a real installation, you can't run Gparted from that same running system. If you were trying to do it from a LiveCd, the swap partition still has to be unmounted first. But in either case, we recommend shinking/expanding any Windows partition with Windows software whenever possible.

---

### Post by wilee-nilee on 2012-06-13
> **Cavsfan said:**
> **sudo grub-install /dev/sdx** where x is the hard drive. sda if you only have one.
That might fix it.

This would have to be done from a chroot on a live cd or from the ubuntu install.

OP use this tool the recommended repair. If you still have problems be sure to save the bootinfo summary HTTP to post, so we can help you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by GreatDanton on 2012-06-13
Thanks for replies.

I typed:
sudo fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005b5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   722040831   361019392   83  Linux
/dev/sda2   *   722040832   722245631      102400    7  HPFS/NTFS/exFAT
/dev/sda3       722245632   970481663   124118016    7  HPFS/NTFS/exFAT
/dev/sda4       970483710   976771071     3143681    5  Extended
/dev/sda5       970483712   976771071     3143680   82  Linux swap / Solaris

Disk /dev/sdb: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bb00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192    15687679     7839744    b  W95 FAT32

```

and then:sudo grub-install /dev/sda1
```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

```

I Unmounted both partitions in Nautilus.
How can I solve this?

---

### Post by Cavsfan on 2012-06-13
Enter 
```
sudo mount /dev/sda1 /mnt
```
Then 
```
sudo grub-install /dev/sda
``` not [COLOR="Red"]sda1[/COLOR] just sda

---

### Post by GreatDanton on 2012-06-13
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt ubuntu@ubuntu:~$ sudo grub-install /dev/sda /usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).     The same error.

---

### Post by Cavsfan on 2012-06-13
> **GreatDanton said:**
> ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt ubuntu@ubuntu:~$ sudo grub-install /dev/sda /usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).   The same error.
**Drs305** will have the answer. He knows grub pretty well.
Hopefully he will return shortly.

---

### Post by drs305 on 2012-06-13
Your situation could require just a few simple commands but we really don't know.

I highly recommend you install Boot Repair while running the LiveCD. All you should have to do after installing is press the "Recommended repair" button and it will figure out what needs to be done.

If that doesn't solve the problem, it will offer to run the boot info script. Run that and post the contents and we can see what your system looks like.

There is a link to Boot Repair in my signature line.

---

### Post by GreatDanton on 2012-06-13
Thank you for your reply. I downloaded Boot repair, and now everything is fine. Now I have only one problem in Ubuntu. The upper part of the windows (where are buttons for closing and minimizing windows/window border) is freezing. This means I am unable to close windows, and that's is very annoying. Also some shortcuts doesn't work properly (like super and W). Sometimes I am also unable to click on the Unity.

Any solutions for this?

Here is the address of my Boot repair: paste.ubuntu.com/1039702

---

### Post by drs305 on 2012-06-13
You can try the F11 key to maximize then return the Windows to their normal size. I recall that is a temporary solution but don't recall the fix. I believe it's been covered quite a bit so you might be able to find some threads here.

Glad your Grub is now working.

---

### Post by GreatDanton on 2012-06-13
I think this thread could be marked as solved.

Thanks everyone for support :)

---

### Post by Cavsfan on 2012-06-13
This forum is the best and *drs305* knows grub. You might look at the how to in my sig. if you want. The last post is what my current grub screen looks like.
Look through this thread** Precise known bugs with workarounds** for some solutions to your other problems:
[[color=blue]_http://ubuntuforums.org/showthread.php?t=1968155_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1968155)

---

### Post by GreatDanton on 2012-06-13
Now it's not freezing anymore. I unplugged power cable and now, knock on the wood, there is no more problems. Restarted computer twice and no problems at all :).

Cavsfan: Your thread about Grub is awesome. I am gonna try to add some picture one day when I will have time.

---

### Post by drs305 on 2012-06-13
> **GreatDanton said:**
> I am gonna try to add some picture one day when I will have time.

All you need to do for that is place a PNG image in /boot/grub. Simple. There's more you *can* do regarding backgrounds, but that is all that you really *have* to do (except run "sudo update-grub" after you've put an image in the folder).

[https://help.ubuntu.com/community/Grub2/Displays]("https://help.ubuntu.com/community/Grub2/Displays")

Happy Ubuntu-ing !

---

### Post by Cavsfan on 2012-06-14
> **GreatDanton said:**
> Now it's not freezing anymore. I unplugged power cable and now, knock on the wood, there is no more problems. Restarted computer twice and no problems at all :).

Cavsfan: Your thread about Grub is awesome. I am gonna try to add some picture one day when I will have time.

That is good you got it to quit freezing. I had several problems when I first installed. I decided to stick with Ubuntu Unity and things eventually became more stable.
Some times I have to log out and back in to get Emerald window manager to work but, other than that it keeps getting better.
I just got 68 updates a while ago.
Not sure what that was about but, things are looking up.
Good luck!

---

