---
title: "broken splash/startup-manager"
date: 2009-09-13
forum: General Help
---

### Post by fritzman on 2009-09-13
Trying to fix a broken boot-splash, I've made it much worse.  I now have two problems.  I'll list them separately;
1.  When I click Start>System>Administration>Startup-Manager, after the password prompt, I get a brief splash "Performing pre-configuration tasks."  It then goes away, and nothing else happens.  I've tried uninstalling it and reinstalling it, but no help.
2.  The problem with startup-manager began when I was trying to fix a broken boot-splash.  I attempted to change the Debian boot-splash to the Ubuntu boot-splash.  Now, when the splash should appear, the screen goes completely black for a second or two, and then reverts to the scrolling boot text.
Sure could use some help with this.
Which should I fix first, and how?

fritzman:confused:

---

### Post by fritzman on 2009-09-14
Well, I managed to fix this problem.  Thankfully, I didn't have to wait for help from this forum.  If anyone is interested in the solution, respond to this post.  Likely, even that won't happen.  But.....

---

### Post by scion xd on 2009-09-14
so which problem did you solv, first one or second one.

---

### Post by sefs on 2009-09-14
It would be helpful to the entire community if you would simply post your solution for others who may have the same problem in the future.

---

### Post by fritzman on 2009-09-15
Interesting that I got no response to the original post, but received two quick respnonses to my sarcasm.....
The truth is I solved the problems not by a surgical repair to whatever faulty file/files involved, rather by my backup-paranoia.  Being a technician, I would much rather have found the specific problem and fixed that.  But, I confess I was too impatient to wait any longer for help, and fixed it by transplant.
I was relatively certain that the problem was somewhere in /etc or /usr.  Somewhere in the Atlantic or the Pacific.
My habit has always been, when installing a new or different distribution, to make frequent backups at various critical points so that if something drastic happens, I can restore to a known good point, and try again.  After installing 9.04, and getting all the updates, but before installing much else, I made a complete copy of the / on a separate partition.
Frustrated that I hadn't gotten a response, I booted to my Fedora 10, mounted the partitions with Ununtu 9.04 and the backup for it.  Then I made a directory called 'save' in the Ubuntu /, copied /etc and /usr to the /save directory, and then copied the /etc and /usr directories from the backup to the Ubuntu.
Although this took me back about an hour in my progress, the problems I had were gone.  Then I continued with my customization of Ubuntu.  This time, I did NOT install any of the optional splash, keeping only the Ubuntu splash.  I made the necessary change to the resolution using Startup Manager, and everything is cool.
I continued on, then, installing all the rest of the stuff I like, and configured Win4LinPro to run on Ubuntu 9.04.
$ uname -a
Linux uglybox 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
$ /usr/bin/lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
I've had problems with the fglrx proprietary driver, frequently having better performance with the generic driver, so I've chosen NOT to use it with Ubuntu 9.04 unless problems arise.

fritzman

---

