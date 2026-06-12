---
title: "Unable to delete certain file from wastebasket"
date: 2011-02-23
forum: General Help
---

### Post by AgentY on 2011-02-23
Hi all. I've tried various suggestions on previous posts with no luck so I thought I'd try ask specifically for my problem:

I have a problem deleting a certian file from a NTFS format 1TB USB HDD.

I attempted to MOVE the file (x.avi) to another directory on the same drive. On the MOVE process I accidently cancelled it. I then COPIED the file to another directory, this copied fine so i just need to delete the original x.avi.
(note; when I now attempt to move the original x.avi I get an error message:
   "Error while moving "x.avi". There was an error moving the file into /media/1TB/Movies.
     More details: Error moving file: Numerical result out of range. (I'm assuming a corrupted file)?

Lastly, every time i attempt to delete x.avi, it puts the file in the wastebasket but doesnt delete it; Every delete attempt makes a new file in the wastebasket (e.g. x, x.1, x.2, x.3, x.5 etc etc).

All other files/folders are fine its just this 1 folder/file.

Any help grealty appreciated as it's annoyed me most of the evening now!


Thanks.

---

### Post by jwcalla on 2011-02-23
Have you tried manually deleting it from ~/.local/share/Trash/files/ and ~/.local/share/Trash/info/?

Oops I see the wastebasket is ok, you want to delete it from the USB drive.  Have you tried using the command line to delete it?

---

### Post by AgentY on 2011-02-23
> **jwcalla said:**
> Have you tried manually deleting it from ~/.local/share/Trash/files/ and ~/.local/share/Trash/info/?

Oops I see the wastebasket is ok, you want to delete it from the USB drive.  Have you tried using the command line to delete it?

I haven't yet but thanks for the suggestion. I'm still trying to delete the original x.avi file before I get to the trash issue. I'm running a chkdsk in windows now and seeing how that turns out.

---

### Post by jwcalla on 2011-02-23
Can you delete it in Windows?

---

### Post by doas777 on 2011-02-23
one caution, before you proceed further.
if you copy a file from one location to another** on the same partition, **the system just adds a new file reference (in unix they are called "inodes", in windows "MFT entries") in the new folder which points to the existing files data. the file data however is not duplicated. a move (between locations on the same partition) creates a new inode pointing to the new file data, and deletes the existing inode. 

if this scenario matches yours, then it is possible that as your methods get more exotic, that if you do delete the old copy, you may end up deleting the file data from your archived copy as well. since your hdd appears confused regarding this file, caution is warrented, so I would backup the file off to some other partition before going too much further.

after that, you may want to try chkdsk in windows to see if your filesystem needs some repair.

---

### Post by whatthefunk on 2011-02-23
Reformat the harddrive.

---

### Post by AgentY on 2011-02-23
Thnks doas777, I'll backup the file to another drive before I go any further.

---

### Post by AgentY on 2011-02-23
Chkdsk /f found an error and 'fixed' it. The avi is now gone and the Trash folder is also empty. The only problem now is i can't delete the empty folder via Ubuntu nor Windows. Both OS's state the file/folder is corrupt. Is there a terminal command which would force deltetion of the empty folder? Or any other suggestions? Thanks.

---

### Post by doas777 on 2011-02-23
> **AgentY said:**
> Chkdsk /f found an error and 'fixed' it. The avi is now gone and the Trash folder is also empty. The only problem now is i can't delete the empty folder via Ubuntu nor Windows. Both OS's state the file/folder is corrupt. Is there a terminal command which would force deltetion of the empty folder? Or any other suggestions? Thanks.

well, here is the ms support page on the topic:
[http://support.microsoft.com/kb/320081](http://support.microsoft.com/kb/320081)

they seem to recommend that if chkdisk doesn;t work, that backing up to other media and reformatting the drive is indicated. there are some other ideas in the kb article however.

---

### Post by AgentY on 2011-02-23
I read the ms support site before I posted here but thanks. In the end i erased the parent directory where the corrupted files were via command prompt which solved the problem. Thanks for all replies.

---

