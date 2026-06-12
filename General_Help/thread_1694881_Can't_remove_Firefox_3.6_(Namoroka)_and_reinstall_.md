---
title: "Can't remove Firefox 3.6 (Namoroka) and reinstall Firefox 2"
date: 2011-02-25
forum: General Help
---

### Post by Frogbarf on 2011-02-25
Running Ubuntu 8.04

Thought I'd be clever and upgrade Firefox to v. 3 using instructions at 

[http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html")

Ended up with "Namoroka" which seems to be Firefox 3.6, and it's a prerelease version.

Flash works under my admin id but not under normal user id. Reinstalling Flash didn't help. Want to revert to Firefox 2 that came with Ubuntu 8.04 so Flash will work again.

Can't uninstall "Namoroka" - uninstalled Firefox-3 but it's still hanging in there!

Can't reinstall Firefox 2

Yikes! Help!

---

### Post by An Sanct on 2011-02-25
8) Those instructions are **one year old** and shouldn't be used!

Firefox 3.6.13 is in the repositories, remove Namoroka and install it instead of FF2

```
sudo apt-get remove firefox firefox-3.5 firefox-3.6 
sudo apt-get install firefox

```I strongly advice to use that stable version and either keep away from older alphas/betas or use the newest one (currently v4.0b12pre)

[PS. You might also want to check this thread]("http://ubuntuforums.org/showthread.php?t=1483901")

---

### Post by Frogbarf on 2011-02-25
> **An Sanct said:**
> 8) Those instructions are **one year old** and shouldn't be used!

Firefox 3.6.13 is in the repositories, remove Namoroka and install it instead of FF2

Thank you. I managed to stumble into this. The key lay in removing the references to the prerelease versions in /etc/apt/sources.list

Flash also works. The trouble was that cookies were enabled for YouTube but cookies for other domains weren't. By completely disabling cookies for YouTube, things started to work.

---

