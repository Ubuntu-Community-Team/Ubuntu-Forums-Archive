---
title: "Print No More"
date: 2006-05-21
forum: General Help
---

### Post by GNULinuxGeek on 2006-05-21
Weirdness has happened.  I have 5.10 Kubuntu and it has now stopped printing to my networked Samsung 2251.  Other Kubuntu systems in the house are fine.

As root, I can't even get the print manager to run.

Tried re-installing the entire CUPS system.   Next, tried to just lp a file. No good.

Don't know what to try next.  My guess is that something changed permissions on either the executable, or prnitcap file.

Thinking about a complete re-load, but might wait until Dapper comes out.

Thanks,

Ralph

---

### Post by alarson on 2006-05-21
The same thing happened to me sometime in the last two weeks.  I regularly upgrade when updates are available, then one morning my printer didn't work.  I've tried various forms of re-install to no avail.  Attempting to install the printer via KDE errors out with a "driver not found or permission" error.  I verified my printer is still good by trying it out on a different computer with Dapper, and I tried moving the cable to a different USB port.

As with GNULinuxGeek, I haven't tried very hard to fix it since I'll upgrade when Dapper comes out, but its hard to believe we're the only ones with this problem.

---

### Post by GNULinuxGeek on 2006-05-21
Come to think of it, I have an EPSON R320 hooked up USB and it didn't work either.  I don't print to it much so I thought it might have been nozzle issues.

Wonder if scrapping the printcap fille might do the trick.

I musr say I am a little worried that Dapper might have the same problem.  Really like Kubuntu and would like to keep using it.  I think it needs a tool to clear things and start over.  I find it very odd that when I try to run "printmgr" it acts like it will launch but then does not, and with no error reported such as can't find config file" or "you must be root to run this" etc.

Ralph


[QUOTE=alarson]The same thing happened to me sometime in the last two weeks.  I regularly upgrade when updates are available, then one morning my printer didn't work.  I've tried various forms of re-install to no avail.  Attempting to install the printer via KDE errors out with a "driver not found or permission" error.  I verified my printer is still good by trying it out on a different computer with Dapper, and I tried moving the cable to a different USB port.

As with GNULinuxGeek, I haven't tried very hard to fix it since I'll upgrade when Dapper comes out, but its hard to believe we're the only ones with this problem.[/QUOTE]

---

### Post by jetpeach on 2006-05-23
i am now just getting blank pages on my samsung 2010, not sure where/when things when wrong though.  read someones rant about the cups 1.2 being a bad choice for dapper since it's not that well developed yet...

---

