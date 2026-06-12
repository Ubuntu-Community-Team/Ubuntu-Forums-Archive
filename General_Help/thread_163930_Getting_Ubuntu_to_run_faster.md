---
title: "Getting Ubuntu to run faster"
date: 2006-04-21
forum: General Help
---

### Post by Burden on 2006-04-21
If this is the wrong forum I aplogize.

Basically what I am wanting to know is how to run faster. It's not as snappy as Windows is and I really want to learn linux. I have newbie/intermediate linux knowledge, if anyone can point to an links or articles it would be greatly appreciated. Also how can I remove bulk applications such as Evolution from Ubuntu, where I go through Synaptic it says ubuntu-desktop is dependant on it and I am worried of making the Gnome GUI unbootable.

So yeah I am pretty sure sure this a kinda broad question, but hopefuly one of you may help me out. :D

BTW I forgot my specs.

Intel Pentium III 550MHz
256MB RAM
Nividia TNT2 Video Card
120GB WD Hard Drive

---

### Post by Slasher9641 on 2006-04-21
If you have a resembly fast CPU it should run fairly well as long as it has enough RAM for applications.

EDIT: I don't know why you would stick a 120GB hard drive into an old PC it basically does not help the hardware and can create bottle necks. I suggest you upgrade the whole PC, keep the hard drive and the wideo card. Upgrade the RAM and the CPU.

---

### Post by Frem on 2006-04-21
Ditch Gnome. Go with something lighterweight, maybe install Xubuntu or IceWM. Heck, even KDE is faster. (ducks)
Google around, there are plenty of howtos about lightweight linux apps.

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=Burden]If this is the wrong forum I aplogize.

Basically what I am wanting to know is how to run faster. It's not as snappy as Windows is and I really want to learn linux. I have newbie/intermediate linux knowledge, if anyone can point to an links or articles it would be greatly appreciated. Also how can I remove bulk applications such as Evolution from Ubuntu, where I go through Synaptic it says ubuntu-desktop is dependant on it and I am worried of making the Gnome GUI unbootable.

So yeah I am pretty sure sure this a kinda broad question, but hopefuly one of you may help me out. :D

BTW I forgot my specs.

Intel Pentium III 550MHz
256MB RAM
Nividia TNT2 Video Card
120GB WD Hard Drive[/QUOTE]
1. Since you don't have much ram/cpu, use XFCE.
2. Use InitNG ([www.wiki.ubuntu.com/InitNG](www.wiki.ubuntu.com/InitNG))
3. Disable uneeded services from starting
4. Make sure you have the latest Nvidia drivers
5. Prelink
6. Make sure DMA is enabled
7. Tweak your ext3 filesystem for a performance boost.
8. Compile the newest kernel from kernel.org and disable all uneeded modules/features.
9. Have a specific kernel for your processor (686,386,w/e)
10. In terminal type 
> sudo apt-get clean
This will clean all tempoary packages.

Hope that helps :) That is stuff off the top of my head.

---

### Post by Burden on 2006-04-21
[QUOTE=Slasher9641]If you have a resembly fast CPU it should run fairly well as long as it has enough RAM for applications.

EDIT: I don't know why you would stick a 120GB hard drive into an old PC it basically does not help the hardware and can create bottle necks. I suggest you upgrade the whole PC, keep the hard drive and the wideo card. Upgrade the RAM and the CPU.[/QUOTE]

Currently I am running a stripped version of XP and its pretty snappy, and what you're telling me is to upgrade my computer to run linux!?

---

### Post by Slasher9641 on 2006-04-21
[QUOTE=Burden]Currently I am running a stripped version of XP and its pretty snappy, and what you're telling me is to upgrade my computer to run linux!?[/QUOTE]

Basically, yes.

---

### Post by sto6ma9ch on 2006-04-21
My laptop has similar specs, and the GNOME desktop does seem to be a little sluggish. You may want to try a lighter GUI like [XFCE]("https://wiki.ubuntu.com/Xubuntu") or [Fluxbox]("http://fluxbox.sourceforge.net/") or maybe upgrade some of your hardware if possible. 

To install XFCE (XUbuntu)

```
sudo apt-get install xubuntu
```

To install Fluxbox

```
sudo apt-get install fluxbox
```

Uninstalling big apps like Evolution may not necessarily make your experience any faster (looks like you have plenty of hard drive space). You could also try recompiling your Linux kernel omitting options that you don't need. This, I've heard, may only have a slight impact on performance.

---

### Post by PhoenixP3K on 2006-04-21
You don't need to upgrade anything! With [Xubuntu (XFCE) ]("https://wiki.ubuntu.com/InstallingXubuntu") you'll get a snappier system. It's not going to be hyper fast, but I did experiement with XFCE on a PII 266Mhz with only 192MB - On a 3GB hard drive. The experience was fine, it wasn't as fast as Windows XP because I didn't optimize the kernel and there was a ton of unneeded packages...

