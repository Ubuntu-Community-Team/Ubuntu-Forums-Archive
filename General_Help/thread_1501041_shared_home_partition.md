---
title: "shared /home partition?"
date: 2010-06-03
forum: General Help
---

### Post by notesetter on 2010-06-03
I've had many problems since upgrading from 9.10 to 10.04 and I'm going to do a reinstall. Some of my problems are described [here]("http://ubuntuforums.org/showthread.php?t=1493215"). But I'm also going to install Xubuntu on a separate partition and see if it's xfce is more stable for my computer.

I'd like to share a /home partition between the two root partitions and want to know if this is a good idea or if it will probably lead to problems.

Has anyone tried this approach? Would you recommend it (or against it)? What are the pros and cons?

Thanks in advance,

David

---

### Post by BoneKracker on 2010-06-03
It will work, but I recommend against it.  There are configuration files in your home directory, and you might have conflicts.  If you ultimately eliminate one of the systems, you'll have extraneous files in your home directory.

Better to create a "data" or "docs" partition that you mount to a /data or /docs mountpoint within each of two distinct home directories.

---

### Post by dcstar on 2010-06-03
> **notesetter said:**
> I've had many problems since upgrading from 9.10 to 10.04 and I'm going to do a reinstall. Some of my problems are described [here]("http://ubuntuforums.org/showthread.php?t=1493215"). But I'm also going to install Xubuntu on a separate partition and see if it's xfce is more stable for my computer.

I'd like to share a /home partition between the two root partitions and want to know if this is a good idea or if it will probably lead to problems.

Has anyone tried this approach? Would you recommend it (or against it)? What are the pros and cons?

Thanks in advance,

David

The main issue of sharing /home between distros/versions is that some settings may become incompatible.

As an example, my backup 9.04 system does not like my /home after my 10.04 system has been using it because the Gnome version is different and some app settings that are valid in 10.04 cause 9.04 versions of the same app to barf.

For most things it is fine **if** the differences between booted systems are not that great, but there inevitably will be some anomalies.

---

### Post by mrinehart93 on 2010-06-03
The only thing I could thing of would be files conflicting with each other... you know, the stuff in the ".texthere" directories in the home folder. This may or may not be what you want, but this is what I do in order to share data between different OS' (in my case Windows and Linux):

1. Create a NTFS partition (for you, make an ext3 or ext4 partition)
2. Put all of your documents, pictures, movies, etc. in that partition, but make sure to retain the names that Ubuntu gives them. So keep the movies folder labeled as "Movies", etc.
3. Remove the folders that are NOT hidden in your current home folder, ie. Movies, Pictures, etc.
4. Create a shortcut from the new partition you made earlier from each folder into your OLD home folder.
5. Repeat step 4 for Xubuntu.

Basically by doing this, Ubuntu and Xubuntu will treat those shortcuts as if they were the original named home folders (at least in my case). Now you can access the folders in the shared partition you made through your original home folder, as well as copy and paste stuff into them. With this kind of setup, you retain your home folder for that distro, but you still get to share the files.

---

### Post by srs5694 on 2010-06-03
Note first some terminology about which I want to be crystal clear: The /home partition is a partition that's mounted at /home. The /home directory is the directory identified as "/home"; it's located in the /home partition when you use a separate /home partition, but the /home directory can be an ordinary directory if there's no separate /home partition. Note the leading slash on both these terms. A user's home directory, by contrast, is a subdirectory of /home (or conceivably some other location, although that would be unusual) that's used by a single user. This is distinct from the /home partition or the /home directory. Note that I don't use a leading slash when referring to a user's home directory.

It's possible to share a /home partition between multiple installations. If the distributions are similar enough, you can share your home directory (/home/notesetter or whatever it is) without problems; but if the distributions are different, it's safer to create separate home directories for each installation. You can do this either by using different usernames on each installation (say, notesetter910 and notesetter1004) or by using the same username but specifying a different home directory in /etc/passwd (or by using a GUI tool to change your home directory) in at least one installation. In some cases, you've got to be careful with your user ID (UID) numbers in both installations to be sure they match. With a single user on both Ubuntu and Xubuntu, though, the UID numbers should match by default.

