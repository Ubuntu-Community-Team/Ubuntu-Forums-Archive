---
title: "A few Questions about Data Partitions"
date: 2009-08-24
forum: General Help
---

### Post by beastrace91 on 2009-08-24
I have a 190gig data partition on my hard drive and I was wondering a few things. 

First off when it mounted it auto mounted to the point /media/disk - from this point forward will it continue to mount to that same point or do I have to do something special for it to do this?

Second, can I install applications to a data partition instead of /home? My Cedega folder gets rather large when I have all my games in it and I would much prefer them to reside on the larger partition.

Lastly, I have a Desktop, Documents, Videos, Pictures, ect folders on my data partition. How would I go about creating a 'symlink' between these folders and the corresponding folder in my /home directory?

Thanks for taking the time to read this, any help/pointers would be great :)

~Jeff

---

### Post by P4man on 2009-08-24
> irst off when it mounted it auto mounted to the point /media/disk - from this point forward will it continue to mount to that same point or do I have to do something special for it to do this?

It probably will as long as you dont add other drives, but to be sure, you can add a line in /etc/fstab to mount the partition. more info here:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

> Second,  & last 

It sounds like you're better off using that partition as your /home . Before I start telling how, is there a reason you can't do this?

---

### Post by beastrace91 on 2009-08-24
Multiboot system with OpenSUSE and Fedora. Thusly why I also want to symlink the folders so they are shared between the distros.

~Jeff

---

### Post by oldfred on 2009-08-24
If you have it as a permanent mount you can edit the config file.
~/.config/user-dirs.dirs

Which has entries like this and info on how to modify:

XDG_DOCUMENTS_DIR="$HOME/Documents"

---

