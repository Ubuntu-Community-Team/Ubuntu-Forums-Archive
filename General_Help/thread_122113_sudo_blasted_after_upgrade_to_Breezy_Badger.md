---
title: "sudo blasted after upgrade to Breezy Badger"
date: 2006-01-26
forum: General Help
---

### Post by Ingurogl the Black on 2006-01-26
[ [COLOR="Blue"]where are *Frodon*, *BonzoDog* & *Artificial Intelligence*...[/COLOR]]

[Noobs, please read-on for personal knowledge, you encounter
something as bad one day...]

Has anyone experienced difficulties in their Ubuntu system, in particular the su and sudo commands, after [COLOR="Red"]upgrading[/COLOR] to Breezy Badger. A friend of mine has a box that he installed Hoary Hedgehog. He then  upgraded to Breezy, and had been running that for a week. Everything was running fine up until a day ago. The last day he worked on his system, he installed Wine thru Synaptic, and then stopped to do further research. He shutdown cleanly.

The following day, he was able to login as his acct (the one prompted for at installation), but he was **not** able to initiate any GUI function requiring su-priviledges (i.e. Users & Groups, Terminal, et al). Frustrated, he came to me due to experience with debian...

Following several threads ([http://ubuntuforums.org/archive/index.php/t-75144.html](http://ubuntuforums.org/archive/index.php/t-75144.html), [http://ubuntuforums.org/archive/index.php/t-75236.html](http://ubuntuforums.org/archive/index.php/t-75236.html), [http://ubuntuforums.org/archive/index.php/t-75254.html](http://ubuntuforums.org/archive/index.php/t-75254.html), among others), i worked my way into the Failsafe Terminal logged-in as root. From this terminal, i can *su, sudo, passwd, chown, chmod*, et al. Group membership for users is correct. But, when i log out of failsafe mode and go back into gnome, two things happen. First, i get a "GDM" error relating to xterm. Secondly, I STILL CANNOT INVOKE SU-PRIVILEDGED COMMANDS. This i do not understand.

When in the failsafe terminal, i can *su* into root. i can *passwd root*. Yet i cannot initiate sudo from gnome. i have never run into this before, and i have setup/used debian, mandrake, redhat, fedora, knoppix, bsd, with gnome, kde, afterstep, and others.

seems to me that during the upgrade to Breezy, the installer entered Expert mode (as addressed eslewhere), invoking root, and playing havoc with the *sudoers* file. But i don't understand how this could only plague the GUI, not bash. visudo brings up a blank file. syslog has entries for the failed su-requests; error message after su-attempts state that <user> is not found in the sudoers file.

i can get into more technical detail, but left this abbrv so as not to overcome noobs w/syntax and to get my point across quickly...

---

### Post by mrwrath on 2006-01-26
I am the friend...Everything is 100% correct in the above situation.
We have been working on this for 2 days now](*,) ...we need help.
THANKS. :smile: :smile:

---

### Post by Mr Wrath on 2006-02-09
Here is an update for those who have been wandering what happened to the system...We tried every possible way of to solve this sudo problem...We tried to fix the problem for about a week and a half, but to no avail.  With no support from any forums, I made the decision to nuke the problem.  Thank you DBAN. (Darik's Boot and Nuke for those newbies who want to know.)

---

