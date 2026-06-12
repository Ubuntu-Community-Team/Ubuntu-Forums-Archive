---
title: "[URGENT] I lost access to sudo"
date: 2011-03-24
forum: General Help
---

### Post by n4pgw on 2011-03-24
buck@Bear:~$ sudo -s
sudo: /etc/sudoers is mode 0444, should be 0440
sudo: no valid sudoers sources found, quitting
buck@Bear:~$ 

Ubuntu 10.10 desktop

I lost access to sudo.  It originally said sudoers mode was 0755.  I booted to the recovery section and changed chmod sudoers and sudoers.backup to 0444.  I also had to add my user to admin and sudoers.  When I rebooted, I still get the message.

I am unable to run updates or install packages. 

Please advise.

Thanks
Buck

---

### Post by Another Monkey on 2011-03-24
Does [this]("http://www.psychocats.net/ubuntu/fixsudo") help?

---

### Post by n4pgw on 2011-03-24
I am looking at it right now.  Thanks

---

### Post by n4pgw on 2011-03-24
Apparently, VirtualBox inadvertently changed the mode of /etc/sudoers to 0755 when it edited the file. (That's my guess, anyway.)

When I changed it, I misread the error message and set the mode to 044[COLOR=DarkRed]**4**[/COLOR] instead of 044**[COLOR=DarkRed]0[/COLOR]**.  

I caught that when following the directions.

Thank you, Monkey. 

Buck

---

