---
title: "Duplicate source entries in Karmic"
date: 2010-03-23
forum: General Help
---

### Post by afrodeity on 2010-03-23
I used to be able to resolve this problem by simply opening my sources.list file and doing a search and delete, but now Ubuntu appears to have two completely different methods of handling sources. What is is the simple solution? I would really like to have everything all in one place.

```

W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_sunab_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by patchwork on 2010-03-23
Go to System > Administration > Software Sources

Click on the 'Other Software' Tab and check for duplicates.

EDIT: As far as I know, the only file being read is still the /etc/apt/sources.list, this just gives a GUI interface to the file.  Any changes won't become permanent until the sources are updated using the apt-get update command

---

### Post by afrodeity on 2010-03-24
Gosh, I guess it must be the number of ppas I've got hooked and me wishing there was a single sources.list. Because opening this at first didn't help

So I went through my sources.list and #commented everything. Then when I opened the admin panel I could see which ppas were in my sources.list and which ones were add-apted. 

I am now busy commenting them and wish I had done this sooner, because I don't always know which bits are associated with which ppas, but I am sure Synaptic will try to tell me. :)

---

