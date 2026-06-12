---
title: "Help please! i think somethings wrong with computer. ubuntu 10.10"
date: 2011-03-30
forum: General Help
---

### Post by kaisar89 on 2011-03-30
Hi,  				**Recover Data from quick formatted DVD-RW and +RW.....Please help!!!** [http://ubuntuforums.org/showthread.php?t=1715042](http://ubuntuforums.org/showthread.php?t=1715042) 

Im following the tutorial given to by another user, im not to  sure if im carrying out the process correctly. So far its taken 2 hours and still going  to make images of the disc which im trying to recover lost data from. should this  happen or have i done something wrong? 

0+0 records in 
0+0 records out
0 bytes (0 B) copied **[COLOR=Red]7405.22 s,[/COLOR]** 0.0 k/Bs
dd: reading '/dev/cdrom': input/output error

1110 s and still counting

Same script is continuing with number increasing each time. What is happening? Could someone please explain.

Thank You..



Quote:
 	 	 		 			 				 					Originally Posted by **newbuntuxx** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10603329#post10603329") 				
 				[I]Yes it is possible.

Install testdisk:

 	Code:
 	sudo apt-get install testdisk 
Before you run testdisk, you must first backup an image of the  DVD, in case your DVD gets damaged. To do so, you will need to insert  your DVD into the drive. Then make sure that it is unmounted like this:

 	Code:
 	sudo umount /dev/cdrom 
Now, you need to use the dd command to create backup image of the DVD like this:

 	Code:
 	sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc,noerror 
This will create a raw image file backup of your DVD. The raw  image file will be placed in your home directory, which is located in  (/home/yourname/). The file is called "backup.img". It is important that  you keep that file and not delete it until all pictures are recovered.  Your DVD can not be mounted when this is happening. Once the back-up  image is created, you can now start the recovery process.[/I]
 			 		 	 	 
[http://ubuntuforums.org/showthread.php?t=1715042](http://ubuntuforums.org/showthread.php?t=1715042)

---

