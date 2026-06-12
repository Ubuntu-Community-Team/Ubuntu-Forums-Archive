---
title: "error starting synaptic"
date: 2011-06-13
forum: General Help
---

### Post by Wizb on 2011-06-13
I'm runing UBUNTU 11.04 and new to UBUNTU and LINUX. Everything was working fine for me, but somehow Synaptic Pakage Manager and Software Center are now messed up.

When I try to open Synaptic I get this error message:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/downloadue.info_repo_dists_natty_all_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry http://extras.ubuntu.com/ubuntu/ natty/main amd64 Packages (/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages)
```I can open the Software Center but it hangs when I click on any of the options or try to do a search.

Does anyone know what I need to do to fix this?

---

### Post by drs305 on 2011-06-13
You most likely have a corrupted *lists* file. If you delete it, all the list files will be created when you run an update.

Open a terminal. You will be running these commands as root, which means you can do damage if you don't type them correctly. Either copy the commands or verify they are correct before you press ENTER:

```

sudo rm -vf /var/lib/apt/lists/*  # Removes the lists
sudo apt-get clean # Removes downloaded packages (not needed after they are installed)
sudo apt-get update  # Fetch the latest package lists.

```

The 'duplicate lists' error may or may not be fixed by the above. If it reappears, it means you have the 'extras' repository listed twice in your /etc/apt/sources.list or a file in /etc/apt/sources.list.d folder.

---

### Post by Wizb on 2011-06-13
Thanks for the quick reply. When i entered these commands I got the following error:

```
W: GPG error: http://downloadue.info natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/natty/Release  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```I also still have original problem trying to open Synaptic.

---

### Post by Wizb on 2011-06-13
> **drs305 said:**
> ... The 'duplicate lists' error may or may not be fixed by the above. If it reappears, it means you have the 'extras' repository listed twice in your /etc/apt/sources.list or a file in /etc/apt/sources.list.d folder.

There are quite a few files in /etc/apt/source.list.d folder. Should I delete them?
How do I find and fix a duplicate in /ect/apt/source.list? When I double click on that file it opens Software Sources utility. Everything is listed twice, with the second entry having "(source)" at the end.

---

### Post by Wizb on 2011-06-13
OK, I opened the " /etc/apt/sources.list" file with text editor and did not see any duplicate entries.
I also deleted Extras.list and extras.list.back from the /ect/apt/source.list.d folder. When I try to open Synaptic I get this error message:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/downloadue.info_repo_dists_natty_all_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```So at least the duplicate part of the error is gone.

---

### Post by Wizb on 2011-06-13
I think I Figured it out. I unchecked [http://downloadue.info/repo](http://downloadue.info/repo) in Software Sources and everything is working now.

---

