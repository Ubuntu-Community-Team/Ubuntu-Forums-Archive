---
title: "Can I share /home after install?"
date: 2012-04-29
forum: General Help
---

### Post by tadpole1954 on 2012-04-29
I've been using Precise since beta 2.  I intend to use it as my main os.  My hd is set up with Mint 12 (sda1), swap, home and another partition I use for distro hopping.  I installed Precise onto the latter (sda7), but I like it so much I'd like to keep it.

Can I share the /home partition with Mint?  When I installed Precise I didn't choose a home partition.

I've been mounting the home partition when I need something there, but it would save me some steps if I could do this.

---

### Post by uylug on 2012-04-29
> **tadpole1954 said:**
> I've been using Precise since beta 2.  I intend to use it as my main os.  My hd is set up with Mint 12 (sda1), swap, home and another partition I use for distro hopping.  I installed Precise onto the latter (sda7), but I like it so much I'd like to keep it.

Can I share the /home partition with Mint?  When I installed Precise I didn't choose a home partition.

I've been mounting the home partition when I need something there, but it would save me some steps if I could do this.

Seriously, why would you want that?

You could always mount any partition you'd like, and access your files as if they were on your home folder.

Sharing home folders between two different operating systems could be a pain, specially if the same username is used on both.

---

### Post by tadpole1954 on 2012-04-29
I didn't realize it was a bad idea.  Like I said, I've been mounting the home partition and using it.  I thought by sharing it may reduce the number of mouse clicks somewhat.  I will take your advice tho and leave this alone.  I don't need any extra problems.  My user name and passwords are identical for both.  Thanks for replying.

---

### Post by oldfred on 2012-04-29
The user settings in /home are tiny. Most of it is your data, some is your data in hidden files & folders like Firefox profile or Thunderbird profile. Everything that is data not user settings can be in a separate data partition which since it is only data you can mount in many installs. 

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

