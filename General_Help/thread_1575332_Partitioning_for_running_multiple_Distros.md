---
title: "Partitioning for running multiple Distros?"
date: 2010-09-15
forum: General Help
---

### Post by Arla on 2010-09-15
I'm interested in testing Maverick, (or the next release, or the one after that) but always run into a problem with testing that runs alone the lines of

I have my current install (10.04) I have two partitions, / and /home, it works well.

As soon as I add a new version it seems to be recommended NOT to have them both point to the same /home partition, the problem is, if I don't do that I don't have all my files, and it's a pain in the rear to setup.

So what I was thinking is to have three basic partitions, 

/
/home (for config files, and true HOME files)
/data (for all my actual data)

Create links from say /home/james/documents to link to /data/documents that way I can get to my documents.

This way if I add a new version I can setup either the same (two partitions, / and /home and point /home/xyz/documents to /data/documents) or keep it slightly simpler for testing, just have one partition and repoint /home/xyz/documents to /data/documents.

Are there issues with doing this? The main one I can think of would be permissions for files/folders?

---

### Post by SavageWolf on 2010-09-15
I have a /home partition which I have switched OS on/with... I can't see anything wrong with it myself...

---

### Post by Arla on 2010-09-15
Having a single home with multiple distros? Or my listed setup?

I know something I am now running into, is having installed 10.10, decided it wasn't complete enough for me to actually run it as my "day to day" OS and backed up to 10.04 every time I start Rhythmbox I get a message about "the database was created using a later version of Rhythmbox and isn't available to use"

Plus I figure I wouldn't end up with a ton of clutter from programs I installed in testing, but never really intended to use?

---

### Post by oldfred on 2010-09-15
I have exactly that setup. I set  permissions in the /data partition, but I run a small script to create mounts, auto edit fstab to include /data and create the links. My /data has all the folders that are data from /home so /home only has hidden folders & files (some misc). With script I can install to my portable & my desktop with only minor changes and reinstall, new installs at will and have all my data locally.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I created script by listing my history from the first time, cleaning up my errors and copying into a bash file.

From my script
sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
cp /etc/fstab /etc/fstab.backup
#Edit fstab first
str1="# Entry for /dev/sdc6 :"
str2="UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  "
fname=/etc/fstab
echo $str1 >> $fname
echo $str2 >> $fname
rm -rf Documents/
rm -rf Downloads/
etc
# All folders to be linked in /home are in /data as folders
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

I used to do this but the above does all 14 folders I currently have. Since I run script in /home the default location for the link is where it is run from, so a second entry is not required unless you want the link in a different place.

#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
etc

---

### Post by WorMzy on 2010-09-15
I keep /home on my / partition and have my data (Documents, Pictures, Downloads, etc) stored on an NTFS partition which I set to be automatically mounted at boot time on all my Linux OS'. The partition is mounted, and then the separate folders (/media/Terastore/Downloads, /media/Terastore/Videos etc) are mount --bind'd to their respective home directories.

All of this is done automatically by fstab.

It works very well. I can log into Ubuntu 9.10/10.04, Arch, Debian 5.04, or Windows and have all my files ready and waiting for me.

---

