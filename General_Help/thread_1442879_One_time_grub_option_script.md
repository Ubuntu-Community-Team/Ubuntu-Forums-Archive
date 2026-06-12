---
title: "One time grub option script"
date: 2010-03-30
forum: General Help
---

### Post by conradin on 2010-03-30
Hai All,
I just had a thought of something I would like to do But I'm not entirely sure how to do.  I have a desktop dual booting Karmic and server 2003. Mostly I boot into Ubuntu but when i have to boot into server I usually forget to scroll down and select my Windows partition. 

What I want to do is have a script where I can specify a one time boot option. As in, I want to run a script, have it reboot my computer and tell grub to boot into Windows server 2003, but not effect future reboots or cold boots. Is there any way to achieve this?

I believe my grub is version 1.97

---

### Post by 98cwitr on 2010-03-30
i might be wrong, but it sounds like the easiest way to do this would be to write a short shell script to a "secondary" menu.lst file that overwrites the current (boot linux first script) menu.lst with a copy that has been modified to boot linux first.

Then have a start-up shell command that does the same thing, only puts the "boot-linux-first" script in place of the "secondary"

just typing out loud ;)

---

### Post by conradin on 2010-03-31
This might reflect my ignorance, but isn't GRUB loaded first then the shell?
If I rewrite (and backup) the grub.cfg file, it seems to me, I would need to have the reverting script function in server2003. I could write a little program in MSserver2003 and run that at start up to move a grub.cfg backup (if it exists) to grub.cfg and end. 

Like I said, Im not sure, is there a pure Linux alternative? 

hmmm, maybe I can do it with the at command,or IDK.

---

