---
title: "Recovering data from damaged WIN XP hard drive with Ubuntu Installation disk"
date: 2011-01-18
forum: General Help
---

### Post by Trent T on 2011-01-18
I have used this procedure to recover data twice from crashed Win XP hard drives-- These notes will help me remember what I did the next time it happens, and may help you too!

Materials:
1) External backup drive sufficient to hold your data, preformatted, empty, and clean of viruses.

2) Ubuntu Linux Installation Disk.

3) 1 Working CD/DVD drive on damaged computer.

4) Another working computer, connected to the internet.

Procedure:
1) On your working computer,
    Download .iso  disk image, and burn an Ubuntu Linux installation disk.
     [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

2) Boot your damaged computer from the Ubuntu Linux disk, (in the read-only or non-burner drive, if you have only one DVD burner).
     DO NOT INSTALL UBUNTU to your damaged computer.
     When you boot from the Ubuntu disk, you will have the option to run Ubuntu from the disk without changing the damaged computer hard drive.
     Run from the disk--
     You will eventually get to an orangey-brown desktop-- This is the Ubuntu desktop.

3)  Plug in your external backup drive.
      The drive will appear as an icon on your Ubuntu desktop.


4)  Mount the damaged hard drive.
      Ubuntu will not automatically let you look at your damaged hard drive;
      You have to give it permission to do so first.
      Click on "Places" (upper left corner of the screen),
       then "Computer."
       The column at the left will have a list of hard drives and other data storage devices.
       Some of the drives have an Up arrow with an underline, others do not.  
       The up arrow means that the drive is mounted, and you can look at it.
       Hard drives are also represented as icons in the middle of the window.

       Left click on the drive that you think is holding your data.  If not mounted, Ubuntu will ask you if you want to mount the drive. 
       Click 'yes' and the up arrow will appear next to the drive description in the column at the left.
      
       Click on the drive again.
       Navigate to 'Documents and Settings', then eventually to  'My documents'
       Resize your document browser window to half a screen or less.

5)    Select folders to copy.
        Hold [Control] down and left click all the folders you want to copy.
        Hit [Control] C to copy.

6)     Select your backup drive.
         Click the backup drive in the left column.  Find your target directory.
         Hit [Control] V to paste the files to your backup drive.

7)     If you suspect virus(es) or trojans...
         Windows viruses won't be able to work in a Linux environment-- But if you plug your backup drive into another WIN machine, they may infect it too.  If you have Linux experience, you may want to try ClamAv, a linux-based antivirus software, or possibly plug the drive into a Mac and disinfect it there.

8)     Shut down the damaged computer, and Load your data onto the next machine....
         IF you are sure it's virus/trojan-free

---

