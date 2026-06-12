---
title: "Full Ubuntu 10.04 Installed on USB, Help."
date: 2010-10-04
forum: General Help
---

### Post by Resist on 2010-10-04
I made a previous thread asking how to install Ubuntu on a USB drive.  I managed to do it now by removing my HDD and just installing to the USB drive.  It seems to work fine, however it is really quite slow and sluggish.  I can't really run more than one or two programs at once with out it freezing.

Does anyone know why this could be?  Is there anyway to improve speed?  Is it due to my USB drive?  I'm using a Super Talent Pico-C 8GB.  Would a different USB drive work better?

Thanks,

---

### Post by C.S.Cameron on 2010-10-04
Some USB sticks are faster than others, but no USB2 sticks are faster than SATA.
USB3 will change this.

I understand that Ubuntu can be run in ram which is extremely fast but I have not tried it yet.

See:

[http://ubuntuforums.org/showthread.php?t=1499338&highlight=usb](http://ubuntuforums.org/showthread.php?t=1499338&highlight=usb)

---

### Post by sikander3786 on 2010-10-04
> I understand that Ubuntu can be run in ram which is extremely fast but I have not tried it yet.

It can but it will be a real pain every time you cold boot your PC with a slow USB device.

---

### Post by oldfred on 2010-10-04
Are you for sure running at USB 2 speeds? Disk Utility on my system shows speed.

Have you done some of the settings that reduce writes as writes are very slow.


Herman has some of the settings shown in this example, mostly at the end.
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by Herman on 2010-10-04
:)
Yes, USB2 is a relatively slow interface, and USB3 will fix that.
There is a big difference in performance between brands and models of USB flash memory sticks. Price is not always a reliable indicator.
I think it's best to use ext4 with journaling.
I think it's best to have a swap area or a swap file in the flash memory and to set swappiness to 10.
I agree with the other suggestions by oldfred.
Also, try setting 'System','Preferences','Appearance','Visual Effects' to 'none'.

A full Ubuntu installation in a USB flash memory stick is a great idea because it boots with GRUB2 and you can use it as an auxilliary operating system when your internal hard disk or ssd Ubuntu needs another operating system to perform maintenance tasks on it or if you need to travel and carry your operating system in your pocket. 
[**[COLOR=#980101][B][ubuntu]**[/COLOR] How to install ubuntu on USB drive and carry entire computing system in pocket?  [/B]]("http://ubuntuforums.org/showthread.php?t=789528")
:)

---

### Post by Resist on 2010-10-05
Thanks for the advice guys.  How do I use ext4?  Do I partition with that on install?  Also how do I create a swap area?  Sorry for the noob questions, I am a complete noob.

---

### Post by Herman on 2010-10-05
:) You don't need to do anything special to use the ext4 file system or a swap area because those are the default for recent versions of Ubuntu.  

If you're installing Ubuntu from the 'Desktop' Live/Install CD, as most people would do nowadays, step 4 of 7 of the installation is called the 'Partitioning stage' of the installation.
There you will see choices like, 'Install them side by side, choosing between each at startup', 'erase and use the entire disk', or 'Specify the partitions manually, (advanced).
The easiest way if you're not too sure what you're doing and you have no files in your USB external flash memory stick would be to choose 'erase and use the entire disk', and then everything will be done pretty much automatically for you.
Just make sure you choose the right disk!

That's pretty much all you need to know really, you can stop reading the rest of this post here if you want.
I'll add some extra info which you might not really need to know, but I will mention it anyway just in case you're curious and for the benefit of others.

The ext4 file system is the latest in the ext series of file systems and it features many enhancements that make it ideal for use in flash memory as well as ordinary hard disks compared with its predecessor, ext3. 
The ext3 file system was dog slow for running an operating system in flash memory and before ext4 was introduced to the masses I used to use and recommend the reiser file system for flash memory instead. Now I just use ext4 for everything.

