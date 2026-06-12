---
title: "How to backup and restore a triple-boot system?"
date: 2010-06-14
forum: General Help
---

### Post by manojit_r on 2010-06-14
I am curious about the best/simplest way to back up my triple-boot machine, which has Karmic 32-bit, Karmic 64-bit and Windows 7 (64-bit) installed on 3 equal slices of the internal 1TB disk. There are a total of 6 partitions (1 primary+1 logical partition each for the two Karmic, and 2 primary partitions for Win7), and I would like to back it up on an external disk such that the whole system can be restored as-is by writing over the disk. I guess this means correctly backing up data+partition table+MBR, and I would also prefer backing up only the used portion of the disk (rather than creating a 1TB mostly empty image file).

To my knowledge the only way to reliably do this is with "dd" command, but I have never used it ("fsarchiver" seems to be the next best option, but it cannot back up MBR yet; and "partimage" does not have ext4 support). As described _[COLOR=Blue][here]("https://help.ubuntu.com/community/DriveImaging#Backup%20with%20dd")[/COLOR]_ and _[COLOR=Blue][here]("http://ubuntuguide.net/backup-and-restore-entire-hard-disk-with-dd-command")[/COLOR]_, I should run the following commands from a **live** boot:

1) To back up entire data in compressed format (using 1MB read block to speed up the process):
[FONT=Courier New][SIZE=2]dd if=/dev/sda bs=1MB | gzip > /backup/image.gz[/SIZE][/FONT][SIZE=2]
[/SIZE] 
2) To back up MBR+partition table (stored within the first 512 bytes of the disk):
[FONT=Courier New][SIZE=2]dd if=/dev/sda bs=512 count=1 of=/backup/image.mbr[/SIZE][/FONT]

3) To restore data:
[FONT=Courier New][SIZE=2]gzip -dc /backup/image.gz | dd of=/dev/sda[/SIZE][/FONT]

4) To restore MBR+partition table:
[FONT=Courier New][SIZE=2]dd if=/backup/image.mbr of=/dev/sda[/SIZE][/FONT]

Has anyone used this method to successfully back up and restore a multi-boot system? I would appreciate if someone can confirm/correct/improve the steps I have listed here.

Thanks,
Manojit

---

### Post by Mark Phelps on 2010-06-15
I haven't actually used it, but Clonezilla has an option to backup an entire physical drive. And, since it works both with Ext4 filesystems and NTFS filesystems, it will be able to backup all your partitions.

I only use the partition backup/restore option because that's how I prefer to work.

But it would be worth your looking into Clonezilla.

---

### Post by manojit_r on 2010-06-15
Mark,

Thanks for your suggestion. I am aware of Clonezilla as may be the easiest backup tool available (never used though, and do not know how easy it is for multi-boot and multi-partition-type systems), but I thought it requires the backup disk to be at least as big the original disk (which is 1TB). I wanted to back up only the used part of (still) mostly empty disk. In any case, to be safe I just ordered a 1TB external disk, so I can fall back on Clonezilla if needed.

You mentioned using "partition backup/restore option" - can you please elaborate a bit on this? Can I use it to back up and restore my entire system?

(3500 beans! that should help you stay awake :) Keep up the good work)

---

### Post by -kg- on 2010-06-15
> **manojit_r said:**
> Mark,

Thanks for your suggestion. I am aware of Clonezilla as may be the easiest backup tool available (never used though, and do not know how easy it is for multi-boot and multi-partition-type systems), but I thought it requires the backup disk to be at least as big the original disk (which is 1TB).

