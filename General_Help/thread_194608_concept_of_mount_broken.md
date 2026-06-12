---
title: "concept of mount broken"
date: 2006-06-11
forum: General Help
---

### Post by deb2006 on 2006-06-11
I accidentally hit the button of my CD-ROM player - to my surprise the CD ejected and the ripping of the CD was interrupted. This is definetely not how it is supposed to work in a UNIX system. Only umount is supposed to unmount the CD; eject then unlocks the CD-ROM tray and enables the ejection of the CD.

I have noticed this in terms of how other things are implemented. I firmly believe  it is not acceptable to ignore common concepts of UNIX in this distribution. So please be so kind and don't change this only they do work this way in Windows. There is already Windows - Ubuntu does not need to implement it anew!

---

### Post by dalee on 2006-06-11
Hi,

Yes, you are correct. Proper *nix would be issue mount/umount commands. But, auto-magic is what people want. And the customer is always right. 

If you want, you can certainly edit your fstab to disable automount. The choice, like most things in Linux, is yours:cool: 

dalee

---

### Post by mlind on 2006-06-11
yup. feel free to address a bug about this on Ubuntu's bug tracking system
[https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/)

---

### Post by grsing on 2006-06-11
Change it if you like; most of us can manage to avoid hitting the CD eject button and prefer the convenience.  Not trying to be snarky, it's just that you obviously know your way around *nix, so it's easy for you to change; for the average user Ubuntu is trying to appeal to, it's not, and many newbies would be rather perturbed when they can't get their CDs out.

---

