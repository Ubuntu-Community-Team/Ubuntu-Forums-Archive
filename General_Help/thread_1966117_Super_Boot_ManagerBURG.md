---
title: "Super Boot Manager/BURG"
date: 2012-04-26
forum: General Help
---

### Post by Ken147 on 2012-04-26
here is the breakdown....

1) Super boot loader:

- when I add and update the PPA it gives a 404 error for that ppa, I did find a older version of SBM but when it loads in the software center it gives a dependencies (I think that's right).

2) BURG:

- installs but on reboot does not load.

---

### Post by PhantomTurtle on 2012-04-26
1. If you are using Ubuntu 12.04, then the Super Boot Manager repository will not add because a presise one has not been made.

2.Not sure actually but if you want to repair grub then here is a guide: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")(This can be done with the Ubuntu live CD).

---

### Post by Ken147 on 2012-04-27
> **PhantomTurtle said:**
> 1. If you are using Ubuntu 12.04, then the Super Boot Manager repository will not add because a presise one has not been made.

2.Not sure actually but if you want to repair grub then here is a guide: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")(This can be done with the Ubuntu live CD).

thanks for the info, grub is working fine, when I installed burg and rebooted it was like it wasn't even there. I just booted to GRUB.

---

### Post by zombifier25 on 2012-04-27
FYI, I have Super Boot Manager on Precise, using the repo for Oneiric.
Did you
1. Install Burg?
2. Run ```
sudo burg-install /dev/sda
```
(Replace /dev/sda with your appropriate disk. But usually you don't need to)

---

### Post by Ken147 on 2012-04-27
> **zombifier25 said:**
> FYI, I have Super Boot Manager on Precise, using the repo for Oneiric.
Did you
1. Install Burg?
2. Run ```
sudo burg-install /dev/sda
```
(Replace /dev/sda with your appropriate disk. But usually you don't need to)

I tried the one I had on Oneiric but, it gave me a 404 when I added the ppa and ran sudo apt-get update. I also found a package of the same one but it gives me a dependencies unsatisfied error.

---

### Post by zombifier25 on 2012-04-27
What ppa are you using? Mine is **ppa:ingalex/super-boot-manager**

---

### Post by Ken147 on 2012-04-27
> **zombifier25 said:**
> What ppa are you using? Mine is **ppa:ingalex/super-boot-manager**

yep same ppa. (I also did a clean install of 12.04 so there should be no lingering stuff from 11.10 hanging around.)

---

### Post by zombifier25 on 2012-04-27
Weird. Try double-checking in Software Sources to see if the distro is set to "oneiric".

---

### Post by Ken147 on 2012-04-27
> **zombifier25 said:**
> Weird. Try double-checking in Software Sources to see if the distro is set to "oneiric".

you mean in here?

---

### Post by Ken147 on 2012-04-27
SBM is installed now!!! now to see if BURG will install properly.

---

### Post by Ken147 on 2012-04-27
nope :(

says an error has occurred

---

### Post by Ken147 on 2012-04-27
could burg not installing have something to do with the 404 errors I getting when i do apt-get update?

---

### Post by zombifier25 on 2012-04-28
Are you still getting an 404 when apt-get updating?

---

### Post by Ken147 on 2012-04-28
> **zombifier25 said:**
> Are you still getting an 404 when apt-get updating?

disabling the one that gave me 404 error let me install SBM (still getting 404 errors though) but now I'm having this problem

[http://ubuntuforums.org/showthread.php?t=1966877](http://ubuntuforums.org/showthread.php?t=1966877)

---

### Post by kryten2k35 on 2012-05-01
I couldn't get SBM to install using the precise repo, but I edited the source back to oneiric, updated and installing it now. I'll let you know if it works.

---

