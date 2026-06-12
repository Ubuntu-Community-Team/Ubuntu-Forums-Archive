---
title: "RAR Archiver/Unpacker"
date: 2010-02-04
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-02-04
Hi, i'm looking for a rar unpacker and archiver. I've used unrar, but everytime i try to extract contents from an archive using 'unrar -x <archive> i get:
   
Extracting <File_Name> Failed     
X Failed

or for 'unrar x <archive>'

Skipping <File_Name>        
All OK

The archives unpack ok under windows so its not a problem with the archives. i can't see why it wouldn't work..

Does anyone know of a good unpacker/archiver?

---

### Post by Leppie on 2010-02-04
have you tried to let package-manager handle the archives? just open them (doubel click) in your file manager (nautilus for ubuntu, konquerer for kubuntu, thunar for xubuntu, etc.)

---

### Post by NiGhtMarEs0nWax on 2010-02-04
yeh its doesn't unpack rar files unfortunately. seems to work with everything else, just not rar archives.

---

### Post by Enigmapond on 2010-02-04
if you install the unrar non-free package, I believe this will help. Also 7zip will unpack it.

---

### Post by ajgreeny on 2010-02-04
> **NiGhtMarEs0nWax said:**
> yeh its doesn't unpack rar files unfortunately. seems to work with everything else, just not rar archives.
It certainly does!  I have used it many times for exactly that.

---

### Post by sisco311 on 2010-02-04
> **ajgreeny said:**
> It certainly does!  I have used it many times for exactly that.

The free version of unrar can't handle the RAR 3.0 format. 

@OP try to install [unrar-nonfree]("apt://unrar-nonfree").

---

### Post by NiGhtMarEs0nWax on 2010-02-04
> **sisco311 said:**
> 
@OP try to install [unrar-nonfree]("apt://unrar-nonfree").

Works! must have been in 3.0. Thanks!


'sudo apt-get install unrar' for anyone who is interested.

---

### Post by Leppie on 2010-02-04
> **NiGhtMarEs0nWax said:**
> Works! must have been in 3.0. Thanks!


'sudo apt-get install unrar' for anyone who is interested.
had you not already installed that package?

---

### Post by NiGhtMarEs0nWax on 2010-02-05
> **Leppie said:**
> had you not already installed that package?

i had the free version, for some reason once its installed the binary was just called 'unrar,' same as the non-free version. it was on my system at least, which is a bit confusing :P

---

### Post by Leppie on 2010-02-05
> **NiGhtMarEs0nWax said:**
> i had the free version, for some reason once its installed the binary was just called 'unrar,' same as the non-free version. it was on my system at least, which is a bit confusing :P
lol, confusing indeed.
i installed the unrar package, but never had this issue... maybe because i always enable the universe repo.

---

### Post by NiGhtMarEs0nWax on 2010-02-05
yeh probably ;)

---

