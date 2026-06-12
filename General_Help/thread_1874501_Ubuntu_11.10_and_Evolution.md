---
title: "Ubuntu 11.10 and Evolution"
date: 2011-11-03
forum: General Help
---

### Post by chemjeff on 2011-11-03
Hi all,
I just upgraded to Ubuntu 11.10 and now Evolution mail does not work. I try to run Evolution from the menu and I get "Failed to execute child process "evolution" (No such file or directory)". I try "sudo apt-get install evolution" in the terminal and I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
evolution : Depends: evolution-common (= 3.2.0-0ubuntu2) but 2.32.2-0ubuntu7 is to be installed
E: Unable to correct problems, you have held broken packages.


How can I fix this problem? I cannot read my email because of it!

chemjeff

---

### Post by chemjeff on 2011-11-03
Okay, I went on to the chat room and they helped me through a solution.

So I did:

sudo apt-get remove evolution-*

and then:

sudo apt-get install evolution

And now it works.  I had to reconfigure evolution to connect to my email, which was a pain, but I did not lose any email.

Just posting it here in case someone else has the same issue.

---

### Post by Howie Williams on 2011-11-11
Wife has same problem on her laptop. Deleted folder.db file as advised in another post. Open home folder then press ctrl+H to reveal hidden folders so the path is home/.local/share/evolution/mail/local/folders.db Then open terminal sudo apt-get remove evolution reboot then sudo apt-get install evolution.Evolution works fine until next reboot then problem reappears. Other users on the same PC don't have the problem so could it be a problem with her mail provider account, though we all use same provider (virgin media) all be it mine is on a separate laptop?

---

### Post by torsionbar on 2011-11-11
Evolution has its own backup and restore utility.  File -> "Backup Evolution Settings", and "Restore Evolution Settings".  This backs up not only the account settings, but also all your mail, folders, rules, contacts, calendars, everything.

I would be sure to take a backup before upgrading the OS, or even upgrading the version of Evolution.  That way, if things don't go smoothly, you can always do a restore.  I back mine up once each month "just because".

---

