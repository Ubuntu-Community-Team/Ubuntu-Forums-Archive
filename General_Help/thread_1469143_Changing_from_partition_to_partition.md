---
title: "Changing from partition to partition"
date: 2010-05-01
forum: General Help
---

### Post by louis.roux on 2010-05-01
I have Ubuntu 10.04 on a separate partition with vista on the other side.  Once in a while I have to go over to vista.  Is there a way to simply do that or do I have to reboot every time?

---

### Post by WorMzy on 2010-05-01
You have to reboot to boot into Vista, but you can still access files and folders that are on the Vista partition without needing to reboot. You can even run some of Vista's programs without rebooting, if you have Wine installed.

---

### Post by louis.roux on 2010-05-01
I try that but I cant seem to make it work.  For example, I try to get photos that are stored on vista but I cant find the folders.  In fact I cant find any folders or files in vista using wine.  I am obviously doing something wrong.

---

### Post by WorMzy on 2010-05-02
Ah, no, you've misunderstood what wine is. Wine doesn't give you access to your Vista partition, it creates a fake windows-style filesystem in your home folder so that you can trick windows applications into thinking they're being run on windows. (Actually, it does a lot more than that, but this is a nice and simple way of explaining it).


To access your Vista partition:
1) open nautilus (the file manager; you can open it by clicking Places on the main menu, then clicking home)
2) look on the left of the window, you should see a list of folders, like Desktop, File System, and (hopefully) one saying "XXX GB Filesystem" (the XXX will be a number relating to the size of the partition)
3) Click this icon, and you will either be A) taken to the "root" folder of your Vista partition, or B) be prompted for your password THEN taken to the "root" folder.
4) From there you can navigate to where your photos are.

---

### Post by xxander on 2010-05-02
Wine basically acts as an emulator, even though it is not (W-ine I-s N-ot an E-mulator)... And yes, you must reboot each time.

---

### Post by louis.roux on 2010-05-02
Unfortunately I do not have that.  this is what I see to the left

Owner
Desktop
File System
Network
Data
Trash
Documents
Music
Pictures
Videos

---

### Post by ranch hand on 2010-05-02
It should be there.

However, before trying to figure out what the configuration problem is, go to Places>Computer (instead of home) and see if it is listed there.

I seldom look at that but it could be.

I am not on my test drive and that is where all my 10.04 installs are I am on 9.04 so I can't check this but you may want to open the "Disk Manager" just to see if it is listing that partition.

I would also check in synaptic for all tools for ntfs, I would think that they would be there but I never need them so do not think about them.

You could use my solution to all problems caused by vista and delete it too but I suppose you don't want to do that.

---

### Post by WorMzy on 2010-05-02
Data sounds promising. Try that. :)

If that's not it, could you open a terminal (Applications -> Accessories -> Terminal) and type 'sudo blkid' and hit enter. You'll be asked for your password, then it'll list all the partitions that Ubuntu knows about. Could you copy and paste what it says here, and I'll see if I can give you clearer instructions.

---

### Post by louis.roux on 2010-05-02
yeah I think data is where it is suppose to be but I still cant find anything.  Here is what the terminal gave me

/dev/loop0: UUID="58cf1cb1-6b98-4050-a108-709672560d78" TYPE="ext3" 
/dev/sda1: LABEL="PQSERVICE" UUID="A290C56816D9B5D2" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="145409E65409CC04" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="3C5473ED5473A7F2" TYPE="ntfs"

---

### Post by WorMzy on 2010-05-02
What was in the data folder?

If it had a folder called Windows, then I think it's the right place. You'll need to navigate to users/<USERNAME>/Documents to get to the Windows equivalent of "My Documents". I have Windows 7 instead of Vista, so the folders might be different for you.

---

### Post by louis.roux on 2010-05-02
I still don't see it.  It is 1:30 am here, I'm going to bed and will tackle this in the morning.  Thanks

---

