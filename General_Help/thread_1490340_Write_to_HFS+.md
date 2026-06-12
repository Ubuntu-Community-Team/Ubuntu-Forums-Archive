---
title: "Write to HFS+"
date: 2010-05-22
forum: General Help
---

### Post by lancerocke on 2010-05-22
the error i get```
danny@danny-desktop:~$ sudo mount -t hfsplus -o "rw" /dev/sda1 /media/mac_os_xdanny@danny-desktop:~$ sudo rm /media/mac_os_x/Extra/Themes/Default/background.png
rm: cannot remove `/media/mac_os_x/Extra/Themes/Default/background.png': Read-only file system
danny@danny-desktop:~$ 

```thanks in advance for any help

---

### Post by srs5694 on 2010-05-22
Chances are the filesystem is journaled. Linux's HFS+ support is read/write only for non-journaled HFS+. I believe there's some way to force the issue via a mount option or an additional command, but I don't recall the details. Alternatively, you could try disabling the journal in OS X and then try again in Linux. I'm afraid I also don't recall the command to disable the journal from OS X. Perhaps a Web search will turn up an appropriate command, now that you know it's related to the journal.

---

### Post by timbosity on 2010-07-05
I've been wondering about this issue (writing to journaled hfs+ from ubuntu) for a while because I have a back up disk drive for my imac that I've increasingly used as a transferer of data from imac -> ubuntu pc and would now in fact much appreciate the ability to go back and forth between systems via this drive. I see that the solution is apparently out there ([ubuntu brainstorm]("http://brainstorm.ubuntu.com/idea/5878/")) but I have not been successful.

Anyone with any experience with the hfsplus/hfsplusutils packages in the repositories at getting writing support for journaled hfs+ formatted disks?

---

### Post by bumanie on 2010-07-05
There is a command line tool in ubuntu hfsutils. Also, I traced this through the puppy linux forum, a beta driver to allow read/write to hfs+ from linux - beware, it says to use at own risk as it is (or was) still in beta). Here's the [link]("http://www.ardistech.com/hfsplus/") if anyone wants to try it, I can't as I don't own an Apple. Would be prudent to backup important stuff first.

---

### Post by timbosity on 2010-07-06
OK, fine thats what I came across, the hfsplus utils yoke that the ubuntu brainstorm folks have apparently used to implement writing to journaled hfs+ filesystems. Maybe I'm an idiot but I cant seem to find anywhere exactly how one goes about actually using the functionality in that driver to mount my hfs+ drive and read/write away. [This]("http://ubuntuforums.org/showthread.php?t=1488160") thread is more or less same topic and having tried the suggestion there (to force mount hfs+ drive) ```
mount -t hfsplus /dev/xxx /xxx/xxx -o force
``` I still cannot do the write thing:D

As for hfsutils as a command line tool, anyone with experience using it?

---

### Post by timbosity on 2010-07-07
anyone?

---

### Post by timbosity on 2010-07-07
Ok so, having disabled journaling from imac, I can now write fine to this drive, but on imac there appears to be a problem with reading the files I write from ubuntu. I understand its something about permissions?

Real shame about the journaling thing because I thought that it was possible...

---

### Post by lukewitmer on 2010-10-22
> **timbosity said:**
> Real shame about the journaling thing because I thought that it was possible...

@timbosity I'm in the same position. Did you get this figured out so that you can read and write successfully on both Mac and Ubuntu?
Even if you couldn't get it with journaling, I would appreciate hearing the specific steps you took to get it to work with HFS+ (NOT journaled), for successful and reliable read and write on both platforms to the same drive.

---

### Post by 4plaay on 2011-03-26
If you have disabled journaling and were able to write to the HFSplus drive in the past then the problem is caused by a failure of the drive to unmount properly. This may work if you've disabled journaling and haven't been able to write to it in the past but I have not tried.

Make sure you've added the hfsprogs package in synaptic then go to terminal and run the following.

sudo fsck.hfsplus /dev/sdaX
sudo mkdir /media/XXXX
sudo mount -t hfsplus -o "rw" /dev/sdaX /media/XXXX

Of course replace the X's with whatever fits your computer. If your unsure what your device is under run before hand. Also make sure the drive isn't mounted before trying to do any of this.

sudo fisk -l

---

### Post by TechGeekT on 2013-04-02
For anyone who has the problem on Mountain Lion

I followed instructions from [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) to install Ubuntu without the need for hybridMBR (I've learned my lesson). I must I completely forgot but GOD put in mind to check the install instructions for rEFInd [http://www.rodsbooks.com/refind/installing.html#installsh](http://www.rodsbooks.com/refind/installing.html#installsh). Going back I realized I completely forgot to "bless" the drive. Which was more than completely important. I thought the idea od partioning the drive to share data between Mac and Linux was a great idea. Now to save you the trouble this is what I did with GOD, google, and some knowledgeable people out there. In mountain lion I had no choice but to choose FAT, exFat, or between two journaled choices. I choose journaled since it seemed easiest to work with. I followed instructions I had found to disable journaling the changed the permissions. The easiest I found is to:
On the Mac side of course:
Open Disk Ultity
Select the drive
Press and hold down the Option key then select File
Then the Disable Journaling option should be available to select

After that change the permissions which I found [http://www.makeuseof.com/answers/change-read-permision-external-hard-drive-mac/](http://www.makeuseof.com/answers/change-read-permision-external-hard-drive-mac/).

I thank The Lord for guiding me through. I now finally can read and write on both sides. ;-) YAY!!!!!

---

### Post by oldos2er on 2013-04-02
Closed, please don't bump old threads.

---

