---
title: "Error trying to install Virtual Box V 3.1.2"
date: 2010-01-05
forum: General Help
---

### Post by ibates on 2010-01-05
Auto upgrade presents a dialogue advising that an upgrade from my installed Virtual Box ver 3.0.1 to ver 3.1.2 is available.

Upon selecting the upgrade, the new version is downloaded, but will not install displaying the following message:

Error: Conflicts with the installed package 'virtualbox-3.0'

Sounds a rather unusual message from a program upgrading itself?

But what is the solution?  And if it necessary to uninstall the older version, how do I go about doing that, And would I lose my current configuration settings and Virtual Machines?

---

### Post by ibates on 2010-01-05
Further to my post above, to be more accurate, the currently installed version of Virtual Box is 3.0.12 r54655.

The new version I am attempting to install is shown in the following link.

[http://download.virtualbox.org/virtualbox/3.1.2/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb](http://download.virtualbox.org/virtualbox/3.1.2/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb)

I am currently running

Ubuntu Release 9.10 (karmic)
Kernel Linux 2.6.31-16-generic-pae
GNOME 2.28.1

---

### Post by howefield on 2010-01-06
I think version 3.1.2 being a major release will mean you need to uninstall your current version before installing your new version.

You can use Synaptic Package Manager to remove it, any VMs you have created will remain untouched and be accessible for your new version.

---

### Post by ibates on 2010-06-21
Problem solved by installing 10.04 LTS.  Staying well clear of VB.

---

