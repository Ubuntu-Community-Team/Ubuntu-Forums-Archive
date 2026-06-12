---
title: "update manager problem"
date: 2009-08-22
forum: General Help
---

### Post by lightnin on 2009-08-22
[I]Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'[/I]

any ideas ?

same error in package manager


TIA

Rich

---

### Post by lightnin on 2009-08-23
bump :)

---

### Post by michy99 on 2009-08-23
Try this:```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by lightnin on 2009-08-25
no luck with that one :(

thanks you anyway :)

anyone else ?

can I delete the old file and let it rebuild a new one ?

---

### Post by lightnin on 2009-08-26
bump :)

---

### Post by lightnin on 2009-08-28
:-(  anyone ?

---

### Post by HiImTye on 2009-08-28
try changing the servers that Ubuntu is updating off of

[LIST=1]
[*]administration > preferences > Software Sources
[*]under 'Ubuntu Software' click the drop down for 'Download From' and choose a different server
[/LIST]
hopefully that will help :)

---

### Post by lightnin on 2009-09-08
nope - that didn't work.

I think the problem is a file on my drive.

I now want to load some more hardware, so I will give it a bit more attention :-)

this is the message today

[I]'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/deb.playonlinux.com_dists_jaunty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
[/I]

so I am guessing if I get rid of 'play on linux' then things will improve ???

but how ??? !

Rich

---

### Post by lightnin on 2009-09-08
*This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.*

---

### Post by lightnin on 2009-09-08
*Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs*

---

### Post by lightnin on 2009-09-08
I think it's solved ...

I looked in sources.list and un-checked the playonlinux deb 

update manager is now running :-)

I'll let you all know in a bit if it completes ok

Rich

---

### Post by lightnin on 2009-09-08
success :-)

---

