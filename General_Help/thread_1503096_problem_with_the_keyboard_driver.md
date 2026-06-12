---
title: "problem with the keyboard driver"
date: 2010-06-06
forum: General Help
---

### Post by ailatzis on 2010-06-06
i am trying to put the new ubuntu 10.04 in a vm. 
The installation completes with no problem , i am using the 64bit version,
but i can't login the keyboard doesn't respond
i am using microsoft wireless desktop elite keyboard.
thanks

---

### Post by an0dos on 2010-06-06
What type of VM is it? Are you using virtualbox? VMware?

---

### Post by ailatzis on 2010-06-06
it's vmware 7.0.1 build-227600

---

### Post by an0dos on 2010-06-06
> **ailatzis said:**
> it's vmware 7.0.1 build-227600

Does your problem seem to be related to this?

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891)

Check out the following blog post:

[http://www.solo-technology.com/blog/2010/05/01/ubuntu-10-0-4-vmware-and-no-keyboard/](http://www.solo-technology.com/blog/2010/05/01/ubuntu-10-0-4-vmware-and-no-keyboard/)

The blog post seems to indicate that you can activate the onscreen keyboard and use it to log in. Once in, your keyboard will work like normal.

---

### Post by pancakelizard on 2010-06-10
> **an0dos said:**
> The blog post seems to indicate that you can activate the onscreen keyboard and use it to log in. Once in, your keyboard will work like normal.

I'm having the same issue but what I would like to know is how to get this from not occuring anymore. From the blog link, there is another link ( [http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/) ) that states:
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

