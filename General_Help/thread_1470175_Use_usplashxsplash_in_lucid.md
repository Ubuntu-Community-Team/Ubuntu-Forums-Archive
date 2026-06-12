---
title: "Use usplash/xsplash in lucid?"
date: 2010-05-02
forum: General Help
---

### Post by hellfeuer on 2010-05-02
I have an nvidia card, and as everyone knows by now plymouth make startup look horrible with the propriety drivers. The underlying problem is unlikely to be solved anytime soon and all the workarounds posted in various places don't fully work for me.

So, is there some way to go back to using usplash/xsplash in lucid? It appears that uninstalling plymouth is very hard but would it be possible to keep it installed, not use it during boot and instead use the old method of booting?

And frankly, I cannot understand who thought it was a good idea to change to plymouth when it is going to give so many user's a horrible first impression of lucid. I have a backup of my karmic install and I am seriously considering reverting to that.

Alternatively, has anyone had any luck using noveu's 3d support from git?

---

### Post by BrokeMahPC on 2010-05-02
This is a widespread problem - ignore the splash trouble for now - I imagine they will work to fix it asap. It's not worth using all sorts of fixes - they will probably end up breaking your install. I tried everything, even a newer kernel - I now just ignore the Plymouth splash.

---

### Post by almalaci on 2010-05-15
Have you tried this workaround?:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

It worked for me with an nvidia card. 

I agree it can be a very seriously annoying problem ie. you have a non-booting system that drops you back into a garbled terminal not being able to figure out what the heck is going on.

---

### Post by jerome1232 on 2010-05-15
I used a much less complicated method, I don't get a seamless boot (meaning the screen still flickers because it has to swtich modes) but I do get a highres plymouth that I see for a total of 2 seconds, unless there is a disk check scheduled, then i get to see it for 4 seconds :P

I edited /etc/default/grub, the sections that are highlight in red are the lines I added/edited.

```
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[COLOR="Red"]GRUB_CMDLINE_LINUX="nomodset"[/COLOR]

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
[COLOR="Red"]GRUB_GFXPAYLOAD_LINUX=1024x768[/COLOR]
```


After editing you need to run
```

sudo update-grub
```

Using this method allows tty's to work, at a nice res too.

---

### Post by shadmego on 2010-05-18
I am in the process of troubleshooting an upgrade from 9.10 to 10.04. I've been able to get as far as a plymouth-splash termination "with status 1". Unfortunately, I've not been able to find any solid leads on the problem and attempting to circumvent plymouth sounds like the best solution other than a complete reinstall.

The problem has kept the system from being able to boot at all. I can't even load previous versions of the kernel or any recovery modes from Grub.

Booting from the Live CD of 10.04 throws all kinds of errors and eventually hangs the system. Booting from the Live CD of 9.10 allows me to see the contents of the hd, but I can't find anything on what to do or how to circumvent the problem to get Ubuntu to boot.

This is not a new system. It would not be a good choice to simply wipe and restart from scratch. From what I've read, it could spell problems for the stability of the system if I don't have the right hardware/drivers for my video card.

Any help at all would be beneficial!

~regards

---

### Post by angry_johnnie on 2010-05-18
As far as going back to usplash, i've done it ([i did, really]("http://ubuntuforums.org/showthread.php?t=1464173")), and it hosed everything, so i had to reinstall from scratch (it's a lot easier and faster than fixing) :)

As far as why they picked plymouth... well, i guess it's the same as when Hardy Heron came out, and everyone (including me) was complaining about pulse audio, and firefox 3 beta, and this and that... it's LTS, so i guess it makes sense.

---

