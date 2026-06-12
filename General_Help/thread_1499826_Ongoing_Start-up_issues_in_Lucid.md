---
title: "Ongoing Start-up issues in Lucid"
date: 2010-06-02
forum: General Help
---

### Post by Warthaug on 2010-06-02
I have been having trouble with lucid since install with certain startup programs not starting during boot.  At first I thought this was only occurring after updates, but it now appears to be happening totally at random.

I've only noticed three programs/services doing this.  They are:

1) Boinc client.  Sometimes it doesn't start at boot.  To make it work I must run the command "sudo /etc/init.d/boinc-client start"

2) CUPS.  If Boinc doesn't load, neither does CUPS.  To make it work I must run the command "sudo service cups start"

Moreover, once the above things stop running, they won't run (even after a reboot) unless I run the above commands first.  Then I'll get a few boots in before I have to re-run the above commands.

3) I am also having trouble with virtual box, although I don't know if there is a temporal connection to the above, as I use vbox somewhat irregularity.  I'll try to start a virtual machine and get an error that the kernel needs to be recompiled.  Recompiling the kernel fixes things temporarily...

Any ideas on what is going wrong, and how to fix it?

thanx

Bryan

PS: I'm running 64 bit 10.04, on a dell XPS M1330 laptop.  Intel chipset, 2 gig ram.

---

### Post by Warthaug on 2010-06-11
bump - anyone, please

---

