---
title: "Wubi to the real thing"
date: 2010-03-30
forum: General Help
---

### Post by bluepowelly on 2010-03-30
Hi Guys,

I have been using Wubi for a few weeks now and I am really impressed. I have endured a lot of problems with grub and kernel problems etc but now realise that its just the Wubi inside windows!

I have it all set up with the cube to perfection and all drivers are running great after a bit of tweaking.

So a bit of a lazy question really, can I install it properly onto my drive, and retain all the hard work I have put in setting it up?

I have tried, but when it comes to selecting the drive that the Wubi is installed on it just says format with no backup option.

---

### Post by oldfred on 2010-03-30
Welcome to the forums. hope we can help. 

I have installed Karmic on two different computers without any real issues at all, but if you look at the number of posts, not everyone has such success. Sometimes a little planning can save many issues and problems. If wubi is running well your hardware should be fine and not an issue. What version of windows do you have as that makes some difference to the best way to install.

You can copy your /home from the wubi to your new /home whether it is a separate partition or part of root, most of your settings are in the hidden files and folder in /home. You also can export a list of all the additional applications you have installed and automatically reinstall all of them from the list.

How much space do you have on your drive and how many partitions have you used.

sudo fdisk -l

and for mounted partitions use.

df -h

---

### Post by Rocket J Squirrel on 2010-03-30
Hi oldfred,

I, too, am an Ubuntu newbie and have test-driven ubuntu with wubi enough to know that I would like to dump the Windows 7 Starter partition and go fully ubuntu. I've spent the past week getting the wireless card stable using backports, and have installed a lot of printer-related things, like cups+gutenprint and TurboPrint. These are things I'd like not to have to re-install so I'm hoping to find a way to make the changeover without starting from scratch. So a "nuke the Windows partition and grow the Linux partition" approach would be peachy. If such exists.

Update:
fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16135ee7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       30402   231506210    7  HPFS/NTFS

and

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             29G  3.4G   24G  13% /
udev                  497M  260K  497M   1% /dev
none                  497M  384K  497M   1% /dev/shm
none                  497M  108K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda3             221G   47G  175G  22% /host

---

### Post by colorlessprism on 2010-03-30
im not sure if remastersys will work from inside wubi, but its supposed to take you current install and turn it into a LiveCD iso. then you could use the "usb startup disc creator" to put the iso flash  drive. then you could boot from the usb and just "install" and run through the formatter. since it is an "iso" format you will be  limited to the size it can back up. i use tar.gz to backup my Documents,  Music, Pictures, Video, and .wine. i would deffinitly test it out by booting into the usb fully and make sure it actually works...

[http://www.geekconnection.org/remast...ersystool.html]("http://www.geekconnection.org/remastersys/remastersystool.html")

---

### Post by oldfred on 2010-03-30
If you have space I would make root 10-20GB and swap 2GB or size of RAM memory if larger or 2x RAM if smaller than 2GB. Windows will need at least 20% free space, do not make it too small.
If windows XP you can use Gparted to resize windows and make partitions. If Vista or 7 use the windows tools to shrink windows and reboot to make sure it works, Then use gparted to make new partitions. To install Ubuntu, use manual install and select the partitions your have created for root (/), swap & /home.

they used to have an automatic tool LVPM for conversion but it has not been updated. On its site is this info:

Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
1. Create 3 new partitions with the Partition Manager : a 5-10 GB (ext3 format) partition to use as root (/), a ~1 GB (equal to RAM size) (swap format) partition to use as swap, and make the rest a (ext3 format) partition to use as /home.
2. Boot back into the Wubi-generated Ubuntu install, mount the new partition that will be used as /home in the dedicated-partition install to /media/disk, and copy the contents of the current /home recursively over to the new partition:
rsync -avx /home/ /media/disk
Additionally, if you want to avoid the hassle of manually reinstalling all the packages you currently have installed, run:
dpkg --get-selections > selections.dpkg
That'll generate a list of packages you have installed (back up that list to somewhere safe); after reinstalling the system, just open Synaptic, go file > read markings, select that file that was generated (selections.dpkg), press apply, and it'll reinstall all the software you have on your current system ). You can also do this from command line.
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

More info on installing:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

### Post by kokkus on 2010-03-30
Yes, remastersys will do the job as long as you go for distro backup and not the full backup. You can put your personily files and documents on a memory stick or something.
After burning the new distro cd (using remastersys), reboot your pc and start the installation. You can wipe out the windows partition during the installation process if you don't want windows on your PC anymore. Good luck.

---

### Post by Rocket J Squirrel on 2010-03-30
Hi folks,

