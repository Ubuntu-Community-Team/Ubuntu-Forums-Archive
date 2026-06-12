---
title: "Unable to log in after update!"
date: 2010-02-06
forum: General Help
---

### Post by Richiegs on 2010-02-06
I have used Ubuntu 9.10 for a few months. I like it because it seems faster than Windows XP or Vista. Nevertheless, it has happened many times that I couldn't log in Ubuntu after an update. I thus had to uninstall Ubuntu from Windows and reinstall a clean copy of Ubuntu again. 
1. Is this common to you guys or just me alone?
2. What are the causes?
3.Does Wubi play a role in causing this login problem since I install Ubuntu thru Wubi?
4. What are other solutions in solvng this login problem?

Thank you for anyone who answers.

---

### Post by dolphinaura on 2010-02-06
> **Richiegs said:**
> I have used Ubuntu 9.10 for a few months. I like it because it seems faster than Windows XP or Vista. Nevertheless, it has happened many times that I couldn't log in Ubuntu after an update. I thus had to uninstall Ubuntu from Windows and reinstall a clean copy of Ubuntu again. 
1. Is this common to you guys or just me alone?
2. What are the causes?
3.Does Wubi play a role in causing this login problem since I install Ubuntu thru Wubi?
4. What are other solutions in solvng this login problem?

Thank you for anyone who answers.

IMO, a lot of users have weird stuff happen when using wubi.
I advise you to boot from the cd, select "install ubuntu". When you get to the parittioning stage, choose to resize the windows volume.

2, Wubi users have a lot of mysterious problems that happen to random people, theirs a lot that have never gotten fixed, or have never recieved a response.

3. Could be, since ive seen that a lot of people like
[http://ubuntuforums.org/showthread.php?t=1363374](http://ubuntuforums.org/showthread.php?t=1363374)
are having problems after updates

4. see #2

---

### Post by brianfactors on 2010-02-06
I'm pretty sure it's Wubi. Wubi is not supposed to be a permanent solution; it's just for testing Ubuntu out.

You really should install Ubuntu on its own partition. That allows you to have other good stuff like hibernation and it'll be even faster.

Unless I'm mistaken, the problem arises when a ubuntu update updates the actual kernel. In a regular installation, another entry is added to grub. I'm presuming that the boot.ini file in windows isn't updated when ubuntu is.

---

### Post by Richiegs on 2010-02-06
Brianfactors, thanks for your prompt reply. I guess it is not good to install Ubuntu thru Windows.
1. If I install Ubuntu on it s own partition, am I still able to access Windows files?
2. If I install Ubuntu on it s own partition, is it easy to uninstall it if there is a problem?
3. If I install Ubuntu on it s own partition, am I able to access Ubuntu files from Windows?
Many thanks

---

### Post by TriadHonor on 2010-02-07
Wubi's Grub bug is well knowed, and it is possible to fix it from Windows.
I just post a guide on how to do that, read it.

The guide is here ---> [http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)

Please, tell me if it works like for me.

---

