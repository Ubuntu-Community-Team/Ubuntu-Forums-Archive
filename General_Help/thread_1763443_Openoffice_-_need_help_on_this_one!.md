---
title: "Openoffice - need help on this one!"
date: 2011-05-20
forum: General Help
---

### Post by Quarkrad on 2011-05-20
My wife had 10.04 and there was no problem using openoffice to open ods spreadsheets - specifically via **File/Recent Documents**.  Last week I upgraded to 10.10 (to make samba easier between her machine and mine - now both run 10.10) and there is a problem with openoffice. (note.  I changed the default path in openoffice for opening/saving docs to her directory as per the 10.04 setup).  What happens now is if you open a ods spreadsheet, work on it and close it down - you cannot open it again next time via **file/recent documents**.  If you switch off the pc and on again, launch ooo the document is listed under **recent documents** but you cannot open the doc - a window comes up saying the document or path does not exist.  You can open the doc if you go via **file/open**.  I kept 10.10 and decided to change to Libreoffice, exactly the same thing! The file(s) exist so it must be the path - but why do I have this problem with 10.10 whereas it wasn't there in 10.04?

---

### Post by grahammechanical on 2011-05-20
Where are these documents stored? On the hard disc in your wife's machine or on the hard disc in your machine?

I have different versions of Ubuntu on different partitions. Openoffice/Libreoffice on partition B is not able to open documents stored on partition A (where the documents actually are stored) until I mount that partition by using Nautilus to browse the partition. I do not know if this will help.

Regards.

---

### Post by Quarkrad on 2011-05-20
Thanks - the documents are all on my wife's machine, samba was for something else.  The docs are on a difference partition (sda5/ext4) to ooo (sda1/ext4) but I have set it up so all partitions are mounted automatically on boot.

---

### Post by AlphaLexman on 2011-05-20
I believe the files in 'File -> Recent Documents' are just a link to the path/filename. If you rename the path or move the file, you will break the link.

Check 'Tools -> Options -> OpenOffice.org -> Paths - > My Documents' and make sure the default location matches the location of her files.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Try upgrading to LibreOffice

---

### Post by linuxinstalledfromhdd on 2011-05-20
The LibreOffice PPA installation instructions are about half the way down the list:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Quarkrad on 2011-05-20
I'm using the latest version of Libreoffice from the reps and I have changed the default path location in Libreoffice (and previously in ooo) to where her files are. E.g. I have set her default location (on sda5) within Libreoffice to **test/documents**.  In **test/documents** there many other folders, if, in Libreoffice, we go file/open  *(this will open test/documents)* finance/money.ods  we open the spreadsheet money.ods  (test/documents/finance/money.ods).  The next time we switch on money.ods appears in the Recent Documents list, but if you click on it you get the message that the path or document does not exist.   I have not changed anything from 10.04 - everything appears to be exactly the same including the default path within ooo/Libreoffice.

---

### Post by Hagar Delest on 2011-05-20
You can try to install the vanilla version (both LibO and OOo can run in parallel), but not really sure it would help: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by AlphaLexman on 2011-05-20
Try using a terminal,
```
oocalc test/documents/finance/money.ods
```
and post **ANY** output or errors you get.

---

### Post by Quarkrad on 2011-05-21
Opening via the terminal did not work - file still does not exist.  However, I think I have found out the problem but do not know how to solve it - perhaps a re-install of 10.10 but that seems a bit over-the-top, or I go back to 10.04?

The issue seems to be when I go **Tools/Options/Libreoffice/Paths** and change the path of **My Documents**  (the new path is another ext4 partition (sda5) on my HD - **not** the partition (sda1) where libreoffice/ubuntu is installed). I can go **file/open** and I'm presented with options in my preferred (sda5) folder set - from here I can choose a specific folder and open a file.  If I close down I can relaunch libreoffice and open the previous file via **file/recent documents** - all is working fine.  The problem seems to be when I switch the PC off/on, if I launch libreoffice and look at **Tools/Options/Libreoffice/Path** I see my preferred sda5 folder setting.  However, if I go **file/open** the list I'm presented with is not my sda5 preferred list as shown in **Tools/Options/Libreoffice/Path** but something different.  So although **Tools/Options/Libreoffice/Path** shows the right path it appears to have changed 'in the background' to something different.  This would explain why **file/recent documents** cannot find the file.   On my machine (10.10) this does not happen but on my wife's it didn't using 10.04 but does in 10.10 using both ooo and libreoffice.  I tried another folder on sda5 as the default path but I get the same problem - although I set the default path to /media/aaa/bbb/ccc it looks like it cannot maintain this and changes to /media/.  When I go **file/open** I'm at /media/ and get the choice to open two folders, floppy0 or floppy - I should be at /media/aaa/bbb/ccc that I set (and shows) in **Tools/Options/Libreoffice/Path**.