A 'swap' area to Linux is something akin to what is called a 'page file' in Windows language, except most Linux users like to create that in its own separate partition instead of as a file inside the operating system partition.
A typical size for a swap area would be anywhere between around 125 MB to 1 GB of a hard disk. If you're cramped for space, a smaller one will have to do, but more than 1 GB is probably a waste of disk space, even for computers low on RAM.
The swap area or ('swap file' if it's inside the partition) is an area on the hard disk, (or in the flash memory) for the kernel to use as extra RAM and is especially important for computers with less than around 360 MB of installed RAM.

Many computers now have over 512 MB of installed RAM and some even have 1 or 2 GB or more, I have heard of computers now with 8GB of installed RAM, which is larger than the hard disk I had in the computer I first installed Ubuntu in!
Even if your computer has lots of RAM, it still seems to help performance if you have even a small swap area, even if it doesn't seem to ever be actually used. I don't know why, but I have run my own experiments and made my own observations and that seems to me to be the case. I don't know how to explain it in technical terms but my feeling is perhaps the kernel looks for the swap area and if it doesn't find one it's not happy. Here's a great link that does a better job of explaining what a swap file is and why it's important, [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") - Ubuntu Community Docs.

If you read that link you may have noticed that down around half way under '[What is swappiness and how do I change it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?"),' it says the default setting in Ubuntu is swappiness=60, and that would be ideal for a server, but value of swappiness=10 is recommended for a typical Ubuntu desktop installation.
I arrived at that same figure independently from my own trials and I agree with that, 10 is a good value for swappiness. It will improve performance because your computer will use RAM more, which is faster, and it will also tend to reduce wear on your flash memory too, which is an added benefit.
Links for more on swappiness, [Linux Performance tuning - vm.swappiness]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html") - unixfoo.blogspot.com, and [What Is the Linux Kernel Parameter vm.swappiness?]("http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/") - Linux Open Source Blog

Regards, Herman :)

---

### Post by Resist on 2010-10-06
Thanks for your detailed post, that's the kind of info I was looking for.  

