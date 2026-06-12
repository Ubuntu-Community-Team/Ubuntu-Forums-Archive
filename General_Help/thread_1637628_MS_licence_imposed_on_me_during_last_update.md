---
title: "MS licence imposed on me during last update"
date: 2010-12-04
forum: General Help
---

### Post by kvant on 2010-12-04
I've just ran update manager to be presented with a pop-up window with Microsoft EULA for MS fonts intaller. I do not want to accept it, but the "back" button isn't working and the only other present button is "forward".

Can anyone tell me what the hell is this?

I really doubt that one or two other PPA's that I have set up are trying to pull this, but I'll leave that option open until I get an answer.

Thank you.

---

### Post by endotherm on 2010-12-04
well the ubuntu-restricted-extras package (or mabey its mediubuntu? I forget) installs the MS truetype fonts package. the last update contained an update for that package, so the installer license came back up. you likely already agreed to this license as some point in the past while initially installing it, and kind of missed what it was asking you (all too common with eulas.) this woudl make sense if you installed the restricted extras via the commandline. the lincense dialog in that case is a blue screen, that requests you to type y or n, iirc. the new update-manager dialog box looks much more official.

---

### Post by kvant on 2010-12-04
> **endotherm said:**
> well the ubuntu-restricted-extras package (or mabey its mediubuntu? I forget) installs the MS truetype fonts package. the last update contained an update for that package, so the installer license came back up. you likely already agreed to this license as some point in the past while initially installing it, and kind of missed what it was asking you (all too common with eulas.) this woudl make sense if you installed the restricted extras via the commandline. the lincense dialog in that case is a blue screen, that requests you to type y or n, iirc. the new update-manager dialog box looks much more official.

This Ubuntu installation is about 3 days old, unless it was in super fine print somewhere I don't remember seeing any licence like this and that is exactly what I don't expect from a GNU/Linux distro.

I'm pretty serious about licences on my GNU/Linux and I wouldn't go though any licensing just like that.

I don't have Medibuntu.

---

### Post by endotherm on 2010-12-04
interesting. so you don;t have the ubuntu-restricted-extras or any restricted codecs installed?

---

### Post by kvant on 2010-12-04
> **endotherm said:**
> interesting. so you don;t have the ubuntu-restricted-extras or any restricted codecs installed?

Unfortunately, I do, but no Medibuntu. What's troubling me (and I know it could be just clasified as a bug) is that I couldn't refuse this licence, but also that this is the first time that I see a big-mumbo-jumbo licence widnow pop-up like this on Ubuntu. It's a bit shocking :)

---

### Post by dFlyer on 2010-12-04
MS Font is part of ubuntu-restricted-extras package.

---

### Post by endotherm on 2010-12-04
> **kvant said:**
> Unfortunately, I do, but no Medibuntu. What's troubling me (and I know it could be just clasified as a bug) is that I couldn't refuse this licence, but also that this is the first time that I see a big-mumbo-jumbo licence widnow pop-up like this on Ubuntu. It's a bit shocking :)

well I think you can uninstall them with:
```
sudo apt-get remove msttcorefonts
```
that meets the MS terms for terminating the license.

---

### Post by kvant on 2010-12-04
> **endotherm said:**
> well I think you can uninstall them with:
```
sudo apt-get remove msttcorefonts
```that meets the MS terms for terminating the license.

Aye, thanks, I just did (actually I've removed the installer, so it seems, I didn't find the msttcorefonts package installed at all).

I'll go file a bug report fot the inability to refuse the licence.

---

