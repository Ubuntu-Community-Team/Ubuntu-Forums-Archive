---
title: "Internal Error msg in 12.04"
date: 2012-09-06
forum: General Help
---

### Post by freesitebuilder on 2012-09-06
Did a clean install of 12.04 about 10 days ago, and I'm getting frequent "internal error" messages. Sometimes it simply goes away when I choose to send report. Sometimes I don't get the message, it just goes to full-screen "terminal" mode and I have to do a hard reboot.

My machine is quite old, Intel Celeron(R) D CPU 3.33GHz processor, ATI Radeon Xpress 200 graphics card which isn't recognised ("graphics unknown") but works OK otherwise.

Doesn't seem to relate to a particular program - if I choose the "show details" button on the error dialogue, it shows a lib file which relates to the program which has focus at the time of the error.

I'd like to track this problem down if possible, but don't know where to start, apart from looking at the logs which don't mean much to me!

TIA

---

### Post by freesitebuilder on 2012-11-02
I'm getting this message several times a day, along with regular crashes when my system goes to text mode, but with no cursor so I can't interact with it.

Update manager has also stopped working - I get the following message:
==
Please report this bug for the 'update-manager' package and try to
include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing
libtemplateparser4 (NewVersion2), E:Problem with MergeList
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-
security_main_binary-i386_Packages, E:The package lists or status file
could not be parsed or opened.'
==

I've reported the bug, and tried sudo apt-get install -f && sudo apt-get
auto-clear && sudo apt-get update (suggested by a mailing list member) but that gives me the same error message.

---

### Post by ibjsb4 on 2012-11-02
try

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

