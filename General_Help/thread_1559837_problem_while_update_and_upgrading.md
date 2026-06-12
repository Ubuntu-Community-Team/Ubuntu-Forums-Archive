---
title: "problem while update and upgrading"
date: 2010-08-24
forum: General Help
---

### Post by maizuddin35 on 2010-08-24
Hello. I have this problem occur when I want to update and upgrade the software, both, via terminal and synaptic...

please look at the image

[IMG]http://www.glowfoto.com/static_image/23-232216L/9726/png/08/2010/img5/glowfoto[/IMG][IMG]http://www.glowfoto.com/static_image/23-232216L/9726/png/08/2010/img5/glowfoto[/IMG]

---

### Post by plucky on 2010-08-24
> **maizuddin35 said:**
> Hello. I have this problem occur when I want to update and upgrade the software, both, via terminal and synaptic...

please look at the image

Try putting [noparse][]()[/noparse] codeblocks around the link instead of [noparse][img][/img][/noparse] codeblocks.

Like

[http://www.glowfoto.com/static_image/23-232216L/9726/png/08/2010/img5/glowfoto](http://www.glowfoto.com/static_image/23-232216L/9726/png/08/2010/img5/glowfoto)


Are you close to running out of space on your / partition?

Post output from a terminal of ```
df -h
```

Good Luck

---

### Post by maizuddin35 on 2010-08-24
thanks for the reply plucky, i did not know about that, and now i face this problem, FYI, i installed my ubuntu inside my 250 external hdd.

```
adibmobile@empatbelas:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              79G   44G   31G  59% /
none                  876M  280K  875M   1% /dev
none                  880M  3.6M  876M   1% /dev/shm
none                  880M  192K  879M   1% /var/run
none                  880M     0  880M   0% /var/lock
none                  880M     0  880M   0% /lib/init/rw
/dev/sdb3             151G   67G   84G  45% /media/Elements

```

---

### Post by maizuddin35 on 2010-08-24
here is the output from the terminal when I sudo apt-get update 

```
Fetched 767kB in 42s (18.0kB/s)                                                
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libopal-doc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_lucid_main_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

```

its kinda frustrating when you can update.

---

### Post by richs-lxh on 2010-08-24
First clean the apt cache:
> sudo apt-get clean
or
> sudo aptitude clean

As var has only got 800Mb allocated cleaning /var/cache/apt/archives will at least allow you to use a smaller sized cache.

In failing that, just up the cache size by editing:
> sudo nano /etc/apt/apt.conf.d/20archive

And increasing the MAXSIZE:
> APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";


PS: You used to be able to edit /etc/apt/apt.conf on Debian and add "APT::Cache-Limit", but that doesn't seem to be available on Ubuntu.

Maybe it could be added to: /etc/apt/apt.conf.d/70debconf, but i'm not sure.

---

### Post by maizuddin35 on 2010-08-24
this is when i sudo aptitude clean

same thing happen.

```
adibmobile@empatbelas:~$ sudo aptitude clean
[sudo] password for adibmobile: 
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libopal-doc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_lucid_main_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libopal-doc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_lucid_main_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

```

---

### Post by richs-lxh on 2010-08-25
Yeah, there's the problem. Your apt-cache size is too small:
> E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)Unfortunately, the solution that the (Debian) man pages suggests will only work with Debian, not Ubuntu as there is no /etc/apt.conf file.

You are getting a problem with the "nilarimogard webupd8" PPA, so I would suggest you remove it, and do an "apt-get clean" and see what happens. 
> Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_lucid_main_binary-i386_Packages

I did a Google, and could only find references to apt.conf on older Ubuntu releases, so you can try creating one and see if apt uses it.
> gksudo gedit /etc/apt/apt.conf
Then add:
> APT::Cache-Limit "8388608";

However I would recommend sticking to the new Ubuntu Apt config files and edit /etc/apt/apt.conf.d/20archive and change the 500 to 800
> APT::Archives::MaxSize "500"; 

---

### Post by maizuddin35 on 2010-08-25
thank you for the reply richs-lxh, let me try to solve what you told me to do.

---

### Post by maizuddin35 on 2010-08-25
after removing the "nilarimogard webupd8", and after sudo apt-get clean and sudo aptitude clean here is the output
still the same thing come out..

```
adibmobile@empatbelas:~$ sudo aptitude clean
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libjson-glib-1.0-0 (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libjson-glib-1.0-0 (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

```

I have also increase the cache size 

> APT::Archives::MaxAge "50";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "800";

is there any chance to fix this thing up.? thank you in advanced

---

### Post by maizuddin35 on 2010-08-25
i have tried something from this post [http://search.yahoo.com/search?p=E: Problem with MergeList /var/lib/dpkg/status]("http://search.yahoo.com/search?p=E: Problem with MergeList /var/lib/dpkg/status")

---

