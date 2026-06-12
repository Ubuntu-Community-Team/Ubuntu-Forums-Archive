---
title: "Hard Drive Partition Trouble"
date: 2011-08-03
forum: General Help
---

### Post by morris14ccm on 2011-08-03
when I installed Ubuntu on my computer I made the partition all of the space I had left, which I don't want. So I deleted the partition and now it has become an "Extended Partition". Now I need to delete this partition and then create a new partition that I can use for storage for both Ubuntu and Win 7. Whenever I try to though I get an error. Any advice?

---

### Post by leclerc65 on 2011-08-03
It looks like you attempt to have more than 4 primary partitions.

---

### Post by morris14ccm on 2011-08-03
well i want it partioned so i have my 100MB one that Windows needs, then my Win 7 partition, then my Ubuntu partition, then my Swap file (currently the one that's 3.67gb, trying to increase that) and then a big storage partition. how can i do that?

---

### Post by garvinrick4 on 2011-08-03
Use 3 primary partiions for your windows. Make 1 extended partition and inside the extended partition make a logical partition for Ubuntu a logical partition for swap inside the
extended partition and a NTFS logical partition inside the extended that can be shared between Windows and Linux, windows will automatically give the ntfs parition a letter. 

You then have 4 primarys only, extended is a primary also.
Can put as many logical partitions inside of extended as needed. Though Windows prefers to Live in a Primary not in a logical, Linux will survive inside of logical partition just fine.

Make your partitions first then at install choose "other way" I believe it is and put your  (older installations called manual install)
/ (file system) in the one you made. Put swap in one you made and do not bother with
Ntfs partition just format it when making partitions and all is fine there. 
/ file system is formatted in ext4 at install tell it so. So in linux your new partitions will be sda5 and sda6 and sda7 after you make the extended will number them itself as you make your logicals no worrys there.
Install Cd using Try Ubuntu (Live Cd) has a App. called gparted that is a partition manager that I use. Some use the Windows one different opinions by all, I like gparted.
Gparted illustrated link below:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

P.S. grub bootloader go's in sda not sda1 or sda5 but in sda you do that you will boot no problem.
Couple of grub links to keep in bookmarks in case you get out of wack with grub2 anytime or need
to pass on to others.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
## Sometimes better to back up your /home folder and then partition your drive right and reinstall.
Need to get your HDD in proper shape if you dual, triple or have 6 Linux partitions inside extended.
I keep a Windows (came with machine) 6 different 10 gig / partitions for linux, 1 /home to share amongst them and 1 NTFS that is shared with Windows install.
Nice to test others out and keep a couple of stable and keep a couple of Under development installs of Ubuntu. This seems to happen overtime with Linux to most of us.

---

### Post by morris14ccm on 2011-08-03
i don't know how much of what you're saying i understand, but i would really prefer to not have to reinstall ubuntu. what can i do?

---

### Post by garvinrick4 on 2011-08-03
> **morris14ccm said:**
> i don't know how much of what you're saying i understand, but i would really prefer to not have to reinstall ubuntu. what can i do?
Go into Ubuntu and open gparted if not installed;
```
sudo apt-get install gparted
```
Open it and take a screenshot of it and post back here.

---

### Post by garvinrick4 on 2011-08-03
> i don't know how much of what you're saying i understand, but i would  really prefer to not have to reinstall ubuntu. what can i do?
That is OK, one day you should read up on basic drives with Master boot Record (mbr)
That is what comes with PC's and will help you out to understand your HDD. 

Now lets see what you can do without reinstalling. (post the screen shot if you would)

---

### Post by morris14ccm on 2011-08-03
> **garvinrick4 said:**
> Go into Ubuntu and open gparted if not installed;
```
sudo apt-get install gparted
```Open it and take a screenshot of it and post back here.
got an error...

---

### Post by garvinrick4 on 2011-08-03
Do you have another package manager open, synaptics, Ubuntu software center, something is open. Close whatever it is then rerun.
```
sudo apt-get update
``````
sudo apt-get install gparted
```

---

### Post by morris14ccm on 2011-08-03
got it

---

### Post by garvinrick4 on 2011-08-03
It is set up guite nice and has a what 230 some gigs to work with. Swap is fine at close to 4 gig so lets work on giving you a big data partition that you can use in both Windows and Linux.
Right click on unallocated and choose to make a new partition and make sure it is logical should be set as logical. Choose the size you want and format as NTFS and then hit OK and then hit the green apply arrow. Gparted will do the rest, when you open windows and in computer will have a new parition called G. or J. or whatever next letter in line. In Linux
will give you next sda# in line. Let me no, your drive looks nice though. You can label it what you want like data or something in gparted under label after right click.

---

### Post by morris14ccm on 2011-08-03
> **garvinrick4 said:**
> It is set up guite nice and has a what 230 some gigs to work with. Swap is fine at close to 4 gig so lets work on giving you a big data partition that you can use in both Windows and Linux.
Right click on unallocated and choose to make a new partition and make sure it is logical should be set as logical. Choose the size you want and format as NTFS and then hit OK and then hit the green apply arrow. Gparted will do the rest, when you open windows and in computer will have a new parition called G. or J. or whatever next letter in line. In Linux
will give you next sda# in line. Let me no, your drive looks nice though. You can label it what you want like data or something in gparted under label after right click.
alright, it says operation pending so hopefully it will work. thanks for your help!

---

### Post by garvinrick4 on 2011-08-03
> alright, it says operation pending
That means hit the green apply arrow up on top.
> thanks for your help!
You are welcome, enjoy. Under thread tools in upper right say Solved.

---

### Post by morris14ccm on 2011-08-04
it's not working on windows, but worked fine on ubuntu.

---

### Post by garvinrick4 on 2011-08-04
I see the E: Drive in Windows it says 231 of 236 gig. Do not know why it says error application not found?
You already put 5 gig in there?
## Backtrack used to be in that Windows Letter E drive. You deleted it and the data drive got the same letter E:
Find out from a Backtrack forum or from google search how to fix it. I will try to look also. I have never used backtrack
at all so have no knowledge of.

EDIT: Been looking around and it is a Windows problem with it using the same letter as backtrack and didn't your cd drive
used to be E at one time also when recovery or Backup was D drive. Hit the Windows Forums and see whats up some Windows user can surely fix you up.

---

### Post by garvinrick4 on 2011-08-04
I think you were using 10.04 or maybe 10.10 if you are, try using the Mozilla ppa in this
link and use firefox stable or next and the rendering is just so much better. You will be amazed how much better firefox looks, big difference.
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

---

### Post by morris14ccm on 2011-08-04
well i woke up this morning, booted into windows, was alerted that i got a blue screen last night, but the hard drive seems to work now.

the only ubuntu i ever used is 11.04

---

