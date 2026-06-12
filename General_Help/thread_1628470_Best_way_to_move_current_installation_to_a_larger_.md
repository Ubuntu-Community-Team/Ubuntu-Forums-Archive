---
title: "Best way to move current installation to a larger drive"
date: 2010-11-22
forum: General Help
---

### Post by lukemk1 on 2010-11-22
So the question is very straight forward. I am upgrading to a different drive and I want to keep all my current settings and whatnot from my current drive (/home program & system settings) 

What program would allow me to do this best?

---

### Post by Calcipher on 2010-11-22
Can you have both hard drives plugged in at the same time?

---

### Post by lukemk1 on 2010-11-22
That is a possibility, but if possible I would like to know how to do it with them separated as well as being in at the same time.

---

### Post by Calcipher on 2010-11-22
> **Calcipher said:**
> Can you have both hard drives plugged in at the same time?

Ok, I'm just going to assume you have the ability to have them both plugged in.  If that is the case you have a myriad of options, below are a few of them and Googling will find you more.  

1. Using DD to clone one drive to another (easiest, longest): [http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation](http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation)

2. Using partimage to create a drive image and imaging that to the new drive (medium*, shorter): [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

3. The best way (hardest, medium time needed) would be to partition the new drive with a separate home directory, use dpkg to create a list of installed programs from the old drive, rsync your /home to the new partition, and use dpkg to install the software you were missing in the new install.  I'm not giving detailed instructions on this one because it might be more of an advanced technique.  The plus side is that upgrading at any future point is a snap.

* I say medium because partimage mentions that it doesn't support ext4.  I'm not sure exactly what they mean by 'not support' so you'd have to do some research.

---

### Post by Calcipher on 2010-11-22
> **lukemk1 said:**
> That is a possibility, but if possible I would like to know how to do it with them separated as well as being in at the same time.
How do you plan to move stuff between them if they aren't plugged in at the same time?

---

### Post by lukemk1 on 2010-11-22
I was thinking of like a kind of backup software that would fully back up /home or something. I can have them both in at the same time but I just wanted to know of other ways just for knowledge's sake.

---

### Post by oldfred on 2010-11-22
I have not used these as I just copy data from one drive to another and typically reinstall.

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/]("http://www.geekconnection.org/remastersys/remastersystool.html")

---

### Post by Calcipher on 2010-11-23
> **lukemk1 said:**
> I was thinking of like a kind of backup software that would fully back up /home or something. I can have them both in at the same time but I just wanted to know of other ways just for knowledge's sake.In that case, try rsync.  It makes a complete copy of anything you throw it at to anywhere.  A good front end backup software you might try is [BackInTime]("http://backintime.le-web.org/") (be sure to use their PPA to get the newest version with some bug fixes).  With BiT you could actually backup your entire install and restore it to a new disk (which might be a bit hard), but backing up /home is well within its purview.

---

### Post by Calcipher on 2010-11-23
One more thing.  If this is more of an intellectual pursuit let me point you to two resources that might be of use to you (really, just providing a couple of resources for my option #3).  Please keep in mind that you can screw things up using this method so be very sure you understand what you are doing.
Backing up your software sources: [http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
Making a list of what is installed: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
When restoring stuff, you'd want to restore the software sources first, then load the package list from the second link.  Please keep in mind that you would have to install dselect first.

---

### Post by lukemk1 on 2010-11-23
@Calcipher Thanks for those I will read into them. As for the backing up of the sources & list I have already done those. I've actually made a script for myself that will back it up and then reinstall it all if I so desire. The main reason is I just want to keep all the settings that are stored in /home that way I can migrate to a larger drive soon.

---

