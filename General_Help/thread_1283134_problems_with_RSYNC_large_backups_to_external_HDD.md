---
title: "problems with RSYNC large backups to external HDD"
date: 2009-10-05
forum: General Help
---

### Post by yanvolking on 2009-10-05
Hello Community,

I have decided to use RSYNC to backup my main multimedia collection (movies, music, photos etc..).  The total content is 350 GB and stored on an IOMEGA 1TB mains fed external HDD.  I bought a LACIE 500GB mains fed external HDD to copy the original content directory to.  I used the command :

  	 	 	 	 	 	   rsync --delete -av /media/"Iomega HDD"/ALL /media/LACIE/lacie_backup


At first all went well and I started to see the lines of copied files piling upwards.  After abouot an hour (the whole process of copying the 350GB takes about 12 hours) the process stopped.  Below is a section of the last few lines before everything stopped:


   	 	 	 	 	 	  ALL/FILMS/BMORN/UFO/1-12 -- UFO ~ Court Martial.avi  
 ALL/FILMS/BMORN/V.For.Vendetta[2005]DvDrip[Eng]-aXXo/Thumbs.db 
 ALL/FILMS/BMORN/V.For.Vendetta[2005]DvDrip[Eng]-aXXo/V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi 
 rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)  
 rsync: write failed on "/media/LACIE/lacie_backup/ALL/FILMS/BMORN/V.For.Vendetta[2005]DvDrip[Eng]-aXXo/V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi": Input/output error (5)  
 rsync error: error in file IO (code 11) at receiver.c(298) [receiver=3.0.3]  
 rsync: connection unexpectedly closed (4227 bytes received so far) [sender]  
 rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]  
 y
 
 
In the end the destination HDD unmounted itself and it became impossible to remount it.  Even shutting down the computer the destination HDD couold not be mounted anymore.  Nevertheless it worked fine on Windows where I could access freely the copied files.  But to resume the RSYNC operation, I had to reformat the HDD and start from scratch.  Now I RSYNC in stretches of about 1 hour at a time.  Shut down the computer for half an hour then resume the command.  I have about another 2 1 hour sessions to complete the operation and I'm nervous.

Does anyone know why I have problems like this in UBUNTU whilst the same harware works fine in Winfows.  The same LACIE HDD successfully performs the full 12 hour backup operation with Windows Backup without the slightest Hitch.  Note that the LACIE HDD is formated using windows in NTFS.  Also the information on the box of the LACIE says it is compatible with Windows and Mac OS, but says nothing about linux.  

I am lost and worried and any information or suggestions would be welcome.

yanvolking

---

