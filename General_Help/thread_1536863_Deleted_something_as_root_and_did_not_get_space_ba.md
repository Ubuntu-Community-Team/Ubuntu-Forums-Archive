---
title: "Deleted something as root and did not get space back. Nothing in root trash..."
date: 2010-07-22
forum: General Help
---

### Post by The Flying Penguin on 2010-07-22
So I transfered a few folders with videos in them to the public folder on an Ubuntu 10.04 laptop I have from my Ubuntu 10.04 64bit laptop. When I wanted to delete the folder I didn't have permission so I ran "gksudo nautilus" so I could delete it as root. So I deleted the folder but I did not get the space back!

I went to /.local/Shared/Trash and one of the folders I deleted was there but deleting it didn't get that space back either.

I did some searching but most of what I find doesn't help or tells me to look in the folder /.local/Shared/Trash folder but that didn't help any.

---

### Post by moore.bryan on 2010-07-22
Do you find anything in "gksudo nautilus /root/.Trash"?

---

### Post by drs305 on 2010-07-22
A couple of things about deleting root trash. First, if using a file browser normally you have to use SHIFT-DEL to actually remove the trash from a trash bin. If you just press the DEL key, it deletes the trash and moves it to ... you guessed it ... the trash.

Also, the root trash should be in /root/.local/share/Trash, in two folders called *info* and *trash*. You probably found them, but just in case you didn't.

Also, if the files are in a non-Linux partition, there may be a folder called .Trash-1000 (or whatever your uid is).

---

### Post by The Flying Penguin on 2010-07-22
Doh! Simple error on my part. I was looking under /.local/Share/Trash for the user and not /root/.local/Share/Trash where the files were awaiting removal. I deleted them with SHIFT-DEL and now I have my space back!

Thanks guys! :D

---

