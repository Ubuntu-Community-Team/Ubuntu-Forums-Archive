---
title: "Saving Files In /boot/grub/"
date: 2010-03-03
forum: General Help
---

### Post by P-Geist on 2010-03-03
Hello,

Im new to Ubuntu and Linux for that matter and need to know how i can change permissions so that i can save in the /boot/grub folder.

Need any more info just post.

Thanks
P-Geist

---

### Post by Pritamsng on 2010-03-03
1st tell me what you wan to save...
to change permissions you need to login as root or you should have root privileage.

---

### Post by QLee on 2010-03-03
[QUOTE=P-Geist]
Im new to Ubuntu and Linux for that matter and need to know how i can change permissions so that i can save in the /boot/grub folder.[/QUOTE]

First off I'm going to recommend that you not try to do that as a new user, it has the potential of causing you much trouble. Those files aren't meant to be user edited, even though it is possible. Just not a good idea until you have a bit more experience and understanding about how GNU/Linux permissions work.

[QUOTE=P-Geist]Need any more info just post.[/QUOTE]

OK, I'll take you at your word, why do you want to do that? There are very likely better ways to accomplish whatever goal you have in mind, share and someone may be able to help you do it in a recommended way.

---

### Post by P-Geist on 2010-03-03
When i boot Ubuntu it loads grub and says no device i fixed that by deleting the no floppy line. Now i need to edit grub.cfg and remove the no floppy lines there so that every time i boot i no longer need to delete the no floppy line.

---

### Post by QLee on 2010-03-03
> **P-Geist said:**
> When i boot Ubuntu it loads grub and says no device i fixed that by deleting the no floppy line. Now i need to edit grub.cfg and remove the no floppy lines there so that every time i boot i no longer need to delete the no floppy line.

Do you realise that each new kernel upgrade will regenerate that file and erase whatever changes you made to it?

---

### Post by mcduck on 2010-03-03
> **P-Geist said:**
> When i boot Ubuntu it loads grub and says no device i fixed that by deleting the no floppy line. Now i need to edit grub.cfg and remove the no floppy lines there so that every time i boot i no longer need to delete the no floppy line.

You are not even supposed to edit that file yourself (it actually tells you that on the beginning of the file).

All configuration for grub2 is done in /etc/default/grub and the files inside /etc/grub.d/

What comes to permissions, changing the permissions and/or ownership of system files is usually a very bad idea. To get permissions to edit the files you should sue "sudo". [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by P-Geist on 2010-03-03
So how can i fix my it so that when i boot i dont always need to edit the boot commands so that the "no floppy" line is no longer present?

:(

---

### Post by QLee on 2010-03-03
> **P-Geist said:**
> So how can i fix my it so that when i boot i dont always need to edit the boot commands so that the "no floppy" line is no longer present?

If I remember correctly, this was an error that occurred in the early stages of the change to GRUB2 and what you are trying to do was a workaround that some people used at the time. I think the problem was corrected by reinstalling a newer(current) version of GRUB
to the MBR because early GRUB code produced that error.

I think I also remember some people having success by disabling the floppy drive in the system BIOS.

---

### Post by P-Geist on 2010-03-03
Whats the best way, and how do i do it.

Also im on a Laptop....

---

### Post by QLee on 2010-03-03
> **P-Geist said:**
> Whats the best way, and how do i do it.

Also im on a Laptop....

See if this wiki page helps. Come back if there are things you don't understand. 
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by P-Geist on 2010-03-03
This is why i needed to edit the file grub.cfg

[https://wiki.ubuntu.com/Grub2#--no-floppy](https://wiki.ubuntu.com/Grub2#--no-floppy)

And the first post here is also what i need to do thats why i need the permissions

[http://ubuntuforums.org/showthread.php?t=1194714&page=2](http://ubuntuforums.org/showthread.php?t=1194714&page=2)

EDIT: Never mind i did what the above forums link said and im fine now.

Thanks
P-Geist

---

### Post by QLee on 2010-03-03
[QUOTE=P-Geist ]This is why i needed to edit the file grub.cfg

[https://wiki.ubuntu.com/Grub2#--no-floppy](https://wiki.ubuntu.com/Grub2#--no-floppy)[/QUOTE]


Did you notice the date there?  Monday June 22, 2009. It's an old issue that has been fixed in newer versions.

[QUOTE=P-Geist ] And the first post here is also what i need to do thats why i need the permissions

[http://ubuntuforums.org/showthread.php?t=1194714&page=2](http://ubuntuforums.org/showthread.php?t=1194714&page=2)

EDIT: Never mind i did what the above forums link said and im fine now.[/QUOTE]

Well, you probably still have the old version in your MBR. However, if you're happy, that's fine.

---

