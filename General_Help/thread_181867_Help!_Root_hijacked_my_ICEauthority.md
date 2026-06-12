---
title: "Help! Root hijacked my ICEauthority"
date: 2006-05-24
forum: General Help
---

### Post by mun on 2006-05-24
I normally log on to a client and ssh to work on a Fedora Core 2 server that serve /home directory through NFS to all my machines.

Recently I replace FC2 with Kubuntu.  Now whenever I tunnelling sudo'ed KDE application through ssh, my .ICEauthority is overwritten by Root's (root:root with permission 600).  This causes KDE to be very unstable and preventing me from logging in to any machines.  This never happened on FC2.  I would appreciate any helps.  Thanks!

---

### Post by mun on 2006-05-24
On hindsight.  On FC2 I have to su root but now on Ubunto I sudo.  Is this the reason? And how can I solve it?

---

### Post by kko1 on 2006-05-25
Hello.

I am not sure I have understood you correctly. Is there a specific reason you want to run KDE applications as a root? If yes, fair enough. ;)

Now as to your problem - I would venture a guess that your problem is caused by "sudo"ing KDE programs. You should use "kdesu" for KDE programs and "sudo" for command line programs.

Please post back and tell us if the problem persists after switching to use "kdesu" to start the programs. (...after deleting the root-owned file, naturally.  :))

HTH,

kko

PS. Could you tell a bit more about your setup, please. I'm curious.

---

### Post by kko1 on 2006-06-07
Any success?

kko :KS

---