---

### Post by grahammechanical on 2011-05-21
I have just repeated your experiment. This is what I noticed. File> Recent documents will list an previously opened file on another partition as being in the folder media/ and it remembers that when you open and shut Libreoffice but shutdown and reboot the computer and even though the location is in File>Recent Documents it cannot open the file.

This is because the file is not in /media. There are only the two folders in media called floppy0 and floppy1 as you noticed. The files/documents are actually in the home folder under the username. In my case the path to one document is /home/graham/Documents. But Libreoffice File>Properties gives the path as /media/some numbers representing the partition ID/home/graham/Documents.

Could it be that when you set the default path you are not including the ID of the partition? I think that when you open the document in Libreoffice which is on sda1 it creates a link in the /media folder on sda1 to the location of the document on sda5. This setting remains whilst the OS is running but is lost when you shutdown and reboot. I think that Libreoffice is still looking in sda1 /media/ folder for the link to the actual location of the document.

Little bit of clarity, may be, but not a solution. I am sorry.

Regards.

P.S. I have not tried this because I do not want to mess up my Libreoffice but, when you set the path try leaving out the reference to /media. Keep the ID of the partition. I wonder if it is possible to set multiple paths for Libreoffice to search for documents. Like giving it a list of locations to search. First /home/user/documents, then /ID partition1/home/user/documents and next /ID partiton2/home/user/documents. As I say. I do not wish to experiment.

Regard again. I hope this gets solved.

---

### Post by Quarkrad on 2011-05-21
Thanks for trying to help.  What I have is Ubuntu and apps (inc Libreoffice) on sda1 that is ext4.   I have another ext4 partition where I keep all my documents (spreadsheets, letters, etc).  So in effect when I launch Libreoffice on sda1 it is looking at and loading/saving files from sda5 (obviously via RAM).  I do not have any user files on sda1.  I will look at what you say about the partition ID - but, as a newbie, I set the **Path** within Libreoffice via it's GUI, so when it comes to selecting the Default Path via **Tools/Options/Paths/My Documents/Edit** I choose from the GUI nautilus type window that comes up.  Are you suggesting/is there a way, of entering the partition UUID (similar to fstab) in the My Documents field within Libreoffie?

---

### Post by grahammechanical on 2011-05-21
Libreoffice allows you to edit the path. I know that you have tried this. I am thinking that if the path was /media/partition UUID/documents folder/ then Libreoffice will look in the media folder on sda1 for a link that will direct Libreoffice to the documents folder on sda5. I am thinking that this link in the /media folder only exists until you reboot the computer. Let us use my computer as an example.

Libreoffice is on sda1 and all my documents are in the home folder (this is a separate partition, but lets us not confuse things even further). The Libreoffice path is /home/graham/Documents.

I open a document on sda5 and Libreoffice File Properties lists the path as

> /media/5850813d-ef57-4157-adec-9b3d5ffaa5oc/home/graham/DocumentsI am wondering if it is possible to set the path in Libreoffice to (A):

> /5850813d-ef57-4157-adec-9b3d5ffaa5oc/home/graham/Documentsomitting the /media bit. Or even (B):

> /home/graham/Documents /media/5850813d-ef57-4157-adec-9b3d5ffaa5oc/home/graham/DocumentsThere would need to be some kind of separator such as a comma or semicolon. What kind I do not know. But if this path could be set up then Libreoffice would know that there were documents in /home/graham/Documents on the partition that Libreoffice is running from and also on sda5 under /home/graham/Documents.

Incidently, If boot into Ubuntu on the sda5 partition and load Libreoffice on that partition and open the test document, then File Properties will list the file in /home/graham/Documents. which is where it actually is on sda5.

So, I am tempting you to set the Path in Libreoffice Tools>Options>Paths without the /media bit but starting with the relevant partition UUID.

I always try to work using a GUI. I do not want to spend my time and limited brain power studying commands.

Regards.

P.S. I have just checked my /media folder and there are links (folders) to the other partitions that I have loaded Libreoffice documents from. If I shutdown and reboot those folders will disappear and there will only be folders for floppy0 and floppy1. As we know. And Libreoffice will not be able to find the files on those other partitions.

---

### Post by Quarkrad on 2011-05-21
graham - I think you are right.  But I do not know how to manually edit the path name in Libreoffice.  Just spent the last hr googling trying to find out how to/if you can manually set the path name.  Do you know how to do this?

---

### Post by grahammechanical on 2011-05-21
I am sorry. I thought that you were more experienced than I at doing this. I have never tried it and I get scared that I might break things. I sometimes do.

