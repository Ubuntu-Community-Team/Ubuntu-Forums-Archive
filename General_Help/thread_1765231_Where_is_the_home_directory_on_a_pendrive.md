---
title: "Where is the home directory on a pendrive?"
date: 2011-05-22
forum: General Help
---

### Post by cleerline on 2011-05-22
Hi, I am having problems with my live ubuntu usb installation.

I created the usb installation using pendrive.

I now cant boot from the pendrive usb stick.

My last hope is to decrypt the home directory (i selected persistance and encrypted home directory). So I am looking for the wrapped-passphrase file, but I dont know where to look.

So is there anyway I can find where my home dirctory is on the pendrive?

Thanks for any help.

Cleerline

---

### Post by ericzmeh on 2011-05-22
The home directory should be within the root directory.

```

cd /home

```

so on your pendrive it would be 

```

cd /media/yourpendrive/home

```

---

### Post by cleerline on 2011-05-22
well it turns out that on a live usb installtion the filesystem is contained within a file filesystem.squashfs

I have now used unsquashfs to uncompress the file system but when I go to the home directory it is empty.

I am looking for /home/myusername/.ecryptfs/wrapped-passphrase

Amy ideas where this might be?

---

