---
title: "Deleting the ubuntu"
date: 2010-08-11
forum: General Help
---

### Post by capsaicin on 2010-08-11
I know that ubuntu is much better than the xp but i play a lot of game and i cant play any game in ubuntu.
So i have tried to install my xp again. Deleted partition which includes the ubuntu. It looked like worked but at the second boot xp didnt start the graphich installer.
 There was already a 8 mb free space on the disk and when i make a new partition it makes another 8 mb free space.
 I have important data in my other partition and cant delete it.
How can i install xp again ?

---

### Post by Phil Stone on 2010-09-07
capsaicin,

You dont want to lose your important data so you will need to treat your drive as a storage disk. I do not know enough about partitions to understand what is causing your problem but if you ever 're-installed' your Ready To Go OS (RTG OS) then this is the same sort of approach but adapted.

You will need: Another disk,   sata cable Or ide cable & Jumpers. Suggested item is a good book such as Eye of the World by Robert Jordan.

1. remove your current experimental disk (dual boot) from the motherboard
2. attach your new disk to the motherboard
3. install your RTG OS onto the new disk. 
4. boot your RTG OS up make sure it is working then shut down. 
5. Attach your storage disk as secondary disk to the motherboard or via ide cable.
 i. If you have Sata you are probably not going to have many problems
ii. 0x0.If you are using IDE cables you may need to set the jumpers so that the xp disk is the master and the dual boot is the slave. If needs be you can look this up once you have installed your xp, basically if the system doesn't start up properly you will need to set the jumpers back to the default, so before you attempt '5' note where they are to begin with when only the working primary disk is attached (by drawing on a piece of paper!)
ii. 0x1. in extreme circumstances you may need to set your boot priority in BIOS as well as this woks along side the master slave jumper thing. this is where you will have noted the disk names down when in disk manager usually look something like XFS-yu87ay7

6. Once you have booted up your RTG OS disk and can see the secondary disk in your RTG OS File System PC folder, this should be the dual boot and remember just because it boots doesn't mean it will see the disk, try those jumpers again! 
7. Grab your data from the storage disk onto the xp disk.

So now you have a primary disk with your RTG OS and important data on it.
And a secondary 'experimental' disk.

you can either format the secondary disk to NTFS and backup your important data
and try again with dual boot on the primary disk. Or maybe you will create a dual boot with two disks installing the linux on the secondary disk and keep the primary as the storage.

Whatever you do keep important data out of the way of experimental OS situations and you will remain a happy wizard. 

Hope this helps you and anyone who is experiencing dual boot dilemmas

Phil

---

### Post by uRock on 2010-09-07
Insert the **[COLOR=Sienna]ubuntu[/COLOR]** liveCD boot it without making changes to your PC. When it is done, go in the menu to System> Administration> GParted or Partition Editor, whichever shows, then if you do not have any NTFS partitionss, then click and delete all of the partitions and create one big partition and set the file system as NTFS.

Then throw in the Windows XP installer and go through the installer for a happy machine.

---