Um -- wow. That's a lot of information, very dense ... and possibly nutritious! 

Okay, lemme see if I understand: 

1. remastersys can be used to make a backup of my _current installation_ of Linux and Ubuntu. This can be burned to a CD* and used to install Linux/Ubuntu onto the machine, and, as kokkus says, I can also wipe out the Windows partition in the process. 

Yes? 

2. My personal files, which aren't many since this is a fairly new install, would best be backed up and reinstalled separately.


============
* Question: The machine, a netbook, doesn't have an optical drive -- I reckon there is some way to use a USB stick for the reboot/install process?

---

### Post by kokkus on 2010-03-30
Sure you can. Reboot your pc and hold down the comma key (,) and it will take you to your BIOS. from there you can choose to boot from the USB instead of the hard driver. The USB stick will boot if you choos Removable device. Depending on what bios version you have.

---

### Post by oldfred on 2010-03-30
On my desktop it is f12 and on the portable f2. My desktop motherboard said it would boot USB and it lists 3 or 4 usb devices usb cd, usb floppy etc but I could not get it to boot. I knew the USB key worked since it booted my portable. Later I had it plugged in and happened to choose to change Hard drives and there it was. My USB key was not a USB device but a hard drive.;)

---

### Post by Rocket J Squirrel on 2010-03-30
> **kokkus said:**
> Yes, remastersys will do the job as long as you go for distro backup and not the full backup. You can put your personily files and documents on a memory stick or something.

How do I know what files are personal files and which are distro files? What files does remastersys not back up when "Dist" is chosen?

---

### Post by colorlessprism on 2010-03-31
i personally have always selected the "backup" option. when y personal files grew too large i started commenting out the biggest files and backing/restoring separately. i am not sure your settings will be copied over if you use the dist option. try editing your remastersys config file and adding you big folders to the "Exclude" placeholder (mine were:Documents,  Music, Pictures, Video, and .wine) and run remastersys normally. but really if your using usb, you can experiment with all the different options by running each option and booting into it to check it out (assuming of course you have formatted ;)) make sure you run "sudo remastersys clean" from the command line after you've made you bootable flash drive as this will remove all the files remastersys created when it was running. i really think if you use remastersys you will continues to use it for a backup program...i can be back up in running in no time if i have to restore

---

### Post by Rocket J Squirrel on 2010-03-31
Thanks, colorlessprism.

Of course, something that was said caught my attention and leads to a question: 

> **colorlessprism said:**
> ...but really if your using usb, you can experiment with all the different options by running each option and booting into it to check it out (assuming of course you have formatted ;)) ...

As in, the usb stick must first be formatted, I reckon? They usually come pre-formatted, but is there some additional step I need to take? Again, I'm a newbie.

---

### Post by colorlessprism on 2010-03-31
sorry that should have read [SIZE=3]**"NOT FORMATED"**[/SIZE] DO NOT FORMAT YOUR HDD until you are ready to commit what you have created. it was early, and i hadn't had my coffee yet. you should be able to run the different Remastersys options (i.e. backup, dist, etc) use usb startup creator on the iso that was generated, when finished open a terminal and type "sudo remastersys clean" and restart when finished. assuming your BIOS is set to boot from USB your flash drive should start up and you'll be presented with a couple boot options. if your just test driving go ahead and press enter and let it load up. eventually the GUI will start up and you can play on it just like it was the real thing. if you not pleased with something (maybe your settings have dissapeared like themes) you might try another remastersys option. just shutdown your computer remove the flash drive and start the computer again. your original system should start up again. once inside ubuntu you can run remastersys again. i always run the "backup" option and i modify the config to not back up my Document, Music, Pictures, Videos, .wine. what that means is when i boot into the usb my documents are not there and none of my wine applications will work. i put them back in place when i am done with the install. let me know if you have any more questions.

---

### Post by Rocket J Squirrel on 2010-03-31
Hi colorlessprism,

That helped. 

With regard to formatting the HDD, once I am happy with what's on the remastersys'd USB stick, I need to know how to do that format. Use the BIOS or does remastersys offer this functionality, or . . . ?

---

### Post by colorlessprism on 2010-03-31
actually installation/formatting is very easy. there should be an "Install" icon in your "settings" tab, but i think there is also one on your desktop. you will do this after you have booted into the flash drive. once you click install you should be guided through a series of questions/options. when the time comes you will select "use entire hard drive" (or something to that effect) and once installed you will shutdown the computer, remove the flash drive and turn the computer back on. after you computer has booted back up you should see you new login screen. after you login dont forget to to move any folders you backed up separately, these are the ones you added to the remastersys "exclusion" section, to their rightful place (i.e. Documents, Music, .wine, would go in /home/tb64 for me). good luck, and let me know if you have more questions. i am not a programmer, artist, or translator so this is my only way to give back to the amazing Ubuntu community.

