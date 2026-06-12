---
title: "sudo umount /dev/cdrom &gt; sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc"
date: 2011-04-01
forum: General Help
---

### Post by kaisar89 on 2011-04-01
Hi,[COLOR=Red] How long does this process take (the 1s in the title - to backup dvd)[/COLOR]? Basically i quick formatted a dvd-rw which had holiday pics stupidly. And now i need to recover the data. I asked a user from this forum to help, he has given me some instructions, but im not to sure if they correct.

Can someone verify that the instructions are correct. TY

----------------------------------------------------------------------------------------------------------------------------------------

                                  **Re: Recover Data from quick formatted DVD-RW and +RW.....Please help!!!**             
                                                                Yes it is possible.

Install testdisk:

     Code:
     sudo apt-get install testdisk 
Before you run testdisk, you must first backup an image of the  DVD, in case your DVD gets damaged. To do so, you will need to insert  your DVD into the drive. Then make sure that it is unmounted like this:

     Code:
     sudo umount /dev/cdrom 
Now, you need to use the dd command to create backup image of the DVD like this:

     Code:
     sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc,noerror 
This will create a raw image file backup of your DVD. The raw  image file will be placed in your home directory, which is located in  (/home/yourname/). The file is called "backup.img". It is important that  you keep that file and not delete it until all pictures are recovered.  Your DVD can not be mounted when this is happening. Once the back-up  image is created, you can now start the recovery process.

Mount the cdrom again like this:

     Code:
     sudo mount /dev/cdrom 
Now, you need to create a directory to store all of the recovered files, so use terminal like this:

     Code:
     cd ~
mkdir dvdbackup
cd dvdbackup 
Then run:

     Code:
     sudo photorec 
This will show you a list of all your mounted disk/cd similar to this:

     Code:
     Disk /dev/sdb - 160 GB / 149 GiB (RO) - ATA ST3160812AS
Disk /dev/sr0 - 654 MB / 624 MiB (RO) - HL-DT-ST DVDRAM GE20LU10 
- Now, use the arrows to select the DVD/CD rom (/dev/sdr0 normally) and click on proceed.
- Select Intel and hit enter
- On the next screen select file Opt
- Make sure that all the options have an X in them. You can put an X using the space bar
- Then click b to save the settings
- Then click Q to go back
- Now select search
- It will ask you for the partition type, select other
- It will then ask you the following: Do you want to save recovered files in /home/yourname/dvdbackup ? [Y/N] Click Y
- and it will start the backup process
- The recovered files will be placed in different directories in /home/yourname/dvdbackup/recup_dir
- Please note that the file names will be changed, and directory  structure will be lost. But the files will be recovered nonetheless
- Once the recovery process is done, you will get a similar output to this:
     Code:
     191 files saved in /home/yourname/dvdbackup/recup_dir directory.
Recovery completed.
jpg: 191 recovered 
Of course, your output will be different. 

- Select quit and hit enter. Quit again and enter
- You can now open the file browser and browse to that directory: Click  on the Places menu - Home Folder, and find dvdbackup, double click it  and you should hopefully find all of your brother's pictures there.



let me know how things go..
                                                                                                                                    *                                              Last edited by newbuntuxx; 5 Days Ago at 04:13 PM..                                                           *

---

