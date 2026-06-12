---
title: "Boot Questions"
date: 2011-10-10
forum: General Help
---

### Post by chayes627 on 2011-10-10
Hello, I am new here and new to linux. I have searching the net for about a week now and havent really found the answers im looking for.
Some background, first install went great, going at it completely blind, wiped drive, created partition, and installed.  I like to tinker so i created anther partition to install fedora 15. installed fine. went to boot up went right to fedora.  me not knowing much i wanted to use ubuntu, so i wiped the hard drive completely and started over, installed ubuntu so i could do some research on proper/best way to install, partition, everything. Now it wont boot at all unless i use the usb/live version.
So some initial questions are,
1. I want to try out a couple different versions of linux.  From reading Ubuntu and fedora and 2 of the bigger distros. they will probably be staying for awhile. plus trying out some smaller distros  here and there. Plus windows 7 (probably second hard drive) --How should I set up my partitions and size?-- I have no lack of hard drive space. I have 2 hard drives the are identical 640 gb WD SATA. 
2. Swap partition- I read that there could be an increase in performance by having it on the second hard drive. True or bad information?
3. I think ill just leave it there for now, i have other questions but they might be answered from the other ones.

---

### Post by drs305 on 2011-10-10
First, about what happened when you installed Fedora. During the second installation, Fedora probably installed it's own bootloader and overwrote the Ubuntu one. I've dealt with some Fedora issues lately and from what I recall Fedora isn't using Grub 2 (or it's not compatible, I can't recall).

Regardless, the best option is probably to keep Grub 2 and let it sort out additional OSs. If given the option, don't install the bootloader for the other OS. If that isn't an option, you should be able to reinstall Grub 2 from the LiveCD. It's a very simple thing to do and should restore booting to Ubuntu and Grub 2.

If you install a second OS on another drive, you can load it's bootloader on that drive and leave Grub 2 on the Ubuntu drive. In this case, the bootloader in control will most likely be the one BIOS has listed first in the boot order.

As far as size, I'll not say a lot except that 10GB is a healthy minimum size for the Ubuntu installation. Increase the size by the amount of data you might store in your /home folder. I recommend keeping your data in a separate partition.

Ubuntu and swap can be in extended partitions, Windows (at least through 7) still require installation on a primary partition I believe.

If you are using multiple Linux OS's, they can share a swap partition. 1-2 GB is generally sufficient. I don't think you will notice any performance increase by having it on a separate drive. It might improve it marginally - I don't know.

If you are thinking of using RAID, there are some special considerations about using it with GRUB. I'll have to leave that discussion to others who use it.

---

### Post by garvinrick4 on 2011-10-10
> from what I recall Fedora isn't using Grub 2 (or it's not compatible, I can't recall). Yes, that is true Fedora uses grub-legacy in 15 and does not play well with grub2 chayes627. 
Will make a /boot partition also if grub installed, fedora uses /boot to dist-upgrade
with for a reason I have never looked into.
Install Ubuntu first and fedora second and choose not to install grub boot-loader at all
at install of Fedora. Anaconda its installation package will give you that option. Believe
it also gave you LVM option if wanted, choose No. 
Then boot into Ubuntu and:
```
sudo update-grub
``` Will put Fedora in config file and as a menu entry for you to boot off of. Ubuntu will always be in control of grub for Fedora does not have a config file for grub-legacy not being installed.

## As I understand Fedora 16 will use grub2 (grub-pc). Do not know if other RedHat cousins are going to grub2.
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by chayes627 on 2011-10-10
Thank you both for the quick replies. 
drs305 - i have 8gb of ram is 1-2gb for swap still sufficient? i read that it was good practice to have at least the amount of ram that you have, but that might have been an older reference. it seems like alot of the information that i had found was older and not sure how much applies.
garvinrick4 - i have read the article that you posted a link to. what I didnt pick up from it is which partitions are needed in my case /boot /usr /home etc. as i had it set up 1 hd the whole thing is extended partition. under that 4 100 gb and 1 240 gb logical partitions. swap space i had on the second hd at 10 gb.
let me know if anything that i am saying is outdated or doesnt apply. i really like linux in general but some stuff is foreign when all i know is windows

---

### Post by garvinrick4 on 2011-10-10
> garvinrick4 - i have read the article that you posted a link to. what I  didnt pick up from it is which partitions are needed in my case /boot  /usr /home etc. as i had it set up 1 hd the whole thing is extended  partition. Before doing anything else you
can post a screenshot of "gparted" in Ubuntu to this thread, take a screenshot and upload
it with paperclip (attachments) on top. Will not see it after upload until you submit reply on bottom. We will be able to see what is going on. I think a / and a /home are good enough.
Cannot use same home with Fedora and Ubuntu one has UID (can google) of 1000 Ubuntu
and 500 Fedora so permissions are different. Is a real pain unless you have oodles of 
experience in that field. Do not really need a /boot at all. Just a / ( file system) and 
a /home in Ubuntu. That way when you want to do a fresh install will not effect /home files
and can share with other Ubuntu installs in future.
> drs305 - i have 8gb of ram is 1-2gb for swap still sufficient?drs305 is around still but you got plenty of RAM do not knock yourself out with swap worries.
Swap is a scratch disk on drive for when you are getting low on RAM, with 8 gig just isn't going to happen.
Some might say something about hibernation and Swap but we will see if someone chimes in on that subject.

---