You can specify the backup to be compressed using one of two compression schemes, one of which is bz (and the other I can't remember).  Using compression will decrease the file size...I believe significantly, using the highest compression scheme.

I like and use Clonezilla, but there is another available which I haven't checked out yet.  It purportedly will not only back up the entire hard drive, but the hard drive's MBR and even BIOS settings, as well.  It's called [PING]("http://ping.windowsdream.com/ping.html").

---

### Post by manojit_r on 2010-06-15
-kg-

Good info, thanks! Compression support could make Clonezilla a good alternative to dd - wondering though, does this mean Clonezilla will back up on a smaller disk, or still needs 1TB disk but creates smaller images? (The point is moot - I will use the 1TB external disk for backup once it arrives.)

PING looks promising, but the full name ("Partimage Is Not Ghost") seems to suggest it is based on the original [_[COLOR=Blue]partimage[/COLOR]_]("http://www.partimage.org/Main_Page"), which does not have ext4 support (I could be wrong about PING though).

One reason I was leaning towards dd is because it is a time-tested veteran, which not only makes dd very reliable (big plus when backing up entire systems), it also supports _[[COLOR=Blue]a rich set of functionalities[/COLOR]]("http://wiki.linuxquestions.org/wiki/Dd")_ via _[[COLOR=Blue]several arguments[/COLOR]]("http://linux.die.net/man/1/dd")_. The downside is the command-line interface, which can make the experience a bit hairy for newbs like me.

---

### Post by -kg- on 2010-06-16
> **manojit_r said:**
> Compression support could make Clonezilla a good alternative to dd - wondering though, does this mean Clonezilla will back up on a smaller disk, or still needs 1TB disk but creates smaller images? (The point is moot - I will use the 1TB external disk for backup once it arrives.)

Oh yes.  As a matter of fact, "dd" will actually back up to a smaller disk.  It all depends on what OS is on the disk, and how much data you have on it.  I have read that, unlike Ghost, which copies each partition sector-by-sector (requiring either compression or a partition of the same size), dd copies and replaces only the data in the partition.  You can also pipe the results of the dd command through compression software (like bzip or gzip) before sending it to the "of" (output file).

If I'm not mistaken (and I could be) Clonezilla is a GUI frontend for the "dd" and other commands to make the process easier.

> **manojit_r said:**
> PING looks promising, but the full name ("Partimage Is Not Ghost") seems to suggest it is based on the original [_[COLOR=Blue]partimage[/COLOR]_]("http://www.partimage.org/Main_Page"), which does not have ext4 support (I could be wrong about PING though).

Unfortunately, your assumption is correct.  I checked the website and, as of yet, PING (and Partimage) does not support the ext4 filesystem.  That would seem to be an issue that both need to make a priority to correct.  If they don't, they will quickly be left in the dust.

Fortunately, Clonezilla *does* support ext4.

> **manojit_r said:**
> One reason I was leaning towards dd is because it is a time-tested veteran, which not only makes dd very reliable (big plus when backing up entire systems), it also supports _[[COLOR=Blue]a rich set of functionalities[/COLOR]]("http://wiki.linuxquestions.org/wiki/Dd")_ via _[[COLOR=Blue]several arguments[/COLOR]]("http://linux.die.net/man/1/dd")_. The downside is the command-line interface, which can make the experience a bit hairy for newbs like me.

Yes, I know what you mean.  Personally, I like using GUIs, if for nothing else, because it eliminates mistakes and typos in the commands.  I'm also a bit oriented towards the "visual".

I like to introduce newbies to concepts using GUIs because:

1. - It's easier for them, and what most of them are used to, coming from Windows.

2. - Once they get used to the concepts, they are free to investigate and learn command line methods, should they choose to.

The command line is very powerful, and sometimes it's necessary to use it to do certain things more efficiently, not to mention that there are some things that just *must* be done that way.  But I'm basically lazy, and if there's a GUI that will do what I want to do (especially if it's something I do regularly) I'll install and use that GUI.  If that GUI combines multiple command usage required to perform an operation, I would rather click a few times and have that GUI-based software perform them for me than to sit for several hours having to figure out what commands I have to use, in what order, and the exact numbers I have to use with them, and then edit those commands, making sure I have no typos or errors (did I use that "rm" command exactly right, or is it going to delete everything on that whole partition?).

There's another reason I like to use GUIs.  Someone sat and wrote those GUIs to make life easier for themselves and others.  When they see many others using their software and liking it, it encourages them (and others) to continue to improve that software and write more.  I like encouraging the continuing development of software, especially GPL/GNU software.

But that's just me. :p

---

### Post by amsterdamharu on 2010-12-30
Sorry to resurrect an old thread here but if you want to backup your system then you can use tar.
From a life CD you can mount your / filesystem, for example in /mnt/sda5  (and if needed mount /boot in /mnt/sda5/boot). Home folder needs to be backed up separately.
Say the backup file goes to sda1 and is mounted under /mnt/sda1

