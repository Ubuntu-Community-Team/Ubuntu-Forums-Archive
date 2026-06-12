---
title: "Beginner questions: next step in disk recovery?"
date: 2012-01-16
forum: General Help
---

### Post by gmwhite999 on 2012-01-16
Hello,
 
I'm a novice at disk recovery so have been trying to follow advice on forums such as this, but can't get any further. Can any one advise me what to do or try next.
 
I have a Windows Vista desktop with a 160Gb boot disk and a 1TB storage disk (with one solo partition which was about two-thirds full). Shortly after new year, the storage disk failed: Windows recognised a disk in the Windows Explorer listings but was unable to access it.
 
A more-technically minded friend suggested booting up in Ubuntu and looking at the disk that way, so I downloaded and burnt an Ubuntu 11.10 boot disk and booted the desktop from that. Through Ubuntu I could see the disk and it showed the correct "name" label I had given it, but I could not mount or look at the disk.
 
I acquired a new 1.5 TB external hard drive and using the Ubuntu disk and trying to follow the Ubuntu Data Recovery guide below, I used ddrescue to create a 1 TB image of my poorly storage disk and stored it onto my new external hard disk. This process took a few days to do and I cancelled it after it spent two or so days retrying bad sectors.
 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
 
I then started looking at foremost, ran an audit through it and got log files and screen messages showing files names I had expected to see, suggesting at least part of the image was salvagable. I know that at the moment I don't have the disk space to do a full restore through foremost (and am not sure whether such a restore would preserve the file names or directory structure I had in place on that faulty disk) so started surfing around for other approaches.
 
One of them suggested below was to use P2 eXplorer to look at the image and try to extract/copy the files out that way.
 
[http://www.myfixlog.com/fix.php?fid=21](http://www.myfixlog.com/fix.php?fid=21)
 
This approach is currently proving problematic: I can't get P2 eXplorer to install on my desktop but it does install on my Windows Vista laptop. I then plug my external drive with the image on to the laptop, which P2 eXplorer finds and mounts but then returns an error "Cant get disk info. Media is write protected". Naturally it appears through Windows (looking both from my laptop and from the desktop) that the image file and directory structure has Full Control permissions for Everyone, yet looking at it through Ubuntu terminals it appears only to have Read/Write access to the owner (the user Ubuntu).
 
So, can anyone advise me as to what I should do or try next to examine and recover from this image file?
 
Regards,
Confused, near Alicante

---

### Post by oldfred on 2012-01-16
Did you run chkdsk on the failed partition/drive? And you have to rerun chkdsk until there are no errors as it does not fix everything on one pass.

Ubuntu runs its fsck every 40-60 boots but Windows does not, and seems to never run chkdsk on a second drive/partition unless you manually do it.

I have used photorec to recover data, but it does not recover file names just extensions. Often Ubuntu will not mount a NTFS partition that needs chkdsk to prevent further damage that then chkdsk may not be able to fix. Sometimes testdisk will show the entire partition and let you copy all the  data.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Some here have recommended Windows recovery software also, but I have not saved links. I would not mix Linux & Windows repair tools.

---

### Post by gmwhite999 on 2012-01-16
Oldfred,
 
Thanks for your suggestions.
 
I cannot run chkdsk through Windows on the failed drive.  I did try through the command shell but it keep freezing while checking file sectors, at something like 299,000 into 335,000 or so.  While running that is when I read about not running chkdsk on the disk but to create an image of it, after which I got into reading about Ubuntu and ddrescue.
 
Should I attempt to run a chkdsk (windows vista or command prompt) on the disk image (alone or on the drive it sits on) and will that help?
 
Photorec is a latter stage attempt as ideally I don't want to have to rename the file names and directory structures, especially when the image audits where giving me expected file names back. TestDisk might be an option - if/when I am ready to try it and my image is ready for it.
 
If I continue down this P2 eXplorer route, I still can't fathom what is up with this file permission problem with the image file.  Each new article or forum post I read on NTFS and UNIX permissions only seems to confuse me further.
 
Or - going back to using Linux only tools - do I need to mount the disk image before running something like fsck or e2fsck?  I was having trouble creating any new mounts so either I had the syntax wrong or had the wrong permissions, or was trying to create the mount in the wrong place, or from the wrong source folder/file.  Can I just run fsck/e2fsck on the image itself, and if so with which flags?
 
Regards,
Confused

---

### Post by oldfred on 2012-01-16
Linux fsck is only for ext2, ext3 or ext4 formats. It will not run on NTFS. You have to run chkdsk on NTFS or FAT from Windows.

Normally the automount works from the file browser, Nautilus. But if chkdsk is needed it may not mount at all. And yes chkdsk can take many hours especially on a large partition.

I think testdisk mounts anyway.

With manual mounting you have to set permissions and ownership as part of the mount command as NTFS does not support those settings. So all you get is one default. It will often show as root but if set correctly you can read & write without issue.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by gmwhite999 on 2012-01-18
All,
 

An update.

 
I found Wondershare Data Recovery as directed to by another site, and considered using Data Doctor Recovery too. Using Wondershare on the drive which contains my image file, it successfully found and listed almost all of the files I had expected on the image and in the expected directories too with a few missing directories. I then tried to do an extract of a small sample set - small jpg and txt files covering a variety of directory trees and Excellent to Bad statuses, but none of the files were successfully restored. None of the jpg files were viewable in the standard Windows packages or Photoshop, and the txt files were all garbled (almost seeming encrypted) with all sorts of funny characters showing.

 
Any ideas from here?

 
I am currently trying a small extract from the image using testdisk/photorec back in Ubuntu to see what that reveals.

 
Should I have stored the original disk image file on its own disk or partition though, rather than as a normal file on a larger disk which already had some files on it? Would that have made a difference to how a recovery package/tool finds and receovers the content of the files?

 
Regards,
Still Confused

---

### Post by oldfred on 2012-01-18
I just lost files & most were just text files. Photorec found the text files, but I have saved some of them many times. Photorec found all the old saved versions and some text files were they must have been saved next to each other. It took a while to sort thru, not sure I every found the final file but found quite a bit. 

With Photos any corruption causes issues.

I just recovered from one drive to another and did not worry too much about an image backup as I did have backups, just not current ones.

---

