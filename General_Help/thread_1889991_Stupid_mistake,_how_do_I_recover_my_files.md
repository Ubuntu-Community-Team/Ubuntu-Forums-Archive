---
title: "Stupid mistake, how do I recover my files?"
date: 2011-12-02
forum: General Help
---

### Post by dgc.ie on 2011-12-02
Dont ask me how I messed up so bad, I have no idea what I was thinking.

Ubuntu was installed via the wubi installer in windows a few months back.

Then today like a dope, I wiped the windows partition and installed a new clean install.

As you can guess, Ubuntu isnt working anymore and there are some very important files on it.

Using the new windows install I can see the Linux partition and I can see how much space its using and what not. But I cant seem to access the file system. The few folders that are there dont really lead to anything.

Is there any way I can either get Ubuntu working again, or retrieve the files from it via the new windows OS.

Any help would be very very much appreciated. I am in a world of pain if I cant get these files back.

---

### Post by bcbc on 2011-12-02
Use this: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (look for the download page link and avoid the advertising banner - can be misleading).

Then run it and point it at the \ubuntu\disks\root.disk (or home.disk if you have a separate one).

It's also possible to loop mount the virtual disks from an Ubuntu live CD/USB. If you have the virtual disks it's possible to recover the ubuntu install, but first make sure you can get your data.

---

### Post by dgc.ie on 2011-12-02
Hi bcbc

Thanks for the recommendation. That program works great. Its a lil bit buggy (crashes every time I try to move multiple files) but its getting the job done. I only have a few more files left to get so it should be all done soon enough. Once again, many thanks for your advice :)

Harry

---

