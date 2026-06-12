---
title: "trouble rcovering files from broken ubuntu install"
date: 2011-03-22
forum: General Help
---

### Post by Ashkwil on 2011-03-22
Hi I was attepting a boot loop fix when my ubuntu froze half way through uninstalling gnome, I am unable to boot in any mode from the grub and get errors about failing to load duv or sys or something of the kind, I cannot reach any command line either...

Now if I boot in a live cd my hdd is visible but I cannot mount it, no problem mounting a windows drive but the ubuntu one will now I get many errors such as a job is pending and others that are similar, I have tried last night for 5hours (not an exagguration) many solutions to get it mounted.

If I boot the windows hdd the ubuntu drive does not display in my computer and.I have the cable and jumpers set correctly.

Basically I cannot view what is on the drive at all, I'm wondering is there anyway to copy the drive to another hdd or usb other than what I have done, or could you suggest something to make one of these methods work?

Thanks a lot, I need to get some very important files back from the drive, and from now on I will backup A LOT!!!

Cheers

---

### Post by rmemm on 2011-03-22
Some ideas.  First see if your ubuntu partition is still there.  You can do that in fdisk or using cat on /proc/partitions.

If your partition is still there than you can do a couple of things.  You could use dd to copy the whole partition elsewere -- even into a large file if you have the space.  Other thing you could do is use a disk repair program on it -- if it's ext2,3, or 4 then e2fsck for example.  Other thing you might be able to do -- manually mount it with the mount command and if needed use the -t options to specify the type.

Probably best option -- use e2fsck to try to check/repair it.  You might also want to use dd to back it up first.

Rob

---

### Post by 741Baus on 2011-03-22
To transfer files for back up , I recently hosed my system and needed to get my documents to my backup hard drive , I couldn't do it, permission problems ,even using

```
gksudo nautilus
```

I found a solution using a live cd also you must have and internet connection .

Transferring files using live cd with a working internet.
open terminal
```
sudo apt-get install hfsplus libhfsp0
```

```
gksudo nautilus
```

hope this helps as it worked for me.

---

### Post by Ashkwil on 2011-03-23
@rmemm
Ok first off if i open the ubuntu partition gparted application i can view the partition on the HDD so im guessing that means it is still there.

Secondly will the dd work if the drive cannot be mounted? Oh and as for the checking / repairing a lot of places sy not to do this as you could lose everything? or should i only do it if I have it backed up first?

@741Baus
It will not mount but i could possibly try mounting using sudo nautilus, as for the rest "sudo apt-get install hfsplus libhfsp0" what doees this do and how would I use it to help transfer the files bearing in mind it CANNOT be mounted? Just wondering as im new to this and dont really understand what this will do!

Thanks again guys for the help

---

### Post by arif920629 on 2011-03-23
Try to chroot from a liveCD to your broken installation. Refer to this guide:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Ashkwil on 2011-03-23
@Arif

yeah i had a quick look and it seems the drive needs to be mounted e.g. "sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
"

However the drive will not mount using any software or terminal commands and i only receive errors, i will give it a go though when i am home.

Cheers

---

### Post by Ashkwil on 2011-03-23
Justbto let you know non of the above works, I did not try a repair on the disk as I want to get it backed up first, if I could mount the drive it would be simple but a get An error saying a job is pending, I can mount usb drives and my windows drive just fine

Any further suggestions??

---

### Post by Ashkwil on 2011-03-23
Justbto let you know non of the above works, I did not try a repair on the disk as I want to get it backed up first, if I could mount the drive it would be simple but a get An error saying a job is pending, I can mount usb drives and my windows drive just fine

Any further suggestions??

---

### Post by deconstrained on 2011-03-23
> **Ashkwil said:**
> Now if I boot in a live cd my hdd is visible but I cannot mount it
Does this mean it shows up over in the left navigation panel in a Nautilus window? Or that it is present in /dev?

Either way, **yes, you can mount it**, you're just going about it the wrong way. When booted to a livedisk, try:
```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# blkid
```
That should help you determine which device in /dev corresponds to your Ubuntu drive. Then, to mount it (Ubuntu = /dev/sda3 for example)
```
root@ubuntu:~# fsck /dev/sda3
root@ubuntu:~# mount /dev/sda3 /mnt
```
Your drive will be mounted at /mnt. Then open a Nautilus window as superuser as has been suggested and you'll be able to access/copy the files.

