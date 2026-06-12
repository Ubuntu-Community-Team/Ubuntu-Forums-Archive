---
title: "DPKG doesn't work"
date: 2010-09-22
forum: General Help
---

### Post by Mentlegen on 2010-09-22
I have troubles wits Software Center and Synaptic Package manager.  They don't work. Terminal says : dpkg: failed to open package info file `/var/lib/dpkg/updates/0000' for reading: Input/output error

---

### Post by SaintDanBert on 2010-09-22
Both **dpkg** and **synaptic** require administrator privileges to accomplish their work. We usually use **sudo** to launch dpkg.
Synaptic will prompt for a password.

First, try to run this:
```

$ dpkg --list

```

You should get output like: (sorry it is wide text output)
```

Desired=Unknown/Install/Remove/Purge/Hold | Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                                                Description
+++-==========================================-======================================================================-==========================================================
ii  2vcard                                     0.5-3                                                                  perl script to convert an addressbook to VCARD file format

ii  acl                                        2.2.47-2                                                               Access control list utilities

ii  acpi-support                               0.121                                                                  scripts for handling many ACPI events

ii  acpid                                      1.0.6-9ubuntu4.9.04.3                                                  Utilities for using ACPI power management

ii  adduser                                    3.110ubuntu5                                                           add and remove users and groups

ii  alacarte                                   0.11.10-0ubuntu1                                                       easy GNOME menu editing tool

... and so on

```

If you get this output, then dpkg works.

Next, try to repeat your dpkg command as follows:
```

$ sudo  dpkg  {my options}


```

Does it work now?

Good luck,
~~~ 0;-Dan

PS/  One common trouble is the password used with either sudo or with Synaptic.  Use the same password that you typed to login as this user.
The "sudo" idea is (a) authenticate this user as YOU, (b) check if this user is configured into the sudo lists, (c) grant privileges according to how this user is configured. ~~~ 0;-D

---

### Post by andrewthomas on 2010-09-22
post the full output of:
```

sudo apt-get update && sudo apt-get upgrade 
```

within code tags

---