What I'm trying to say is that IceWM or XFCE will be good enought for you to learn Linux. Just forget about XGL and all that sci-fi stuff :p

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=Burden]If this is the wrong forum I aplogize.
Also how can I remove bulk applications such as Evolution from Ubuntu, where I go through Synaptic it says ubuntu-desktop is dependant on it and I am worried of making the Gnome GUI unbootable.
[/QUOTE]
Don't worry, you can remove it. The ubuntu-desktop package is actually a meta package left over from install. I have removed it and my system is fine.

---

### Post by Ramses de Norre on 2006-04-21
But you'll need to reinstall ubuntu-desktop when you're going to dist-upgrade to dapper.

---

### Post by adamkane on 2006-04-21
Disabling services turns out to be unnecessary. Ubuntu ships with with a 386 kernel. You should upgrade to a 686 or k7 kernel. Fortunately, this is very easy.

Check which kernel, you have:

```

uname -r

```

This should say:
2.6.12-10-686 or 2.6.12-10-k7

If not:

Intel Pentium:
```

sudo apt-get install linux-686 linux-image-686
linux-headers-686 linux-restricted-modules-686

```

AMD K Series (Duron, Athlon, Sempron):
 ```

 sudo apt-get install linux-k7 linux-image-k7
 linux-headers-k7 linux-restricted-modules-k7

```

Older legacy PC (Intel Pentium Pro or 486):
 ```

 sudo apt-get install linux-386 linux-image-386
 linux-headers-386 linux-restricted-modules-386
 
```

Reboot.

Disabling services helps as well, but may not be necessary, and you may get yourself into unnecessary trouble.

---

### Post by az on 2006-04-21
On a 550 Mhz box, Things are a little slower than Windows, but there are fewer "lags" or "Freezes" that make working on a big document in Windows unproductive.  All in all, I can say that, although the Ubuntu desktop is less snappy, you are more productive on it than Windows.

Dapper is also a little snappier (and Gnome will get even faster in coming releases) and it boots faster, too.


[QUOTE=adamkane]
Intel Pentium:
```

sudo apt-get install linux-686 linux-image-686
linux-headers-686 linux-restricted-modules-686

```
.[/QUOTE]

That would be the one you want.  You just need to install the linux-686 package.  It depends on all those other ones except the headers, which you don't need.

apt-cache shoubuntu@ubuntu:~$ apt-cache show linux-686
Package: linux-686
Priority: optional
Section: restricted/base
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.15.19
Depends: linux-image-686, linux-restricted-modules-686

---

### Post by felosi on 2006-04-22
I recently compiled a list of things that has made my ubuntu faster. It is just stuff I picked up off the net and here like pre linking, latest kernel with ck patches, disabling unecessary services and dameons which ubuntu seems to have a LOT. That and running xubuntu does great by me. I used to think that the ext2 filesystem was fastest. That may be but you better have an ups ot your power never goes out or system crash, especially on dapper. i recently had to reinstall cause of that but anyway on compiling and patching the kernel the 2.16.6 was the newest one I seen to work with the ck patch and making it into a deb package, others didnt patch properly. When you do your xconfig or menuconfig on your kernel before compiling you will be amazed at all the unecessary modules is compiled stock. If you copy your config over from your ubuntu kernel and take a look you will be an hour unmarking unecessary, old, and obsolete modules and support. My site is [www.blackhat-alliance.org](www.blackhat-alliance.org) Just go to about the 3rd page in the news and there is a 2 articles on it. Nothing I discovered just knowledge I obtained, and put it to use and didnt have no problems
Good luck

---

### Post by adamkane on 2006-04-22
felosi:

Try to be aware that most of your readers will be new users, so be sure to warn them that may run into trouble installing the latest kernel, installing kernel patches, and disabling services.

Warn of the pitfalls, and try to help new users avoid unnecessary frustration. 

Very likely new users will end up with missing functionality they weren't expecting, and will become disappointed/disenchanted.

---

### Post by Burden on 2006-04-22
Alright I am having trouble installing XFCE I followed the
instructions from the link sto6ma9ch gave me to a tee and I
don't know why its not working :/ and now im having to use
lynx and irssi, I don't get any errors and I've tried typing
in startxfce4 and xserver like the instructions say but it
says it cannot find the command, any ideas people?

---

### Post by sto6ma9ch on 2006-04-22
The XFCE website will probably have instructions on how to compile it XFCE from source. This can be an uphill battle. Instead,try using the Ubuntu-specific packages by running this command:
```
sudo apt-get install xubuntu-desktop
```
This command should be all you need to do to get XFCE installed and configured properly. Once that's done, you should be able to select XFCE from the GNOME login manager. Keep us posted.

---

### Post by adamkane on 2006-04-22
If you go the xfce route, be aware that once you start using gnome apps (nautilus) and kde apps (konqueror), you start losing your speed benefits. 

You have to use xfce apps only, if you want to maintain the speed benefits of xfce.

If you've got gnome and kde base apps installed, because you're using nautilus or konqueror, xfce won't seem as fast as it might. 

xfce uses rox, so you used to that first.

In other words, those who say, "just use xubuntu", aren't telling you the whole story.

---

