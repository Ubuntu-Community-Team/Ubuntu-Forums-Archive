---
title: "E: Problem parsing dependency Recommends"
date: 2011-02-10
forum: General Help
---

### Post by clooless001 on 2011-02-10
I was installing sun java with:
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```And my power went off (Talk about bad timing)

Now whenever I open synaptic manager or try to install anything through terminal I get:
```
E: Problem parsing dependency Recommends
E: Error occurred while processing collectd (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

---

### Post by clooless001 on 2011-02-10
Oh, and if I try to do

```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```I get 

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

EDIT: I realised i did that while having synaptic open (Silly me!)
The message i get back with synaptic closed it:

```
Reading package lists... Error!
E: Problem parsing dependency Recommends
E: Error occurred while processing collectd (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by clooless001 on 2011-02-10
I just tried opening  
[FONT=monospace]/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages

[/FONT]And it can't figure out the coding....

Could not open the file /var/lib/apt/lists/gb.ar&#8230;erse_binary-i386_Packages using the Western (ISO-8859-15) character encoding.

---

### Post by clooless001 on 2011-02-10
I fixed it!

```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages 
```

Hope i can help others with this!

---

