---
title: "Any way to disable Installation/Try Live USB Prompt?"
date: 2010-09-10
forum: General Help
---

### Post by antimatter15 on 2010-09-10
I configured my flash drive to be bootable using the gui startup disk creator, and it's working pretty well for me, but every time it boots, it pops up the dialog where you have two options, to use the live usb mode or to install. Is there any way to bypass that prompt and just go straight to the live usb mode?

---

### Post by dcstar on 2010-09-11
> **antimatter15 said:**
> I configured my flash drive to be bootable using the gui startup disk creator, and it's working pretty well for me, but every time it boots, it pops up the dialog where you have two options, to use the live usb mode or to install. Is there any way to bypass that prompt and just go straight to the live usb mode?

Edit the /syslinux/text.cfg file.

---

### Post by antimatter15 on 2010-09-24
I didn't try your suggestion but I assume it's not quite what I'm looking for. I think syslinux is referring to the bootloader prompt which isn't quite the issue. I'm talking about the one that seems to be made with gtk (the theme gets loaded, there's a mouse, it's after the bootsplash).


I can't quite take a picture since it's before the desktop is loaded. But I found this screenshot of the same thing somewhere.

[IMG]http://2.bp.blogspot.com/_9NdcYBKsZyo/TAaTIS9FZiI/AAAAAAAAAUw/vrrvt9aWGGQ/s1600/Screenshot.jpg[/IMG]

Is there any way to skip the prompt?

---

### Post by dkbiby on 2010-10-16
Between this stupid prompt and moving the window controls to the left (which I immediately changed back) I am wary of showing off my USB Ubuntu install on friend's computers.  I know its free and I've always been a big proponent of Open Source but it seems the last two versions of Ubuntu have just been an exercise in foot shooting.

---

### Post by Baffetto on 2010-11-19
Maybe this could help:
[http://ubuntuforums.org/showthread.php?p=10136413#post10136413]("http://ubuntuforums.org/showthread.php?p=10136413#post10136413")

---

