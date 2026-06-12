---
title: "How to remove the separate /home partition?"
date: 2011-05-17
forum: General Help
---

### Post by FancyBoy on 2011-05-17
Hi,

I have ubuntu installed as my main operating system with a separate home partition, I also have windows 7 here, although I haven't used it since I installed it. I was planning on using it a bit more, since I'm getting a bored of ubuntu, so I thought I'd get a little variation :)
Anyway, I have this separate home partition (ext4) formatted, that I logically can't access from windows. So I thought I'd make a "shared" partition (NTFS) with my files on it, so I could access them from both ubuntu and windows. 
Now, can I revert to having my home partition on my Ubuntu partition, or do I have to reinstall or something?

Thanks in advance,
FancyBoy

---

### Post by seawolf167 on 2011-05-17
Windows can only read NTFS & FAT formatted partitions, it will not read your ext4 formatted /home partition. Additionally, your /home partition needs ext4 because NTFS doesn't store things like permissions.

That said, what you are probably looking to do is fire up GParted (System -> Administration -> GParted) and resize your /home partition, making enough free space (whatever you think you need). Once you have space unallocated, boot up in Windows and use the Windows disk utility (right click "my computer" select "manage), and format the unallocated space as NTFS.

If you are at all unsure about what you are doing, backup first (I suggest [Clonezilla]("http://www.clonezilla.org"))

Note that your partition needs to be unmounted in order to resize it - so if you want to resize / for example, you'll need to boot off a LiveCD and use GParted in that enviroment

---

### Post by FancyBoy on 2011-05-17
Yeah, I can do that, but it seems so dumb to have a whole separate partition for config files only...

---

### Post by lithopsian on 2011-05-17
You can mount /home anywhere you want.  To avoid disruption you would want to copy your existing /home files to a new location on your main partition.  Then edit fstab so that /home is not mounted on a separate partition.  If you just move the mount point without copying your files then you won't have a valid set of config files and things will be ugly.  Lots of other stuff like email and browser profiles are also likely to be missing.  You can keep the /home partition (not mounted as /home!) or wipe it once everything works OK.

Shared partitions between Windows and Ubuntu are very useful, even if you don't keep much on them.  One day you'll want to move a whole lot of stuff from one to the other and this is the simplest fastest way.

---

### Post by FancyBoy on 2011-05-17
Ok, so I removed the entry for my home partition from the fstab, I copied all the files to /home folder, can't login, it gives me a bunch of error messages about files he can't find... any way I can fix this without having to reinstall?

---

### Post by hcm_ on 2012-01-14
Did you ever get a resolution to your login problems? 
I plan a similar effort to rid myself of a separate /home. Any suggestions from you would be helpful. I am thinking along the lines of:
 copy /home from separate partition to the root directory 
 change fstab to remove /home mount
 reboot
In my naivete I would like to think this will work. But your login problems alluded to above have me realizing there is probably a lot I do not understand.

---

### Post by SeijiSensei on 2012-01-14
You'll need a place to park the files in /home while you do this.  You'll also need to boot in recovery mode to shuffle things around.

Steps:
1)  Copy (as root with sudo) the contents of /home to another location in the root file system.  I'd use rsync for this task like this:
```
sudo rsync -av /home /usr/local
```
That will make a copy of /home as /usr/local/home.
2)  Remove the /home mount from /etc/fstab.
3)  Reboot using recovery mode and open a root shell when prompted.
4)  You'll see /home still exists, but it now is simply another directory in the root filesystem.  Copy over the saved contents to /home.  Following the example above:
```
cd /usr/local; rsync -av home /
```
5)  Reboot as normal.  Everything should work as advertised.

Remember you need to do everything with root permissions, especially if there's more than one account on this box.

---

### Post by hcm_ on 2012-01-14
Thanks. That worked for me.

---

