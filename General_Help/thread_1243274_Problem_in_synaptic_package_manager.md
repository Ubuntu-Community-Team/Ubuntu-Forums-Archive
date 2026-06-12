---
title: "Problem in synaptic package manager"
date: 2009-08-18
forum: General Help
---

### Post by keera on 2009-08-18
i tryed to install some software on my ubuntu 9.04 but i got problem
here is what i got using sudo apt-get install in terminal
```
ke3ra@Ke3rA:~$ sudo apt-get install perl
[sudo] password for ke3ra: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_fta_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```hope someone can help fixing this problem
i can't open the synaptic package manager not even the add/remove

---

### Post by wojox on 2009-08-18
Go to System > Admin > Software Sources
First tab Ubuntu Software look for download from:
Pick a new mirror.

Perl is already installed by default.
Open a Terminal 
```
man perl
```

---

### Post by keera on 2009-08-18
reloading the new mirror i got this message 
```
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
```

and this is what i got when i open synaptic package manager 

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_fta_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

---

### Post by riazrahaman on 2009-08-18
can you try this

reboot your machine and give "sudo apt-get upgrade"

If there are any errors then you would get a command in the same log that would fix the issues like it might say "run dpkg .... to fix the issues"

---

### Post by keera on 2009-08-18
same msg ```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_fta_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

i did reboot my computer , open a terminal enter sudo apt-get update but i get the same msg i showed u

---

### Post by wojox on 2009-08-18
```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

---

### Post by nikhilk on 2009-08-18
Could you post the content of your "/etc/apt/sources.list" file?
```
gksudo gedit /etc/apt/sources.list
```

---

