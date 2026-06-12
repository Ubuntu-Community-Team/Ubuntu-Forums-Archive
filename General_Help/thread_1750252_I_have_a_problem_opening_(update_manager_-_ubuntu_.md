---
title: "I have a problem opening (update manager - ubuntu softw...)"
date: 2011-05-05
forum: General Help
---

### Post by ramy_ahm on 2011-05-05
Hello ,

The following applications are not working anymore on my ubuntu:

[COLOR=Blue]1- Update manager [COLOR=Black].. it gives the following msg :[/COLOR][/COLOR]

<< Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'>>

[COLOR=Blue]2- Ubuntu software center[/COLOR] .. it opens window but there are no applications 

[COLOR=Blue]3- Synaptic package manager[/COLOR] .. it gives me this msg :

<<E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.>>

- I use Ubuntu unity 11.04 & i just installed it 4 days ago ..
- Everything else is working well .. only these applications don't work ..

so please i really need any help .. and thx a lot 4 reading my post ^^

---

### Post by vagrale13 on 2011-05-05
Run the following two commands in terminal
```
sudo find /var/lib/apt/lists/ -type f -delete
sudo apt-get update
```and see then if is ok!

---

### Post by ramy_ahm on 2011-05-07
Hello ,

Thanks a lot my brothers .. i did what you said & everything is working good now ^^

many thanks again my bro :-)

---

