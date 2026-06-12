---
title: "Applications stop launching?"
date: 2006-02-08
forum: General Help
---

### Post by xEN6 on 2006-02-08
I've got 2 Ubuntu systems, one at work running Breezy i386 and one at home running Breezy AMD64.  Both systems have the same weird issue that, for the life of me, I can't seem to figure out.

After the system is logged in for some time applications simply stop launching from Gnome.  If I am lucky enough to have a terminal open then I can still launch the same applications from there, but clicking on the launchers (either in the menus or panels) bring up a "Starting xyz" and then nothing.  No errors, no application, no beeps, nothing.

The only remedy I have discovered thus far is logging out.  Once I log out and log back in everything goes back to normal for a bit.

Anyone have any ideas?

Sorry if this has been asked before, I searched but didn't seem to find anything pertinent.

Thanks

---

### Post by lamego on 2006-02-08
The only time i had similar problems was about network/dns config issues.
Somehow X was trying to resolve my system hostname when the applications were launched from the menu.

---

### Post by xEN6 on 2006-02-08
[QUOTE=lamego]The only time i had similar problems was about network/dns config issues.
Somehow X was trying to resolve my system hostname when the applications were launched from the menu.[/QUOTE]

How did you end up diagnosing and correcting that?  Seeing as both my computers live in drastically different networking environments (at work everything statically assigned and actually running as a network bridge to my QEMU windows install and at home it's just plain old DHCP) I don't see how they could have that kind of issue in common, but I'm not going to rule it out!  This whole logging out three or four times a day business is driving me nuts!

---

### Post by dahewpro on 2008-02-22
I've been experiencing the same problems, without warning the applications I have open stop working, and all other applications stop opening past the "starting 'program'" message on the panel. I think it involves processes opening and closing, because I get a message when I try to start firefox that says a process is currently running and not responding, try end the process or restarting the computer.

---

