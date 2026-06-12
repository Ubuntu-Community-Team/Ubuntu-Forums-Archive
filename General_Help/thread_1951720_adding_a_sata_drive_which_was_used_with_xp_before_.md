---
title: "adding a sata drive which was used with xp before unbuntu 11.10 install"
date: 2012-04-03
forum: General Help
---

### Post by petereview on 2012-04-03
I just built a new system last month running xp sp3. Recently, I messed with the power supply to reduce fan noise. On the next start up - it gave me a blue screen error.  So I attempted to reinstall xp and it said the second drive needed some info put on it for installation.  That made be feel defensive so I unplugged the second drive from the motherboard (the second drive 500gb has all my music,videos, photos and important docs). Afterward, the XP installation would hang at 35 min.  After several tries I gave up.
That is when I went to my wife's laptop and downloaded and burned unbuntu 11.10. It working well. My motherboard has intel graphics integrated which unbuntu does not recognize. After several restarts it somehow works fine now.

**My question is - should I plug the second sata drive in and restart computer?  Will it be a problem since it was originally set up using xp?**
My worry is I will lose my 500gb of collected music,video and photos in this experiment. I am aware each operating system puts some info on the drive that might make it incompatible with other operating systems.  Please help me avoid that issue.    
Thank you
Intel Core i5-2400 CPU @ 3.10GHz × 4 
Motherboard GA-H61M-S2H 
Intel graphics - not recognized by Unbuntu
sata hard drive one WDRaptor 74gb - has Unbuntu installed
sata hard drive two 500gb Western Digital - music,video,photos -not connected.
4 gb mem

---

### Post by davidvandoren on 2012-04-03
I think something is wrong with your hardware configuration, and you should fix that first.
If windows cannot be installed then there is clearly something wrong, 

The Intel graphics are usually recognized by any Linux system the best as far as I have observed. 

To your original question: You can connect any drive as you wish. Then push F11 Or F12 depending on your bios to boot from any of those drives. 

You can disconnect you working Ubuntu drive also then connect one drive and install windows on it. After you finished your installation reconnect the Drive with Ubuntu on it and push F11 or F12 to choose the drive you want to boot from either the one for linux or the one with windows. 

Another way would be to change the boot order in the bios to do the same thing.

Look in the bios under integrated peripherals or so to find the entry for your Graphics and set the options appropriately.

---

### Post by Mark Phelps on 2012-04-03
If you're seeing a desktop, not stuck in a text-based command line interface, then Ubuntu IS seeing the Intel graphics card and has already installed the proper drivers for it.

Regarding the other drive, when you connect it to the PC, be sure to continue to boot from the Ubuntu drive.  Depending on how your drives are connected, once there are two drives, the BIOS might automatically choose the "other" drive to boot from.  Boot into the BIOS settings and confirm that you're booting from the Ubuntu drive before you proceed to the desktop.

Once you do that, you should be able to see all the folders and files on the other drive without any problems.

---

### Post by gordintoronto on 2012-04-03
I agree that your computer has hardware issues. You can't expect an operating system to solve hardware problems.

As for the media on your other hard drive: go and buy an external drive, plug in the media drive, and copy all your files onto the external drive. Or buy a spindle of DVD-R discs, and burn copies of your media onto DVD. Having no backup, on a flaky computer, is a recipe for future tears.

---

### Post by petereview on 2012-04-06
I studied and tried all the suggestions and had success. The motherboard has intel video built in. The BIOS setting was set to seek a PCI video card on default.  I changed it to use the video onboard.  Unbuntu 11.10 did recognize intel sandybridge graphics driver in system settings after that.  If I have to do a clean install I feel it will be easier next time because of that change.  Thx for that!

I went and bought a sata to usb connector to convert the 500gb media file drive into a external.  Once it was connected it showed up while in Unbuntu.  As recommended I started to transfer some of the most precious files to Unbuntu drive - about 50gb max.  Then I burned some dvd back ups of the rest which was about 150gb.  Now I feel safe again Thx!

Then I wanted to try installing xp on a old 40gb sata drive in my closet.  The Unbuntu drive cable was uninstalled then reinstalled my old sata drive as the only primary drive.  Put the xp cd in and crossed my fingers.  It hung at 35min like before.  This is just after preparation of xp and before it is installed.

The main mission was accomplished thank to you guys!  Thank you!:guitar:

---

