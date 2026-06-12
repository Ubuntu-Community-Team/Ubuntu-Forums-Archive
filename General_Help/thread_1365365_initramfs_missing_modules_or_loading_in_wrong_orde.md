---
title: "initramfs missing modules or loading in wrong order."
date: 2009-12-27
forum: General Help
---

### Post by quequotion on 2009-12-27
System: Jaunty Jackalope x86_64

After an update, wherein linux-image-2.6.28-17 was installed, I noticed that the system was unbootable with the new kernel. The previous kernel, linux-image-2.6.28-11 was still working, so I ignored the problem and continued working with the old kernel. Another update (package unknown, several were upgraded at the time) called update-initramfs on 2.6.28-11 and ruined everything.

Now both kernels exhibit the same boot failure:```
Starting up ...
[    5.110355] i8042.c: No controller found.
Loading, please wait...
/sbin/usplash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
/sbin/udevd: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dmraid: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wiat fo rthe right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/nvidia_dgcgcffh1 does not exist. Dropping to a shell!
```And then I get BusyBox. Unfortunately, there's no keyboard driver so I can't use BusyBox.

i've tried the solution from this page:```
http://chevdor.blogspot.com/2009/06/installing-ubuntu-on-raid10-sata-array.html
```Unfortunately, there are a lot of type-os in the code. i found the same solution on launchpad and gave it a try, but it was no help. However after striping the initramfs and checking which modules it has in a manner similar to that suggested, i find that my initramfs HAS the modules for dmraid at least... although i can't tell what it's doing with them.

this page discusses the problem I'm having as well, but the solution is no good:```
http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html
```Since I don't have a spare working system nearby and can't install another one anywhere.

This issue has been a problem for me in Intrepid, Jaunty, and Karmic.
In Intrepid it only happened at fresh install and was simple to fix, one simply had to boot form the live cd, install dmraid, chroot in, install dmraid on the system, update initramfs, and install grub.. The process for fresh install in Jaunty is practically the same, with the exception of compiling a custom dmraid to fix a mistake in it's initramfs hooks (and i did that, and that is the dmraid package i have installed now).
Karmic would install out of the box, but got the same error because it installed a GPT partition table which nothing can boot (why do that?), so it could be fixed by changing to an MSDOS partition table.

Both Karmic and Jaunty have exhibited this tendency to break a working initramfs periodically and in the past i just reinstalled the operating system...

In the past month, I tried to upgrade from Intrepid to Jaunty to Karmic and have formatted and reinstalled dozens upon dozens of times in the process... finally I just gave up on Karmic. Jaunty was working, beautifully, until a few hours ago.. After reading endless pages of forums, wikis, chatlogs, and blogs about dmraid and initramfs and the linux kernel... i'm no closer to booting my system than I was last night when it suddenly lost the root partition...

## UPDATE ##

It turns out that mkinitramfs was adding libraries i'd specified in ld.so.preload and somehow that broke everything. Why that happens and if it's a bug or a feature I do not know.

I do wish I had seen some kind of warning about that however, as I was following the instructions specified in dante-client's man page.

---

### Post by ibuclaw on 2009-12-27
Hmm... looks like you need to readd the dmraid modules.

Boot into the Ubuntu LiveCD, mount the RAID and the main root filesystem and chroot into it. (be sure to mount --bind the /proc /sys /dev and /dev/pts filesystem before you do).

First, ensure that dmraid exists in the initramfs hooks.
```
ls /usr/share/initramfs-tools/hooks/dmraid
```
Then create a modules file:
```
sudo nano /usr/share/initramfs-tools/modules.d/dmraid
```
add the modules you need for the RAID to load and save.

Then rebuild using update-initramfs -c -k all
```
update-initramfs -c -k all
```
Sorry can't go into more detail, as I don't have a RAID setup myself.

Regards
Iain

---

### Post by quequotion on 2009-12-27
A little more information.

I tried update-initramfs -u -v -k all.

As you can see, lots of modules go into the initramfs, including dmraid. So why aren't these being loaded at boot?

Please, if anyone can help. My computer has become a very expensive paperweight.. I can only access my system through a chroot on the live cd.. If I have to format and install one more time I will seriously go bonkers...

---

### Post by quequotion on 2009-12-27
> **tinivole said:**
> Hmm... looks like you need to readd the dmraid modules.

Boot into the Ubuntu LiveCD, mount the RAID and the main root filesystem and chroot into it. (be sure to mount --bind the /proc /sys /dev and /dev/pts filesystem before you do).

First, ensure that dmraid exists in the initramfs hooks.
```
ls /usr/share/initramfs-tools/hooks/dmraid
```
Then create a modules file:
```
sudo nano /usr/share/initramfs-tools/modules.d/dmraid
```
add the modules you need for the RAID to load and save.

Then rebuild using update-initramfs -c -k all
```
update-initramfs -c -k all
```
Sorry can't go into more detail, as I don't have a RAID setup myself.

Regards
Iain

it is in /usr/share/initramfs-tools/hooks/, and I have dm-raid4-5 specified in /usr/share/initramfs-tools/modules. If i make an extra dmraid file in modules.d, what modules should I add there? i'm trying to get a RAID0 to boot.

Anyway, i suspect something far more insidious has happened than just the dmraid module not loading. I have reason to believe it is in initramfs but it's either not getting called or not loading in the right order.

---

### Post by john newbuntu on 2009-12-27
Just curious on whether you have libdl.so.2 linked properly in /lib:
/lib/libdl.so.2 -> libdl-2.10.1.so

---

### Post by quequotion on 2009-12-27
> **john newbuntu said:**
> Just curious on whether you have libdl.so.2 linked properly in /lib:
/lib/libdl.so.2 -> libdl-2.10.1.so

it is linked to libdl-2.9.so

---

### Post by quequotion on 2009-12-27
i added```
 echo "Made it this far!" 
