---
title: "Duplicate OS HDD including Grub"
date: 2010-03-25
forum: General Help
---

### Post by jamesisin on 2010-03-25
I have a drive that is dying and I'd like to duplicate that onto another drive I have.  Is there a simple way to do this?

The dying drive is 120 GB and the other one is only 40 GB, but this drive only has the basic Ubuntu 9.10 build and there are other storage drives (so the installed OS comes in, what?, around 6 GB).

I'd rather not rebuild the machine if this (above) can be done without too much headache.

---

### Post by byStanderone on 2010-03-25
...something abut cloning:[http://ubuntuforums.org/showthread.php?t=135172](http://ubuntuforums.org/showthread.php?t=135172)

---

### Post by Serpher on 2010-03-25
Use the dd command

```
$sudo dd if=/dev/sda of=clone.img
$sudo dd if=clone.img of=/dev/sdb
```

I believe that will work. It won't delete anything and the commands will take quite a while to execute. Also you need to check where your drives are actually located in /dev/ being sd[a-z]. The first command will take your current partition, and turn it into an image. The second command will copy that image onto that device as a filesystem.

---

### Post by Herman on 2010-03-25
You can make an exact copy of one hard disk to another hard disk with the following dd command, providing the disk you are copying to is equal size or larger than your old hard disk,
```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```You would need to remove or disable one of the hard disks before booting because the file system UUIDs will also be copied and that would probably cause some interesting booting problems. 

Serpher's idea of copying a partition to a file will avoid any booting issues. I agree with Serfer, but I'd like to point out that some command line options can improve the command, also since your old hard disk is larger, a partition at a time will be necessary,
```
sudo dd if=/dev/sda1 of=clone.img bs=4096 conv=notrunc,noerror
```You should reduce the size of your partition first with a partition editor since the dd command will make a perfect copy, including empty space, and you can't restore to a smaller partition. If you shrink first it will save you trouble later.

---

### Post by jamesisin on 2010-03-26
Thanks for the information about the dd command.  It looks like what I need.

The old drive isn't really up to booting.  I'm gonna toss it into another machine along with the new one and hope for the best.  Shall I assume I need to mount these drives first, or do I run dd on an unmounted drive?

Herman - What do these arguments (bs=4096 conv=notrunc,noerror) do?

Assuming the drive will mount with gparted I should be able to resize down to 40 GB before running dd.  I can edit fstab with the new UUID information.  One question though, are UUID's consistent between systems?  In other words, if I get the UUID while on my other system will it remain the same when I put the drive back into the machine in question?

---

### Post by jamesisin on 2010-03-26
Is there something special I have to do to get grub to use UUID's?

I am putting these drives into a 9.10 system (default installation) with a SCSI drive for the OS.  That SCSI drive was sda when I built the machine but of course gets bumped when I add these other drives.  The fstab file contains UUID's.

All attempts to boot with the other drives attached fail.

---

### Post by Herman on 2010-03-26
> The old drive isn't really up to booting. I'm gonna toss it into another machine along with the new one and hope for the best. Shall I assume I need to mount these drives first, or do I run dd on an unmounted drive?Yes, on unmounted partitions except if you're using Serfer's command for making backups of your partitions to files, then the partition you want to create the backup in can be mounted.

Here's how I would clone partitions directly from one disk to the other,[B]

1.[/B] First plug both of your hard drives in and boot with Ubuntu in a LiveCD, or a USB flash memory stick or some other hard drive. 

Don't bother to mount any file systems in either of your hard disks.

**2.** Open GParted and reduce the size of the partitions in your 120 GB HDD which is failing.
Reduce them as small as possible to make sure they will all fit easily into the free space you have in the new empty 40 GB HDD.

**3.** Use GParted to create the same partition scheme you had, but in the smaller disk, each partition must be larger than the corresponding ones in your original hard disk.

**4.** Check and double-check which hard disk number and partition numbers belong to your original disk, with your operating system and files to make sure there is no confusion about which disk is which. This is to avoid making any mistake of running the dd command backwards which would cause you to lose your data!
[COLOR=Sienna]**Take particular care to note down your disk and partition numbers, draw a representation of your disks and partitions in a piece of paper to be sure.**[/COLOR] :idea:

**5.** One partition at a time, run the dd command like this,
```
dd if=/dev/sda**1** of=/dev/sdb**1** bs=4096 conv=notrunc,noerror
```WHERE: You want to copy partition number 1 from the first hard disk (sda), to the second hard disk (sdb).
[COLOR=Red]**Be certain never to run the dd command the wrong way, as it will do exactly what you tell it to do and it is perfectly capable of zeroing any and all data if you erronously copy an empty partition to one that contains data!**[/COLOR]

---

### Post by colorlessprism on 2010-03-26
i know i say this over and over, but Rmastersys. run remastersys with the "back up" option while commenting out your big folders (Documents, Music, .wine come to mind). take the iso thats made and run usb startup disk creator. thats it you now have a bootable, portable, and installable version of your install (dont forget to tar.gz the folders you commented out and back them up a flash drive so you can restore them when you reinstall

---

### Post by Herman on 2010-03-26
**6.** After you copy your partitions from your old drive to your new one, open GParted again or click 'refresh devices' if you still have GParted open.
Right-click on each partition, one at a time and select 'check', from the right-click menu in GParted, and click the 'Apply' button, and also the 'Apply' icon to run a file system check. This runs e2fsck and resize2fs for you.

**7.** Install GRUB to MBR in your new hard disk.

**8.** Shut down the computer and remove the old hard disk.
Since the dd command makes a perfect copy of your partitions and the file systems they contain, your new hard disk will have the same file system UUID numbers as the old hard disk and that can confuse GRUB and other software at boot time. Unless you take additional steps to edit and alter the UUID numbers, you should not use these two hard disks in the same computer unless one is unplugged from now on.

---

### Post by nerdopolis on 2010-03-26
wait...

It seems like the hard drive you are backing up to is smaller then your source drive.

The dd command also copies the "hidden" bytes on the drive, the bytes that are ignored on the file system, so even though you are using only 6GB, there are 112GB of empty space that dd will try to stuff on the 40GB drive

---

### Post by Herman on 2010-03-26
> Herman - What do these arguments (bs=4096 conv=notrunc,noerror) do?:D Here's a link to [Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") by AwesomeMachine - LinuxQuestions.org

What I do know from my own personal experience and observations is that the bs=4096 part enables the command to work much faster than it would run otherwise without any options.
I forget why I use the other options to be honest, I remember reading the web page I linked to above and running a lot of experiments and those are the options I found worked best at the time and have used ever since.
I'm open to corrections  if somebody has more information they care to share. :D

---

### Post by Herman on 2010-03-26
> wait...

It seems like the hard drive you are backing up to is smaller then your source drive.

The dd command also copies the "hidden" bytes on the drive, the bytes that are ignored on the file system, so even though you are using only 6GB, there are 112GB of empty space that dd will try to stuff on the 40GB drive:D See step 2'
> **2.** [I]Open GParted and reduce the size of the partitions in your 120 GB HDD which is failing.
Reduce them as small as possible to make sure they will all fit easily into the free space you have in the new empty 40 GB HDD.[/I]

---

### Post by Herman on 2010-03-26
> i know i say this over and over, but Rmastersys. run remastersys with the "back up" option while commenting out your big folders (Documents, Music, .wine come to mind). take the iso thats made and run usb startup disk creator. thats it you now have a bootable, portable, and installable version of your install (dont forget to tar.gz the folders you commented out and back them up a flash drive so you can restore them when you reinstall:D Thanks colorlessprism,
I've heard of remastersys but I don't really know anything about it.
Thank you for reminding us and explaining it a little.
That sounds like a really cool idea, I'll give that a try ! :D

---

### Post by jamesisin on 2010-03-26
Herman - Is there any reason to duplicate the extended and swap partitions?  If not I will merely create those partitions and allow Ubu to put into them what it wants.  (Of course, I will duplicate the ext4 primary partition.)

I'm still hoping you will tell me something about the arguments you suggest using:

```
bs=4096 conv=notrunc,noerror
```

I have finished the partition work and am just waiting now to run dd.

colorlessprism - Thanks for telling me about Rmastersys or remastersys, but I don't see how that would help in this circumstance.  Let me know if I'm not seeing something interesting.

---

### Post by jamesisin on 2010-03-26
Oops.  Looks like we are a little out of sync.

Let me know about the extended/swap question.

---

### Post by jamesisin on 2010-03-26
> **Herman said:**
> Install GRUB to MBR in your new hard disk.

Also, I believe I can do this from the LiveCD but can you point me to the steps/commands for doing so?

---

### Post by Herman on 2010-03-26
> Herman - Is there any reason to duplicate the extended and swap partitions? If not I will merely create those partitions and allow Ubu to put into them what it wants. (Of course, I will duplicate the ext4 primary partition.)I'm not certain because I don't have info on your exact partition arrangements, but I'd guess no, you probably don't really need to dd those, especially the swap area. You can always make a new swap area.


Actually, I use a swap file instead of a swap area in most of my Ubuntu installations now, see                           [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=make+swap+file+hibernate") by iva2k - Ubuntu Web Forums. 
With a single dd command similar to the one Serpher posted eariler in this thread I can quickly and easily back up my entire installation to a file in another hard drive.

---

### Post by Herman on 2010-03-26
> Also, I believe I can do this from the LiveCD but can you point me to the steps/commands for doing so?(Install GRUB to MBR in your new hard disk.)
:grin: Sure ...
                         [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900") - Ubuntu Web Forums

The steps described in the above linked thread should do it.

---

### Post by jamesisin on 2010-03-26
Ok, let me see if I have this grub thing right...

Will I need to run these?

```
sudo grub-install
sudo update-grub
```

I think I will then need to run something like this:

```
sudo grub-setup -d /media/KARMIC/boot/grub [UUID for / partition]
```

(I'm running gnome.)

And that's all?

---

### Post by Herman on 2010-03-26
> Will I need to run these?

     Code:
     sudo grub-install
sudo update-grub
Probably not.


> I think I will then need to run something like this:


```
sudo grub-setup -d /media/KARMIC/boot/grub [UUID for / partition]
```(I'm running gnome.)
  Yes, but you don't need the UUID number, I'm not sure if that's even possible, as explained in the thread I linked you to,  I would do something like this,
```
sudo grub-setup -d /media/KARMIC/boot/grub /dev/sda
```
WHERE /media/KARMIC is the mount point for the installed Ubuntu which contains GRUB2 which you want to install to MBR in /dev/sda.
> And that's all?That is all, Grasshopper ...

---

### Post by jamesisin on 2010-03-26
Ok, so /dev/sda is only telling grub-setup where the MBR is to be located and not actually being used by grub itself (my fstab does use UUID's).

---

### Post by jamesisin on 2010-03-26
Ok, I ran this:

```
sudo grub-setup -d /media/Ubu910/boot/grub /dev/sda
```

Got the map error:

```
grub-setup: error: Cannot open '/boot/grub/device.map'
```

I then added the -m /media/Ubu910/boot/grub/device.map and got this:

```
grup-setup: error: cannot stat /media/Ubu910/boot/grub//core.img
```

(Note the lack of quotes and the double slash.  There is a file called boot.img in /media/Ubu910/boot/grub but not one called core.img.)

What's next?

---

### Post by Herman on 2010-03-26
Is your partition mounted?

Also, see [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900") - Ubuntu Web Forums again.
If you still can't do it with grub-seup then you might need to resort to chrooting and running grub-install, see  			#[**37**]("http://ubuntuforums.org/showpost.php?p=8995103&postcount=37") (in the same thread).

---

### Post by jamesisin on 2010-03-26
> **Herman said:**
> Is your partition mounted?


Most definitely mounted.  I double, nay triple, checked that I was mounting only the new drive and running all of my commands aimed at that new drive.

The problem with core.img that I am seeing is not mentioned in that other thread.  I hope I don't have to do the whole chroot thing:

[http://ubuntuforums.org/showpost.php?p=8995103&postcount=37](http://ubuntuforums.org/showpost.php?p=8995103&postcount=37)

Anything else we can try first?

---

### Post by Herman on 2010-03-26
For a few minutes I thought to check back in this thread and make sure you are using GRUB2, and in #[**6**]("http://ubuntuforums.org/showpost.php?p=9032592&postcount=6") you said you're using Ubuntu 9.10.
You should have a /boot/grub/core.img and a /boot/grub/device.map. Perhaps you should check with 'ls /media/Ubu910/boot/grub', to make sure those files are there. 
```
ls /media/Ubu910/boot/grub

```

---

### Post by jamesisin on 2010-03-26
Yeah, I think grub2 is the default for 9.10.

There is a device.map, a boot.img, but no core.img.  However, the original drive (which I just popped back into the old machine and booted) doesn't have one either.  What's up with that?

(I am trying to minimize spin time on that old drive.)

---

### Post by Herman on 2010-03-26
core.img is a file that is made by the grub-mkimage command which is run by the grub-install command along with grub-setup.

If you don't have a core.img file then I guess we'll need to chroot and run grub-install so that it can run all the other commands it runs and we can't take a shortcut by just running grub-setup as we had hoped.  

[grub-install]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install") - runs a host of other commands, grub-setup only being one of them.

---

### Post by jamesisin on 2010-03-26
I currently have the old drive booted in the machine in question.  Can I just create the core.img file there and then put it on the new drive after?

---

### Post by jamesisin on 2010-03-26
Alright.  I ran through that whole chroot thing.  Not so bad really; just a lot of mounting and unmounting.  Really only one command beyond that.

No errors reported.

One of my storage drives lost its automount.  Palimpsest says it has bad sectors and I'm running a self-test on it now.  I suspect the OS drive is to blame and not an actual bad sector (I lost my mounts when I looked at the desktop before shutting that machine down to pull the OS drive).

I'll post here any further matters of interest.

---

### Post by Herman on 2010-03-27
> i know i say this over and over, but Rmastersys. run remastersys with the "back up" option while commenting out your big folders (Documents, Music, .wine come to mind). take the iso thats made and run usb startup disk creator. thats it you now have a bootable, portable, and installable version of your install (dont forget to tar.gz the folders you commented out and back them up a flash drive so you can restore them when you reinstall:D Hey colorlessprism,
 I'm interested in trying out remastersys and I'd like to try using it to make a Live Ubuntu DVD which might contain pictures, videos maps and other files promoting attractions and telling stories about my home town and its surrounding countryside.
If it turns out nice enough I might make it available at our local tourist information building.

Would remastersys be useful for something like that?
If I decide to try it how much room will I have for videos, pictures and other files?

---

### Post by Herman on 2010-03-27
> I'm still hoping you will tell me something about the arguments you suggest using:

     Code:
     bs=4096 conv=notrunc,noerror 
:D I invested some time re-reading the link I gave you earlier and these are some paragraphs I picked out that seem to answer your questions,
From [Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") by AwesomeMachine - LinuxQuestions.org
> Notrunc means 'do not truncate the output file'. 
Noerror means to keep going if there is an error. 
Dd normally terminates on any I/O error.From [Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") by AwesomeMachine - LinuxQuestions.org
> (conv=notrunc) Tells dd not to abbreviate blocks of all zero value, or multiple adjacent blocks of zeroes, with five asterisks (when you want to maintain size) Do not use notrunc for copying a larger volume to a smaller volume. Without (conv=notrunc)
From [Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") by AwesomeMachine - LinuxQuestions.org
> (noerror) Does not stop processing on an input error. 
When an input error occurs, a diagnostic message is written on standard error, followed by the current input and output block counts in the same format as used at completion.
If the sync conversion is specified, the missing input is replaced with null bytes and processed normally. Otherwise, the input block will be omitted from the output. notrunc Does not truncate the output file. Preserves blocks in the output file not explicitly written by this invocation of dd. (See also the preceding      I interpret that to mean if there's an I/O error, (like if the dd command encounters a bad sector), it will skip the bad sector and keep going rather than halt on an error message.

---

### Post by jamesisin on 2010-03-27
Wow.  This is proving to be the worst disaster recovery experience ever.

I now have the new drive in place and am getting a host of errors at boot time (including errors claiming a boat load of bad sectors on the storage drives--what are the odds?).

Here are a couple of boot time screen shots for your entertainment.

(These screens appear in reverse order from their placement below.  All of those UUID's exist.)

---

### Post by jamesisin on 2010-03-27
Herman - Thanks for the additional information.  I noticed that when dd ran it finished without errors (so presumably it would not have halted anyway).  Good to know going forward though.

This system has now moved into a Completely Forked state.  I can no longer mount the music storage drive which is the entire point of having this machine.  I may just go ahead and rebuild the OS tomorrow.

I really hate computers.  What a bunch of BS.

---

### Post by Herman on 2010-03-27
:-k Hmmm ... That is strange, having problems with more than one hard disk drive in a short time.

How are you testing your hard drives, are you using the badblocks command?

I do look at my boot-up messages sometimes, but I normally take them with a grain of salt, I think you need to be a kernel developer to understand them properly.

---

### Post by jamesisin on 2010-03-27
Yeah, I don't typically see drive troubles at all; so to see two of them having troubles consecutively on the same machine suggests foul play, er, that the second one is likely just a mistake.

I have run these tests using palimpsest.  If you have some better testing methods I'd love to hear about them.

As to the boot time errors, this machine had none prior to this problem.  That second image outlines some mount troubles on all three of the drives which are supposed to mount at boot time (through fstab).  That text actually appears below the Ubu circle icon, and I've not ever seen text there before on any machine.

---

### Post by jamesisin on 2010-03-27
When I attempt to mount this renegade storage drive using Palimpsest I am told:

```
Error mounting: mount exited with error code 1:helper failed with:
mount:only root can mount /dev/sda1 on /media/Tunage
```

I am not prompted for my password (and I believe I normally am).

Gparted does prompt for a password, but takes tens of minutes to scan through the devices for partitions.  It tells me for sda1 (the renegade storage drive):

```
Couldn't find valid system superblock.

dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs:Attempt to read block from filesystem resulted in a short read while trying to open /dev/sda1

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
```

This sounds so lame.

---

### Post by Herman on 2010-03-27
:-k  Hmmm ... 
Yes that does look bad. 

So You've tried running a file system check with e2fsck? 
Normally my next step would be to try running e2fsck on the unmounted file systm without the -y option (presuming you have an ext series file system), to see what feedback the e2fsck command reports,
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```Where: /dev/sda1 is the partition containing the unmouted ext series file system.

That command often repairs file system problems, but in addition to that, it also produces valuable feedback which I have come to believe is fairly reliable and if it encounters a problem it cannot repair, it will give us a nice informative error message.
```
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device> 
```:-({|= Okay, that's a bit sad for the file system's first superblock, but we have lots of spare copies of the superblock that we can replace it with, so to take a look, we do,
```
sudo dumpe2fs /dev/sda1 | grep -i superblock
```The output from the above command should give us a list of alternative superblocks which we can use to replace the faulty superblock, and the following command can be used to do that,
```
sudo e2fsck -b 32768 /dev/sda1
```WHERE: '32768' is a sector number reported by the previous command as one containing a spare copy of the superblock for this file system which we hope will be in better condition.

All hard disks have bad sectors, even brand new ones , and bad sectors do appear from time to time during normal service. If a bad sector happened to occur suddenly at a file system superblock this series of commands should rectify the situation at least temporarily. (We hope).

If the hard disk is really deteriorating then probably it won't be long before we run into more problems, but if the hard disk is okay we might not see another problem like this for years. :D

---

### Post by Herman on 2010-03-27
```
sudo badblocks -sv /dev/sda1 >> badblocks.report
```To follow up on that, I would run the badblocks command, which will search the partition for bad blocks on the disk surface itself, (as opposed to reading the drive's firmware), and will report any badblocks it detects in a file named 'badblocks report'.

[LIST]
[*] If this file is empty, it means your hard disk has passed, and the hard disk hasn't run out of spare badblocks yet.
[*] If you see one or two or even a handful of badblocks, they could be new badblocks that the drive hasn't had time to map out yet, so keep an eye on things by running the command again after a time.
[*] If you see a big long list of badblocks here it is a sign that your hard drive is failing.
[/LIST]
 I would pay more attention to the output from the badblocks command that I would to anything else as I've used it a few times and found it to be fairly reliable.

EDIT: I just remembered to let anyone who might want to try the badblocks command know, (if they haven't tried it before), that it takes quite a while to run and we can expect our terminal prompt to disappear for a long time. That's normal and we should be patient and leave the terminal open until the command completes.

---

### Post by jamesisin on 2010-03-27
Both of these commands gave about the same output:

```
sudo e2fsck -C0 -p -f -v /dev/sda1
sudo dumpe2fs /dev/sda1 | grep -i superblock
```

Namely:

```
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
```

I will report the output from bb when it finishes.  Let me know if there are other things we should be looking into.  Thanks again.

---

### Post by jamesisin on 2010-03-27
Well, it's only about 1/3 done, but there is a proverbial fork-load of numbers in the file currently.  Mostly they begin at a point and continue contiguously for a huge span (thousands? not sure yet).  I'm scratching my head.

---

### Post by Herman on 2010-03-27
:sad: It doesn't look good.

I suppose it could happen that more than one hard disk drive can develop problems within a short space of time of each other, but it seems like unusually bad luck to lose two hard disks in such quick succession like that.

---

### Post by jamesisin on 2010-03-28
I guess it's possible it wasn't the OS drive that was making noise.  Still this is a giant pain in the asp.

I looked at my most recent backup and it looks like it was back in December.  Which means that any music I downloaded or ripped since then hasn't been synked.  Not the end of the world but more pain in the asp.  I suppose I should finish that backup script (lazy battered).

Any chance to recover data off the drive in this current state?

---

### Post by Herman on 2010-03-28
> I guess it's possible it wasn't the OS drive that was making noise.Maybe not, I would try running the badblocks test on that one sometime and see if that confirms the Palimsest (SMART) report or not.
> Any chance to recover data off the drive in this current state? 	You can try but it might be more work than it's worth by the sounds of things.

Incidentally, did you see anything in your Palimsest report on this disk that could indicate possible causes? Maybe your hard drives are just getting old or maybe they're getting hot or something like that? Or did they just die from old age?

I have a friend who owns a laptop and the monitor used to go blank on her. 
The cause turned out to be a magnetic bracelet she liked to wear, it had fairly powerful magnets in it, some people believe magnets can reduce pain. Anyway, the magnetic bracelet was interfering with the operation of her laptop's hard disk drive now and again. 
I was wondering since you mentioned music, if you would have any speakers anywhere close to your computer box? (Probably you would already have thought of that, but I just thought I'd mention it in case).

---

### Post by jamesisin on 2010-03-28
Would be nice to see a message *before* the drive dies: Attention, you are about to be fuxored!

I'll test that old drive, but I suspect (now) that it's probably ok.

Oddly about a year ago (when I built this server) I had a 500 GB IDE drive die in a similar manner.  It had the music on it that I was moving onto the server.  That drive *was* a bit older, but it hadn't really seen much work so it was out of place.

Now this SATA drive dying in this machine in a similar manner: Palimpsest complaining it was dying and showing bad sectors.  I'm starting to wonder if EXT4 or Ubu9.10 or FLAC have the power to crush drives.  At least the old one (500 GB) died slowly enough for me to get most of the data off of it.  This new one died at hyperspeed--and it's 1.5 TB.

If you think of any possible avenues please let me know and thanks again for your help.

---

### Post by jamesisin on 2010-03-28
Oh, the speakers...  This machine is acting as the music *server* so it doesn't even have a sound card.  There are speakers all over the place here, but nothing plausibly close to these machines.

---

### Post by Herman on 2010-03-28
Yes, it's amazing to be able to store so much information in a hard disk, truely a marvelous feat of modern science and engineering, and yet it's always disappointing when hardware doesn't live up to our expectations for longevity.

Your hard drive manufacturer might value the return of one of their hard drives if it has failed prematurely so they can study it to find out what happened and learn how they can improve.
Some hard disk drive manufacturers offer free replacements for hard drives that fail within a warranty period, especially if the drive was registered at their web site when it was purchased, and/or if you still have the purchase dockets. Maybe try taking a browse around in your hard drive manufacturer's web site and see what they have to offer you. 
That won't get your music back, but it's at least worth a try for a replacement hard disk. 
More than that, it's a way to get your message through to the right people.

---

### Post by Herman on 2010-03-28
You might be  able to use ddrescue to recover files from a hard disk with bad sectors, I think that's what it's for. I haven't tried it yet myself though.

[*ddrescue* - Linux *How to*]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&ved=0CAgQFjAA&url=http%3A%2F%2Fwww.cyberciti.biz%2Ftips%2Ftag%2Fddrescue&ei=oOyvS53AIdCgkQXhruGzDQ&usg=AFQjCNGqGcLdrSkVYxW5diNFed2JN8acMA&sig2=PXKWOGi1nYq-utEfV2T27Q")

[*Ddrescue* - GNU Project - Free Software Foundation (FSF)]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=3&ved=0CBMQFjAC&url=http%3A%2F%2Fwww.gnu.org%2Fsoftware%2Fddrescue%2Fddrescue.html&ei=oOyvS53AIdCgkQXhruGzDQ&usg=AFQjCNEDxqN2pSC4hsYH2a51vElQRTXuoQ&sig2=Prwd6QNRZ27Rfgu1CKd0Kw")

[*HOWTO*: Recover Data From a Dead Hard Drive - Ubuntu Forums]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=4&ved=0CBcQFjAD&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D308821&ei=oOyvS53AIdCgkQXhruGzDQ&usg=AFQjCNGp_EKcZaLfAs5ZhlN0PdnKp2EjDQ&sig2=FlZ4nUiDEFoeRS5vX1QLhQ")

---

### Post by jamesisin on 2010-03-29
I'll check those links out.  Thanks.

I ran badblocks on that old OS drive and came up null.  I forked up.  Twice: a) chose the wrong drive as bad b) didn't write my bu script.

Not the end of the world but a lesson sincere.

(The bb report for the dead drive was 3.8 GB and that for the OS drive was 0 bytes.)

---

### Post by jamesisin on 2010-03-29
I am preparing to attempt to rescue that data and I've been reading through those links you posted (and some others).  I noticed this:

> If the drive is so damaged that the file system in the rescued partition can't be repaired or mounted, you will have to browse the rescued data with an hex editor and extract the desired parts by hand or use a file recovery tool like photorec.

I am not able to mount the partition; does this mean ddrescue will fail and I should be using (something like) photorec?

Any clues?

---

### Post by Herman on 2010-03-29
That's disappointing news, your file system doesn't seem to be repairable at all, so I don't think ddrescue will help, given that information. Sorry about that, I was hoping it might be worth a try, but now I think probably not.
I have also read that in some cases leaving a hard disk in the refrigerator for a while can help with data recovery, but that would probably depend on what the exact problem with the hard drive is.
You can try with photorec and see if you're lucky, I guess it wouldn't do any harm to try, apart from the time you might waste.
It's beginning to look as if it would be quicker to just fall back on your backup and go collect the music you lost over again.
Sometimes is better to just accept our losses and move on.

---

