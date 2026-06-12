---
title: "Admin password all the time !!"
date: 2010-04-16
forum: General Help
---

### Post by ubun2warrior on 2010-04-16
Hi 
I am using Ubuntu 9.10 (along with Win xp). I have to authenticate everytime I mount filesystem(My d: , e: drives in windows). Or to connect to the internet (i use mobile broadband) i have to authenticate, also if i have to install something from synaptics i have to authenticate.

I know this is good for security but i am the only person using my computer , so is there any way out of this authentication business. 

My regards to all

---

### Post by maddg3241 on 2010-04-16
if you use kde there is no auth. in that os

---

### Post by sdowney717 on 2010-04-16
research about running as root user.
Some linux distros easily let you do this, like Fedora. Ubuntu sort of hides the gui root login. Running as root will let you do all that you want and it is also much easier to mess up your file system aod other things. So ubuntu discourages this.

---

### Post by wojox on 2010-04-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by doas777 on 2010-04-16
there are ways to eliminate the checks, but they do seriously weaken system security. my best advice, is just get used to it. 

keep in mind, the sudo system does a lot to protect you both from threats locally (primarilly Software) but also remote ones.  sudo is not trying to protect you from local users (any sudo capable user already knows the password, and admins should know what they are doing), but it does require a given peice of software to warn you before it takes an administrative action. 

ubuntu is often much more secure than the latest windows, but if you disable sudo checks, then you reduce it to windowsXP levels. Windows vista/7 won't let you install software or modify system files without simmilar checks.

here is some info on the sudoers file, should you choose to continue down this path:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

not trying to lecture, but I don't get why entering your password 2 times per boot is all that onerous. 

also, I recommend that you don't mount your ntfs drives all the time. ubuntu won't ever check them for filesystem integrity, so unless you boot into windows pretty often to do a chkdsk, the damage to the fs can really pile up. instead if I need a file available cross-platform, i share it to the network on another box.

in general, once you have a box set up and configured to taste, if you still feel like you have to put your password in all the time, then something may be suboptimal with the way you are using it. I only have to sudo a handful of times a week, unless it;s release week for the latest greatest ubuntu. 

hth

---

### Post by maddg3241 on 2010-04-16
ya if you do run as root you can mess up important files but that would work too

---

### Post by doas777 on 2010-04-16
> **maddg3241 said:**
> ya if you do run as root you can mess up important files but that would work too
the bigger problem is that you are giving carte blanche to any application (including a malicious PDF with java shell code in it ) to delete your files, compile exploits, install rootkits, use your computer for cyber crime, etc. sudo at least ensures that these actions require that the user be aware of them.

---