```to /etc/initramfs-tools/scripts/local-top/dmraid

At boot that line now appears just before dmraid fails to find libdl.so.2. It is AFTER usplash and udevd fail. What is going on here?

---

### Post by quequotion on 2009-12-27
Change of focus: BusyBox could probably help with this problem a great deal. So how about getting some keyboard drivers loaded so I can use it?

The keyboard works in BIOS and GRUB, but all the LEDs go dead after grub and nothing responds. As far as I can tell the only button that the computer will respond to is the power button.

---

### Post by john newbuntu on 2009-12-27
"ldd /sbin/usplash" or "ldd /sbin/udevd" should tell the location of libdl.so.2.
Does that library exist?
Some other things to look at would be searching the /etc/ld.so.cache for the library and rebuilding this if necessary (ldconfig?)

---

### Post by quequotion on 2009-12-27
> **john newbuntu said:**
> "ldd /sbin/usplash" or "ldd /sbin/udevd" should tell the location of libdl.so.2.
Does that library exist?
Some other things to look at would be searching the /etc/ld.so.cache for the library and rebuilding this if necessary (ldconfig?)

It does exist. I'll try ldconfig, but i doubt the problem actually has anything to do with libdl.so.2. I've had this error often, very often, and it always means that the disk libdl.so.2 is on wasn't found.

The problem seems to be that modules are either not loading, or loading out of order. Specifically, there are no input modules (no keyboard or mouse drivers at least) and no raid modules (root partition "does not exist") although it seems like those modules are in the initramfs...

---

### Post by quequotion on 2009-12-27
Tinivole:

Your suggestion did not work, although I still am not sure what modules to list in /usr/share/initramfs-tools/modules.d/dmraid. I added dm-raid45 and dm-raid4-5.

I have searched and searched and asked around a lot but no one ever confirms or denys that one of those is the module for raid0...

---

### Post by quequotion on 2009-12-27
I give up... I've been at this for two days and my computer has not been usable during any of that time.. I'm going to format and reinstall, just like i would with Windows ME--twice a month.

I really enjoyed Ubuntu Intrepid. It had bugs, but there was always a work around or a fix out fast..

Jaunty and Karmic have been depressing. Especially Karmic...

In the last month I have been up until morning every night trying to get Karmic or Jaunty to work with my system, and every time I get close something like this happens and I have to format and install again because nobody's ever heard of the problem I have and I don't have the expertise to narrow down some kernel bug that got past the release team.

I'll come back to this thread when it happens again.

---

### Post by ibuclaw on 2009-12-28
[QUOTE=Your initrd output]Adding library /usr/lib/libdl.so[/QUOTE]
I suppose the better question would be why it is adding that library, and not /lib/libdl.so.2

Looks like something went wrong in your shared library system... you don't use prelink, preload, or any other tinkering program, do you?

---

### Post by quequotion on 2010-01-03
When this problem originated, I had two libraries specified in /etc/ld.so.preload; those needed to use dante-client (socksify - my internet connection is a socks proxy through an iPhone) in the background. I have had successful initramfs updates under the same conditions so I don't think that would cause it to fail, but I'll try once more without ld.so.preload just in case.

Just to be sure--do you mean to say something went wrong with my linked library system and that is why my computer will not boot OR something went wrong with my linked library system and that is why mkinitramfs fails?

The funny thing is, my installation is fully functional. I can boot a live cd, chroot in, and do whatever... except make a functional initramfs.

By the way, the same problem has occurred again. Fresh install-->boot-->attempt to reinstall packages & update-->never boot again.

I could fill an almanac with all the dmraid-related solutions I've tried, but I can't find much concrete info about how mkinitramfs or update-initramfs work other than the man pages...

Just for fun, I tried booting with no initramfs at all, but the system reboots immediately after grub!

####

if anybody out there has an HP Proliant ML115 with a working initramfs for amd64 with dmraid, would you mind sharing it with me?

---

### Post by quequotion on 2010-01-03
A flash of brilliance came over me just a moment ago. The live cd always works right? So why not install dmraid in the live session, mkinitramfs -o livecd.img in the live session, mount my installation to /target/ copy that to /boot/ on my installation, edit /boot/grub/menu.lst on my installation, chroot into /target/ and update-grub?

IT WORKED. It's loading all kinds of modules I don't need; xorg won't start; and I refuse to call this a solution as I still don't have a clue what the initial problem was, but it worked. My system booted (sort of), and now I know for sure that mkinitramfs within my installation was spitting out bad initramfs.

I recently had the joy of explaining this problem and the general way things get fixed in Linux to one of my windows-only friends.... Unfortunately I think I scared her away for life... There has got to be an easier way of getting things done than dodgy workarounds and command-line magic (it really does sound like hocus-pocus to the typical windows or even mac user when you talk about controlling a computer without a mouse)... How about in lucid or lucid+1 we implement some kind of error detection system? (windows vista has such a thing, a somewhat inept and patronizing implementation of it, but it catches things from time to time) of course there's no way to debug every package a user might install, but something could run checks or simulations on say... Kernel updates, initramfs, linked libraries, essential package dependencies, etc.

I also rebuilt my other initramfs without ld.so.preload (not for the first time I think...) and will be testing those shortly.

---

### Post by quequotion on 2010-01-03
Tinivole - you were right. Removing ld.so.preload and rebuilding my initramfs solved my problems... mostly... Gnome seems to be frozen but everything pretty much loaded.

Problem.... solved? I'll be back to confirm this later.

---

