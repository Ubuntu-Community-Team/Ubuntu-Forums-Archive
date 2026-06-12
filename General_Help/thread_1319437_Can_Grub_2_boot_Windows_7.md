---
title: "Can Grub 2 boot Windows 7?"
date: 2009-11-08
forum: General Help
---

### Post by hoppipolla on 2009-11-08
Mine can't ._. heh

Can yours? :o

---

### Post by The Funkbomb on 2009-11-08
brb trying lol

---

### Post by praveesh on 2009-11-08
Yes but only original 7. No beta or rc

---

### Post by The Funkbomb on 2009-11-08
yes.  yes it can.

---

### Post by hoppipolla on 2009-11-08
> **The Funkbomb said:**
> yes.  yes it can.

INTERESTING! I shall have to re-install GRUB. The problem I had was I just did a standard GRUB 2 reinstall (sudo grub-install from within my Ubuntu) - it detected 7 and added it, but then failed to boot it when I tried :(

---

### Post by marchwarden on 2009-11-08
Boots into 7 RC fine for me.

---

### Post by The Funkbomb on 2009-11-08
Yeah, I'm using the RC too.

Oddly enough, I have EasyBCD installed and it still has a section for Ubuntu 9.04.  I gotta change that at some point.

---

### Post by hoppipolla on 2009-11-08
wow I wonder what I'm doing wrong. I think I have 1.97 beta 4.

(I have been doing regular updates so I believe I have the latest version in the standard repos but it's possible I'm wrong)

---

### Post by shafin on 2009-11-08
Works perfectly.
And grub-2 update is neat. It originally added a grub 2 chainloader to my grub 1 installation, after I tested and got satisfied with grub 2 I was able to remove grub 1 and get totally on grub 2 with a single command.

---

### Post by hoppipolla on 2009-11-08
oh, mine are on different disks - will that make a difference? o.O

I have Ubuntu on my... primary master I think, and 7 on my secondary slave.

---

### Post by mmix on 2009-11-08
slightly offtopic, qemu-kvm is works fine with [real hdd partition](http://bbs.archlinux.org/viewtopic.php?id=68216) or iso.

so you don't have to reboot, every time.

---

### Post by hoppipolla on 2009-11-09
sorry to bump this but... do you think it's coz the two OSs are on different hard disks? :)

---

### Post by home ubub on 2009-11-10
plz do tell how can i install grub 2

---

### Post by hoppipolla on 2009-11-10
> **home ubub said:**
> plz do tell how can i install grub 2

it comes with Karmic :)

---

### Post by Tynach on 2009-11-12
Mine didn't at first. Windows would start to boot, then it would just randomly reboot.

Here's my workaround:

In /boot/grub/grub.cfg (I think, I don't remember the exact path right now. I'm on my old computer with Ubuntu 8.10 right now), you scroll down to where it has the list of commands to boot into Windows 7. It should look something like this:

```
insmod ntfs
set root=(hd0,1)
<really long command that looks confusing>
chainload +1

```

Or something like that. hd0,0 might be different.

I just took out the really long command, and it works fine. However, the file is read-only by default, so you kinda have to change the permissions first. As root, of course.

By the way, BACKUP YOUR ORIGINAL grub.cfg FILE!!!

I didn't screw mine up, but I'm not exactly giving exact instructions, and that config file looks nasty to edit.

Edit: hoppipolla, I like your signature. I myself run Kubuntu with KDE 4.3.3, and while it's a little rough with a few things, it is much more dynamic than Windows 7.

Windows 7 is a little uneven... In parts where identical eyecandy is observed, it reacts differently. Like in the taskbar, hovered items get the two bars next to them, but they don't fade; In the system tray, you get the same thing, but they DO fade.

---