---

### Post by garvinrick4 on 2010-03-31
You are rather new to Linux I am going to assume.

Under organize bookmarks in firefox you can back-up bookmarks.

In Synaptic package manager you can save markings (your installed packages)

Put these on a flash drive or backup drive.

Uninstall Wubi in folder in Windows that says Ubuntu not from ADD and Remove programs in Windows. 

Take your install CD and boot off of it.

Choose install and answer the questions and let gparted make install for you. It will tell you what it is going to do on each page. It is good software gparted. 

Do not use manual because you do not know what you are doing yet.

It will make and extended partition and put your Linux inside in a logical partition

I am going to give you something to read about partitions and dual booting and gparted.

If you have to get your system back into the shape you like after install it is good practice for
you. After a while you will be able to do it blindfolded. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Do not try nothing to fancy if you do not understand it!!!!!

---

### Post by kokkus on 2010-03-31
> **Rocket J Squirrel said:**
> How do I know what files are personal files and which are distro files? What files does remastersys not back up when "Dist" is chosen?


Distro doesn't include your home folder but everything you have installed, the ubuntu system files etc (all the packages).
A normal backup will include your home folder, private settings and stuff too. 
So if you want your wine programs and firefox bookmarks to be backed up, take the full backup and not the distro backup.

---

### Post by Rocket J Squirrel on 2010-03-31
Thanks again, colorlessprism!

garvinrick4: yes, I am very new to Linux. Thanks for the homework, I'll read it. I'm not planning anything fancy, just hoping that the process does not pop up an unexpected surprise that I'll be expected to deal with. 

and kokkus, thanks for explaining that /home and the subdirectories are where I want to keep my files. It's the Linux equivalent of Windows' My Documents.

---

### Post by Rocket J Squirrel on 2010-04-15
> **garvinrick4 said:**
> You are rather new to Linux I am going to assume.

Does it show? How can you tell? ;)

<snip>

> **garvinrick4 said:**
> Uninstall Wubi in folder in Windows that says Ubuntu not from ADD and Remove programs in Windows. 

Easy enough to do.

> **garvinrick4 said:**
> Take your install CD and boot off of it.

Choose install and answer the questions and let gparted make install for you. It will tell you what it is going to do on each page. It is good software gparted. 

I have prepared two LiveCD USB sticks, one with gparted on it, the second contains the remastersys full backup. From the above instructions, it appears that the remastersys stick will have gparted already on it?

> **garvinrick4 said:**
> Do not use manual because you do not know what you are doing yet.

Yes, well, I think that has already been demonstrated. 

I think that once I am clear on the remastersys + gparted thing I'll be ready to do this. "This," in case the intent of the thread has been lost, is to take this wubi-fied dual-boot Windows 7 + Ubuntu laptop and switch it over to a full ubuntu laptop without the W7 training wheels, and preserve the config changes and backports and other things that I had to install into ubuntu to get the wireless and Windows Network Shares up, running, and stable. If anyone sees that I'm about to start something here that isn't gonna do what I have in mind, please advise. 

Thanks for all the help the community has given.

---

### Post by colorlessprism on 2010-04-15
your remastersys backup probably has gparted on it so there shouldnt be any need for the two flash drives. if you boot into your remastersys backup and find gparted not on there open you can still install it and go on your merry way. remeber though; formatting is forever so measure twice and cut once

---

### Post by Rocket J Squirrel on 2010-04-15
Oh yeah, duh -- the live remastersys usb will have all the stuff my ubuntu already has on it, and I do have gparted installed on the machine.

---

### Post by Rocket J Squirrel on 2010-04-15
Okay, as colorlessprism advises, measure twice, cut once. Not knowing my measures yet, I'll post where I'm at at this moment to see if anyone can spot a gotcha before I move on.

Just bought a 4GB USB stick and formatted it FAT32 in case there was some crap on it. Didn't see any, but didn't see any reason not to play it safe. 

Tried to put the remastersys .iso on it using USB Startup Disk Creator but it griped that there was not enough room on the stick for the iso. It showed two orange and red triangles next to sdb and sdb1 (the stick) and said the stick needed formatting, but was unable to mount it. 

So I ran UNetbootin and it found the stick and installed the iso. 

I rebooted the computer and told the BIOS to boot off the stick and it did. I'm presently looking at my ubuntu desktop and everything seems to be working peachy. 

