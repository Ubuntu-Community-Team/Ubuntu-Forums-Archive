---
title: "how to view files on my C: drive with ubuntu installed as dual boot via Wine ?"
date: 2009-10-25
forum: General Help
---

### Post by SilverBridge on 2009-10-25
i have dual boot , windows vista with Ubuntu 9.04 , i installed Ubuntu using Wubi , but i can`t view the files in my documents folders in Windows Vista , i tried to mount the windows partition with ntfs-config , but sounds i got no clue what i am doing  , so is there any way to get to browse my files in the windows documents folders ?

---

### Post by SilverBridge on 2009-10-25
I installed Ubuntu via Wubi , not wine , i just mixed both , sorry

---

### Post by jrrader on 2009-10-25
Nm

---

### Post by SilverBridge on 2009-10-25
sorry again for mixing Wine with Wubi , 2 letters make such a difference , and thanks for your fast replay jarrader , you are totally right , i installed Ubuntu on what so called virtual box , for example , when i browse my C: folder from my windows vista , there is an Ubuntu folder there 17 GB , to be honest , i didnt get much of what you said , i am still a total beginner , so i will appreciate if you show me the directions , and to be sure i gave the right meaning by my thread , i want to manage to read the files present in my documents in windows vista from Ubuntu ? so any help ?

---

### Post by fluffman86 on 2009-10-25
Click Places on the top bar of Ubuntu, then click on the icon for your hard drive.  It may say "178 GB Media" or have a name like "HP Pavillion"

---

### Post by SilverBridge on 2009-10-25
you still not getting the image people , i got 2 drives C and D , the D is already apparent , and i mount it normally , the issue is with the C drive , the ubuntu is installed as a virtual drive , so windows files present in folders above the root directory of Ubuntu is unreachable , for example , when i browse the C drive from my windows Vista , there is Ubuntu folder , next to it the Documents folder , the issue now , i can`t browse any folders other than the Ubuntu root folder in Ubuntu , so most of my files in the windows documents in the C drive is unaccessable .. any help ?

---

### Post by jrrader on 2009-10-25
No, I wasn't right.  If you installed with Wubi then I was completely off the mark (which is why I removed my reply after you corrected your mistake).

---

### Post by SilverBridge on 2009-10-25
:)

---

### Post by fluffman86 on 2009-10-25
And Ubuntu doesn't care if it's on your "C" drive.  Ubuntu doesn't even know what a C or D or any other lettered drive is.  Everything is *UNDER* / (root) in Ubuntu.  So if you go to Places, just click on each of the drives listed.  It will then be mounted as /media/disk-1 or something similar.  See, it's under /, then media, then disk-1.  

If that doesn't work, or if your drive doesn't show up there, then go to Applications > Accessories > Terminal and type:

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows -t ntfs-3g -o force

where /dev/sda1 is the first partition of your first hard drive.  This is usually C:, unless you have a recovery partition.  If you *DO* have a recovery partition as your D: drive, then use /dev/sda2 instead of /dev/sda1

---

### Post by SilverBridge on 2009-10-25
fluffman86 , You rock , It did work , Thanks Loads for your help

---

### Post by sea_monkey987 on 2009-10-25
> **fluffman86 said:**
> And Ubuntu doesn't care if it's on your "C" drive.  Ubuntu doesn't even know what a C or D or any other lettered drive is.  Everything is *UNDER* / (root) in Ubuntu.  So if you go to Places, just click on each of the drives listed.  It will then be mounted as /media/disk-1 or something similar.  See, it's under /, then media, then disk-1.  

If that doesn't work, or if your drive doesn't show up there, then go to Applications > Accessories > Terminal and type:

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows -t ntfs-3g -o force

where /dev/sda1 is the first partition of your first hard drive.  This is usually C:, unless you have a recovery partition.  If you *DO* have a recovery partition as your D: drive, then use /dev/sda2 instead of /dev/sda1
 +1.  also the reason your "C:" isn't showing up under "Computer" is because it is already mounted.  and then, your ubuntu installation was mounted via the loop-back device.  this is what wubi does (kind of cool actually.  your whole ubuntu partition is contained in one file on your C: ).  anyway,fluffman's solution should work, although i wouldn't use the force option :)

---

### Post by fluffman86 on 2009-10-25
maybe "-o force" isn't necessary with a Wubi install.  but the reason I add is that if windows doesn't shut down properly, it won't mount.  adding the -o force doesn't hurt, so it's easier to just include it. :\

And if you're having to mount via command line, it's probably because it's not showing up under places, becasue it didn't shut down properly...therefore requiring a force.

---

### Post by eriqjaffe on 2009-10-25
Unless things have changed recently, WUBI-installed Ubuntu will mount the host drive automatically at /host, so there's no need to jump through any hoops to get to it.

---

### Post by SilverBridge on 2009-10-26
one last question, after restarting , i had to do the whole process allover again , so is there any option that it can be done automatically whenever i log in into my ubuntu , and just another minor issue , my NTFS Config doesnt appear in my applications list , at all , although it works pretty fine when i use the terminal to make it work ,so , any further help , i will appreciate it alot :)

---

### Post by sea_monkey987 on 2009-10-27
> **SilverBridge said:**
> one last question, after restarting , i had to do the whole process allover again , so is there any option that it can be done automatically whenever i log in into my ubuntu , and just another minor issue , my NTFS Config doesnt appear in my applications list , at all , although it works pretty fine when i use the terminal to make it work ,so , any further help , i will appreciate it alot :)
the simplest way would be to put the mount command (without the sudo) in the /etc/rc.local file.  the /etc/rc.local file is executed as a bash script when everything finishes starting up.  as far linux is concerned, the login screen is handled by the program gdm.  when gdm (the login screen) loads up, linux moves on to loading the rest of the daemons.  you can find more out by looking at the contents of /etc/init.d/ or /etc/rc2.d/ (rc*.d, actually)

however, I think the officially recommended way is to add an entry in the /etc/fstab file.

---

### Post by SilverBridge on 2009-10-28
thanks for your replay Sea_monkey987 , but whenever i try to add any of the following lines to the files u mentioned , i recieve an error message telling me i dont have the permission needed to perform such an operation , i know this is might be just too easy , but it is me who don`t get how to do it , so pardon my ignorance :0

---

### Post by sea_monkey987 on 2009-10-29
sorry if i was unclear.  you have to edit the file with root rights, so use sudo to open /etc/rc.local or /etc/fstab for editing.  so you could say

```

gksu gedit /etc/fstab

```
gksu is the graphical sudo prompt.  you should use it when starting programs that don't stay in the terminal.
more importantly, did you check what eriqjaffe said?  it might be already mounted as /host when you boot

---

### Post by FybrOptx on 2010-02-25
> **eriqjaffe said:**
> Unless things have changed recently, WUBI-installed Ubuntu will mount the host drive automatically at /host, so there's no need to jump through any hoops to get to it.

My drive did mount under /host yet it's owned by root and therefore not r/w unless mounted elsewhere with ntfs-3g.  Does that mean that Windows didn't shut it down properly or something?  I used to hibernate in windows until I got UNR 9.10 installed with Wubi.  On my wife's laptop her dir is mounted under /host but it is r/w.  

I just want to know how I fix it.  Thanks for the info so far!

---

### Post by xnorsx on 2013-04-01
I know this is old thread, but its easy way. Just go to folder Host there are all C:/ drive files. File System/Host
:)

---

### Post by oldos2er on 2013-04-01
Closed, please don't bump old threads.

---

