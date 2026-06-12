---
title: "kdm dying at boot - no graphical login"
date: 2011-11-19
forum: General Help
---

### Post by Guy_H on 2011-11-19
Strange problem, system boots normally, I get the splash screen with the 'dots' but then nothing.

I can Ctrl-F1 to a terminal, login and startx& and everything is fine.

Looking in syslog, the only things that do not look right are

```
Nov 19 10:57:58 AMARI-UBUNTU kernel: [   17.878884] init: apport post-stop process (951) terminated with status 1
Nov 19 10:57:58 AMARI-UBUNTU kernel: [   17.923107] init: kdm main process (912) killed by TERM signal
Nov 19 10:57:58 AMARI-UBUNTU kernel: [   17.938369] init: gdm main process (950) killed by TERM signal

```

kdm.log is empty
nothing weird in Xorg.0.log


I don't know enough about the boot process to delve much deeper :(

Any ideas or pointers please .....

---

### Post by Guy_H on 2011-11-22
anyone?

If someone could please just point me in the right direction it would be appreciated - I have spent hours on this uninstalling and reinstalling and purging various packages without success.

Problem is, some packages in Kubuntu do not work properly when X is started this way (Muon for instance)

I could really do with getting my graphical login back ....

---

### Post by Cotopaxi on 2012-02-04
Same problem here.

I can login as superuser,
but my two sons can't login as client users into their accounts.

Can anyone help please?

---

