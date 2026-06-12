---
title: "Can't boot from CD"
date: 2010-06-16
forum: General Help
---

### Post by TeddyPwns on 2010-06-16
I burned an .iso (gparted-live-0.5.2-9.iso) to a CD-R using the terminal with this:

```
wodim dev=/dev/scd0 -v -data gparted-live-0.5.2-9.is
```After that, I tried to boot from the CD, but it didn't and just went to the GRUB menu. The top item of my boot menu is the CD drive.

After I did this, when I tried to login, I got an error saying that the .ICEauthority file could not be updated. Also, I used to have only a few hundred megabytes of available space on my hard drive, and it seems that after I burned to the CD using the terminal, I now have 1.5 gigabytes of available space. I am not sure if either of these are related to not being able to boot from a CD, but I am posting it anyway in case it does.

I am using Ubuntu 10.04 Lucid Lynx, and I am trying to run GParted from a LiveCD to give my Ubuntu filesystem more space, because my Windows filesystem has about 70 gigabytes of available space. Also, I have been able to boot from a CD before, to install Ubuntu and do other things. How do I get my computer to be able to boot from a CD again, and where did the mysterious extra available space come from?

---

### Post by wojox on 2010-06-16
Don't know? Do you still have your Lucid CD available? Can you boot that? It has G-Parted on it.

---

### Post by TeddyPwns on 2010-06-17
I installed Ubuntu 9.10, and got an upgrade over the Internet. Also, I'm not sure if I can boot from any CD.

---

### Post by wilee-nilee on 2010-06-17
> **TeddyPwns said:**
> I installed Ubuntu 9.10, and got an upgrade over the Internet. Also, I'm not sure if I can boot from any CD.

The best way to boot from any media is using the key prompt to get to the boot from list. Look up your computer on the net with boot prompt or something like that, mine is f12 asus is esc.

---

### Post by TeddyPwns on 2010-06-17
I did use the key prompt. I got a boot menu and selected the CD drive, pressed Return, and it went to the GRUB menu.

---

### Post by wilee-nilee on 2010-06-17
> **TeddyPwns said:**
> I did use the key prompt. I got a boot menu and selected the CD drive, pressed Return, and it went to the GRUB menu.

Is this a install inside of windows=wubi the wording of your original post makes me wonder. If it is a wubi set up the way your going about it will probably break your system. I'm not sure why you wouldn't use the live cd, thats why wubi comes to mind and that you seem to have filled up some section.

I think you may want to use a regular cd burner first of all and maybe ask some questions, before proceeding.

---

### Post by TeddyPwns on 2010-06-20
> **wilee-nilee said:**
> Is this a install inside of windows=wubi the wording of your original post makes me wonder. If it is a wubi set up the way your going about it will probably break your system. I'm not sure why you wouldn't use the live cd, thats why wubi comes to mind and that you seem to have filled up some section.

I think you may want to use a regular cd burner first of all and maybe ask some questions, before proceeding.

I already did it though, so is there a way to fix the problem?

---

