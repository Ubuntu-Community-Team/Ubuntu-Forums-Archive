---
title: "FYI - thinkorswim stock trading client for Linux"
date: 2009-12-03
forum: General Help
---

### Post by celem on 2009-12-03
I just installed the desktop for the thinkorswim.com stock brokerage and I wanted to share a couple of tips.

During install, change the install directory from /opt to /home/yourusername/.thinkorswim

Obviously you must have first created the .thinkorswim folder.

This has two advantages. (1) Not installing into /opt means that gksudo won't be needed in the menu launcher; (2) I backup my /home folder every night (but not /opt) so now my thinkorswim data will also be backed up without a need to alter my backup procedures.

Final notes - (1) the install file is not executable as delivered, so do a chmod 777 on it before you install execution attempt; (2) you'll need to tweak the menu launchers - the install puts it in an odd place - others - I wanted in office.

---

### Post by a2mech on 2010-01-10
Using Ameritrade, the installer downloads as thinkorswim_other_installer.sh which does not open as is.
In terminal I did:
chmod 777 thinkorswim_other_installer.sh
./thinkorswim_other_installer.sh
  Everything appears to be good.

---

### Post by kenp1730 on 2010-01-24
Here is a blog post which shows how to install the TD Ameritrade version of ThinkorSwim without using the terminal at all. 

[http://tradingwithlinux.blogspot.com/]("http://tradingwithlinux.blogspot.com/")

---

