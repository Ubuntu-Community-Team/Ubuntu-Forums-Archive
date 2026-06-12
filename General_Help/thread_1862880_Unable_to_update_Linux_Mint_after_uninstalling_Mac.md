---
title: "Unable to update Linux Mint after uninstalling Macbuntu theme"
date: 2011-10-17
forum: General Help
---

### Post by maf939 on 2011-10-17
Hi, I use Linux Mint 10, I recently wanted to try out Macbuntu theme to change my look and feel to Mac OSX, I noticed after installation that I cannot update mint ( the terminal and Synaptic and Update manager all give this error massage:
" [B]E: Type 'pad.net/tualatrix/ppa/ubuntu' is not known 
on line 2 in source list 
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: Unable to lock the list directory" 
[/B]
or this massage:
[B]" E: Type 'pad.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."[/B]

I am not a Linux expert but I understand that software sources is missed up..
I don't want to freshly install Mint 11 now as Linux 12 is coming with a month from now.
Any help would be greatly appreciated

P.S. I learned a lesson, be careful with third party works :(

---

### Post by blueridgedog on 2011-10-17
I am not a mint expert, but I would try moving /etc/apt/sources.list.d/tualatrix-ppa-maverick.list to a backup location (you home directory for example).  It appears there are sources in that file that it can't find.

---

### Post by maf939 on 2011-10-17
> **blueridgedog said:**
> I am not a mint expert, but I would try moving /etc/apt/sources.list.d/tualatrix-ppa-maverick.list to a backup location (you home directory for example).  It appears there are sources in that file that it can't find.
I copied /etc/apt/sources.list.d/tualatrix-ppa-maverick.list to my home folder but the problem still persists..

---

### Post by blueridgedog on 2011-10-17
> **maf939 said:**
> I copied /etc/apt/sources.list.d/tualatrix-ppa-maverick.list to my home folder but the problem still persists..

Not copy, move, so it is no longer being used as a source.  The reason for moving versus deleting is in case you need to recover the file.

---

### Post by maf939 on 2011-10-17
IT WORKED !!!! Thanks a million bro, that saved my day !!:p:p:p This forum rocks !!=D>=D>=D>

---

