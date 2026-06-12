---
title: "Splash screen - always text fallback"
date: 2011-09-22
forum: General Help
---

### Post by whatthefunk on 2011-09-22
Ive been trying to change my splash screen for months.  No matter what I do, it displays the text fallback splash screen.  All my config files will point to the splash screen I want, but the fallback text one comes up.  My guess is that my video device isnt loading up in time.  Is there any fix for this??

---

### Post by sanderd17 on 2011-09-22
> **whatthefunk said:**
> Ive been trying to change my splash screen for months.  No matter what I do, it displays the text fallback splash screen.  All my config files will point to the splash screen I want, but the fallback text one comes up.  My guess is that my video device isnt loading up in time.  Is there any fix for this??


Do you use open source drivers? Proprietary drivers can't be started early enough for plymouth I believe.

---

### Post by whatthefunk on 2011-09-22
I believe they are open source....how do I check?  I didnt have to install any drivers for my video devices...

---

### Post by sanderd17 on 2011-09-22
Check this wiki page on how to set it up on a basic linux system: [https://wiki.archlinux.org/index.php/Plymouth](https://wiki.archlinux.org/index.php/Plymouth)

You won't need to recompile the kernel, because the Ubuntu kernel already contains those settings. But you can check other settings.

For the video drivers. If you use an ATI or Intel card, you probably use Open-source drivers. If you have an nVidia card, than you probably use closed source drivers. The nouveau drivers are the open source ones, but they don't work with Unity, compiz or Gnome-shell and have bad performance for games.

---

### Post by whatthefunk on 2011-09-22
Its an Intel graphics card so Im assuming that the drivers are not the issue.

The arch page for plymouth doesnt really apply to Ubuntu...Debian based systems use update-alternatives.  Ive been through all that several times.

---

