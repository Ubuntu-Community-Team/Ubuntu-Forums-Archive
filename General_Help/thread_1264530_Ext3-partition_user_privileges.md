---
title: "Ext3-partition user privileges"
date: 2009-09-12
forum: General Help
---

### Post by pveurshout on 2009-09-12
After having huge trouble with NTFS (if interested, see [http://ubuntuforums.org/showthread.php?p=7933951#post7933951](http://ubuntuforums.org/showthread.php?p=7933951#post7933951)) I decided to reformat the partition where I keep my music and downloaded files to ext3, instead of NTFS (I don't really need those in Vista anyway). However, what I liked about using NTFS under Linux was that user privileges didn't work. I once had a great deal of trouble with user creation and user privileges after reinstalling Ubuntu while keeping my separate /home partition, and I don't want to run into that stuff again when I install Karmic in about two months. Is there a way to 'tell' this partition to behave in the same fashion as an NTFS drive, being that it creates all files (regardless of the user who created them) with "chmod 777 privileges" automatically (so without ever having to issue the command manually), and if possible changes the owner of all the files contained in this partition to 'root' as well?

(I'm **not** using this partition as /home (it mounts as /media/Multimedia) and only keep files on it which need absolutely no security or anything)

---

### Post by chriskin on 2009-09-12
you can try the Storage Device Manager application that can be found at add/remove. 

Using it you can change the permissions to whatever you want - at least i use it and i am completely satisfied

---

### Post by pveurshout on 2009-09-20
Sorry for the delayed reply.

First of all: thanks, this is a really useful tool!

Unfortunately, I can't seem to find the option where I can specify the partition to either ignore user rights and automatically make all files accessible to every user ("Others Access: Read and Write"), regardless of the user that created the file (my preferred situation: the way Linux handles NTFS where the owner is always 'root' and there are no restrictions to file access for anyone).

In addition, I noticed there's an option saying you can specify a certain user to 'reserve space' (tab: Miscellaneous, option: User allowed to use reserved space). When torrenting, I'm currently under the assumption that my client (Deluge) creates a sparse file in order to avoid fragmentation. However, as there's nothing specified in the "resuid=" entry I'm starting to wonder whether that actually works?

---

