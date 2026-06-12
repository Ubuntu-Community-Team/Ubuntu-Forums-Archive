---
title: "Cirrus Logic with X.org ?"
date: 2005-02-01
forum: General Help
---

### Post by chris-uk on 2005-02-01
I've got this virtual Cirrus Logic Alpine adapter [http://www.ubuntuforums.org/showthread.php?t=13334](http://www.ubuntuforums.org/showthread.php?t=13334)  that I'd like to use with Hoary Live. It works with Warty Live.
Does it need something different/extra on the CD ? Or does it need a boot option ?

See the link for what a virtual graphics adapter is, and why I need one  :-D

(If you can help me to get a more modern virtual adapter, such as an OpenGL-capable one, that would be interesting too)

---

### Post by daniels on 2005-02-01
The problem is that Cirrus modules are wildly non-standard, and I haven't worked out what to do with them so that they load yet.  I guess no-one ever tried loading it with a Cirrus Alpine card.

---

### Post by chris-uk on 2005-02-02
I've got the source code for this Cirrus 'hardware'. Well, QEMU has. I never saw the source. 
So, wild nonstandardness should not stop anything, and you can change it if you want anyway.
(Also, warty worked. What broke ? Is it a matter of putting the Warty support back in ?)

---

### Post by daniels on 2005-02-02
The problem lies with the Cirrus *modules* in X.Org.  Normal drivers are named foo_drv.o, bar_drv.o, et al, and so when I basically rewrote FindModule() in the loader, I only searched for %s_drv.o and lib%s.a.

The Cirrus driver decides to install cirrus_laguna.o and cirrus_alpine.o, which, needless to say, neither of those patterns match.  So I've fixed this locally, and it will be in 6.8.1-1ubuntu13, at which point the live CD will become bootable by QEMU.

---

### Post by chris-uk on 2005-02-02
I tried with a hoary live 2005-02-02, but got an empty /etc/X11/xorg.conf file (and no Xserver, as a consequence).

I'm 'booting' hoary with qemu by copying the CD to an 'iso' file, then using qemu's support for booting iso files.

If I try to make a 'dual-capable' CD (i.e. by putting qemu on the CD for autorun), I have to give it something to boot. I'm making a 'virtual CD' for qemu to boot ... about 10MB with the contents of the /install and /isolinux directories. It boots the first stage OK, but part way through hardware detection gives a message 'This is not a UBUNTU CD, please insert the correct CD and try again'.

How's it deciding ? Do I need a special volume label on the 'virtual CD' ? Some special files on the 'virtual CD' ? Something else ?

---