BTW you could probably rescue your system without reinstalling, depending on the problem. Have you changed anything in /etc recently? Run a software update that included a new kernel/image? Not being able to boot, especially after a software update, is a very, very, **very** common problem, and hundreds (literally) of threads have been started on this topic. The answer is chrooting.

> **741Baus said:**
> open terminal
...
```
gksudo nautilus
```
Better yet: Alt-F2 gksudo nautilus
much faster.

---

### Post by Ashkwil on 2011-03-23
Hiband thanks for the great post, it shows in the places menu but when I ran nautilus insuperuaer it wasn't at the side, I will give your technique a go tomorrow and get back to you

Oh and as for the software in one session I fully updates, installed themes, nautilus addons, ubuntu tweak, vlc player basically I'd had it running a couple of weeks bog standard andbin one session I'd installed a fair bit so firing the problem would be quite difficult, the grub shows but none of the options work I'm guessing due to gnome not being installed, i get it mounted I'll chroot and reinstall gnome, is that possible?

Thanks again for taking the time to reply

---

### Post by Ashkwil on 2011-03-24
Ok well i got as far as this which is when i ran into the first error..

```
root@ubuntu:~# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
root@ubuntu:~# 

```

Is there anyway around this?

Thanks so far :)

---

### Post by rmemm on 2011-03-24
If its mounted then umount it before scanning.  I.E. "umount /dev/sda1".  I'm assuming your not booted from it of course.  You can check if it's mounted with the "mount" command with no arguments.

I don't know how your booted -- but booting from something like a CD and using either the default ubuntu demo disk or a small distribution like puppy linux is what I would do.  One issue with the ubuntu boot CD is that it does potentially use the swap file on your hard drive. If your hard drive is in good shape -- then this probably is not so important.

Also just a note.  You may want to use the -f options to force checking as a journaled file system normally only replayes the journal.  You may want to force a full scan as well even if the system thinks it's clean.  It don't see where fsck lists this options -- but I know e2fsck needs this sometimes.

Rob

---

### Post by deconstrained on 2011-03-25
Well you certainly don't want to check a mounted filesystem (that can end not well), so it's a good thing you've stopped there. 

Did you open nautilus and mount or try mounting the partition beforehand (which would explain the error message)? Do you have any active logical volume groups on /dev/sda1? Is sda1 the correct partition (and did you use blkid to ascertain which block device was which)? As has been suggested, there's a chance sda1 may actually be the disk you're booted to. Working with block devices requires you be circumspect about it; you don't want to touch anything that you don't mean to, or it could result in data loss.

---

### Post by Ashkwil on 2011-03-25
Ok firstly I am booted in live cd, I have not tried mounting it in nautilus, the live cds config always tries to automount the disk if I'm correct, sonething like geditconfig opens a panel where I can disable automount, however in a live cd the changes don't keep when I reboot, I am deffinately not booted from the drive.

I'm thinking maybe a ubuntu usb install so the automount will stay off?

And then a fresh boot so it will have never tried to mount at all

Also if I open gparted I can see only one drive is connected and one partition has 5gb of data on and its sda1 ext4 and the others have nothing so I'm sure its the right one

I'm still open to suggestions :)

---

### Post by rmemm on 2011-03-25
My experience has been -- live CD does not mount partitions unless you open them from the places menu.

So if I understand correctly -- from live CD, open up a command window.  Then run the command:

sudo umount /dev/sda1

That will un-mount sda1 if it's mounted.  If it fails -- presumably it was not mounted.

Then run your fsck command.  (with sudo in front of it of course).  

Alternative to above -- you can probably umount from the GUI.  By that I mean, if you mounted the volume there is probably a desktop icon, and in the context menu of it there should be something like Eject or Unmount or something similar.  Also your fsck can be run from gparted also and possibly from the new Disk Tools admin tool -- but I'm not very familiar with Disk Tools.

Rob

---

### Post by Ashkwil on 2011-03-25
I will try when i get back but im am sceptical...

My windows drive mounts in seconds along with other usb drives but this one i get an error, so i really doubt running the umount will do anything as it has never mounted successfully and i am sceptical i will ever get it mounted although i need those emails..

Its very frustrating i cant just copy over the files, is there a version of linux i could boot to which would recognise the drive better and possibley mount it? Say a certin build designed for copying drives?

