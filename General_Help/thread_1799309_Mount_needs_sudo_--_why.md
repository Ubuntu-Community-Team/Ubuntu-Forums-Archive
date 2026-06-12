---
title: "Mount needs sudo -- why?"
date: 2011-07-07
forum: General Help
---

### Post by Paddy Landau on 2011-07-07
When I plug in a USB drive, it mounts automatically.

But, if I want to mount it manually, I need to use sudo.

Why is this? Why am I unable to mount manually without sudo when it will mount automatically without sudo?

---

### Post by WorMzy on 2011-07-07
Automounting is handled by udisks, not mount. I don't know the specifics, but I think that the reason you don't need to authenticate when using udisks is because it uses PolicyKit's rules to control what users are able to do, rather than only letting root (or sudo users) have access to that functionality.

---

### Post by Paddy Landau on 2011-07-07
I have tried udisks and it works perfectly.

Thank you.

I'll mark as solved.

---

### Post by Paddy Landau on 2011-08-24
I'm finding one use of udisks does not work.

I have an iso that I'd like to mount. Using sudo, it's easy:
```
sudo mount -o ro,loop [file-name].iso [mount-point]
```Example:
```
sudo mount -o ro,loop lubuntu-11.04-desktop-amd64.iso ~/lubuntu
```.
But I cannot get this to work with udisks. I have tried variations on the following command, from simple to complex, and they all give the same error:
```
udisks --mount lubuntu-11.04-desktop-amd64.iso --mount-fstype iso9660 --mount-options ro,loop=/dev/loop0
[COLOR=Navy]Device file lubuntu-11.04-desktop-amd64.iso is not a block device: Resource temporarily unavailable[/COLOR]
```.
Do you know how a person can mount an ISO without using sudo?

---

### Post by coffeecat on 2011-08-24
> **Paddy Landau said:**
> 
Do you know how a person can mount an ISO without using sudo?

I see you are using Lucid. In versions later than Lucid you can simply right-click on the ISO and "Open with.. Archive Mounter". I seem to remember that wasn't installed by default in Lucid. I don't have access to a Lucid installation at the moment and I can't check but is archive mounter in the Lucid repos?

**EDIT**: sorry, that wasn't very helpful because I can't see atm what package provides archive mounter (in Natty). It looks like a nautilus extension but I can't find it. I'll post back if I find something.

---

### Post by Paddy Landau on 2011-08-24
Thanks for the reply.

I see that Lucid does indeed have that option in Nautilus. (Perhaps I installed something for this, though I don't remember doing so.)

However, I was looking for a command line so that I can use it in a script. Presumably the Archive program does it; but I don't know what command that is?

---

