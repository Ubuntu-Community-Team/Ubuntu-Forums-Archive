---
title: "Synaptic package manager error message."
date: 2006-05-07
forum: General Help
---

### Post by morbid_bean on 2006-05-07
When I open up synaptic package manager...i get some error msg


W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)



WTF???

---

### Post by Sutekh on 2006-05-07
Often local mirrors have hiccups.  Try again later, or if you really need a package now, try removing the **us.** part of the repository source and update your sources.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
Then remove the **us.** parts, save the file and update apt-get sources with
```
sudo apt-get update
```

---

### Post by morbid_bean on 2006-05-07
so basicly i just try again later and if it still shows just do the code you posted???

---

### Post by Sutekh on 2006-05-07
Yeah, you can always try now too.  

The first commands (if you are unfamiliar) just copies the repository sources list (of the online caches of Ubuntu sotware), and then edits the file in a text editor.

The second command just updates the list after you make the changes.

---

### Post by morbid_bean on 2006-05-07
sure ill do that right now but what do you mean by removing the us parts?

---

### Post by Sutekh on 2006-05-07
Ok, when you open the file you will have lots of lines that look like this
```
deb http://**us.**archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://**us.**archive.ubuntu.com/ubuntu breezy main restricted
```
and so on.

All you need to do is remove the **us.** bit from the beginning of these lines, so they look like this
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
```
Then save the file and update the list
```
sudo apt-get update
```
If all goes well the update process will complete with no errors of the kind you had before.

---

### Post by morbid_bean on 2006-05-07
Ok i did that and i also dit the update and i noticed a bunch of errors durint the update and now when i open synaptic package manager i get something similar to before but alot more....

W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Sutekh on 2006-05-07
You need to remove the '**.**' as well. So **us.** not just **us**

---

### Post by morbid_bean on 2006-05-07
k im sure i have no us. in my file and i do the update...and then i get   
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4217kB in 7m32s (9329B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binar](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binar) y-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.
  
Then i open up the package manager and i get
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

---

