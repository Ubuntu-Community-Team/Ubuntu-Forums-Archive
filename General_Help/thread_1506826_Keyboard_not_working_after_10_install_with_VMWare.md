---
title: "Keyboard not working after 10 install with VMWare"
date: 2010-06-10
forum: General Help
---

### Post by pancakelizard on 2010-06-10
I'm having the apparently has a work around however the work around doesn't explain how to actually fix the issue, it just assumes you know what to do. 

From the blog link, there is another link ( [http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/) ) that states:
> I found the :0-greeter.log file in /var/log/gdm had errors complaining about not find symbols for “U.S. English” keyboard layout in us keyboard file. A little grepping later finds “U.S. English” is set in /etc/default/console-setup.
<from original file>
XKBMODEL=”SKIP”
XKBLAYOUT=”us”
XKBVARIANT=”U.S. English”
XKBOPTIONS=”"

<changed to this, matching other linux installs>
XKBMODEL=”pc105&#8243;
XKBLAYOUT=”us”
XKBVARIANT=”"
XKBOPTIONS=”"

Reboot and keyboard now works at login.

How do I boot into the shell from the GUI login screen if I can't use the keyboard? Also, the virtual keyboard doesn't always appear for me whenever I boot the OS (vm).

---

### Post by pancakelizard on 2010-06-11
...Anybody?

---

### Post by dcstar on 2010-06-12
> **pancakelizard said:**
> ...Anybody?

As it has been explained in the Virtualization forum (where all VM questions should be), do not install VMware clients using the Easy Install method.

---

