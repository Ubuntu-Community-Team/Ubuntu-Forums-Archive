---
title: "Edit grub?"
date: 2009-10-26
forum: General Help
---

### Post by k5cqb on 2009-10-26
I recently installed Ubuntu 9.10 on a dell with XP already installed.  The install went fine and ubuntu booted.  A few days later I tried to boot ununtu again but it hung on a blank screen.  I found some suggestions about removing the "quiet splash", I did and it boots fine now.  

My problem is that it does not save the setting.  I tried to go to the /etc/default/grub but it is read only and wont allow me to change it.  I am sure this is probably an easy fix but I have been away from linux for a while now and it's like I am starting over, lol.

---

### Post by macaholic on 2009-10-26
I would read more about the new GRUB2 here, with info on how to edit it properly: [http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by efflandt on 2009-10-26
I am new at Ubuntu and hadn't played with grub for a long time.  But from another post, you edit menu.lst (as in list, not first) in /boot/grub.  But you have to use sudo for your editor in order to have permission to save it, and after that do **sudo update-grub**.  But it would be a good idea to first do something like **sudo cp menu.lst menu.lst.orig** or something as a backup in case you need the original file.

PS: OK I guess grub2 is a little different config file.

---

### Post by Elfy on 2009-10-26
A fairly comprehensive new wiki page for Grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by k5cqb on 2009-10-28
Resolved, thanks for the link.

---

