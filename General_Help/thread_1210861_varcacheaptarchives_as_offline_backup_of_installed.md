---
title: "/var/cache/apt/archives as offline backup of installed programs?"
date: 2009-07-12
forum: General Help
---

### Post by ecmatter on 2009-07-12
Can the .deb packages in /var/cache/apt/archives be saved to a disk and used as an offline backup of installed packages?  Can they be transferred to and installed on another computer running Ubuntu?

---

### Post by Frugoo Scape on 2009-07-12
Pop you ubuntu CD in and configure your apt-get to download off the cd.

I've done this before, but I cant remember the exact code for it since I have not used Ubuntu is so long.

Using this method means you won't have to redownload anything since most the packages are on it.

---

### Post by earthpigg on 2009-07-12
yes and yes :D

---

### Post by navaneethan on 2009-07-12
Copy all the package to desktop

and type this cammand

> cd ~/Desktop

> sudo dpkg -i *.deb

---

### Post by ecmatter on 2009-07-12
You don't know how happy this makes me.  I have a sloooow connection and a penchant for wrecking my installation.  Thanks all around.

---

### Post by Frugoo Scape on 2009-07-12
> **navaneethan said:**
> Copy all the package to desktop

and type this cammand

Yeah, you could do that, but why save stuff that is already "saved" on a CD I bet.
But, good thinking that will work perfect.

---

### Post by earthpigg on 2009-07-12
> **navaneethan said:**
> Copy all the package to desktop

and type this cammand

dont do this right now or you are going to have 50000 .deb files cluttering your desktop :P

and the command i would use is this:

```
sudo dpkg -i ~/Desktop/*.deb && rm ~/Desktop/*.deb
```

the stuff after && will remove the 5000 .deb files from your desktop.

---

### Post by ecmatter on 2009-07-12
> **earthpigg said:**
> dont do this right now or you are going to have 50000 .deb files cluttering your desktop :P

and the command i would use is this:

```
sudo dpkg -i ~/Desktop/*.deb && rm ~/Desktop/*.deb
```the stuff after && will remove the 5000 .deb files from your desktop.

Noted, and thanks.

---

