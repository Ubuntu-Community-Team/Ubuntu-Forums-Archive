---
title: "Does anyone here put /home in its own partition?"
date: 2012-05-27
forum: General Help
---

### Post by listerdl on 2012-05-27
And - is that difficult/ worthwhile to do?

---

### Post by malspa on 2012-05-27
I do, most of the time, not all the time. Not difficult. Opinions vary as to if it's worthwhile.

---

### Post by wilee-nilee on 2012-05-27
Some do some don't, I save all my clones and homes to a external though. I find it easier to do fresh installs, and I have a ton of external space. I also fill up the HD with lots of OS's as well so just my method is all.

Having a separate home is generally used for upgrades and keeping whats there.

---

### Post by drs305 on 2012-05-27
I've done it about every way possible - originally didn't, then did, then did only just before doing an online update and then moving it back. :-)  The one thing I've never done is keep my documents there.

Now I keep it with the main OS but use symlinks for a few of the folders which have configurations I really want to keep (xchat, unison, etc).

As was mentioned, each way has advantages/disadvantages.

If you want to move /home, here are 2 guides. The first mentions ext3 but it's a bit old and I'd recommend ext4.

[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by listerdl on 2012-05-27
i guess i have no need to do /home on separate partition - I was just interested to hear if someone comes out with a really good "valid" reason to...

thanks

---

### Post by derklempner on 2012-05-28
I keep **/home** on a separate partition because if I ever feel the need to reinstall the OS then I know all my configs and saved files will be safely stored on a partition that won't be formatted and erased.

If you ever feel the need to reinstall the OS, then when you do so, all you have to do is format the root partition and assign your old **/home** partition as your new **/home** partition.  This way, if you keep configs and files in **/home**, you won't have to worry about losing data or having to reconfigure all your programs after reinstalling them.

---

### Post by sgage on 2012-05-28
I suppose having a separate /home makes sense if you are staying with one distro "brand". But, like others here, I like to experiment with all sorts of distros/UI's, and a lot of the configuration files/entries are different, so I like them each to have their own /home. I back up everything to an external HD pretty much every day - it's very easy with deja-dup or grsync.

I do both a deja-dup and grsync backup. I will be installing the new release of Fedora 17 tomorrow, and after a deja-dup restore, I'll be all set up, config and all - I'll just need to install a few packages, but they'll be all set up the way I like. (I do the grsync backup so I can pick and choose individual files and such from another distro if I have to/want to.)

Sometimes I think one of the most useful hardware purchases I've ever made was my 1 TB external HD. Being able to back everything up easily and multiply has saved my bacon on a number of occasions.

If I was just sticking with Ubuntu, I might make a separate /home. But then there's always that nagging feeling that you might be wasting some disk space in / ... :lolflag:

---

### Post by codemaniac on 2012-05-28
I have never created a separate /home partition ever .
Still living happily with most of the distributions . :^)

---

### Post by zombifier25 on 2012-05-28
> **derklempner said:**
> I keep **/home** on a separate partition because if I ever feel the need to reinstall the OS then I know all my configs and saved files will be safely stored on a partition that won't be formatted and erased.

If you ever feel the need to reinstall the OS, then when you do so, all you have to do is format the root partition and assign your old **/home** partition as your new **/home** partition.  This way, if you keep configs and files in **/home**, you won't have to worry about losing data or having to reconfigure all your programs after reinstalling them.

This.

---

### Post by matt_symes on 2012-05-28
Hi
 
I have a seperate data partition and i use symlinks for all the folders in my home directory. It makes reinstalling a breeze but i do not have a sperate home partition. 
 
Kind regards

---

### Post by dcstar on 2012-05-28
> **derklempner said:**
> I keep **/home** on a separate partition because if I ever feel the need to reinstall the OS then I know all my configs and saved files will be safely stored on a partition that won't be formatted and erased.

If you ever feel the need to reinstall the OS, then when you do so, all you have to do is format the root partition and assign your old **/home** partition as your new **/home** partition.  This way, if you keep configs and files in **/home**, you won't have to worry about losing data or having to reconfigure all your programs after reinstalling them.

+1 to all of that, and if you are stupid enough to fill your /home then your Linux system won't crash because the root partition will not be affected.

Separate partitions also insulate your system from corruption in the case of a power failure while a filesystem update is in progress. Having only one partition means it will get hit 100% of the time in that situation, having two filesystems (with similar write frequencies) means that only one will be at risk.

IMHO anyone not using a separate /home are being a fool to themselves and a burden to others (as many posts in this forum prove).

---

### Post by sgage on 2012-05-28
> **dcstar said:**
> 
IMHO anyone not using a separate /home are being a fool to themselves and a burden to others (as many posts in this forum prove).

I think you are way overstating the case. In 15 years of using Linux, I have never had an issue related to not having a separate /home partition. 

I also feel that this "burden to others"  thing is a bit moralistic.

---

### Post by hawthornso23 on 2012-05-28
Programs which put their config files directly in your home directory really **** me off.  It means there is no sane way to switch between sets of config files if you are running multple distros with the same home. If all config files were stored even one layer deeper - say in ~/.config/ - then you could symlink it.  

Just because it has been that way since forever doesn't excuse the terrible design.

---

### Post by wilee-nilee on 2012-05-28
> **dcstar said:**
> +1 to all of that, and if you are stupid enough to fill your /home then your Linux system won't crash because the root partition will not be affected.

Separate partitions also insulate your system from corruption in the case of a power failure while a filesystem update is in progress. Having only one partition means it will get hit 100% of the time in that situation, having two filesystems (with similar write frequencies) means that only one will be at risk.

IMHO anyone not using a separate /home are being a fool to themselves and a burden to others (as many posts in this forum prove).

My method is better than yours na, na, na, na, na, na. :)

---

### Post by drs305 on 2012-05-28
I hope the OP has received enough opinions. If not, there are lots of other threads dealing with the topic.

In order to preserve the harmony of these forums:

Thread Closed.

---

