---
title: "Deleting remastersys folder"
date: 2010-09-20
forum: General Help
---

### Post by RogerD on 2010-09-20
Hi

After an unsuccessful experiment with remastersys - I got the message: The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again - I've ended up with a 23.9GB folder cluttering up my home folder. I can't cut and send this to my wastebasket as when I look under 'Permissions' I'm told 'You are not the owner, so you can't change these permissions'. Funny, I thought I was the superuser and could do anything.

Any ideas for how to get rid if the remastersys folder?


Roger D

---

### Post by k33bz on 2010-09-20
```
sudo chown -R RogerD.RogerD path/to/remastersys
``` Then delete however you see fit

---

### Post by RogerD on 2010-09-20
Thanks

I'm not a strong command line user, but I understand you saying I need to use chown to gain ownership of this folder. My username on my system is 'roger' and the offending folder is in /home. Would:

chown roger /home/remastersys

Work?

---

### Post by robert shearer on 2010-09-20
> I've ended up with a 23.9GB folder cluttering up my home folder

Gaaack !.   Remastersys is an app to backup your current **configuration** to a live cd/dvd.
Looks like you tried to backup **everything**.... **23.9GB !!!** LoL!!

Once you have deleted that folder move your **data** (vids, pix, etc,etc to an external drive or another partition and remove/unmount them.

Then rerun the remastersys backup.

it has a 4GB (compressed)file limit and this is more than ample for the backup of your configured/personalised **operating-system** to a live medium.

This allows you to re-install your preferred configuration quickly and easily then add your data from the backed up data source.

it is not meant as a data backup method.
From the remastersys home page.

> # the compressed filesystem will need to be 4GB or less.  No buts about it, unless of course, you're a genius with ample time on your hands.  That also means backup mode will need to include your /home folder in that 4 GB iso.
# Run aptitude clean to get rid of unnecessary .debs.

and
> 
The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes. Mine generally is just a bit over 1 gig.
Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.

Also look for the following folder: /var/cache/apt/archives. That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system. The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason. You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more. 


> 
Any ideas for how to get rid if the remastersys folder?

Run remastersys and choose the 'remove temporary files' option 
this removes the remastersys build folder.
Then close remastersys and you should be good to go.

---

### Post by RogerD on 2010-09-20
OK

Finally got rid of the bugger - upper case R needed in command

That's for your help

---

### Post by k33bz on 2010-09-20
> **RogerD said:**
> Thanks

I'm not a strong command line user, but I understand you saying I need to use chown to gain ownership of this folder. My username on my system is 'roger' and the offending folder is in /home. Would:

chown roger /home/remastersys

Work?

```
chown roger.roger -R /home/remastersys
```


> **RogerD said:**
> OK

Finally got rid of the bugger - upper case R needed in command

That's for your help


No Problem

---

