---
title: "Ubuntu 10.04 log out when resume from suspend"
date: 2010-05-06
forum: General Help
---

### Post by phoenix__ on 2010-05-06
I've just upgraded from 9.10 to 10.04 via the upgrade manager. Prior to the upgrade I was able to suspend and hibernate without any problems. Now that I have upgraded to 10.04, I can suspend however when I resume I am back at the gdm login prompt, logging in again with a new session.

Having just done another test whilst writing this, it actually appears that if I select suspend from the top right I am suspended and can resume my session. If I close the lid on my laptop (which is supposed to suspend) I am logged out and suspended.

Also, Hibernate doesn't work as well - sometimes it never actually hibernates (just sits on a black screen) and sometimes it doesn't resume (it's never hibernated and resumed correctly since the upgrade).

Any ideas?

---

### Post by dino99 on 2010-05-06
might tweak some settings with gconf-editor

---

### Post by phoenix__ on 2010-05-06
> **dino99 said:**
> might tweak some settings with gconf-editor

Thanks, any idea which ones? I've been through them but can't see anything which relates to power, ACPI or suspend.

---

### Post by kikdadog on 2010-05-09
Any resolution to this ??? I have the same problem Log out after hibernation/suspend.

---

### Post by phoenix__ on 2010-05-10
No, it's still happening.

---

### Post by kikdadog on 2010-05-10
anybody out there have a solution to this minor but annoying problem???

---

### Post by kikdadog on 2010-05-11
Help, minor little problem here...............

---

### Post by phoenix__ on 2010-05-11
Stop posting these messages, if someone has the info they will help - unless they get annoyed with all your posts in which case they won't. If you want to do that, create your own thread instead of hijacking this one.

---

### Post by kikdadog on 2010-05-11
Have you done a search ??? I have, multiple questions about this very problem...... no answers. Wonder why??? Leaves the front page and is forgotten. It is called a bump Im well aware of forum etiquette, also to hijack a thread is to change the subject of the thread, I havent done that either. :)



Bump

---

### Post by yura42 on 2010-05-11
I have the same problem :(

---

### Post by Glen007 on 2010-05-12
Since installing 10.04 my PC keeps asking for my password after a few minutes idle time as well.
Rather annoying. How can I disable this?

---

### Post by kikdadog on 2010-05-12
[http://ubuntuforums.org/showthread.php?p=9284425#post9284425](http://ubuntuforums.org/showthread.php?p=9284425#post9284425)

Be sure to thank the guy !!

---

### Post by yura42 on 2010-05-12
This helps me:[INDENT]
**type in terminal**[INDENT]*sudo gedit /etc/default/grub*
[/INDENT]
**then edit the lines** :[INDENT][I]GRUB_CMDLINE_LINUX="_[U]**[U]i8042.reset=1_**[/U][/U]"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **_i8042.reset_**"[/I][/INDENT]

**type again in terminal:**[INDENT]*sudo update-grub*
[/INDENT]

**and reboot**
[/INDENT]

Now it suspends correctly :)

---

### Post by phoenix__ on 2010-05-12
> **yura42 said:**
> This helps me:[INDENT]
**type in terminal**[INDENT]*sudo gedit /etc/default/grub*
[/INDENT]**then edit the lines** :[INDENT][I]GRUB_CMDLINE_LINUX="_[U]**[U]i8042.reset=1_**[/U][/U]"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **_i8042.reset_**"[/I][/INDENT]**type again in terminal:**[INDENT]*sudo update-grub*
[/INDENT]**and reboot**
[/INDENT]Now it suspends correctly :)

Unfortunately this didn't work for me - exactly the same problem when I close the lid on battery.

---

