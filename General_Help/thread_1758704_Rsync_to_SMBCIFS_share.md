---
title: "Rsync to SMB/CIFS share?"
date: 2011-05-14
forum: General Help
---

### Post by Roasted on 2011-05-14
Is it possible to rsync to a samba/CIFS share? If so, how would I do this?

Is there any issues with doing such a thing?

What disadvantages would there be over using NFS instead?

---

### Post by lmarmisa on 2011-05-15
> **Roasted said:**
> Is it possible to rsync to a samba/CIFS share? If so, how would I do this?

Is there any issues with doing such a thing?

What disadvantages would there be over using NFS instead?

I think this is perfectly possible. The only problems would be those related to owners, file attributes (+x) and probably symlinks. They are the same problems of using a NTFS partition, for example.

---

### Post by Roasted on 2011-05-15
So what exactly would I do to rsync to a cifs share? I'm not sure how I'd be able to set the command to do it.

Out of curiosity, are there any rsync gui's that have the ability to handle cifs syncing?

And like I asked before... are there any disadvantages to doing this?

---

### Post by Roasted on 2011-05-15
You mention there might be issues related to owner? What does that mean exactly? Once the files transition over to the NAS box they're under ownership of the same user since that's the user who's logged in. Am I missing something?

Also, is there a "downside" to losing execute rights with the atributes you spoke of? I assume that's what you meant by +x.

Lastly, what are symlinks exactly? My goal here is to have this NAS set up so if a hard drive tanks, I can pull the data back over when I get a new install going. That said, what issues would I run into if a drive failure happened and I pulled the data back over to a new install of Ubuntu?

---

### Post by Morbius1 on 2011-05-15
> So what exactly would I do to rsync to a cifs share? I'm not sure how I'd be able to set the command to do it.I haven't done an rsync in years so I will not be offended if someone else criticizes or corrects my syntax.

Let's take the worst example, that of a home directory to a samba share mounted through "Network" in Nautilus:

```
 sudo rsync -ax --exclude='/.gvfs' /home/morbius/ /home/morbius/.gvfs/"backup on nas"
```[COLOR=Blue]*I'm assuming the share name = "backup" and the server name = nas.*[/COLOR]

You need to exclude ".gvfs" for a number of reasons but in this particular case that's the location of the mount point of the remote share. So unless you exclude it you'll be in an infinite loop.

If you created a classic mount of a samba share then it's the same thing - different mountpoint:
```
sudo rsync -ax --exclude='/.gvfs' /home/morbius/ /mnt/backup
```Either way you have to exclude the ".gvfs" directory.

---

### Post by lmarmisa on 2011-05-16
Samba/CIFS does not match very well the requirements of the native Linux/GNU file systems like ex4, ext3, etc. So, the remote synchronization of files/folders to a samba NAS is not perfect. The problems arise with the preservation of modification times, permissions (for example executable files),  owners and groups of the different files to synchronize.

NFS is more appropriate for rsync because it supports permissions and owners/groups and matches all the basic requirements of the Linux/GNU file systems. NFS  has some limitations related to encryption and security and it is normally used only in trusted networks. 

This is an example of how to mount a remote CIFS directory using samba (install the package smbfs if necessary):

```

sudo mount -t cifs //192.168.2.73/BACKUPS /mnt -o username=luis,file_mode=0777,dir_mode=0777

```This command is an example of rsync:
```

rsync -r -n -v --progress -s /home/luis/Desktop /mnt/backup01

```If you wish a GUI for rsync, I recommend to install Grsync:

```

sudo apt-get install grsync

```

---

### Post by Roasted on 2011-05-16
Yeah, I hear ya there. I've done a lot of homework recently on NFS and CIFS. NFS, while simpler in design, has literally no security. I mean, I just can't imagine using NFS in a production environment. CIFS at least has the security barrier there. I would only consider using NFS in a production environment if they bumped up security to at least require user authentication. Until then, CIFS is the way I'll go.

I've also done a ton of speed comparisons with CIFS and NFS. There is literally no difference in speed. I've taken even the largest of files and pushed/pulled them through both protocols to/from my file server, and in each instance they end the transfer within seconds of each other, which over a 20 minute transfer is remarkable that they can be so close.

That said, it is a little bit of a bummer that Linux file systems don't play too nice with CIFS and vice versa. I can only hope something like BTRFS in the future has better support for this. Nonetheless, I will continue to use CIFS as I find it to be better suited for me.

I'll look into grsync though. I have used it many years ago, but I'll try it now. Again, I just want a reliable way to back up files. If the owner/group doesn't transfer, I really don't see how it matters.

Think about it like this. Let's say your name is Bob, and you log into my FreeNAS file server as Bob. When you transfer files to it, those files take on the ownership of Bob since that's the user you're logged in as. So the files on the file server are thereby owned by... Bob.

On the flip side, let's say your hard drive dies. Ah, crap! Pull data from the NAS. So you log in as Bob and copy the files over. As the data gets written to your newly installed hard drive on your computer, you are writing the data as the owner logged in. Who's logged in? You are. So you thereby own the files you are writing to the local disk of your system.

