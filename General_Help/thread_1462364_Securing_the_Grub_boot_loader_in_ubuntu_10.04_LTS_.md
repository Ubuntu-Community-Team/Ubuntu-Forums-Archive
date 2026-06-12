---
title: "Securing the Grub boot loader in ubuntu 10.04 LTS issue"
date: 2010-04-25
forum: General Help
---

### Post by stroyeror on 2010-04-25
OK so i was following this guide here : [http://ubuntuforums.org/showthread.php?t=715630](http://ubuntuforums.org/showthread.php?t=715630)

First thing i noticed was that it seems that menu.lst is now Grub.cfg, am I on the right track with that?

Also when i get to the part to type in GRUB it says grub is not currently installed.  I get the same things for md5crypt.  any idea what is going on here?

---

### Post by quixote on 2010-04-26
10.04 uses Grub2.  The "How to secure grub" link that you mention refers to old-grub, or grub-legacy as they sometimes call it.  The two are completely different, and you can't use any instructions for Grub2 in grub-old, or vice versa.

In Grub2, you're supposed to confine your editing to the files in /etc/grub.d/, mainly I believe to the 40_custom file.  The standard settings are in /etc/default/grub.  If you change anything in those, then you run "sudo update-grub" and that's what changes the /boot/grub/grub.cfg file.

You probably already know this, but just in case: commands in linux are case sensitive.  So "GRUB" is not the same as "grub".  Typing the former will get you a "not installed" error.  Re md5crypt: start synaptic (System > Administration > Synaptic) and see whether maybe it's not installed?

There's everything about how to use grub2 here: [https://help.ubuntu.com/community/Grub2#File%20Structure](https://help.ubuntu.com/community/Grub2#File%20Structure).  (The link is to just one section, but you may want to look at the whole thing.)

---

