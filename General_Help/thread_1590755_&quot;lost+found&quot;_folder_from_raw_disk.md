---
title: "&quot;lost+found&quot; folder from raw disk?"
date: 2010-10-08
forum: General Help
---

### Post by BrutalSpoon on 2010-10-08
Hi everyone.

So, I'm setting up my new server, and I've got a bunch of raw disks. Raw as in straight from the manufacturer so completely blank (as opposed to secure erased or something similar).

The thing is, whenever I create a device table and format to ext3, it generates a lost+found folder which takes up significant amounts of space.

For example, before building my server I created a virtual machine to test out a few different settings before working with large amounts of data. I accomplished this by creating 4 15GB virtual hard drives from scratch. Each had a lost+found folder in the root of the drive which was about 500MB. When I created a software RAID with these drives there was a lost+found folder which used up around 2GB of space. Furthermore, I'm unable to access this folder at all without chown-ing it.

These drives were created from nothing, so there's no way that there'd be any sort of recoverable data within them. What's the deal with that?

EDIT: I just finished partitioning a 2TB drive as ext3 and it's generated a 29.42GB lost+found folder.

Sorry if somebody's brought this up before, but I searched the forums and couldn't find anything on it.

Thanks in advance for any advice (as always),
BrutalSpoon

---

### Post by yetiman64 on 2010-10-08
What I think you're seeing is the OS reserving a percentage of the drive to allow for managing the filesystem. 

I think the figure is about 5% of the drive, though I'm not entirely sure of the actual figure used. 

Your figures sound pretty right as you've put them in the above post.

Re. your edit, even that sounds OK on the percentage of the size of the drive.

---

### Post by BrutalSpoon on 2010-10-08
> **yetiman64 said:**
> What I think you're seeing is the OS reserving a percentage of the drive to allow for managing the filesystem. 

I think the figure is about 5% of the drive, though I'm not entirely sure of the actual figure used. 

Your figures sound pretty right as you've put them in the above post.

Re. your edit, even that sounds OK on the percentage of the size of the drive.

So why is it in a folder called "lost+found", not "filesystem management" or a completely hidden folder? I thought the lost+found folder was for recovering files when you format a drive with data on it (or something).

I'm assuming that it'd be a bad idea to delete the lost+found folder, then?

---

### Post by yetiman64 on 2010-10-08
> **BrutalSpoon said:**
> So why is it in a folder called "lost+found", not "filesystem management" or a completely hidden folder? I thought the lost+found folder was for recovering files when you format a drive with data on it (or something).

**I'm assuming that it'd be a bad idea to delete the lost+found folder, then?**

lost+founds permissions usually bar me seeing the size of the folder as such and I thought you may have meant the drive size reserved amount. In fact how did you determine the size of the lost+found folder re the permissions are 700 and no one but root should even see the full properties etc?

**YES very bad idea its for the OS**.

---

### Post by BrutalSpoon on 2010-10-08
> **yetiman64 said:**
> lost+founds permissions usually bar me seeing the size of the folder as such and I thought you may have meant the drive size reserved amount. In fact how did you determine the size of the lost+found folder re the permissions are 700 and no one but root should even see the full properties etc?

**YES very bad idea its for the OS**.

I can see the size of the lost+found system on the new drives by seeing how much space is already used in GParted (which I have open to format the drives anyway).

In the case of the virtual hard drives in the VM I was able to see how big the lost+found folder was just by right clicking on it.

On an older machine a while back I added an extra hard drive which I formatted. After formatting it I saw the lost+found folder, which I chown'd and deleted. I didn't notice any ill effects afterwards.

---

### Post by yetiman64 on 2010-10-08
> **BrutalSpoon said:**
> [COLOR=Red]I can see the size of the lost+found system on the new drives by seeing how much space is already used in GParted [/COLOR](which I have open to format the drives anyway).

In the case of the virtual hard drives in the VM I was able to see how big the lost+found folder was just by right clicking on it.

On an older machine a while back I added an extra hard drive which I formatted. After formatting it I saw the lost+found folder, which I chown'd and deleted. I didn't notice any ill effects afterwards.


[COLOR=Red]Red[/COLOR]-GParted will be reporting the size allocated to the filesystem (every file in your system has to be referenced to a table of contents etc- the filesystem takes up space etc) as well.

AFAIK when a filesystem check is performed and data recovered the lost+found folder comes into play, though not sure if removing it will hurt too much, but note I've had files "disappear" on a drive with wrong permissions on lost+found. These files only "reappeared" when the permissions were corrected. Removing the lost+found folder may possibly have some repercussions with regard to your datas integrity/safety.

I'd advise it be left for the system.

---

### Post by BrutalSpoon on 2010-10-08
Thanks a lot for your advice! I'll leave the folder as is and won't touch it.

---

