---
title: "Using dual boot C: as Ubuntu Home"
date: 2012-01-24
forum: General Help
---

### Post by wolf99 on 2012-01-24
Hi Folks

Im due (in a fortnight) to reinstall Ubuntu on my Sis lappy as she wants to add vista dual boot.

To make it easier for her to manage her documents Im thinking it would be good if her ubuntu documents, downloads, music, pictures, videos and dropbox dirs were the same ones as those used by C (mapped to them?)
Im pretty noob at Ubuntu other than running the install itself, and usually go by blogged how-to's etc if problems come up.

Is this possible? Would I have to move the whole Home to C: or can the location thet these folders use be easily changed as they can in windows?
Do I need to automatically mount C: in Ubuntu?

Ta for any help, much appreciated! :)

---

### Post by philinux on 2012-01-24
> **wolf99 said:**
> Hi Folks

Im due (in a fortnight) to reinstall Ubuntu on my Sis lappy as she wants to add vista dual boot.

To make it easier for her to manage her documents Im thinking it would be good if her ubuntu documents, downloads, music, pictures, videos and dropbox dirs were the same ones as those used by C (mapped to them?)
Im pretty noob at Ubuntu other than running the install itself, and usually go by blogged how-to's etc if problems come up.

Is this possible? Would I have to move the whole Home to C: or can the location thet these folders use be easily changed as they can in windows?
Do I need to automatically mount C: in Ubuntu?

Ta for any help, much appreciated! :)

Accessing the files from ubuntu is no problem but /home needs linux permissions which ntfs does not have.

---

### Post by raja.genupula on 2012-01-24
I think it will ask you at the time of installation to synchronize with Windows details . I am sure that step after partition selection step but what i am thinking is will at take all those things what you mention .

But Ubuntu one may be help you , on this 
[https://one.ubuntu.com/help/tutorial/install-and-setup-file-sync/](https://one.ubuntu.com/help/tutorial/install-and-setup-file-sync/)

look at there

---

### Post by Mark Phelps on 2012-01-24
I would advise against writing to the Vista "C" partition from Ubuntu -- which is what is going to happen if you try to share folders between Vista and Ubuntu.  

Vista, like Win7, is very finicky about its filesystem being messed with from outside -- which will sometimes corrupt the filesystem, rendering it unbootable.

If you really want to share files and folders, you would do better creating a shared NTFS DATA drive.  That doesn't have to boot and doesn't suffer from the same limitations.

---

### Post by cortman on 2012-01-24
I agree with Mark Phelps. I asked the same question when I was reinstalling Ubuntu on my HD. I created a separate "mystuff" partition on the HD and saved my personal stuff there, and left home on its own partition.
Besides Windows getting finicky with other OS's messing with its partitions, Ubuntu can get rather touchy about Windows messing around with the user settings and profile info saved in /home.

---

### Post by wolf99 on 2012-01-30
Many thanks folks, advice much appreciated.

Like most very casual users, unless the system does it itself, its a nightmare getting my sis to organise her files in anyway but strewn across the desktop or in folders with names like folder1, folder_1 and folder 1. :rolleyes:

---

