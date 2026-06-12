---
title: "ntfs-config problem"
date: 2011-04-09
forum: General Help
---

### Post by athalsten on 2011-04-09
hey i tryed this [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

now i cant reconfigure the drives. the first and 3rd thumbnail appears from that tutorial..

miss the 2nd thumbnail

and cant unmount a any drive 

itryed uninstall the software and reinstall it. nothing happens
every time i boot all drives mounted automaticaly

plz anybody help

---

### Post by TeoBigusGeekus on 2011-04-09
You want them mounted automatically or you don't?

---

### Post by coffeecat on 2011-04-09
All ntfs-config does is to write entries into /etc/fstab - sometimes badly, unfortunately. 

> **athalsten said:**
> 

itryed uninstall the software and reinstall it. nothing happens
every time i boot all drives mounted automaticaly


As TeoBigusGeekus asks, do you want your NTFS partitions mounted or not?

Post the contents of /etc/fstab and the terminal output of:

```
sudo blkid
```

---

### Post by athalsten on 2011-04-09
> **TeoBigusGeekus said:**
> You want them mounted automatically or you don't?

i want to automount but just one partition

---

### Post by athalsten on 2011-04-09
> **coffeecat said:**
> All ntfs-config does is to write entries into /etc/fstab - sometimes badly, unfortunately. 



As TeoBigusGeekus asks, do you want your NTFS partitions mounted or not?

Post the contents of /etc/fstab and the terminal output of:

```
sudo blkid
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb2 :
UUID=4427ebd5-ef54-4c64-8846-dbdb4f147ee1    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda5 :
UUID=8858F8CB58F8B8D0    /media/Download\040&\040software    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda7 :
UUID=68F421C0F42190FC    /media/Movie_1    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda8 :
UUID=662851B3285182CB    /media/Movie_2    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda9 :
UUID=D82852D62852B36C    /media/Other    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=CE5CE3F35CE3D3ED    /media/Songs_Pictures_videos    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
UUID=0C9066D19066C136    /media/Win_XP    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb5 :
UUID=01CBF17B9992D781    /media/extra    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sdb6 :
UUID=58727e1a-e067-4094-aaac-ced102669daa    none    swap    sw    0    0




and 


/dev/sda1: LABEL="Win XP" UUID="0C9066D19066C136" TYPE="ntfs" 
/dev/sda5: LABEL="Download & software" UUID="8858F8CB58F8B8D0" TYPE="ntfs" 
/dev/sda6: LABEL="Songs Pictures videos" UUID="CE5CE3F35CE3D3ED" TYPE="ntfs" 
/dev/sda7: LABEL="Movie 1" UUID="68F421C0F42190FC" TYPE="ntfs" 
/dev/sda8: LABEL="Movie 2" UUID="662851B3285182CB" TYPE="ntfs" 
/dev/sda9: LABEL="Other" UUID="D82852D62852B36C" TYPE="ntfs" 
/dev/sdb2: UUID="4427ebd5-ef54-4c64-8846-dbdb4f147ee1" TYPE="ext4" 
/dev/sdb5: LABEL="extra" UUID="01CBF17B9992D781" TYPE="ntfs" 
/dev/sdb6: UUID="58727e1a-e067-4094-aaac-ced102669daa" TYPE="swap"



i want to auto mount the drive  download and software. and when i dont need i unmount it. but ntfs config gives one time option to automount..

and never unmount it says

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=0C9066D19066C136 from /media/


plz help me

---

### Post by coffeecat on 2011-04-10
> **athalsten said:**
> i want to auto mount the drive  download and software. and when i dont need i unmount it. but ntfs config gives one time option to automount..

When you (or ntfs-config) sets up an NTFS partition to be "automounted" it does so by adding a line to /etc/fstab, in the case of "Download & Software":

```
#Entry for /dev/sda5 :
UUID=8858F8CB58F8B8D0    /media/Download\040&\040software    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
```By being mounted through fstab on bootup, it is mounted by root and the only way it can be unmounted is by using root privileges. It sounds to me as though you want to mount the "Download & Software" on an as needed basis, not permanently. A much better way is simply by clicking on the "Download & Software" entry in the Places menu or places sidebar of Nautilus. Then, all you have to do to unmount it is right-click on the desktop icon or click on the Places sidebar again. However, you can't do that while it is mounted using fstab. You'll need to manually edit /etc/fstab and I can show you how to do that if you want.

Before we do that, there's something else to think about. You have no less than 7 ntfs partitions mounted by /etc/fstab. This means 7 icons permanently littering your desktop and I find it difficult to believe you need 7 partitions permanently mounted all the time. That's one of my objections to ntfs-config - it's a sledge-hammer to crack a nut. It's so easy to automount ntfs partitions with the Places menu that there is hardly any need to be editing /etc/fstab.

So - which ntfs partitions do you really need to be permanently mounted? Let us know and then I or others can tell you how to edit /etc/fstab and what needs to be edited.

I do have one last comment. On your sda disc you have "Win_XP" which I guess is your Windows C: partition, but you also have "Download & Software", "Movie_1", "Movie_2", "Other" and "Songs_Pictures_video" partitions. Most people would find it easier to have just one "data" partition and organise all that in separate folders within the one partition. It would be easier and far more efficient of disc space. Just a thought.

---

### Post by athalsten on 2011-04-10
> **coffeecat said:**
> When you (or ntfs-config) sets up an NTFS partition to be "automounted" it does so by adding a line to /etc/fstab, in the case of "Download & Software":

```
#Entry for /dev/sda5 :
UUID=8858F8CB58F8B8D0    /media/Download\040&\040software    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
```By being mounted through fstab on bootup, it is mounted by root and the only way it can be unmounted is by using root privileges. It sounds to me as though you want to mount the "Download & Software" on an as needed basis, not permanently. A much better way is simply by clicking on the "Download & Software" entry in the Places menu or places sidebar of Nautilus. Then, all you have to do to unmount it is right-click on the desktop icon or click on the Places sidebar again. However, you can't do that while it is mounted using fstab. You'll need to manually edit /etc/fstab and I can show you how to do that if you want.

Before we do that, there's something else to think about. You have no less than 7 ntfs partitions mounted by /etc/fstab. This means 7 icons permanently littering your desktop and I find it difficult to believe you need 7 partitions permanently mounted all the time. That's one of my objections to ntfs-config - it's a sledge-hammer to crack a nut. It's so easy to automount ntfs partitions with the Places menu that there is hardly any need to be editing /etc/fstab.


So - which ntfs partitions do you really need to be permanently mounted? Let us know and then I or others can tell you how to edit /etc/fstab and what needs to be edited.

I do have one last comment. On your sda disc you have "Win_XP" which I guess is your Windows C: partition, but you also have "Download & Software", "Movie_1", "Movie_2", "Other" and "Songs_Pictures_video" partitions. Most people would find it easier to have just one "data" partition and organise all that in separate folders within the one partition. It would be easier and far more efficient of disc space. Just a thought.



at first i thanked u for the reply. you described detailed which is better for me as a new ubuntu user.

i accidentally automounted all of my drive. i think i can do the same thing. so i want to test it. if i successful then i just mount one of my drive. so i mount all of my drive. then when i tried i cant unmount any drive. just the 3rd screen appears. 


1.plz tell me how can i undo all operation by ntfs config.


 
2. i just need the download and software drive for auto mount

i have 2 hdd and i have to format hdd some times then i may loss all data of my drive so why i make all partition .


thank you 

sorry for my english

---

### Post by coffeecat on 2011-04-10
Hi, no problem about the English. I can follow you. :)

What I suggest is to switch off all NTFS automounting in /etc/fstab and see how well mounting from the Places menu suits you. If you do the simple edits I suggest, it will be easy to switch automounting of selected partitions back on again. It wasn't your fault that you accidentally setup automounting of all your NTFS partitions. It's all too easy with ntfs-config which is one reason I advise people not to use it.

Anyway, here is your /etc/fstab as it is now. I've enclosed it in code tags for legibility and to show the formatting correctly.

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb2 :
UUID=4427ebd5-ef54-4c64-8846-dbdb4f147ee1    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda5 :
UUID=8858F8CB58F8B8D0    /media/Download\040&\040software    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda7 :
UUID=68F421C0F42190FC    /media/Movie_1    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda8 :
UUID=662851B3285182CB    /media/Movie_2    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda9 :
UUID=D82852D62852B36C    /media/Other    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=CE5CE3F35CE3D3ED    /media/Songs_Pictures_videos    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
UUID=0C9066D19066C136    /media/Win_XP    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb5 :
UUID=01CBF17B9992D781    /media/extra    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sdb6 :
UUID=58727e1a-e067-4094-aaac-ced102669daa    none    swap    sw    0    0
```Open a terminal and run this command:

```
gksudo gedit /etc/fstab
```Simply insert seven '#' symbols where I have inserted them in red below. Don't worry about the colour when you do it - that's simply to make it easier for you to see where they should be.

Edited /etc/fstab:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb2 :
UUID=4427ebd5-ef54-4c64-8846-dbdb4f147ee1    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda5 :
[COLOR=Red]#[/COLOR]UUID=8858F8CB58F8B8D0    /media/Download\040&\040software    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda7 :
[COLOR=Red]#[/COLOR]UUID=68F421C0F42190FC    /media/Movie_1    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda8 :
[COLOR=Red]#[/COLOR]UUID=662851B3285182CB    /media/Movie_2    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda9 :
[COLOR=Red]#[/COLOR]UUID=D82852D62852B36C    /media/Other    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
[COLOR=Red]#[/COLOR]UUID=CE5CE3F35CE3D3ED    /media/Songs_Pictures_videos    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
[COLOR=Red]#[/COLOR]UUID=0C9066D19066C136    /media/Win_XP    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb5 :
[COLOR=Red]#[/COLOR]UUID=01CBF17B9992D781    /media/extra    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sdb6 :
UUID=58727e1a-e067-4094-aaac-ced102669daa    none    swap    sw    0    0
```Be very careful when editing this file. If you accidentally make other edits, it could make your system unbootable. Double-check everything. Once you have finished the editing, save the file, close the terminal and reboot. Once you are back in the desktop you will see that none of the seven partitions have been mounted. Now you can mount any of them easily by clicking on it in the Places menu or in the Places sidebar in the Nautilus file browser. And if you want to then unmount it, you simply right-click on the desktop icon and choose "unmount", or click on the eject icon that's by the partition label in the Places sidebar of Nautilus.

If you later decide you want one or more of those partitions automounted when you boot up, all you have to do is run the terminal command as above and remove the # sign at the beginning of the appropriate line in /etc/fstab.

---

### Post by athalsten on 2011-04-11
Thank you very much. i will try it. 


and inform u later

---

### Post by athalsten on 2011-04-13
> **athalsten said:**
> Thank you very much. i will try it. 


and inform u later


thank you

---

