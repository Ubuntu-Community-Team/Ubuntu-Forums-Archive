---
title: "Completely Uninstalling &amp; Reinstalling; Changing Partition Size"
date: 2011-11-22
forum: General Help
---

### Post by laurenbanjo on 2011-11-22
Hi!

I've been having some problems with the newest version of Ubuntu after I upgraded to it, and I want to completely remove Ubuntu to do a fresh, clean, install instead of an install over the version that was already there. Hopefully, it will fix my problems.

How do I go about doing this? Will it delete my files? I have them backed up, but I'm just wondering, as of course it's less of a hassle if they don't get deleted.

Also, I dual boot with Windows 7. While I still need it for a few things, after trying Ubuntu for a few months, I realized I mainly want to use Ubuntu. How can I resize my partition to give Ubuntu more space before I reinstall it? I gave it such a small amount in the beginning, but now I want to give it around 80% of the space, as I barely use Windows anymore.

Thank you! :)

P.S. Please give me easy instructions, as I'm a n00b, and I don't want to end up with an unusable computer. :(

---

### Post by audiomick on 2011-11-22
Hallo. I am going to give you some stuff to read about partitioning. Learning never hurts.
General partitioning info, and suggestions for partitioning schemes:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I use the "separate /home" scheme, which allows you to simply re-mount the existing /home partition to a fresh install. This brings us to your question about your file: if you don't have /home separate, your files will be deleted during the fresh install. Not a great problem if you have everything saved off somewhere else, but tedious putting them back.

You may want to consider creating a separate /home partition before you do your new install using this guide
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I have remounted my /home a number of times without trouble. I do have the feeling that it is good to make it new, i.e. copy everything off and start from scratch, every now and then. I think a certain amount of dross tends to accumulate. It is however definitely the easy option for a new install to get back to where you are now with everything fresh.

---

### Post by laurenbanjo on 2011-11-22
Thank you for the quick reply!

I don't have an external hard drive, but I backed everything up onto an online storage site. However, it only lets me upload files up to 100 MB. Thankfully, this isn't the computer that I do video editing and music recording on, so 90% of my files were small enough. I guess the rest I can back up onto a flash drive or SD card for now. Or maybe copy them onto the Windows partition?

Should I resize the partition BEFORE I do a clean install?

---

### Post by audiomick on 2011-11-22
You can copy into the Windows partition, but that will of course increase the amount of data in there, which will mean it will have to stay big enough to accomodate that.

Just a thought: you could also create a further partition with ntfs as the file system to use as a "shared data" partition for files that you might want to access from windows or linux. I think that this would allow you to re-install windows if it should crash and still have the files in there.

To re-size the windows partition, you should firstly delete anything that is not needed any more. Then you should de-frag it using the windows tool for this. Maybe twice, if you have time.
Then you re-size it. Lots of people say it is better to use the windows partitioning tool  for this. I have also used gparted to do this, but I figure the windows tool is the one designed for the job. Whichever tool you use, start windows a couple of times after the operation and let it do any disk checking or whatever that it might want to do.

When this is all done, you can go ahead and re-install. I like to make partitions first and then install to them, but you can also do this during the installation if you chose the "manual" option. I think this is called "something else" these days.

---

### Post by alphaamanitin on 2011-11-22
Last I checked humyo will let you store up to 5 gb, no restriction on file size.

AlphaA

---