Thanks for the help so far ill try out what you said later on today

Cheers

---

### Post by Ashkwil on 2011-03-25
Ok i tried the suggestions today and heres what i got... nothing new at all =/

```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# umount /dev/sda1
umount: /dev/sda1: not mounted
root@ubuntu:~# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
root@ubuntu:~# 

```

Oh and when i run nautilus with gksudo nautilis i get errors but it does open i dont know if it means anything?
```
root@ubuntu:~# gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:4345): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '4345'

(nautilus:4345): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:4345): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:4345): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

```

Anything else I can try?

Thanks again

---

### Post by deconstrained on 2011-03-26
Okay, good, now that you've ruled out any trivial/banal cause, try this to look for the process(es) that might be using the device:
```
root@ubuntu# fuser -vam /dev/sda1
```
I am as confused as you are. I want to see what on an Ubuntu live disk would monkey around with block devices even before telling it to do anything!

---

### Post by iiiears on 2011-03-26
Testdisk. PhotoRec. 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Best Wishes.

---

### Post by Ashkwil on 2011-03-26
@deacon

I get this

                    USER.             PID. ACCESS. COMMAND
/dev/sda1:


So it's just blank lol does this mean anything to you?

As for iii I'll give it a go after the weekend when  home :)

Thanks again I really appreciate this

---

### Post by rmemm on 2011-03-27
It might be worth checking the following command:

cat /proc/partitions

This will list all of your partitions that are available.  I've gotton the fsck result you did when I've selected the wrong partition.

It would also be interesting to check the result of the command:

mount

This will list all mounted devices.  From comparing the two you should be able to figure what device is what (maybe).

Also from one of the other replies -- one thing that the boot CD will do is use the swap partition on the volume.  So any partition that is labeled as swap (type 82) in the partition table might be in use unless you turn swap off. (see the man page for swapon and swapoff).

You might want to use the command "fdisk -l" to list information about all of your partitions.

I'm assuming your not using Raid, LVM, or anthing similar?  By this I mean -- you expect to find a native ext4 partition at sda1?

Another thing you could try is used e2fsck not fsck.  Don't think this should make any differences, but might be worth a try.

The fsck suggested that it through your volume was ext4.  Is this reasonable?  I ask -- because it's good to sanity check this.

Another thing you could try is to specify the use of one of the super blocks.  With e2fsck the -b xxxx option specifies this -- where xxxx is the location of the backup superblock.  The man page says it's at 32768 if your using 4k blocks in the file system.  There may be some risk to dong this as I think this backup superblock may replace the default superblock in this case -- maybe someone else knows more about how this works.  I also don't know if your using 4k block sizes or not -- this it is probable however.

Another useful command is "dumpe2fs". You use it something like "dumpe2fs /dev/sda1"  where /dev/sda1 is the partitions your selecting.  This will list file system information (if it can), and also the location of any backup superblocks. Check the manpage for more info.

Another thing you could play with -- try one of the small system rescue cds.  I like Puppy Linux.  It's not a rescue CD -- but it's small and fast.  Worked better for me than loading the Ubuntu Live CD in the past.  There are a number of other candidates too -- though I've not tried these -- SystemRescue, Riplinux, Ubuntu Rescue, Finnix.  You can find these discussed on [http://distrowatch.com/](http://distrowatch.com/).  Puppy and SystemRescue I think are GUI based, the others may be command line based.

Sorry if I'm being repetative.  It seems to me like we are forgetting something.  The message you get when using fsck is very strange unless you either (a) don't have permissions needed, (b) are choosing the wrong partition -- that's when I've gotten messages like that.

Anyway -- maybe one of these ideas will trigger some thoughts.

Rob

---

### Post by Ashkwil on 2011-03-27
Ok thanks for that, Firstly i will not have access to the PC until tommorow night but i will try and answer some questions!

Ive ran mount before and the only /dev i can see is my CDrom which is also backed up when i run umount /dev/sda1 it says its not mounted.

As for it being the right partition For example if i open GParted and select the 40gb HDD i have 3 partitions (this is from memory) I have the sda1 which is 5.xgb of used space and which im sure is obviously the filesystem and I have two more partitions i think one is boot and one is swap? I THINK.

As for the raid thing the HDD is not running thorugh RAID although I do have a SATA card but i dont think this would affect anything ive never even plugged anything into it!

As for the superblocks and stuff... wow i am a total noob that was like a foreign language to me!