Sure, maybe not EVERYTHING gets saved. But the critical stuff is there.

---

### Post by lmarmisa on 2011-05-16
If you have decided to use CIFS (I agree with you), maybe **rsync** is not the best solution for your backups.

Consider to use a fine classic tool of the UNIX world: **tar**. **tar** will preserve all the attributes of files and folders. 

This link could help you:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Finally, if you wish to make some complete backups of your system, I recommend Clonezilla Live. It works great with CIFS:

[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

---

### Post by Roasted on 2011-05-16
I love Clonezilla. I use it extensively. But the idea here isn't necessarily to have backups. I have a lot of raided setups so losing data isn't the concern.

Here's my story. My desktop is a gaming rig, dual monitors, blah blah blah. I'm trying to be more green since, well, I'm too poor to afford these energy bills, so I set up a spare box that, according to my wattage meter, is CONSIDERABLY more energy efficient than my desktop. That said, I find myself living off of my CR-48 laptop now, which has a 16gb hard drive.

So... I'm trying to utilize my FreeNAS box (running a ZFS Raid1 array) as my means of being able to access my data. That way I can just connect to it and work from it and even though I have a 16gb hard drive, I realistically have 500gb of space at my disposal.

The catch is this. My desktop will be powered off almost all of the time, but I would like to have some sort of syncing between my desktop and the SAN. That way if I make new changes on the SAN, it'll sync to my desktop. Then if I make changes to my desktop, it'll sync to the SAN so I can access it from my laptop, etc.

So I'm trying to find a logical way of making both locations (desktop and SAN) having the same data. Rsync was the best way I knew of. That said, .tar'ing everything might not be totally optimal. I'm just looking for the data in its raw format.

Do you have any other suggestions? I REALLY appreciate your help so far.

---

### Post by lmarmisa on 2011-05-16
This is an example about how to make a backup of the home folder using tar. The destination will be the CIFS directory mounted in /mnt:

```

cd
tar cvpzf /mnt/backuphome01.tgz .

```

---

### Post by Roasted on 2011-05-16
I fired up grsync. Solid looking application. I mounted my CIFS share from my NAS and opened up grsync. I was disappointed to see I was not able to select the CIFS location as a destination.

Then I remembered someone reminding me that CIFS mounted to .gvfs. A quick CTLR + H to show hidden files and bam. I was in business.

I tested out grsync and it worked beautifully with CIFS. I got some errors when I checked "preserve permissions" but like I said, the NAS takes care of assigning permissions once it lands on that box, so I'm good.

Thank you so much!

EDIT - Now... I wonder if I could set this up on a schedule...

EDIT II - Hey, here's a question. Let's say I was synchronizing my home directory to the samba share. So it would look something like:

rsync /home/jason to /home/jason/.gvfs/network_storage/jason

network_storage being my NAS server.

Since .gvfs sits within the home directory, wouldn't I infinitely loop the rsync cycle? I'm trying to figure out how within grsync I could exclude .gvfs but I'm not sure how.

---

### Post by Roasted on 2011-05-16
All right... so I'm getting warmer to where I want to be.

It seems for this to work, I need to exclude .gvfs. Well, in the GUI, that's kind of hard to do. However it seems most applications support some sort of exclude option. Grsync for example supports "Do not leave file system" which takes out things like .gvfs, etc. So that's good. I believe LuckyBackup had this as well.

I do however have some questions and concerns.

LuckyBackup has a two-way rsync option. That looks nice. However, LuckyBackup won't let me select .gvfs when I run it as super user. Uh. Why can't I?

Grsync does EXACTLY what I need it to. The problem is, I can't find a way to schedule it. Also, is there a way to make Grsync do a two-way backup so both destination/source match each other?

---

### Post by lmarmisa on 2011-05-16
> **Roasted said:**
> All right... so I'm getting warmer to where I want to be.

It seems for this to work, I need to exclude .gvfs. Well, in the GUI, that's kind of hard to do. However it seems most applications support some sort of exclude option. Grsync for example supports "Do not leave file system" which takes out things like .gvfs, etc. So that's good. I believe LuckyBackup had this as well.

I do however have some questions and concerns.

LuckyBackup has a two-way rsync option. That looks nice. However, LuckyBackup won't let me select .gvfs when I run it as super user. Uh. Why can't I?

Grsync does EXACTLY what I need it to. The problem is, I can't find a way to schedule it. Also, is there a way to make Grsync do a two-way backup so both destination/source match each other?

Why do you want to use .gvfs?. 

I recommend to select the directory /mnt or any other created under /media and type a specific command sudo mount similar to this:

```

sudo mount -t cifs //192.168.2.73/BACKUPS /mnt -o username=luis,file_mode=0777,dir_mode=0777

```

---

### Post by Roasted on 2011-05-16
Well, that's what Ubuntu uses by default when you browse for network shares. Plus, if you do a smb://NAS it comes up as .gvfs.

So I'd like to use .gvfs if at all possible since that's kind of the default method.

Is there any fluent easy-to-use ways of doing this? I'd like to find a GUI for it if at all possible since I'm going to try and explain this to relatives over the phones.

---

