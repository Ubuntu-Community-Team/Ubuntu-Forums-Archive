---
title: "Can't login as normal user after uninstalling a program"
date: 2012-02-10
forum: General Help
---

### Post by nipunreddevil on 2012-02-10
Hi,
I just removed MongoDB server using synaptic as i was installing a newer version from source.But suddenly my system started slowing down.It said that no space left.Before that i had 3-4 GB free.On restart, i could not log on.
So finally i logged in as root.
But how can i recover back my normal account.
I am using Lubuntu 11.10 64 bit.

---

### Post by sudodus on 2012-02-10
If you have no space left, probably your software has filled it with something, and you need to take something away. Either delete files belonging to the new software (MongoDB) or some other files, that may not be necessary.

In an extreme case it can be done with a live system booted from a CD or USB drive, that is not depending of free space on the internal drive.

But maybe you should start searching for some big directories/files. If you have a gnome-based system, use ```
baobab
``` It can be installed by
```
sudo apt-get install gnome-utils
``` and helps finding big chunks of data, that you might be able to delete or move to some external media.

---

