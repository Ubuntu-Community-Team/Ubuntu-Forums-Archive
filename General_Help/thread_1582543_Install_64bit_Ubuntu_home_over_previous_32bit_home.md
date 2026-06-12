---
title: "Install 64bit Ubuntu /home over previous 32bit /home?"
date: 2010-09-26
forum: General Help
---

### Post by yoyodyne on 2010-09-26
I was previously running 10.04 32bit. 
Recently upgraded my cpu/ram, so figured I'd try 64 bit.

On my previous setup, I had / in one partition, /home in another, plus a few other partitions (/backup, etc). 

I did the install of 64 bit, but was too scared to point /home in 64bit to the previous /home. After the install, now all those previous partitions/mounts are on /media.

I'd like to just point /home at the previous partition. Should I mess with /etc/fstab to do this or will it cause problems? Is the easiest thing to do reinstall, then point the new install to use the pre-existing /home? Wasn't sure if that would cause problems or not. 

I've backed up most of the previous /home area, so worst case, if it gets blown away, I should be alright.

---

### Post by btindie on 2010-09-26
That shouldn't cause any problems assuming your UID's are the same between installs. You can test it before making it permanent by mounting your existing /home partition over your new home directory then logging in.
 
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)
 
Or, logged in as root from the terminal, rename your home directory on your /home partition to *username_old* then rsync the contents of your new home directory to your /home partition and move your personal files from your old home directory to your new one on your home partition. That way you won't have any stale files left behind from your original install.

---

### Post by yoyodyne on 2010-09-27
btindie,

Thanks. I'm a little more familiar with fstab and mount points, etc, so I might go that route first.

Thanks for the suggestions!

---