I will try the puppy linux, is there a possibility the drive wil just mount without doing anything if i ran it?

Again thanks very much and i will run all of your ideas and post back the results on monday night.

AGAIN, i REALLY appreciate this!

---

### Post by deconstrained on 2011-03-27
> **Ashkwil said:**
> I will try the puppy linux, is there a possibility the drive wil just mount without doing anything if i ran it?
Yeah, at this point I'd be giving up and trying a different livedisk, although I've never had that problem with an Ubuntu CD. If it still gives you problems then there's something wrong with your bios settings/hardware, or there's a corrupt block somewhere on the disk that's interfering with proper use of the hard drive. BTW the output of fuser indicates that nothing was using the partition, so for mount to throw you that error is highly unusual.

---

### Post by rmemm on 2011-03-27
Reason I mentioned puppy linux was that on my wife's computer I had trouble with the Ubuntu Live CD and also a particular ext3 partition.  Puppy would for some reason mount the ext3 partition but Ubuntu would not even after I had reparied it with e2fsck. So it is possible just using a different distribution would solve it.  Here is a link to puppy on distrowatch:  [http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy). I was personally suprised by this -- because it still does not make sense to me why -- by in my case puppy did strangly work. 

Regarding super blocks -- the way linux file systems are layed out is that there is a "superblock" at offset 1024 from the start of the partition.  This is the default superblock.  It contains a bunch of file system information and pointers to other things like the file allocation table, inodes, and other internal structures.  If the superblock get's damaged -- you may essentially loose the ability to access the whole file system.  Because the superblock is so important the system maintains a number of backups throughout the file system.  In principle you can use one of these others instead of the default super block.  The trick is knowing where they are -- and this is dependent on the block size used in the file system which is typically 1k, 2k, or 4k.  Larger file systems are usually 4k.  The other way of finding this out is saving the log when the disk is originally formatted, and using dumpe2fs to find them if possible.

Why I mentioned this is that some of your error messages suggested that either a) the superblock is damaged, b) the fs is not really ext4, c) you don't have the correct access permissions, d) were focusing on the wrong partition.  This is just my impression -- so not certain.  

Other thing I did not mention -- most of the work you do on the hard drive will need to be from a root shell (by this I mean via sudo, or in a shell with the # prompt.).  I'm assuming you know this -- as most of your posts looked like they were recorded from a root shell.

Rob

---

### Post by rmemm on 2011-03-27
Other thing I intended to say.  How ubuntu partitions are layed out depends on how you did the install.  I'm not sure what the default layout is -- maybe someone else knows.  Typically you need a swap partition, and a root partition.  You don't actually need a boot partition.. though you may have set it up that way.  For example I usually use 3 partitions -- Root, Swap, and Home in that order -- but that's just me.

One reason I suggested "sudo fdisk -l" is that it will list the partition type -- i.e. Linux(83), and Linux Swap (82).  It might help identify which partition is what.

Also since the "mount" command did not show sda1 mounted -- than I think this means that it is not mounted -- which is good.

Also some things about puppy.  You'll need a version that has ext4 support.  I used 5.2 myself, and I think this had ext4 support.  The other thing, when you click on the drive icons in the lower left of the desktop in puppy -- it will try to auto mount the partition.  You may then need to un-mount it manually before using fsck or e2fsck.  If it mounts the partition -- then your likely to have access the files you want anyway -- so you may need to do nothing else to copy these onto another drive.  However, I'd be cautious about writing anything to the partition before you complete a full fsck/e2fsck.  

Rob

---

### Post by Ashkwil on 2011-03-28
Ok well I've made progress...

I've booted in puppy Linux and the drive is mounted! I bowser cannot copy all of .evolution folder OCR to USBas 3 files fail, these are all in the mail folder so I'm guessing they are I
Portage when it comes to getting my emails back?

Any help is appreciated
Ash

---

### Post by Ashkwil on 2011-03-28
Hi ok well for some wired reason mounting the drive in pl has allowed it to mount in the ubuntu live cd so I'll get back to you on the results!

---

### Post by Ashkwil on 2011-03-28
Yes! I ran gksudo nautilus and then copied the .evolution folder, I then imputed my emails and they all comenup!

Sorry for the triple post but thank you everyone who helped I amnso glad I got them back and I will get started on a new ubuntu install!!!

Ash

---