```
cd /mnt/sda5
tar -cvpzf ../sda1/backup/backup.tar.gz --exclude=lost+found --exclude=sys --exclude=mnt --exclude=media --exclude=home . 

```

To backup your MBR and partition tables (boot sectors are on the partition table) safe the following in an executable file called backupmbr and unmount all when you run it (it does work when you mount it too but just to be sure).

```
for hds in $(fdisk -l | grep -i '^Disk /' | awk -F' ' '{print $2}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}')
    hds=$(echo $hds | awk -F':' '{print $1}')
    echo $hds
    dd if=/dev/$hds of=$hds.bin bs=512 count=1
done
for hds in $(fdisk -l | grep -i '^/dev/' | awk -F' ' '{print $1}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}');
    dd if=/dev/$hds of=$hds.bin bs=512 count=1
done

```
Delete any sdb.bin or sdb?.bin files if you only want to do sda and or a usb is plugged in.

To restore the mrb make a file restorembr with the following contents:
```
make_backup_first(){
    for hds in $(fdisk -l | grep -i '^Disk /' | awk -F' ' '{print $2}');
    do
        hds=$(echo $hds | awk -F'/' '{print $3}')
        hds=$(echo $hds | awk -F':' '{print $1}')
        echo $hds
        dd if=/dev/$hds of=$hds.bin bs=512 count=1
    done
    for hds in $(fdisk -l | grep -i '^/dev/' | awk -F' ' '{print $1}');
    do
        hds=$(echo $hds | awk -F'/' '{print $3}');
        dd if=/dev/$hds of=$hds.bin bs=512 count=1
    done
}

back_dir_name=`date +%Y-%m-%d`;
if [ ! -d $back_dir_name ]; then
    mkdir $back_dir_name;
    cd $back_dir_name;
    make_backup_first;
    cd ..
fi
for hds in $(fdisk -l | grep -i '^Disk /' | awk -F' ' '{print $2}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}')
    hds=$(echo $hds | awk -F':' '{print $1}')
    echo "Do you want to restore $hds";
    read -p "Type y restore anything else not to overwrite: " var_confirm;
    if [ "$var_confirm" == "y" ]; then
        dd if=$hds.bin of=/dev/$hds bs=512 count=1;
    fi    
done
for hds in $(fdisk -l | grep -i '^/dev/' | awk -F' ' '{print $1}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}');
    echo "Do you want to restore $hds";
    read -p "Type y restore anything else not to overwrite: " var_confirm;
    if [ "$var_confirm" == "y" ]; then
        dd if=$hds.bin of=/dev/$hds bs=512 count=1;
    fi    
done
```
You should run it from the directory where the .bin files are.

To restore the system data:
Mount your system at /mnt/sda5 (and possibly your boot in /mnt/sda5) I have home in a separate partition and have a different backup scheme for it. The backup is stored at ```
/mnt/sda1
cd /mnt/sda5
mkdir lost+found 
mkdir sys 
mkdir mnt 
mkdir media 
mkdir home
tar -xvpzf ../sda1/backup.tar.gz -C .
```

---

### Post by perspectoff on 2010-12-30
You can backup Linux filesystems with tar, but not Windows.

Linux filesystems can be moved as a series of files, and therefore compressed.

But Windows partitions have a MFT that is not strictly a file as is the case with Linux.

It is much safer to copy the entire partition when backing up Windows. Partimage will do this.

Also see:

Ubuntuguide.org at
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Maverick#System_Backup_and_Recovery)

or Kubuntuguide.org at
[http://kubuntuguide.org/Maverick#System_Backup_and_Recovery](http://kubuntuguide.org/Maverick#System_Backup_and_Recovery)

---

### Post by amsterdamharu on 2010-12-31
Oops, yes. Windows cannot be tarred like that. 
I use ghost in a dos image and stick the whole thing on a usb or even DVD depending on how many installed programs you want to take in the backup.

There should be a different approach to backing up your system and your personal files. A system, be it a bit tedious, can be re installed but the pictures you took back in 2003 can't be re taken.

---

