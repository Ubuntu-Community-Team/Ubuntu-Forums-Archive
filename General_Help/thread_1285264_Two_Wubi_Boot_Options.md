---
title: "Two Wubi Boot Options"
date: 2009-10-07
forum: General Help
---

### Post by Sup3rkirby on 2009-10-07
And now to clarify in order to dispell confusion. There shouldn't be 2 Wubi boot options for me. My real question is how to remove them.

I first installed Wubi on Vista. Later, I upgraded to Windows7 for a short time, and then reinstalled Vista. Well, even though I did a completely fresh install, the Ubuntu data was still saved(somewhat) it seems, and so I have always had the option to boot in to Ubuntu, even though it was installed through Wubi and my Hard Drive was reformated(or at least should have been since I installed an OS fresh).

But it seems problems started to arise and now that partition of Ubuntu won't boot. It doesn't show in the installed programs, so I can't simply uninstall, and the folder doesn't exist anymore. I used EasyBCD and reset my Vista bootloader, but the option remained.  I even installed Wubi again on this laptop and now I have 2 options for Ubuntu, and only one boots of course.

I was really curious as to a way to remove these options. I mean, if a fresh OS install didn't do it as well as reinstalling the Vista bootloader, then I'm clueless.


[EDIT]
Before I forget, I've checked the partitions in Vista, and there aren't any extras for Ubuntu to delete(which would make sense as I used Wubi). So yes, I'm at a hault on this one. No partition to remove, reinstalling the bootloader didn't change anything, nor did resinstalling Vista as a clean install.

---

### Post by Sup3rkirby on 2009-10-10
Uhh, bump?

I uninstalled Wubi, and the 'Ubuntu' option is still listed when I start up the laptop. I messed around with UNetBootin, and at one point had Sabayon listed when I started my laptop up(although this didn't boot), but the Ubuntu option still remained, and even now, after removing and uninstalling every possible linux boot related program and file I have access to...


Is there no real way to clean the bootloader, particularly of certain options that shouldn't exist or don't work?

---

### Post by wilee-nilee on 2009-10-10
I did a wubi install in XP and then removed it and had the same problem in XP you can run msconfig and edit the bootloader, in vista I have no idea where this is. I also just had XP look for wubi in all the files and removed all links, the bootloader edit is what fixed the problem though. I have reinstalled xp via a disc telling it to reformat the partition and install off the disc only to find it just ignored the commands and installed what it felt like. This link gives somewhat of a description of the history of the bootloader in vista it might be helpful.
[http://www.microsoft.com/whdc/driver/tips/Debug_Vista.mspx](http://www.microsoft.com/whdc/driver/tips/Debug_Vista.mspx)

---

### Post by Sup3rkirby on 2009-10-10
Thank you very much.

I found EasyBCD is a nice GUI application that can allow you to edit a lot of the bootloader data, and using this I was able to manually remove Ubuntu from the list so it no longer appeared at startup.

It turns out Vista doesn't use the same set up as XP for the bootloader, but the concepet is the same; the bootloader was holding bad data, and repairing or reinstalling the bootloader only affects the Microsoft OS. So yes, either manually edit the boot file, or use EasyBCD if you are not as comfortable with such things.

---

