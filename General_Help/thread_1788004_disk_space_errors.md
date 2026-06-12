---
title: "disk space errors"
date: 2011-06-21
forum: General Help
---

### Post by hirojrocker on 2011-06-21
I'm currently running ubuntu 10.10 64bit
My problem started occurring a couple days ago
When i check my disk space using either disk usage analyzer or Gparted it says I have about 69 gigs left. But say im in a folder on the bottom of the window it will tell me i only have 48 gigs. And just to test I tried going over the amount specified in the folder window and it tells me I have insufficient space. Does anyone know why and a fix for this?

---

### Post by slooksterpsv on 2011-06-22
Could I have you do the following:

Click Applications -> Accessories -> Terminal

Now type in: 

df -h <press enter>

And copy and paste the results here.

Also how big is your HDD?

---

### Post by hirojrocker on 2011-06-22
the spacing on this keeps getting messed up but here it is

Filesystem   Size     Used     Avail    Use%   Mounted on
/dev/sda1               421G   351G       49G       88%      /
none                                    1.5G   276K      1.5G        1%       /dev
none           1.5G   252K      1.5G         1%       /dev/shm
none           1.5G   224K      1.5G         1%       /var/run
none                                    1.5G      0                 1.5G       0%    /var/lock

my total harddrive size is 465 gigs i have two other partitions on my harddrive but that shouldn't affect my Ubuntu partition.

---

### Post by slooksterpsv on 2011-06-22
> **hirojrocker said:**
> the spacing on this keeps getting messed up but here it is

Filesystem   Size     Used     Avail    Use%   Mounted on
/dev/sda1               421G   351G       49G       88%      /
none                                    1.5G   276K      1.5G        1%       /dev
none           1.5G   252K      1.5G         1%       /dev/shm
none           1.5G   224K      1.5G         1%       /var/run
none                                    1.5G      0                 1.5G       0%    /var/lock

my total harddrive size is 465 gigs i have two other partitions on my harddrive but that shouldn't affect my Ubuntu partition.

Ok so df -h is saying you have 49GB left (probably 48.xxxx).

Try this: 
ls -alh | grep .xsession

How large are those files? The reason I ask is cause those files are usually the largest when I find I have disk issues (something with Compiz racking up the .xsession errors file). 

Other than that, you could always run a: 
du -h

And see what the folder sizes add up to be for your home directory (this will go through and show every file and every size, you can also do this:

du -h | sort -h

to have it list everything but sort it by size to find out what's taking up the most space).

Sounds like gparted may be wrong, I'd reboot, could be in your /tmp too

---

### Post by hirojrocker on 2011-06-22
well the du -h | sort -h command showed me something interesting

151G    ./.local/share/Trash/expunged/3060461171

it turns out that is an old set of recup_dir files from a photorec i ran to get back some files for a friend. What does expunged mean and how can i get rid of it, i just try deleting it, then deleting it from the trash but it just popped right back in there.
:popcorn:

---

### Post by slooksterpsv on 2011-06-22
It means to strike out, obliterate, mark, etc. lol

Run this:

rm -R ./.local/share/Trash/expunged

That should delete it, then reboot. That will clear out most if not everything in your Trash bin so hopefully you don't need anything in there.

---

### Post by hirojrocker on 2011-06-24
yep it worked, thanks for your help

---

