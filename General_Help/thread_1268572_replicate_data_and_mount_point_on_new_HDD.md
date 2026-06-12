---
title: "replicate data and mount point on new HDD?"
date: 2009-09-17
forum: General Help
---

### Post by porchrat on 2009-09-17
Hi all

Bit of a cryptic title, but here is the full story:

I am currently storing some data on a 1TB RAID0 array and while it has served me well 1TB drives are cheaper so I have bought one and want to replace my RAID array with a single 1TB drive.

Problem is that I have all the various applications on my machine pointing to data on that RAID array and redoing all of that would take a lot of time.

Is there a way to just replicate all of that data onto the new drive and make the new drives mount point the same as the old RAID array?

I have all sorts on there (subversion repository, mysql databases etc.) and I really don't want to have to go through all the dumps required to transfer that stuff I would much rather just do some sort of "cp -a" command and be done with it, but I don't know what that will do to the system.

I also don't know how to give it the new mount point. Would I remove the current drive and then modify the fstab?

Note that this RAID array isn't a system drive at all it just contains a whole lot of data. / , /home etc. are on another drive.

---

### Post by CatKiller on 2009-09-17
> **porchrat said:**
> Is there a way to just replicate all of that data onto the new drive and make the new drives mount point the same as the old RAID array?
...
I also don't know how to give it the new mount point. Would I remove the current drive and then modify the fstab?


Pretty much.

Or you could mount the new drive somewhere else, and then when you've copied all the stuff across, unmount the old mount point and symlink the new mount point to the old one.

Or you could do it from a live cd so that you prevent the contents being changed as you're copying them (not so much an issue for straight data, but if you were doing this with a /home partition it could be a problem).

---

### Post by StuartN on 2009-09-17
> **porchrat said:**
> I also don't know how to give it the new mount point. Would I remove the current drive and then modify the fstab?

I replaced my OS drive just recently with Clonezilla. If you have a spare drive connector then insert the new, blank drive and boot from Clonezilla CD or USB (so your primary drive is not mounted) and get Clonezilla to duplicate the primary onto the new drive. Then swap them over and boot up! It did the whole ID, GRUB, fstab thing without intervention.

If you don't have a spare connector then you would need external storage or an external caddy to connect the new drive.

Either way, the old drive is untouched so you have a backup if anything goes wrong.

---

### Post by tgalati4 on 2009-09-17
If your RAID0 is shown as a single device (e.g. /dev/sda), then you can use the cp command.  Plug the second drive in a spare SATA cable (it might be called /dev/sdb)

sudo cp /dev/sda /dev/sdb

Remove the RAID0 drives and try to boot.

sudo fdisk -l

To show how your drives are enumerated.

---

### Post by porchrat on 2009-09-25
Hi all

Haven't been around much lately but just wanted to say thank you for all the replies.

I am going to give this a go today and hopefully get everything up and running by late this afternoon.

I suppose it is probably safe to bring down the MySQL and Subversion servers before I attempt this.

This drive isn't actually a system drive or anything (/ and /home are on the third drive), but it does automount. Is there anything other than the UUID that I would need to alter in fstab to get the new drive mounting properly?

I may just try a "cp -Ra" unless someone can give me a good reason why not.

If I ran CloneZilla would it also preserve the permissions of the various files and directories. That is rather important for the functioning of these servers.

---

### Post by StuartN on 2009-09-25
> **porchrat said:**
> If I ran CloneZilla would it also preserve the permissions of the various files and directories. That is rather important for the functioning of these servers.

It would clone an identical drive, including the UUID (!) so far as I know - my system just GRUBed up straight away without editing menu.lst (unless Clonezilla edited anything) after replacing the drive.

---

### Post by porchrat on 2009-09-27
Well apparently clonezilla doesn't support software RAID so I'm going to have to try something else.

Oh well. Thanks anyway I think I'll just try a giant "cp -aR" unless anyone can provide a reason for why I shouldn't.

Either that or just dump everything and reload it on the other side.

---

### Post by CatKiller on 2009-09-27
When I was doing something similar some time ago, a friend of mine suggested tar was the way to go. In his mind there was some advantage to tar over cp, but I never established exactly what that advantage was. The command he offered was ```
(cd */mnt/source* && tar clf - . ) | (cd */mnt/dest* && tar xvpf - )
```

---

### Post by porchrat on 2009-09-27
> **CatKiller said:**
> When I was doing something similar some time ago, a friend of mine suggested tar was the way to go. In his mind there was some advantage to tar over cp, but I never established exactly what that advantage was. The command he offered was ```
(cd */mnt/source* && tar clf - . ) | (cd */mnt/dest* && tar xvpf - )
```

He probably recommended it because of the very nature of "tar".

tar stands for "tape archive" and was so named becaue it's original purpose was to store files on tapes so  I assume it would probably end up causing the writing of larger blocks then the "cp" command would and because it is generally faster to write fewer larger blocks to a filesystem as opposed to lots of tiny ones it would dramatically speed up the process especially when you're dealing with large amounts of data.

Just a guess though, I'm not that familiar with the tar format but from what I recall it is basically all the files concatenated together with small header regions in between.

However if I'm going to that root I may as well just use mysqldump and svnadmin to dump the files and recreate them on the other side as I trust those systems far more than I do tar or cp.

---