### Post by chayes627 on 2011-10-10
attached should be gparted of both hds the first being the main one. let me know if there is anything else that i can provide to help out. thanks alot

---

### Post by wildmanne39 on 2011-10-11
Hi, just thought I would offer another suggestion since you already have great advice about booting, I put all my extra operating systems in virtualbox that way I can run them and restore them in seconds if a mistake happens and they do not effect my ubuntu ever.

Here is a link for virtualbox so you can read about it.
[https://www.virtualbox.org/](https://www.virtualbox.org/)
Thank you

---

### Post by garvinrick4 on 2011-10-11
You made the /boot when you installed Ubuntu. So it is there and Ubuntu is installed.
If you want to install Fedora then choose to install in manual. Choose to make install
as / in sda7 in ext4 as format and tick format box. Just say no to swap when it asks. 
Any questions at install about LVM say no, you do not want that.
Choose not to install grub at all when the page comes up on where to install grub. Let install finish and then
restart into Ubuntu and:
```
sudo update-grub
```Will now have both installs in as menu entrys in Ubuntu's grub2.

#Since you have a /boot partition when you ever want to install grub in live CD (install cd
using Try Ubuntu) you have to mount both /boot and / when installing grub2 to mbr through
a live cd. Link on how to do this below if I have not given already. Always use the quide
to install grub with /boot partition.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

## Keep posted on progress or questions.

---

### Post by chayes627 on 2011-10-11
wildmanne39 - thanks for the info that could come in handy in the future.

garvinrick4 - is it worth having the boot partition? being able to keep my files isnt the biggest concern for me since anything that matters i will have backed up either to data partiton or ext. hd. I havent really touched anything since i posted my question so i am really at scratch. 
in my case,
1. which partitions are necessary if any other than / (root)
2. which partitions could improve performance or are helpful

btw thanks for everything so far

---

### Post by drs305 on 2011-10-11
I wouldn't bother with a /boot partition with two exceptions. I'm not familiar enough with Fedora, but from what I've read above you may need a boot partition to upgrade it. If that's not a deal breaker, I'd skip it. 

The second reason (for your Ubuntu installation) is if your BIOS doesn't recognize the hard drive past 137 GB and your Ubuntu partition extends beyond this point of the disk. In that case you would want a /boot partition within the first 135GB of the drive. I don't think this is a factor for you.

Give the two situations, I don't think you need a separate /boot. It adds a level of complexity you probably don't need.

Necessary partition(s): /
Desired partition(s): swap (or swap file)
Optional partition(s): /home and data.

My preference is to leave /home in the / partition, and just have a data partition where I keep data, music, video, etc. If you intend on keeping your data within the /home folder, I'd devote a separate partition for /home.

---

### Post by chayes627 on 2011-10-11
drs305 - thank you for that info. ill try this out in about an hour and get back to you

---

### Post by chayes627 on 2011-10-12
update: got everything working last night. Boots up and gives me the option for what to boot into.
Couple more questions now
1. boot list shows ubuntu, ubuntu recovery mode, mem test etc..... then fedora. how can i make it so it only shows ubuntu and fedora no other options?
2. how can i make it so it boots automatically into ubuntu if no option is selected in say 5 or 10 seconds?

on a side note - im setting up a friends system tonight. he wants ubuntu and windows 7. they will be on separate partitions, i know windows has to be on primary partition. will ubuntu boot windows in the same way i set it above or will i have to do it the other way around?

---

### Post by garvinrick4 on 2011-10-12
> 1. boot list shows ubuntu, ubuntu recovery mode, mem test etc..... then  fedora. how can i make it so it only shows ubuntu and fedora no other  options?[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
Look at section /etc/default/grub
That is what you have to edit to remove anything from boot menu:
Then 
```
sudo update-grub 
```
to make permentent.
> on a side note - im setting up a friends system tonight. he wants ubuntu  and windows 7. they will be on separate partitions, i know windows has  to be on primary partition. will ubuntu boot windows in the same way i  set it above or will i have to do it the other way around?     
 Windows most likely already installed can choose to let Ubuntu installer install
side by side and it will take care of makeing partitions. Or make your own partitions and
install into a particular partition with your own hand using "something else" at install instead of side by side.

---

### Post by drs305 on 2011-10-12
For menu manipulation like removing and renaming entries, I recommend a GUI app called Grub Customizer. Clicking on the 'Customizer' thread in my signature line will take you to the thread that describes how to install and run it.

---

### Post by chayes627 on 2011-10-12
drs305 - thanks for the grub customizer it worked great.

I hosed something up. I did the grub customizer, got it the way i wanted still the way i want it. I was in the process of setting things up wireless, bookmarks, firefox addons, etc...  I ran update manager, finished, said to resart system, restarted and no ubuntu. grub bootloader is still there just with fedora only. what could have happened? let me know anything i can provide.

sorry for the 100 questions.

---

### Post by drs305 on 2011-10-13
chayes627,

The best thing to do would be to (boot the LiveCD and) download/run the Boot Info Script. You should be able to run it from Fedora. Then post the contents of RESULTS.txt here. It will show us the status of your boot files and help us figure out what went wrong.

My guess is the Fedora Grub took back control of the boot. You can reinstall Grub 2 from a LiveCD by mounting your Ubuntu partition and then reinstalling Grub 2. XY are the drive letter and Ubuntu partition number:
```
sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**
```
Example: 
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

You can get to the script's page by clicking the "BIS" link in my signature line if the above doesn't work or you have questions.

---

