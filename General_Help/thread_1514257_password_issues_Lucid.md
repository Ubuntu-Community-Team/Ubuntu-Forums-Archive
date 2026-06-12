---
title: "password issues Lucid"
date: 2010-06-20
forum: General Help
---

### Post by liz_bliz on 2010-06-20
Hi, I have recently starting using Linux on my home PC.

I downloaded and installed Lucid on my computer and outside of some Plymouth unhappiness related to my video card it has been working well for some time. Recently however, it refuses to accept my administration password for synaptic and the like. The password still works for operating sudo commands within terminal and logging on. It only denies me access when the graphic UI terminal pops. I could not find a thread adressing the issue and I am certain there is one (there alway is!). Could someone give me a workaround or point me in the direction of a relevant thread you would be my hero.

liz_bliz

---

### Post by JC Cheloven on 2010-06-20
Have you tried to change your password? (you can change it back to your previous one afterwards). Either by the users&groups gui menu or by terminal ```
passwd
```
Hope this helps

---

### Post by liz_bliz on 2010-06-20
Yes, I had tried changing the password prior to posting it did not help the same issue continues.

Thank you for the quick response.

---

### Post by liz_bliz on 2010-06-20
bump

---

### Post by MooPi on 2010-06-20
Try in terminal ```
gksudo synaptic
```
If that doesn't work post your contents of this command:
```
sudo less /etc/sudoers
```

---

### Post by liz_bliz on 2010-06-20
> **MooPi said:**
> Try in terminal ```
gksudo synaptic
```If that doesn't work post your contents of this command:
```
sudo less /etc/sudoers
```
The first bit of code does allow me to access the packet manager through the terminal, but it does not fix the underlying problem of a handful of my programs refusing to take my password.


This is the contents that the second command outputs:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL


Thank you again for the help

---

### Post by MooPi on 2010-06-21
Your /etc/sudoers file seems to be missing the last line or at least the same line included in mine:```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```I have additional lines for NOPASSWD options but aren't relevant.
The gksudo is designed for use with graphical programs needing root privileges. That aside edit the /etc/sudoers file can be dangerous as I recently discovered. I edited the file and left a segment that should have been deleted and lost all sudo function. The solution was I booted from a USB pen drive that is my recovery tool and edited the /etc/sudoers file.I'm telling you this as a warning because I'm also giving you the instructions to edit this file. ```
sudo visudo
```

---

### Post by liz_bliz on 2010-06-21
Thank you for the help so far, but while I am trying to find a permanent fix for the issue, could you give me a similar work around to the gksudo synaptic command, but for the update manager? It is another of the programs that is not taking the admin password as legitimate and I have updates in need of installing.

I assume the command also starts with gksudo?

edit: nevermind, I found the command. I will continue to work on the problem, any further help is much appreciated! :D

---