Go to Tools>Options and select Paths. Select My Documents. The complete line should become highlighted. Click Edit and a Select Path Dialog box will appear. In the left side panel do you see something like 10GB File System? This is what I see. Your sda5 partition will be a different size. You are trying to select the File system that represents the sda5 partition. When you click on that file system a list of folders will appear in the central panel. Click on home and then the user name folder and then the folder with the documents in. That might do it.

Regards.

P.S. It just occurs to me that I see the words File System because I have installed versions of Ubuntu on those partitions. You might not see the words file system. You should see something representing the sda5 partition and then see the folders on that partition. Browse to the correct folder just like using a file browser.

P.P.S. I have just tried it myself and the thing puts the /media bit in front of the rest. Which is what we do not want. Sorry if this fails.

---

### Post by Quarkrad on 2011-05-21
Ok - I believe I'm doing this, perhaps I need to get more specific.  In nautilus the location of the file I'm referring to is:

/media/HomeFiles/Home/LIZ/Finance/Spending by month 1112/2 Spending by month May 2011.ods

where HomeFiles is the name/label given to /dev/sda5.  So, as a newbie, I think possible locations could be:

/media/HomeFiles/Home/LIZ/Finance/Spending by month 1112/2 Spending by month May 2011.ods

or

/dev/sda5/Home/LIZ/Finance/Spending by month 1112/2 Spending by month May 2011.ods

or

ae207b6d-9c06-4865-b0a4-4f3f16f60e25*/Home/LIZ/Finance/Spending by month 1112/2 Spending by month May 2011.ods

* partition UUID

If you look at my default path for My Documents in Libreoffice (Tools/Options/Path) the entry is:

/media/HomeFiles/Home/LIZ

this is what I want because when my wife goes **file open** she is where all her files/folders are - within her LIZ folder on sda5.  It works when she creates a new file and goes **file save** - she is presented with her top level folder.  The problem is when she opens a file, e.g. 2 Spending by month May 2011.ods and then closes the pc down.  On restart under, libreoffice Recent Documents, you see at the top of the list  1:/media/Home...2 Spending by month May 2011.ods.  If you click on it a window pops up saying the file does not exist.  **File/open** and navigating to it manually opens it. As per 10.04 the default path for My Documents in Libreoffice **/media/HomeFiles/Home/LIZ** is the same - but for some reason I cannot open it via Recent Documents after a reboot.

note:  If I could start again I would change the folder / file names but my wife has spreadsheets that link together so changing the folder structure/naming is not an option.  All this worked like a dream from 8.04 to 10.04 - for some reason 10.10 does not like it.

---

### Post by marshag63 on 2011-05-21
Perhaps trying this might help:

[http://en.libreofficeforum.org/node/489](http://en.libreofficeforum.org/node/489)

MDG

---

### Post by Quarkrad on 2011-05-21
Thank you all - I appreciate the help.  Is it OK if I pick this up on Monday?  I have to go out now and I'm out all day tomorrow.  Much appreciated. I would be nice to get this working on 10.10 - going back to 10.04 seems a backwards step.

---

### Post by grahammechanical on 2011-05-21
I am turning my mind to the /media folder. I have just unmounted my sda5 partition (the one with the test document on it). And the folder representing the sda5 partition in /media is removed. This I think is what happens at shutdown. And which in turn is causing the problem you are having.

Are you absolutely certain the your sda5 partition is being mounted at boot time? You say that this happens and I accept your word for it. But as I do not know how to do this, I wonder if it really is happening. I think that we can eliminate Libreoffice not having the correct default path but it always directs to /media before going to the partition and its folders. I think that the issue is occurring because the partition is not mounted. What else could it be?

Tell me how do you fix things so that a partition mounts at boot up?

Regards.

P.S. I have found this link
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by marshag63 on 2011-05-21
Actually, disregard my other post about menus, I think post #10 here has some clues:  

[http://ubuntuforums.org/showthread.php?t=1454194](http://ubuntuforums.org/showthread.php?t=1454194)


MDG

---

### Post by AlphaLexman on 2011-05-21
I have to think you are barking up the wrong tree here...

In Linux one can have '/' mounted on one partition, and '/home' on a separate partition, and still '/var' could still be on another completely different partition, but by unix standards, they are all sub-directories of '/', so as long as all the partitions are mounted, the partitions are not the issue here.

I also don't think the problem is the UUID codes are not being translated into the mount paths. (That would occur in more application's than OOo)

I have to think the problem here is with either links, or the 'auto-mount' feature in fstab. 

You could have seventeen partitions mounted, and any program should be able to open, find or link to any file on any of those partitions. (Given the correct -rwx- permissions!)

---

### Post by Quarkrad on 2011-05-22
Managed to sneak a quick look before I went out.  Thank you all -YES it was the auto-mounting issue - I've configured it now and all is well.  I thought that as the partition was ext4 it would be automatically visible (mounted) - guess another good lesson for a newbie.  Many thanks, appreciated.

---