UNetbootin provides an "install" option at boot time. Is there any reason why I can't use that feature to install my ubuntu system onto the computer once the computer is ready to go?

---

### Post by colorlessprism on 2010-04-15
i have not used UNetBootin, though i am familiar with the USB startupdisc creator problem. for somereason it sees and displays both the disc and the partitions. sometime it takes formatting them both before it will let you continue. when you load UNetBootin are you given options like:

Boot from Hard Disc press enter
Check Disc for Defects
Memtest
Install

if so you should be ok, but hopefully someone here has used Unet and can give firm advice, you should have an install option on your "system" menu and MAYBE one on your desktop (UNR shows install in "favorites")

---

### Post by Rocket J Squirrel on 2010-04-15
M-kay, booting off the UNetbootin stick gives
[INDENT]Live
xforcevesa
install
text only
check
memtest
hd
[/INDENT]So, based on what I read in this thread, my next moves would be to 

1. Boot off the HDD into Windows 7 and uninstall wubi using the method described by garvinrick4 earlier in this thread (Uninstall Wubi in folder in Windows that says Ubuntu not from Add and  Remove programs in Windows.)
2. Boot to the UNetbootin stick and gparted the HDD. 
3. Install ubuntu from the UNetbootin stick. 

Forgive me for belaboring the steps. It seems pretty straightforward from this point on out, but I want to do this carefully.

---

### Post by colorlessprism on 2010-04-15
if you want to COMPLETELY REMOVE WINDOWS there is no reason to uninstall wubi as the formatting would make the point moot. if you want to keep windows and dual boot then you will need to uninstall wubi as described. 

if you are dual booting you will need to run gparted to shrink you windows partition. you should decide how much space you want to give your OS's at this point. shrinking partitions takes an incredibly long time (it took hours on my HDD and i was shrinking a 200GB partition to 190GB to make a bootable rescue partition). be prepared to leave your computer be for a very long time. i would go ahead and use gparted to format the new space you created to "ext3" (it will make it easier to find during the installation). when finished run the installer and when the time comes you will have ubuntu install to the "ext3" partition NOT the NTFS/FAT32 etc.

if ubuntu will be your only OS then you can just run "install" and dont have to worry about gparted. when the time comes all you need to do is select the "use entire disk" option. 

when finished you will need to restart your computer. make sure you remove the flash drive before booting back up. if ubuntu is all you have then it will boot right up. if you dual booted then you will have to pick Windows or Ubuntu in the grub menu. 

let me know if i can elaborate further for you. i have a tendency to speak in fragments and incomplete thoughts.

---

### Post by Rocket J Squirrel on 2010-04-15
"i have a tendency to speak in fragments and incomplete thoughts."

Perhaps. But you also have the patience to help. Thank you.

Yes, this is meant to be a ubuntu-only install. If the "install" function does what needs to be done to wipe the Windows partition, then that's all I need to know. 

"Install," then, is a brute-force take-no-prisoners procedure. If someone selects it, then the assumption is that they are done with whatever OS is on the machine, and are starting fresh. 

I like it. 

I'll either resurface here with a question, if things get snarled; or to say that the training wheels are off and I've got a big boy bicycle.

Again, thanks.

---

### Post by colorlessprism on 2010-04-15
i look forward to hearing how things turn out. good luck

---

### Post by Rocket J Squirrel on 2010-04-16
I'm back. Miss me?

I'll be hornswoggled* -- it worked flawlessly. 

Windows be gone!

Thanks for all the help. Really.  Now I gotta get a ubuntu sticker for the laptop so all the hipsters in the coffee shops will know that I have geek cred. 

========
* Soon's I find my swoggling horn.

---

### Post by colorlessprism on 2010-04-17
i am pleased to hear it all worked out. remember to do regular backups, as you are bound to play with things and that when things get broken (believe me i know). system76 still has the advertisment on their website for free case stickers. you even get a keyborad sticker to cover the "windows" key. 

[http://www.system76.com/article_info.php?articles_id=9](http://www.system76.com/article_info.php?articles_id=9)

---

### Post by Rocket J Squirrel on 2010-04-17
Thanks for the link to the freebie stickers!

IRT backing up, I've been looking for some good app that can backup to a shared folder on my Window network's NAS. No dice, yet. Shell scripts and cron are frequently mentioned on the forum but having just finished writing a lot of backup batch files to drive XXCOPY for all our Windows machines, I'm pretty much burned out on debugging scripts. 

But that's a subject for another thread, no sense hijacking this one.

---