I DBAN'd the USB stick and reinstalled the full version of Ubuntu 10.04  alternate so I could set up encryption.  It seems to run OK, installing  updates takes it's time though.  I found out my USB stick reads at  around 30MB/s and writes at only 8.5MB/s :( this was someone else's  tests on a review site.  How do I find my actual read/write speeds in  Disk Utility as oldfred mentions?  There doesn't seem to be that kind of  info there.

As for changing swappiness, how exactly do I do that?  I am completely  new to Linux and am not familiar with the setup at all yet.  The  tutorial in the link you posted says to "edit the configuration file  with your favorite editor", I'm not quite sure exactly what that means  but I searched for "swappiness' in the file system search.  I found a  swap file with a value of 60, this opens in gedit but it does not allow me to change the value, it has a locked symbol on the icon.  Could you  please tell me how to edit it and change swappiness?

Many thanks.

---

### Post by Herman on 2010-10-06
If you want to test your drive's read speed with Disk Utility, go 'System', 'Administration', 'Disk Utility', and select the drive you want to look at from Disk Utility's left-hand column.
In the much larger right-hand pane of Disk Utility, if you look around the center there you should be able to find a button called 'Benchtest'.
After you click on that button you'll see a new window with a button at the bottom left called 'Start read-only benchmark', and one on the right called 'Start read-write benchmark'. 
You can use the left-hand button any time, for the read-only test.
I was given a warning message when I tried the right-hand one, apparently the read and write test is only for blank drives, and I'll try it out sometime when I have a blank drive.

One way to test the write speed is to write a large file to the drive of known size and see how long it takes. Some people use the dd command for that, because the dd command has shows you the progress in terms of the amount of data moved and the time taken to do it. 

The length of time it takes to install Ubuntu is a good indicator or write speed if you keep track of the length of time it takes to perform a Ubuntu installation in other disks.
Generally I'd say an hour or an hour and ten minutes would be okay for a flash memory stick. Anything over an hour and a half is starting to get a little on the slow side.

There's a benchmarking program called bonnie++ by Russel Croker and I have used a little, it's good and can give you quite a detailed result. [Using Bonnie++ for filesystem performance benchmarking]("http://www.linux.com/archive/feature/139742") - linux.com.

It's normal for flash memory to be slower to write to but they make up for it with the read speeds. Just try tuning your operating system first and it'll probably be okay.

The test editor we use in Ubuntu for most ordinary day-to-day jobs is called 'gedit', (short for 'gnome editor', because we have a gnome desktop in Ubuntu, (as opposed to KDE in Kubuntu). Using Gedit is not all that different from using Notepad in Windows, except there are way more thing you can do with it, but you can learn about those later.
For now you only want to paste a line in the bottom a a file.

To open an operating system file with permisson to be able to write to it in Ubuntu, we need to prefix the word 'sudo' in front of the text editor command. That will make Ubuntu ask for our password, which is one reason why we aren't bothered by viruses in Ubuntu. We need to tell our text editor to open our sysctl.conf file, which lives in our /etc/folder.
So here's how to open your /etc/sysctl.conf file with gedit text editor, type, (or copy and paste), this into a terminal,
```
gksudo gedit /etc/sysctl.conf
```
At the bottom of the file, add this line 'vm.swappiness=10'.
```
vm.swappiness=10
```
Note: You may copy the text from the example abvoe and paste it into your sysctl.conf file instead of typing it if you like. (Recommended).

Then save and close the file and next time you reboot the changes should take effect and you may notice a little increase in performance.

---

### Post by Resist on 2010-10-06
Thanks for your help.  Got a bigger problem now, I can't boot up at all.  I got to the bit where I enter the password for encryption, press enter and then after 10-20 seconds I got a black screen with the following:

(process:356): GLib-WARNING **: getpwvid_r(): failed due to unknown user id (0)

I then restarted and got another black screen that said:

No init found. Try passing init= bootrag.
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

When ever I restart I get that same message, the same thing happened when I previously installed Ubuntu on my USB stick and when I had it on my HDD.  Before I just re-installed Ubuntu but there has to be a way to fix it.

Any idea what it is/how to sort it out?  Your help again would be much appreciated, Ubuntu is becoming quite stressful now. :(

---

### Post by Herman on 2010-10-07
> Any idea what it is/how to sort it out?  Your help again would be much appreciated, Ubuntu is becoming quite stressful now.The first thing to try will be a file system check.
I'm sorry for you choosing to install in an encrypted partition when you're still a beginner. It's a good idea to have an encrypted file system in a USB drive, but it does add a level of complexity to ordinary tasks that would be enough of a challenge for most beginners with just a regular installation.

I'm assuming you installed Ubuntu with a LUKS encrypted file system for  /.
You'll need to run these two command in your Live CD or in some other Ubuntu operating system in a hard disk or USB. 
```
sudo apt-get install lvm2 cryptsetup
``````
sudo modprobe dm-crypt
```After running those two commands, if you plug in your USB Ubuntu encrypted installation, you should be given a window prompting you to type your encryption password to unlock the volume.
Look under your 'Places' menu to see if an icon for your volume has appeared there and click on it, you should be able to open it and see  the files inside.
If you had files in it that needed to be rescued, you would now be able to do so.

But we don't care about rescuing files this time, we need to run a file system check. 
We never run a file system check on a mounted file system, so close any Windows you may have open and right-click on the icon for the volume that you have on your desktop and click 'umount'.

```
sudo lvdisplay
```This command is for taking a look around and reporting back to you what logical volumes might be in your computer or in disks plugged in to your computer.

Mine looks like this,
```
  --- Logical volume ---
  LV Name                /dev/[COLOR=Sienna]**usb-crypt-lynx/root**[/COLOR]
  VG Name                usb-crypt-lynx
  LV UUID                WjwHZr-tVkp-E02j-1IAA-SpCp-cYfT-YRGt6o
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                14.02 GiB
  Current LE             3589
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/usb-crypt-lynx/swap_1
  VG Name                usb-crypt-lynx
  LV UUID                6YBluv-4yzM-2KMf-pe5l-0TWy-A2PL-gafyhE
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                680.00 MiB
  Current LE             170
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

```The reason for running this command was to find out the LV name.
We need to know it because it's an important part of the next command.

For the next command I used 'tab completion', (just type the first two or three letters and then press the tab key for the LV name to be auto completed. As you can see, the LV name in the command below is not exactly as it appeared in the above output.
Remember, always make sure the file system is unmounted before attempting to run a file system check.
Run fsck on the unlocked volume: 
```
sudo e2fsck -C0 -p -f -v /dev/mapper/**[COLOR=Sienna]usb--crypt--lynx-root[/COLOR]**
```Here are what the results should look like,
```
herman@amd-quad-lynx:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/usb--crypt--lynx-root 
                                                                               
  205428 inodes used (22.32%)
     129 non-contiguous files (0.1%)
     329 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 177629/97
 1756458 blocks used (47.79%)
       0 bad blocks
       1 large file

  145978 regular files
   24382 directories
      59 character device files
      26 block device files
       0 fifos
     537 links
   34968 symbolic links (27601 fast symbolic links)
       6 sockets
--------
  205956 files

```

---

### Post by Resist on 2010-10-07
OK I entered the commands, installed cryptsetup and inserted the USB stick, it asked me for my password which I entered.  I then got a message saying:

Unable to mount 7.8GB LVM2 Physical Volume
Not a mountable file system.

I can't look at the files in '7.8GB LVM2' as it isn't mountable, however I can look at '255MB file system', this as a folder with 'grub' in it and some other files.

Anyway I carried on doing what you said, the '7.8GB LVM2' was never mounted anyway so there was no need to unmount, however the '255MB file system' was mounted and would unmount, I got the message:

Unable to eject 255MB Filesystem
One or more partitions are busy on dev/sdd

Again I carried on and entered code: sudo lvdisplay.  This is what returned:

```
  --- Logical volume ---
  LV Name                /dev/Me/root
  VG Name                Me
  LV UUID                deHhTH-mQSB-vRe3-aFKH-lQ0e-Yytg-0ctLOo
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                6.90 GiB
  Current LE             1767
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/Me/swap_1
  VG Name                Me
  LV UUID                7pVSVV-eLE7-6mgN-ZK27-7B6N-MwxJ-olg0D7
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                368.00 MiB
  Current LE             92
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
```Now I didn't really understand what you meant by 'tab completion'.  I tried different variations of the LV Name and got back the following:

```
e2fsck: No such file or directory while trying to open /dev/mapper/root
/dev/mapper/root: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
``````
e2fsck: Device or resource busy while trying to open /dev/mapper/Me-root
Filesystem mounted or opened exclusively by another program?

```Does any of that mean anything to you?  Do you know why this has happened?  There are no documents on the USB so I'm tempted to just re-install, however the same thing has happened before both on my USB and my HDD.  I can't risk it happening when I actually have important documents on it.

Again thanks very much for your help.

---

### Post by TNT1 on 2010-10-07
I reckon the biggest issue is the USB2 transfer speed. USB3 wont fix that, as it wont really get off the ground. The new optical and e-Sata interfaces will see to that. Why can't you install direct to a HD?

---

### Post by Resist on 2010-10-07
I couple of reasons.  A USB would be nice as I could take it pretty much anywhere.  More so though, about security, if I have the USB on me then there's no chance government agencies can get hold of it (going through airport security etc).

I was hoping TrueCrypt would support creating a Ubuntu Hidden OS but it's only for Windows.

---

### Post by Herman on 2010-10-07
> I couple of reasons.  A USB would be nice as I could take it pretty much  anywhere.  More so though, about security, if I have the USB on me then  there's no chance government agencies can get hold of it (going through  airport security etc). I don't want to keep helping you if you're planning on doing anything illegal, sorry.

---

### Post by Resist on 2010-10-08
I'm not doing anything illegal, it's just about personal privacy.  What gives anyone the right to give up your password and look through your personal files?

---

### Post by Ahava591 on 2010-10-08
> **Resist said:**
> I'm not doing anything illegal, it's just about personal privacy.  What gives anyone the right to give up your password and look through your personal files?
Mostly criminal activity you are alleged to have conducted, or criminal activity you are suspected of conducting.

i.e.,  the exact same thing that affords the right to search your car or house. 

If you want to debate the issue, take it to the community cafe' section of the forum.

---

### Post by TNT1 on 2010-10-08
> **Resist said:**
> I couple of reasons.  A USB would be nice as I could take it pretty much anywhere.  More so though, about security, if I have the USB on me then there's no chance government agencies can get hold of it (going through airport security etc).

I was hoping TrueCrypt would support creating a Ubuntu Hidden OS but it's only for Windows.

Well, then you're pretty much stuck with USB and the limitations of the usb2 transfer rate. Your alternative is a SSD with e-SATA or optical interface, although then your limitation is the hardware you plug it into...

---

### Post by Resist on 2010-10-09
I don't want a debate here, I just wanted some help with the problems I was having.  Herman, thanks very much for your help.

@TNT1 I'll look into SSD and e-SATA, however as I'm using a laptop, I don't know if that is possible.

---

### Post by P4man on 2010-10-09
USB interface isnt a bottleneck here. If you are getting 8Mb write speeds, it doesnt matter what interface its on (usb2, 3, esata, firewire). Its those sticks that are relatively slow. 

Btw, its not a great idea to do a full install on a USB stick. It will wear out really fast. A liveCD mounts the / as read only and that avoids lots of small writes that mean death to USB sticks with no or very primitive wear levelling.

OT: I can sympathise with your goal btw. You dont have to be a criminal or terrorist to be concerned about privacy (and corporate secrets!). A police officer cant search your house without court warrant. IMO some airport security guy has no business viewing and copying all my data without court warrant or proper cause. But opinions dont change the fact they have this right and if you encrypt the data, you will have to provide the keys when asked and you risk more trouble then having your data unsecured.

---

### Post by Resist on 2010-10-09
Thanks for your comments P4man.  I did worry about the wear to the drive but figured it would have some form of wear-levelling.  So you reckon LiveCD would be better?  Maybe I'll give that a go soon.

---

### Post by P4man on 2010-10-09
Ive been told newer highend sticks have better wear levelling, but Im not convinced. Ive been through far too many USB sticks, including not so cheap sandisks. Id definitely prefer a persistent live session instead, even though its considerably slower to boot. Ideally there'd be something inbetween, a live session but with a  kernel thats already uncompressed. Im sure someone somewhere made something like that already.

---

### Post by C.S.Cameron on 2010-10-09
[http://www.afterdawn.com/news/article.cfm/2010/10/08/man_jailed_for_refusing_to_give_police_decryption_key_for_computer](http://www.afterdawn.com/news/article.cfm/2010/10/08/man_jailed_for_refusing_to_give_police_decryption_key_for_computer)

---

### Post by Resist on 2010-10-10
> **P4man said:**
> Ive been told newer highend sticks have better wear levelling, but Im not convinced. Ive been through far too many USB sticks, including not so cheap sandisks. Id definitely prefer a persistent live session instead, even though its considerably slower to boot. Ideally there'd be something inbetween, a live session but with a  kernel thats already uncompressed. Im sure someone somewhere made something like that already.

Roughly how long do you think it would take to wear a USB stick down then?  When running a full version of Ubuntu.

---

### Post by Resist on 2010-10-10
> **C.S.Cameron said:**
> [http://www.afterdawn.com/news/article.cfm/2010/10/08/man_jailed_for_refusing_to_give_police_decryption_key_for_computer](http://www.afterdawn.com/news/article.cfm/2010/10/08/man_jailed_for_refusing_to_give_police_decryption_key_for_computer)

Yeah I've seen that, hence why having a USB OS would be best.

---

### Post by C.S.Cameron on 2010-10-10
> **Resist said:**
> Roughly how long do you think it would take to wear a USB stick down then?  When running a full version of Ubuntu.

I think that this is one for myth busters.
I have only read one letter claiming that running Ubuntu has actually bricked the writers flash drive and that writer did not sound like he knew what he was writing about.

Do the math:
A flash drive is good for over 10000 writes.
At 1.5MBS write speed it takes 11 minutes per gig or 3 hours to fill a 16GB drive.
3 hours x 10000 = 30000 hours.
This would be equivalent to 3750 eight hour work days or 750 work weeks.

I have never had a mechanical drive last that long.

---

### Post by P4man on 2010-10-10
> **C.S.Cameron said:**
> 
Do the math:
A flash drive is good for over 10000 writes.
At 1.5MBS write speed it takes 11 minutes per gig or 3 hours to fill a 16GB drive.
3 hours x 10000 = 30000 hours.
This would be equivalent to 3750 eight hour work days or 750 work weeks.
.

You are assuming perfect wear levelling on an empty drive. I fear reality is rather different, the USB stick will be nearly full and the writes wont be spread perfectly, if *at all* on a cheap stick. We are not talking about SSDs here.

I can send you 6 USB sticks that have IO errors that where not abused other than using them. By your logic that would have taken me a few decades, but the oldest one is maybe 3 years old.

---

### Post by C.S.Cameron on 2010-10-10
> **P4man said:**
> You are assuming perfect wear levelling on an empty drive. I fear reality is rather different, the USB stick will be nearly full and the writes wont be spread perfectly, if *at all* on a cheap stick. We are not talking about SSDs here.

I can send you 6 USB sticks that have IO errors that where not abused other than using them. By your logic that would have taken me a few decades, but the oldest one is maybe 3 years old.

Sure send me your old drives, could I have the guarantee cards as well?
It's my understanding that wear is spread out pretty well over the disk.
I've been running Ubuntu from flash drives for over three years with out problem.
I have bricked a few flash drives and memory sticks, but this was due to yanking them while running and formatting multi partition flash drives in Windows, (twice), and a few others for no apparent reason.
It could also be the make of flash drive, I have had really good reliability with Kingstone and really bad luck with Transcend, bricking two of their flash drives and two of their memory sticks.
Have you tried using the guarantee that came with your failed drives?
I just got an old 8GB drive replaced.


See also:
[http://ubuntuforums.org/showthread.php?t=805596&highlight=usb&page=3](http://ubuntuforums.org/showthread.php?t=805596&highlight=usb&page=3)

---

### Post by P4man on 2010-10-10
I can barely remember the last time I had to pay for an USB stick. We have closets full at work (for a reason), you get them at every fair or convention. 

Yes, those are cheap sticks, and maybe high end ones fair better, but one of the few I bought in recent years, a not so cheap sandisk cruzer 8GB didnt live longer than 2 years either with very modest use.

Anyway, here is what I do with my piles of sticks:

[[IMG]http://img63.imageshack.us/img63/2804/sdc10334o.th.jpg[/IMG]](http://img63.imageshack.us/i/sdc10334o.jpg/)
[/URL]

Indeed, build raid arrays :)

BTW, all those sticks tested ok individually. Installed ubuntu on a raid 10, one stick failed in a matter of days.

In my experience these sticks are barely more reliable than 3.25 inch floppies once upon a time.

---

