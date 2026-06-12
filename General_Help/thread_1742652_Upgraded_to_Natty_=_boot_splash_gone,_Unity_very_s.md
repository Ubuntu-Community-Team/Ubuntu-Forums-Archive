---
title: "Upgraded to Natty = boot splash gone, Unity very slow"
date: 2011-04-29
forum: General Help
---

### Post by ternyk on 2011-04-29
I've got few issues after upgrade form 10.10 to 11.04:
1. Boot splash screen gone after the upgrade. I had configured boot splash like in [http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown](http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown)
Checked configuration and is the same. In the log:

Title: plymouthd assert failure: plymouthd: ./plugin.c:540: map_to_device: Assertion `head->size > 0' failed.

2. Loading Unity desktop very slow (>10 sec) and it works very laggy (I'm using fglrx)

---

### Post by Hedgehog1 on 2011-04-29
Please do this to get the boot splash back:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by ternyk on 2011-04-29
Thanks, I tried with:
```
GRUB_GFXMODE=1280x1024
```
Screen changed resolution and colors but no logo visible.

---

### Post by TheCosmicFrog on 2011-04-30
Tried fixing this with my "old faithful" [guide]("https://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/"), which has worked for both 10.04 and 10.10. No luck in 11.04 though. I just have a purple screen (same color as GRUB) for the entire bootup. During shutdown I just have a black standard output screen with kernel dumps ("Unmounting weak filesystems/Will now halt", etc.

edit - forgot link!

---

### Post by timgood on 2011-04-30
Try this: worked for me. [http://ubuntuforums.org/showthread.php?t=1742944](http://ubuntuforums.org/showthread.php?t=1742944)

---

### Post by anothermikemiller on 2011-05-01
This is my first login since upgrade. I agree that everything seems slow. My lm sensors is gone as is the cpu icon so I can't really tell if it's off loading gpu functions to cpu. I saw this same complaint from a user with a modern "gamer" type system.

My main complaints so far is slow rendering effects (workspace switcher, dash, task bar) and laggy application loading. I used unity on a 1st gen acer aspire with 10.04 netbook and had no problems. I'll see about updating this post when I get some tools installed to monitor the system, but I'm switching to gnome for now.

---

### Post by ternyk on 2011-05-04
Thanks for the replies. I uninstalled fglrx (read [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)) and switched to radeon open source drivers and it's working now. 
Minor drawback is  that there are sometimes "artifacts" on Unity dash (white-black rectangles) but as I don't use Unity now but Classic Gnome desktop it's ok for me.

---

### Post by Lupajz on 2011-05-04
I had same problem :P I was experiencing laggs in Unity after upgrade so I updated fglrx but it only solved problem which was occuring after running 

sudo aticonfig --initial -f 

But laggs still presisted, so I dissabled fglrx but my book was overheating.
My question is how to enable open source drives ? ;)

---

### Post by ternyk on 2011-05-04
> **Lupajz said:**
> 
...
My question is how to enable open source drives ? ;)

See: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:  Need to fully remove -fglrx and reinstall -ati from scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need to fully remove -fglrx and reinstall -ati from scratch")

To check if it is configured correctly type:

```
LIBGL_DEBUG=verbose glxinfo
```

and "Make sure your OpenGL renderer string does not say "software rasterizer" because that would mean you have no 3D hardware acceleration." from [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I had to reinstall/reboot twice because at the first time there was no 3d acceleration. Also delete (but backup) your /etc/x11/xorg.conf.

---

### Post by ubumartin on 2011-05-09
> **ternyk said:**
> I've got few issues after upgrade form 10.10 to 11.04:
1. Boot splash screen gone after the upgrade. I had configured boot splash like in [http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown](http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown)
Checked configuration and is the same. In the log:

Title: plymouthd assert failure: plymouthd: ./plugin.c:540: map_to_device: Assertion `head->size > 0' failed.

2. Loading Unity desktop very slow (>10 sec) and it works very laggy (I'm using fglrx)

I got the exact same two problems. The only difference is my install(64 bit) is clean and not an update. The reason i did a clean install is that the update i first did rendered the system completely un-bootable.

I never been more annoyed with an ubuntu release then i am with this one. 

In my case i first got a blank purple screen for about 30sec, then a short flash of the boot splash and it takes about 20 sec until unity is fully loaded. The desktop, especially window dragging, is very laggy when using the by the system recommended third party gfx driver, which i guess is fglrx(?) My hardware is Amd 890gx chipset with built in graphics.

---

