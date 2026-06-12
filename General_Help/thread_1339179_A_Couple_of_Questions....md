---
title: "A Couple of Questions..."
date: 2009-11-27
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2009-11-27
I've just recently started using Ubuntu 9.04, and I have a couple of questions:

Everytime I boot into Ubuntu, I get a window saying: "The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked."

I then have to provide it with a password. I think something to do with this may have come up when I first booted up Ubuntu, asking to create a password, which I did. Is there any way to stop this window coming up?

2nd question: I installed Avant Window Navigator via Add/Remove... command in the Applications menu, but when I tried to launch it, I get a message saying: "Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."" What does this mean?

TIA

---

### Post by ..::| Dave89 |::.. on 2009-11-27
Also is there a way to get a trash icon on the desktop?

---

### Post by H4F on 2009-11-27
I have similar issue . It annoying me each time I reboot.
Also want to know if there are solutions to this

---

### Post by 3rdalbum on 2009-11-27
There are plenty of posts about it. Disable automatic login and your keyring will be unlocked every time you log in. Or change your keyring password to blank and it will be unlocked automatically every time it's needed.

You need to be running Compiz or some other compositing window manager (like KDE's kwin or XFCE's xfwin) before you can use AWN. It relies on the compositing. If you want a dock that can run without compositing, then I believe Cairo Dock can do this; you'd need to add Cairo Dock via a PPA though.

The trash icon can be added using the "gconf-editor" program. Hit Alt-F2 and type "gconf-editor" without the quotes, and you'll find the setting in apps > nautilus > desktop.

---

### Post by ..::| Dave89 |::.. on 2009-11-27
I got the Trash icon on the desktop.  I found SimDock, and uninstalled Avant Window Manager.

---

### Post by ..::| Dave89 |::.. on 2009-11-27
I looked through the settings in Control Center, but I can't find a way to change the keyring password.

---

### Post by NFblaze on 2009-11-27
Try

 Passwords and Encryption Keys in the Admin menu

---

### Post by ..::| Dave89 |::.. on 2009-11-27
I stopped the window coming up at startup by deleting the 2 passwords that was stored in the Password and Encryption keys, restarted the computer, and left the password blank.

I have a question about the GRUB bootloader, or whatever it's called; When the computer boots up, Ubuntu is at the top of the list of operating systems, and the computer boots into Ubuntu after about 10 seconds if I don't intervene.  Is there a way to get Vista to be shown at the top of the list instead? Since Vista is my main OS, I would like it to boot into that without me having to intervene everytime.

TIA

---

### Post by Iowan on 2009-11-28
> **..::| Dave89 |::.. said:**
>   Is there a way to get Vista to be shown at the top of the list instead? Since Vista is my main OS, I would like it to boot into that without me having to intervene everytime. You can edit */boot/grub/menu.lst*. ```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
...
default         0

```You don't necessarily need to move Vista to the top of the list - you can change the **default** line instead.
Dunno if you need to run **sudo update-grub** afterward...

---

### Post by fluffman86 on 2009-11-28
It's not very secure to have *NO* passwords, but if you want to automatically connect to a wireless or wired internet connection, you can right-click on the network-manager next to the clock, and click "Edit Connections."

In the window that pops up, click the connection you want to edit (Auto eth0 for wired, or switch to the Wireless tab for more) and click edit.  In the next window, check the boxes next to "Connect Automatically" and "Available to all users" then click Apply.  Now you can have passwords set to protect your keyrings, and still login and connect to your internet connections automatically.

---

