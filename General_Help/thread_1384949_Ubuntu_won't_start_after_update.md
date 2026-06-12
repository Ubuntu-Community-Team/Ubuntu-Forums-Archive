---
title: "Ubuntu won't start after update"
date: 2010-01-19
forum: General Help
---

### Post by flihot on 2010-01-19
Hi,

I got a new laptop yesterday and installed the latest version of ubuntu on it, (i'd been using ubuntu fine for about a year with no problems) and it worked fine all yesterday until i decided to install some updates at which point it asked me to restart and now it won't boot again. it just hangs after "*starting init crypto disks [OK]" i tried leaving it for 5 minutes and nothing happened. Right now im running off the live cd and can't seem to get access to my home folder either, i did write down that long passphrase but i have no idea where to put it in.

Thanks

---

### Post by flihot on 2010-01-19
Okay i've accepted the fact that im probably going to have to reinstall, i've managed to get into my home folder using the guide here: [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

But have no idea how to move the files out of there using the terminal. I want to put them on a flash drive but don't know how to tell it to move it there. The drive is not showing up in any of the directories in my encrypted home folder but is showing up on my livecd desktop. Does anyone know how to do this?

thanks.

---

### Post by john newbuntu on 2010-01-19
Follow step13 from this guide to recover your installation:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by flihot on 2010-01-19
Hi, i just tried that twice and it didn't work. It still hangs directly after the disk encryption thing.

---

### Post by Grenage on 2010-01-19
Did you actually find the encryption key in the end?

---

### Post by flihot on 2010-01-19
I have the password and the 32 character pass phrase, but now when i try and follow that "ecryptfs-mount-private" im getting "ERROR: Encrypted private directory is not setup properly"

---

### Post by Grenage on 2010-01-19
> about ecryptfs not being setup properly ... are you using your own account to run the command, or root, or the live ubuntu account? You need to run the command as yourself.

That's from the page you're using.  Are you performing it as root?

---

