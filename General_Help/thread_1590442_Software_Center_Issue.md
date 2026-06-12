---
title: "Software Center Issue"
date: 2010-10-07
forum: General Help
---

### Post by beastrace91 on 2010-10-07
When I try to install an application using the software center it simply does nothing when I click install. The following is the output in terminal when I click install - ```
jeff@sager-ubuntu:~$ software-center
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()
WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.103'}) is not authorized: org.debian.apt.install-packages
** Message: console message: undefined @1: ReferenceError: Can't find variable: showProgress

```

What is wrong? Fully up to date 10.04 32bit install.

~Jeff

---

### Post by markh789 on 2010-10-08
Open Synaptic Package Manager.

Type into the search box "software-center"

Should be the top one, already installed. Check it for re-installation. 

Now, re-install it - dose it work now?

---

### Post by ProntoAnthony on 2010-10-19
Interesting. I'm getting similar results. See my post at [http://ubuntuforums.org/showthread.php?t=1317639&highlight=Raleigh&page=2](http://ubuntuforums.org/showthread.php?t=1317639&highlight=Raleigh&page=2)

---

### Post by Cowboybebop79 on 2010-10-19
Ok found two bug reports in launch pad that refer to basically the same problem 
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/537592]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/537592")
and
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/614949]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/614949")

Don't see any resolution for either bug yet but I would keep an eye on them to see if something comes up.

---

