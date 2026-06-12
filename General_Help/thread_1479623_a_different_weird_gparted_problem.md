---
title: "a different weird gparted problem"
date: 2010-05-10
forum: General Help
---

### Post by ronPerloff on 2010-05-10
I have installed Ubuntu 9.10 onto two Dell wintel machines in dual-boot configurations: a tower and a laptop. I have successfully manipulated partitions and made backup images using a combination of gparted and partimage running from many different versions of sysRescueCD, a great tool. I can do the same for my windows partitions running gparted and partimage from Ubuntu installed on my tower. No such luck with the laptop. The symptom is gparted shows the exclamation point icon for the windows partitions. Interestingly enough, I can run gparted successfully from the Ubuntu install CD in live mode. The laptop is an Inspiron 1520.

Has anyone seen this before? Do you have any suggestions to correct it?

Ron

---

### Post by towheedm on 2010-05-10
Have you tried mounting the windows partition first?  You can manually mount the partitions from Nautilus by clicking on the drive icons for the respective partition on the left pane and entering your password when prompted.  Now open GParted and the exclamation icon should be gone for the mounted partitions.

You can also mount the partitions automatically from your /etc/fstab file.

---

### Post by ronPerloff on 2010-05-12
towheedm,

**Thank you** for your prompt reply. I tried what you said and, sure enough, the exclamation point is gone from the mounted ntfs partitions. The problem remains, however, since gparted refuses to manipulate mounted partitions. I tried sneaking up on it by mounting the partitions, launching gparted, and then unmounting the partitions from inside gparted. No luck. As soon as I unmounted a partition, gparted placed the exclamation point icon next to it.

Any other ideas? Again, all of this works without any problems on my Dell tower. It is my Dell Inspiron 1520 that won't behave.

---

### Post by towheedm on 2010-05-12
OK.  I myself never had the need to manipulate any NTFS partitions within Ubuntu apart from simple mounting.  I noticed my system did not allow any resizing operations either.

To allow resizing (and other operations) of NTFS partitions, the [COLOR=Red]ntfsprogs[/COLOR] package must be installed.  It can be installed via Synaptic by entering [COLOR=Red]ntfsprogs[/COLOR] in the search box and clicking on the [COLOR=Red]Apply[/COLOR] button.  Or, install from the command line by entering the following command:
```
sudo apt-get install ntfsprogs
```To check for different file system support in GParted, click on [COLOR=Navy]View => File System Support[/COLOR].  You should see checks marks for all NTFS file system operations after installing the above package.

I learnt something from this.  Thank you.

---

### Post by wilee-nilee on 2010-05-12
Always use a live cd to change any partitions, and you have to turn off swap to do most work.

---

### Post by ronPerloff on 2010-05-13
> **towheedm said:**
> OK.  I myself never had the need to manipulate any NTFS partitions within Ubuntu apart from simple mounting.  I noticed my system did not allow any resizing operations either.

To allow resizing (and other operations) of NTFS partitions, the [COLOR=Red]ntfsprogs[/COLOR] package must be installed.  It can be installed via Synaptic by entering [COLOR=Red]ntfsprogs[/COLOR] in the search box and clicking on the [COLOR=Red]Apply[/COLOR] button.  Or, install from the command line by entering the following command:
```
sudo apt-get install ntfsprogs
```To check for different file system support in GParted, click on [COLOR=Navy]View => File System Support[/COLOR].  You should see checks marks for all NTFS file system operations after installing the above package.

I learnt something from this.  Thank you.


towheedm,

**You nailed it!**

Being the careful sort, I checked my tower system and found that I had installed ntfsprogs on it, though I do not remember why. (I am 68 years old, so that happens a lot!) I installed ntfsprogs on the laptop and it worked as promised.

[B]Thank you.

[/B]> **wilee-nilee said:**
> Always use a live cd to change any partitions, and you have to turn  off swap to do most work. 


wilee-nilee,

You are right, of course. Operating from a live CD creates sort of a *deus ex machina* for dealing with disk issues. Nonetheless, I still do a lot of work in XP and being able to switch over to Ubuntu to take partimage snapshots of my XP system and data partitions is really convenient for me. I can get the whole job done without looking for the CD or  thumb drive. Sometimes I will shrink a partition with partimage before taking the snapshot because partimage does not like to restore to a smaller partition should that need arise. I plan to switch to using   FSArchiver which makes the preshrink unnecessary since it will restore to any partition large enough to accept the contents of the archive. Since   FSArchiverdoes not offer a graphic interface, I will probably end up writing a script to do the deed.

Thank you for your input.

---

### Post by towheedm on 2010-05-13
> **ronPerloff said:**
> towheedm,

**You nailed it!**

Being the careful sort, I checked my tower system and found that I had installed ntfsprogs on it, though I do not remember why. [COLOR=Red](I am 68 years old, so that happens a lot!)[/COLOR] I installed ntfsprogs on the laptop and it worked as promised.

[B]Thank you.
[/B]

:lolflag:  Glad it worked.

---

