---
title: "virus's and firewall."
date: 2009-08-30
forum: General Help
---

### Post by baconbuttyman on 2009-08-30
alls well with my os, just turning my attention to internet security, what the standard proceedure, what is the best firewall and antivirus for ubuntu.
thanx

---

### Post by credobyte on 2009-08-30
There's no need for an anti-virus ( [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) ). Regarding firewalls .. ufw ( an easy way to configure iptables ).

---

### Post by sasho_zl on 2009-08-30
Read the sticky threads in the security discussions.

---

### Post by t0p on 2009-08-30
As you will hear from many people, there is no need to use antivirus software with Linux.  This is because there are no/very few viruses that can affect a Linux system.  So, no AV needed.  Period.

If you dual-boot with a Windows OS, you might want to run software to check any Windows software you've downloaded.  Just so you don't pass on a Windows virus to any Windows-using friends.  If this is the case, try **ClamAV**.  It's in the repos.

---

### Post by jerrrys on 2009-08-30
[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=1002167](http://ubuntuforums.org/showthread.php?t=1002167)

[http://ubuntuforums.org/showthread.php?t=1071799](http://ubuntuforums.org/showthread.php?t=1071799)

---

### Post by PFN on 2009-08-30
I prefer firestarter for the firewall becuse it is easy to configure and customize.Also it is rich in features.You can install it through Synaptic or apt-get.

For virus detection there is clamav if you prefer a lighter client. It is a command line application. If you need a GUI you have to install clamtk also.

You can also try avast for linux. Download a .deb installation file from this site([ http://www.avast.com/eng/download-avast-for-linux-edition.html]("http://www.avast.com/eng/download-avast-for-linux-edition.html")) and install it with GDebi Package Installer. You have to register and need to get a free license key for one year.

---