I don't know offhand if the mainstream Ubuntu and Xubuntu are similar enough to successfully share a user home directory. Probably they are, but I can't be positive of that. If in doubt, use different usernames, or at least different user home directories, on your two installations.

---

### Post by lapcat66 on 2010-06-03
In my experience, sharing a home folder between different partitions/ distros is a bad idea.  I had endless mysterious glitches as config files for programs were re-written by other versions of the same programs.

A better approach is to let your main partition use the separate home folder.  Let the additional partitions use their root as their home folder.  You can still access the 'separate home' folder where your data lives; it's just not your home folder.

---

### Post by notesetter on 2010-06-03
Thanks, everyone for the quick replies and for sharing your experiences.

BoneCracker, and mrinehart93, I use a separate data partition which is mounted as /home/data in my ubuntu installation. in /home/data, I create a directory for each user (I have two sons who are growing up on GNU/Linux) to keep their files in, and subdirectories for Music, Documents, etc. and link to them from each user's home directory in a way very similar to that described by mrinehart93. That way when it's time to upgrade, everyone's files are in a neat, tidy place and I can back up the whole partition before proceeding and restore it later if necessary. That eliminates the need to search for everyone's important files and back them up individually.

srs5694, that sounds like a good idea...something I may try down the road. I think everyone has raised enough doubt that I'll shy away from a /home partition shared between 2 or more distributions. My purpose in trying Xubuntu on this aging machine is to try and isolate/eliminate the problems I'm having with Ubuntu 10.04 LTS so that I can get back to being productive. I don't want to do anything that may cause glitches.

Thanks again,

David

---

### Post by BoneKracker on 2010-06-03
> **notesetter said:**
> Thanks, everyone for the quick replies and for sharing your experiences.

BoneCracker, and mrinehart93, I use a separate data partition which is mounted as /home/data in my ubuntu installation. in /home/data, I create a directory for each user (I have two sons who are growing up on GNU/Linux) to keep their files in, and subdirectories for Music, Documents, etc. and link to them from each user's home directory in a way very similar to that described by mrinehart93.
That's a good strategy.

Xfce4 is a good environment.  You might also like to try e17, which, I was surprised to find, is about as resource-friendly as Xfce4.  (And you're kids might like it better, it's got some cool bling, although it seems to be in a constant "alpha" state.)

I also think a good strategy for a home with kids is for Mom & Dad to buy a powerhouse machine for their own use and use, and put LTSP on it to serve virtual desktops to the kids, which can run on old or inexpensive hardware.  This also allows centralized administration, which is important when they're young, and enables a higher level of control if that is desirable.  But don't listen to me, I'm just an Uncle, not a Dad. :p

---

### Post by sgosnell on 2010-06-03
Like srs5694 said, there is a large difference between a partition mounted as /home and home folders for users.  You can easily use the same /home partition for different distros, as long as you use different usernames on them.  You can use john and john1, for example, and that will give you different home folders in the /home partition, and things won't be mixed up.

---

### Post by sandy8925 on 2010-06-09
I had this idea that I could share a /home partition between different distros (like ubuntu,opensuse,fedora or some other distros). from what i've read above this doesn't seem like a good idea. still i'd like to try it. is this likely to work?

---

### Post by BoneKracker on 2010-06-09
> **sandy8925 said:**
> I had this idea that I could share a /home partition between different distros (like ubuntu,opensuse,fedora or some other distros). from what i've read above this doesn't seem like a good idea. still i'd like to try it. is this likely to work?

Bad idea.

However, you could create a "data" partition to hold your personal files (documents, etc., as opposed to configuration files), and then mount that to a /data directory inside the home folder of each distro.

---

