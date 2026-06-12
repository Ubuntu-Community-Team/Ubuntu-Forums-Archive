---
title: "NTFS not a formatting option"
date: 2009-10-22
forum: General Help
---

### Post by watson524 on 2009-10-22
Hi all,

I'm very new at this so I'll likely have a lot of questions but here's my first one.

I have a machine running with a 250gb drive from a windows machine that I put in my Ubuntu machine and want to use as extra storage. I was able to mount it and it mounts on start up each time. I viewed the files, moved what I needed to over to my Windows machine and now I want to format it as NTFS to wipe it clean. I am in gParted and I unmounted it and when I go to format, NTFS is grayed out and not an option. Any ideas why and how I can fix it?

Bear in mind I'm very new so if it's too simple a question, my apologies.

thanks!

---

### Post by Giblet5 on 2009-10-22
I don't really follow what you're saying.

What type of partition does it have right now? FAT32? NTFS?

---

### Post by sisco311 on 2009-10-22
You have to install the *ntfsprogs* package. 

```
sudo apt-get install ntfsprogs
```

---

### Post by watson524 on 2009-10-22
> **sisco311 said:**
> You have to install the *ntfsprogs* package. 

```
sudo apt-get install ntfsprogs
```

Ran that and I now have NTFS as an option in my format menu (thanks!!) but it doesn't seem to do anything. I run it, takes about 3 seconds and still shows all the data and shows 71gb in use (same as before). Does this not work like when I format on a drive on my windows machine?

==================
never mind, i'm a dumbass. that's 71mb in use which is fine.

thanks again!

now i'm off to figure out how to see files on the ubuntu machine on the ntfs drive from a windows machine.

---

### Post by sisco311 on 2009-10-22
> **watson524 said:**
> 
thanks again!


You are welcome!


Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

EDIT: Thanks!

---

