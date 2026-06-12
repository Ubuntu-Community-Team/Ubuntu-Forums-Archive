---
title: "Booting issues"
date: 2009-11-18
forum: General Help
---

### Post by Tryptamine on 2009-11-18
I formatted and reinstalled windows 7, I previously on start up had the option of choosing windows/ubuntu. Since formatting that option does not come back up. My hard drive still states that ubuntu is present. I just cannot select it, thus unable boot it. I did not use wubi I partitioned and made ubuntu it's own sector. I have the newest version of ubuntu jaunty any and all help is greatly appreciated (this problem is hard to google :D)

---

### Post by Giblet5 on 2009-11-18
You'll need to boot from a Live CD and reinstall grub after you add a Windows 7 menu entry.

Boot in "Try it" mode from the LiveCD.

For this discussion, I will assume that Ubuntu is installed on /dev/sda1 and Win7 is installed on /dev/sda3.

USE WHAT YOU REALLY HAVE. That affects the GREEN entries below.

Open a terminal window (Applications -> Accessories -> Terminal)

Enter the following command:

```
mount [COLOR="Green"]/dev/sda1[/COLOR] /mnt
ls /mnt
```

Is it correct? Is that your / directory for Ubuntu?

If so, proceed:

```
sudo bash ## DANGEROUS! ENTER COMMANDS EXACTLY!
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
cd /boot/grub
nano menu.lst
```

You should add a section near the top like:
```
title           Windows 7
root            ([COLOR="Green"]hd0,2[/COLOR])
savedefault
makeactive
chainloader     +1
```

This is also a good time to change "default=0" to "default=saved". That way, whatever you booted last will boot by default. Handy given Windows tendency to install updates and reboot automatically...

Save it out and exit.

Now enter:
```
grub-install [COLOR="Green"]/dev/sda[/COLOR]
exit
exit ## BACK TO SAFE USER MODE
sudo reboot
```

You will now boot to the grub menu.

---

### Post by Tryptamine on 2009-11-18
I'm at work on my laptop so my PC isn't near me, but those were my mounting directories thank you very much for your reply I will attempt when I get home. Once again, thank you!

---

