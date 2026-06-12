---
title: "Ubuntu boot splash has gone ?"
date: 2010-07-15
forum: General Help
---

### Post by Super_tramp on 2010-07-15
My splash screen at startup and shutdown are no longer shown, I have been editing grub 2 quite a bit lately and not sure if i may of stopped the process? 

I have tried the following commands to try and restore it to default but have had no luck;

sudo update-alternatives --auto default.plymouth
sudo update-initramfs -u

Any ideas ?

I'm running 10.04 :)

---

### Post by linuxman94 on 2010-07-15
Try this command in the terminal.

```
sudo echo "FRAMEBUFFER=y" > /etc/initramfs-tools/conf.d/splash && sudo update-initramfs -u
```

---

### Post by Don1500 on 2010-07-15
> **linuxman94 said:**
> Try this command in the terminal.

```
sudo echo "FRAMEBUFFER=y" > /etc/initramfs-tools/conf.d/splash && sudo update-initramfs -u
```

```
bash: /etc/initramfs-tools/conf.d/splash: Permission denied

```

opps, /etc/initramfs-tools/conf.d/splash does not contain splash

---

### Post by Super_tramp on 2010-07-15
[FONT=monospace]bash: /etc/initramfs-tools/conf.d/splash: Permission denied


:( ... Oh dear.

Any other ideas?
[/FONT]

---

### Post by Super_tramp on 2010-07-15
> **Super_tramp said:**
> [FONT=monospace]bash: /etc/initramfs-tools/conf.d/splash: Permission denied


:( ... Oh dear.

Any other ideas?
[/FONT]


I've been trying to sort this for way too long now.

My /etc/default/grub file i have restored to default so i know it's not that.

I have tried the solution as featured h[ere]("http://reformedmusings.wordpress.com/2010/05/01/corrupt-bootsplash-fix-in-ubuntu-lucid-10-04-lts/") 

I have also tried this [solution ]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

Searched all through forums and IRC. 

I'm totally out of ideas.

---

### Post by linuxman94 on 2010-07-16
Ok then lets try this a different way!

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

Copy this into the file and save and close.

```
FRAMEBUFFER=y
```

Then run:

```
sudo update-initramfs -u
```

---

### Post by Super_tramp on 2010-07-18
No, still no luck. 

I think I'm just going to have to live with it, it doesn't really bother me that I don't have a startup/shutdown splash but I just want to know why ? 

Thanks

---

