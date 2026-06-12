---
title: "Can't access all ntfs particions"
date: 2011-06-11
forum: General Help
---

### Post by allie_jr on 2011-06-11
Dear all:

I am new to linux, I installed Ubuntu 11.04 on my desktop and dual boot with Win 7 a couple weeks ago; in windows I have my personal files on on "d" partition, but from Ubuntu I can only access the folders I have on "C" partition, which are in the host folder under my home folder. I appreciate your help. Thank you.

---

### Post by 3xp10r3r|X13 on 2011-06-11
Isn't there an option to access your d partition while going into "filesystem size of nfts partitions"?
Or isn't it even recognizes as a complete different partition called "filesystem size of d"?

Open up nautilus and have a look at the left side.

When you installed Ubuntu, did you just select "install next to windows".  If you did so and didn't partition manually, your loved partition "d" should have been erased, because it didn't contain windows...sry

Are you still able to access it using windows?

Is the partition shown in the disk manager of Ubuntu?

---

### Post by Yanno on 2011-06-11
Which desktop enviorment did u use???That seems a lot of bugs can be found in the Unity which is a brand new one.Ture 2 Gnome n take another try.Hope that'll help.

---

### Post by coffeecat on 2011-06-11
@allie_jr, from your mention of a host folder I guess that you installed Ubuntu in Wubi. Open a nautilus windows (file browser) by clicking on the "Home Folder" icon, the topmost one in the launcher. In the left pane of the nautilus window, below "File System" and "Network" you should be able to see your D: drive, only it won't be called "D:". That's a Windows-only convention. If it doesn't have a partition label, it will be identified by the size of the partition in Gigabytes. Simply click on it, and it will open in the nautilus window you already have open.

If you have difficulty finding it, boot into Windows and open Computer. Right-click on the D: drive and choose "rename". Call it "Data" or whatever you prefer - something distinctive. Now reboot into Ubuntu, open a nautilus file browser as before and you will see "Data" or whatever you called it in the left pane. Click on it and there will be your files.

---

### Post by allie_jr on 2011-06-12
Thanks to all:

Sorry I had mad my post before searching over and over; last night I saw an icon of a desktop after opening Home on the launcher, I click such computer icon and all drives were shown. 
Thank you again and I promise to take more care before posting.

---

### Post by coffeecat on 2011-06-12
No problem, allie_jr.  We were all new to Ubuntu once.

Good luck! :)

---

