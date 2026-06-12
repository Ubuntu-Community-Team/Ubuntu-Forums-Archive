---
title: "firefox only opens if using 'sudo'"
date: 2011-03-26
forum: General Help
---

### Post by georgec32 on 2011-03-26
I have a win7 laptop and installed a dual-boot ubuntu 10.10.  I'm using firefox & thunderbird, shared between windows and ubuntu (default profiles are on a fat32 disk that is shared between the two OSs).  I can mount the fat32 disk as usual, but I can't get firefox OR thunderbird to start unless I start them from a terminal using 'sudo'.  This is kinda strange.  I used to do this all the time and never had a problem before.  Anyone know how I can fix this?  

I installed firefox, then did:

cd /etc/firefox
sudo firefox -P

in the profile manager, I set the profile file etc, but when I open firefox without doing 'sudo firefox', it hangs up and cannot find the profile.  Why do I have to use 'sudo' to open firefox or thunderbird?

any help would be appreciated.  This is NOT a mozilla problem.  It works fine on my other laptop, but I've deleted & reinstalled ubuntu 3 times on this laptop and still have the same problem.

Thanks in advance!

george

---

### Post by drs305 on 2011-03-26
Try opening it from a terminal with
```
firefox -profilemanager
```
Create a new profile/location or accept the one it offers to make as Default User. If the profile is in your HOME folder or you point it to a folder you own you shouldn't have to use sudo.

If you want to use the profile on your fat32 partition, you may not be mounting the partitions with the necessary permissions. For non-linux partitions, the permissions are set at the time of mounting. You can add an entry to fstab which makes you the owner of the mounted partition. Here is an example:
> UUID=some.alphanumeric /mountpoint vfat users,uid=1000,gid=1000,umask=027 0 2
Make sure you use the correct UUID and that the designated mountpoint exists.

---

### Post by georgec32 on 2011-03-26
> **drs305 said:**
> Try opening it from a terminal with
```
firefox -profilemanager
```
Create a new profile/location or accept the one it offers to make as Default User. If the profile is in your HOME folder or you point it to a folder you own you shouldn't have to use sudo.

If you want to use the profile on your fat32 partition, you may not be mounting the partitions with the necessary permissions. For non-linux partitions, the permissions are set at the time of mounting. You can add an entry to fstab which makes you the owner of the mounted partition. Here is an example:

Make sure you use the correct UUID and that the designated mountpoint exists.

Thanks for the quick reply :)  I had been doing something similar .. I had put in fstab:

UUID=xxx-yyy /media/WINLIN vfat defaults,uid=george,gid=george,dmask=0027,fmask=0137 0 0

I had used this before and am using it in my other setup (same version of ubuntu, so I'm waaaaay confused!).  I switched it to what you suggested but same result .. can't start firefox without going thru a terminal & using 'sudo'.  The vfat partition mounts on startup just fine with either version of the fstab UUID line (yours or mine).  This is just weird since it worked before getting my hard drive replaced, and it works on my other win7 laptop (different manufacturer).  

After installing firefox, I open a terminal and do the profile manager thing (-P is the same as -profilemanager).  I can find the profile just fine and the program will find it just fine IF I start it in a terminal w/ sudo ..

I tried installing firefox through the 'find new software' utility, tried installing it via synaptics package manager, and tried installing it via apt-get in a terminal .. all 3 ways installed it fine, but had this same problem.  I'm stumped ..

george

---

### Post by drs305 on 2011-03-26
I'm not a firefox expert so hopefully someone will come along who is.

You might provide the terminal messages if you just try opening firefox from a terminal with "firefox".

Have you checked the ownership your ~/.mozilla folder and subfolders to ensure you are the owner? 

Hope you get this resolved quickly.

---

### Post by Connyank on 2011-08-04
I ran into a user with the same problem with Thunderbird.
/.thinderbird files all 777.

This post is marked Solved but I see no solution - is there one?

tnx,
jg

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **Connyank said:**
> I ran into a user with the same problem with Thunderbird.
/.thinderbird files all 777.

This post is marked Solved but I see no solution - is there one?

tnx,
jg
running thunderbird or firefox using sudo is not a very smart thing to do for security reasons
also doing so will screw up the permissions on the profile
to fix 
```
sudo chown $USER:$USER -R ~/.mozilla
sudo chown $USER:$USER -R ~/.thunderbird
```

---

### Post by georgec32 on 2011-08-04
yep.  It's been a while, so I don't remember for sure, but I believe the solution was to set the file permissions via chmod.

george

---

