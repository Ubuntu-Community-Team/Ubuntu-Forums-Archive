---
title: "Partition Mayhem ?"
date: 2009-09-27
forum: General Help
---

### Post by Phil Newman on 2009-09-27
Hi everyone :P Not exactly sure if this has been covered already :( but I installed Ubuntu 9.04 yesterday (27/09/09) and while it seems to be working well,I was a bit mystified on the way it handled the partitioning of my hard drive. I had some new hardware installed two weeks ago and asked the "techie" guy to partition into two partitions so that I could dual-boot into Linux and Windows.
He did that tho' I did lose a little bit of stuff but that's ok,so what I ended up with was an 80GB hard drive with WinXP on one partition of about 35Gb and the rest free space.
Now after installing Ubuntu and checking on Windows Disk Management I find I have the below mentioned partitions :
C:/ 26.50 GB's Healthy (NTFS)
7.31 GB's Healthy ( Unknown )
384 Mb's Healthy ( Unknown )
D:/ 38.35 GB's Healthy ( NTFS )
2.50 GB's Free Space
2.33 GB's Healthy ( Unknown )
173 Mb's Healthy ( Unknown )

My question is: Is this normal after installing Ubuntu or has something gone crazy with my installation and should I delete all partitions except for C:/ and start again ?
Any help would be gratefully appreciated :P

---

### Post by HermanAB on 2009-09-27
Windows is too stupid to understand Linux partitions.

---

### Post by akakingess on 2009-09-27
First of all, HermanAB is correct, Windows will not see or even if they do they won't understand Linux partitions as they are formatted in either ext3 or ext4 which Windows doesn't know. Now, the 55 Gb that should be free (the other 35 going to Windows) should have at LEAST 2 partitions, if not more. Let me explain, 1 partition should be the root or OS partition for Ubuntu and you should give it about 15Gb. Second, there has to be a Swap partition, size should vary based on how much RAM you have, but 1 or 2 Gb should suffice. That should be all you need, but I would use the remaining space and partition it and format it ext3 and tag it as the /home partition (it may be called /usr, I can't remember it's been so long) at that should do it.  Please post if you have more questions.

Edit: By the way, never use Windows disk utilities for drives that you are using for Ubuntu as they will not understand ext3 or 4 and possibly mess things up. If you want to look at the drive and repartition, boot up off of the Ubuntu Live CD and run Gparted. That will tell you all you need to know.

---

### Post by 3rdalbum on 2009-09-28
It looks like both hard disks have been repartitioned.

We might be able to get more of an insight if you can post the output of:

```
sudo fdisk -l
```

in Ubuntu, as it gives more information.

---

### Post by Phil Newman on 2009-09-28
Hi everyone :) I actually deleted all partitions except WinXP because I want to keep that for awhile,re-booted ant then got the message "Grub Loading Stage 1.5:Grub Loading Please Wait:Error 22" so I rebooted again with my Linux disc inserted into CD drive,booted from CD,re-installed Ubuntu and when it came to the bit about partitioning again,I just split the hard drive as close as I could to half each.
Now I seem to have three partitions :
C: 35.03 GB (NTFS) WinXP ( Healthy )
?    37.83GB ( Ubuntu 9.04 ) Healthy
1.66 GB ( Healthy) God knows what this is and I'm not messing with it anymore.
So thanks for all the help and you'll probably see me again if I have more problems which I no doubt will but I have to leave now :(

---

### Post by akakingess on 2009-09-28
The 1.66 GB partition should be your Swap partition (necessary for Ubuntu/Linux).

---

### Post by Phil Newman on 2009-09-29
Tis too "akakingess" I decided to go into my Linux distro and have a look at Gparted and it came out with the following partitions :)
/dev/sda1 NTFS 34.03GB (24.9BG Free )
/dev/sda2 Extended Partition 39.50 GB
/dev/sda5 ext3 37.83 GB
/dev/sda6 Linux Swap File 1.66 GB 
So basically it seems to have gone ok but I'm still kind of worried that if I ever decided to upgrade perhaps to Ubuntu 9.10 which I think is coming out this month,I'd probably do something wrong and stuff it up completely. Mind you I still have to do all the updates on this version before I start thinking about the next one. Thanks a lot for your time and patience.
PS: 3rdalbum was saying that I should post "sudo fdisk-1" onto this site :) But as a complete beginner I really don't know how to do that :( Ah well I'll get it sooner or later :)

---

### Post by akakingess on 2009-09-30
to post the fdisk -l, just open up a terminal, in other words go to Applications---->Accessories---->Terminal, that will open a terminal into which you should type in```
sudo fdisk -l
```please note that first of all that is a space then a hyphen and then the letter l, second of all, since you are doing sudo (which means you are doing this command as root) it will ask you for a password, if you are the one that did the install, it should just be your password you enter, then whatever it prints out in the terminal is the output of fdisk -l and that you can copy and paste into a post.  Now for my question to you, when you went into gparted, were the partitions labeled, in other words I believe there is a label field, and at least one of the partitions must be labeled with just a /, that would be where Ubuntu is installed, another has to be labeled swap, which shoud be the 1.6 GB parition, and I am hoping that the other partition is labeled /home, which would be where all of your home directories would be stored, for both yourself and any other users that you decide to add to your machine, if you decide to add other users to it. The output of fdisk -l will not show if a partition is labeled as home or not, unfortunately, so you would need to go into Gparted for that. Sorry it took so long to respond, but let us know what you find out and post the output of fdisk -l as well, as it may be helpful.

---

### Post by Phil Newman on 2009-10-02
Thanks for that "Kingess" :P Will do that and let you know how I get on,tho' I think I haven't got a partition called home.It's WinXP on one,then another large partition with no name,then the small 1.66GB partition which you correctly identified as "swap" :)

---

### Post by Phil Newman on 2009-10-02
Tis me again ](*,)<- This is what I feel like at the moment :confused: I went into Gparted and looked and it came up with the following partitions which I think I've listed before :
/dev/sda1  NTFS 35.03 GB ( WinXP ? )
/dev/sda2 Extended 39.50 GB ( Ubuntu 9.04 I think )
This breaks down to :
/dev/sda5 37.83 GB ( Which is the whole partition apart from )
/dev/sda6 1.66GB ( Linux swap file )
I tried to copy and paste sudo fdisk-1 but I failed miserably and there doesn't seem to be a separate partition for "Home" which I suppose I should create sooner or later :( 
Tell me if I'm wrong but isn't Copy & Paste the same as Ctrl+C then Ctrl+V

---

### Post by jward3010 on 2009-10-02
Trust me, one of the nicest things about Linux is it's partitioning system and GRUB. When you get to know what it all means it becomes so easy and powerful so don't get scared. Great thing about GRUB is it's ability to autodetect other Windows systems on a drive and install options for booting off them. So I'd say experiment like crazy with Ubuntu partitioning and don't worry, you're Windows partition will be safe (unless you accidentally delete it of course, see below, point 4). Couple of simple ground rules:

1. All linux installs require at least 2 partitions: One for the operating system (called root or "/") and one for swap (this is the same as paging file in Windows, memory overflow).

2. The root one (/) will be whatever size you want to make it, it will be where the OS is installed and where you're /home folder will be for your music, pictures, files, documents etc. so make it as big as you want. Swap should at least be the size of your memory and if possible, double the size.

3. In the case where you're starting from scratch with an empty disk, always install Windows first and Ubuntu second. Why? Well Ubuntu can understand Windows is there but Windows can't understand that ANYTHING else is there (except it's own systems - XP, 2000, 98, 95 etc.) and will overwrite any boot sectors that have been put in place by other systems, rendering you're Ubuntu system inaccessible unless you run GRUB tools. Whereas when you install Ubuntu after XP is done, it checks for other installed systems and gives options to access them.

4. Most important: BACK UP ALL IMPORTANT DATA BEFORE YOU TOUCH ANY PARTITIONING TOOL. You never know what you may accidentally hit or what you may unintentionally delete without realising.

---

### Post by jward3010 on 2009-10-02
> **Phil Newman said:**
> 
I tried to copy and paste sudo fdisk-1 but I failed miserably 

To be clear that's an "L" as in linux, not a "1" as in One. And theres a space between the "fdisk" and the "-l". So:
```
sudo "space" fdisk "space" -l ||| sudo fdisk -l
```

---

### Post by Phil Newman on 2009-10-02
Thanks "jward3010" I'll try that again. As you may have realised by now I'm a complete twerp when it comes to some of these commands but I suppose I'll get the hang of it sooner or later

---

### Post by Phil Newman on 2009-10-02
**OK Everyone This is what I got when I did that "sudo fdisk -l" thingie but "Copy&Paste" no can do from Ubuntu to Windows :(**

[B]Disk/dev/sda: 80GB 80026361856 bytes
255 heads,63sectors/track,9729 cylinders
Units=cylinders of 16065*512=8225280 bytes
Device Boot       Start          End                   Blocks           ID               System
/dev/sda1            1           4573                  36732591         7             HPFS/NTFS
/dev/sda2       4574           9729                  41415570         5             Extended
/dev/sda5       4574           9512                  39672486        83            Linux
/dev/sda6       9513           9729                  1743021         82             Linux/Solaris[/B]

[B]I hope this is what you guys were looking for :P I checked and rechecked all the info before I posted it on here and as I was writing it down :( but I'm 100% it's right.
Cya around pretty soon but I'm going to have lunch right now at's 11:55am in my part of the world.[/B]

---

### Post by Phil Newman on 2009-10-03
[B]Disk/dev/sda: 80GB 80026361856 bytes
255 heads,63sectors/track,9729 cylinders
Units=cylinders of 16065*512=8225280 bytes
Device Boot         Start                   End              Blocks                       ID                          System
/dev/sda1            1                4573          36732591           7                                  HPFS/NTFS
/dev/sda2               4574                      9729                           41415570                 5                                 Extended
/dev/sda5               4574                      9512                           39672486                83                       Linux
/dev/sda6               9513                      9729                            1743021                    82                                 Linux/Solaris[/B]

**Sorry about re-posting this :( but I thought it might be easier to figure out what was going on if I separated the info a bit more :) Thanks to everybody who's trying to help me here :)**

---

### Post by Phil Newman on 2009-10-03
[B]Disk/dev/sda: 80GB 80026361856 bytes
255 heads,63sectors/track,9729 cylinders
Units=cylinders of 16065*512=8225280 bytes
Device Boot                 Start                           End                           Blocks               ID                                                                  System
/dev/sda1                       1                          4573          36732591             7                                    HPFS/NTFS
/dev/sda2             4574      9729          41415570             5                                     Extended
/dev/sda5             4574      9512          39672486             83                                       Linux
/dev/sda6             9513      9729          1743021               82                              Linux/Solaris

OK :( This is the last time I'm going to put this up here,but I think it reformats the info from left to right and I'm sorry if it looks weird :(
[/B]

---

### Post by fela on 2009-10-03
You don't actually need a separate home partition - it can work just fine if everything (except swap - although you can even have this on the same partition) is on the same partition. It seems like you did the default ubuntu way of doing things and everything (except swap) is on one partition, which is fine for most people.

By the way it's fdisk -l (letter l as in lantern), not fdisk-1 (number 1).

About the copy/paste conundrum: in the terminal, Ctrl+C means end current program, and Ctrl+V might mean something, so the copy and paste shortcuts in the terminal are Ctrl+Shift+C and Ctrl+Shift+V respectively.

EDIT: missed the second page, d'oh!

---

### Post by Phil Newman on 2009-10-04
Thanks "fela" :) Yea a couple of the other guys explained that to me about the 1 and the l but I'm still wondering if and when I'd like to update to Ubuntu 9.10 :) would I have to remove the old version or does it just get overwritten ? I suppose if one applies all the updates as they come out :) you automatically get bumped up to the next version yes :) Love your avatar :)

---

### Post by fela on 2009-10-04
With most ubuntu releases it's alright to just use the update manager, but with Karmic I recommend doing a clean install (just backup your data to a external drive or something). This is because karmic includes a new bootloader amongst other things.

By the way Fela is my real name :)

---

### Post by jward3010 on 2009-10-04
I'm with fela on this one, grub2 (well 1.97 beta 3 or something) is coming with this release and it differs from previous grub, a future update might mess things up or you may never end up with grub2 and problems may ensue . 

Karmic Beta is just released, still a little incomplete here and there so prepare for something a bit rough.

---

### Post by Bartender on 2009-10-04
Hey, Phil, it's pretty easy to copy/paste from within Ubuntu, then bring it over to Windows, with a thumb drive.

Start up Ubuntu (or even Ubuntu LiveCD) and get to the desktop.  Plug in a thumb drive and wait for it to be recognized on the desktop.    

Say you copy something like your fdisk -l output.  Open OpenOffice, paste the text into a new document, then save as .txt file.  Save it to the thumb drive.  Make sure to right-click on the thumb drive from the desktop and "Eject the Volume"!  This is more important in Linux than it is in Windows.

When you get out of Ubuntu and start up Windows, your file will be on the thumb drive and you should be able to open it even in Word.  This works even better if you have OpenOffice in your Windows install too - then you can just save the document and not worry about formatting it as .txt.

---

### Post by jward3010 on 2009-10-04
Even easier, use gedit in Ubuntu as opposed to OpenOffice Word Processor. It's much simpler, uses less memory and you will see your text as fixed-width just like the terminal text.

---

### Post by Phil Newman on 2009-10-04
Sorry about all the confusion regarding your name fela :( Tis kinda funny though what's happening on this machine.Every time I open Ubuntu, "Update Manager" tells me there's a whole bunch of stuff waiting to download,so I go to "install-update" or whatever that thingie is.It spends about 15 mins updating and when it's finished and I go to Install,it says to me that the downloads have failed.And yes I am online when I'm doing this. Any suggestions. By the way when I was downloading updates the very first time,I didn't want to install a printer as I don't use mine anymore but it still wouldn't let me ignore the "cups" updates which I think relate to that. Ah well I still prefer it over Windows and in time I suppose I'll get as good as you guys :)

---

### Post by Phil Newman on 2009-10-04
Hi "Bartender" :) Thanks for that info :D But I have noticed that when I'm messing around with external or thumb drives (I have a 320GB WD drive and a 500GB Maxtor and about  6 USB sticks of different capacities ) under Ubuntu and I r/click to as you say "Eject the Volume" all I get is the option to unmount.
Is this the same thing because I noticed under Windows when I clicked on "Remove Hardware" after awhile the little lights went out on the drives that had them and a notice came up on the taskbar saying "It is now safe to remove hardware"
This doesn't seem to happen under Ubuntu so I'm never really sure whether to leave them attached or not :'(

---

### Post by Phil Newman on 2009-10-05
[ATTACH]130818[/ATTACH] Hi again everyone :D I've done a bit of running around and I think I finally got that sudo fdisk -l thingie on here as some sort of an attachment but then again I'm not really sure :confused: Ah well have a look ( if you can ) and tell me what you think :P

---

### Post by Vaphell on 2009-10-05
your hdd = [ windows ] [ [ linux ] [ swap ] ]
looks just fine

---

### Post by jward3010 on 2009-10-05
> **Phil Newman said:**
> Hi "Bartender" :)under Ubuntu and I r/click to as you say "Eject the Volume" all I get is the option to unmount.
Is this the same thing because I noticed under Windows when I clicked on "Remove Hardware" after awhile the little lights went out on the drives that had them and a notice came up on the taskbar saying "It is now safe to remove hardware"
This doesn't seem to happen under Ubuntu so I'm never really sure whether to leave them attached or not :'(

This is completely safe, clicking on unmount prevents the system from accessing the stick (reads or writes) and hence makes the stick safe for removal.

In Karmic they've changed it and now it says "Eject the volume" and when you do it unmounts the stick and kills the power to the USB port more like Windows so now it's even more safe, and should make you feel more reassured that its ok to remove.

---

### Post by jward3010 on 2009-10-05
> **Phil Newman said:**
> Sorry about all the confusion regarding your name fela :( Tis kinda funny though what's happening on this machine.Every time I open Ubuntu, "Update Manager" tells me there's a whole bunch of stuff waiting to download,so I go to "install-update" or whatever that thingie is.It spends about 15 mins updating and when it's finished and I go to Install,it says to me that the downloads have failed.And yes I am online when I'm doing this. Any suggestions. By the way when I was downloading updates the very first time,I didn't want to install a printer as I don't use mine anymore but it still wouldn't let me ignore the "cups" updates which I think relate to that. Ah well I still prefer it over Windows and in time I suppose I'll get as good as you guys :)
In regards to errors with updating your system, try a manual terminal based update. It will help us figure out whats going on a little easier. Open a terminal and type:
```
sudo apt-get update
```
When that finishes:
```
sudo apt-get upgrade
```

---

### Post by jward3010 on 2009-10-05
Don't worry about the CUPS updates either - it's part of Ubuntu and so will get updated like lots of other things which you may NEVER use, a whole heap of commands for one thing. Installing the CUPS update wont slow you're system and will protect you from possible security vulnerabilities. The other thing you could possibly do is uninstall cups BUT (and I've just tried it) it will remove the desktop as well, so don't bother. It's what they call a metapackage - part of a baseline of many different packages and made reliant on each other (unfortunately). For example the ubuntu-desktop package consists of GNOME for the panels, nautilus for folder management, metacity / compiz for window compositing etc. etc. It's a package with lots of other major stuff in it. CUPS seems to be included in ubuntu-desktop, hence remove CUPS and you get rid of the desktop. Stupid but thats Ubuntu sometimes.

---

### Post by fela on 2009-10-05
> **jward3010 said:**
> 1. All linux installs require at least 2 partitions: One for the operating system (called root or "/") and one for swap (this is the same as paging file in Windows, memory overflow).

That was a good post but I just wanted to correct you on that. You can have a one partition Linux install with a page file if you wish. Something like (**don't just run this**):

```
sudo dd if=/dev/zero of=/swapfile bs=1073741824 count=1
sudo mkswap /swapfile
sudo swapon /swapfile
```

That will make a 1GiB swap file on your root partition. It's not meant to be run necessarily, it's just a proof-of-concept.

---

### Post by Phil Newman on 2009-10-05
:popcorn: Wow :P:P You guys really rock.Thanks for all the info :KS It's very helpful and I appreciate it a lot. Everything here as far as Ubuntu goes seems to be working well and last night everything updated successfully and seems to be ok.
Now :confused: For my next set of questions :cry: How does one import/export things like My Favorites,Outlook Express, and especially :confused: This is a biggie for me.How do I get .wmv and .wma files to play on Ubuntu. Do I have to convert them to .ogg vorbis and as I have a whole heap of "You-Tube" videos which I downloaded and then converted to .wmv,should I download again because fool that I am I deleted the originals after converting. In other words would I lose quality in converting .wma to ogg vorbis or back to flash video ?

---

### Post by jward3010 on 2009-10-05
No, even horrible proprietary formats like wma and wmv can be played by installing ubuntu-restricted-extras. You need to enable a repository first (a storage server for software if you will): [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Follwow the instructions to install the repository and you'll have all software available in the ubuntu-restricted-extras package.

1. Enable the repository.
2. Install the package:
```
sudo apt-get install ubuntu-restricted-extras
```

In reagards to importaing Outlook Express - I don't think so somehow, not directly anyway.

---

### Post by Phil Newman on 2009-10-05
By enabling the repository "jward3010" did you mean that I would have to type in all those 3 lines of code that are on the "Medibuntu" at the beginning and then type in what you gave me up top ? Or should I just type in your code and then it'll install automatically :D

---

### Post by jward3010 on 2009-10-06
You'll notice on the medibuntu site that this is the one to use to add the repository to any edition of Ubuntu:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

After that finishes, type my one out:
```
sudo apt-get install ubuntu-restricted-extras
```

In a way, I don't think the medibuntu repository is absolutley necessary for 95% of the packages included in the ubuntu-restricted-extras metapackage but w32codecs is one of the packages that the medibuntu repository needs to be enabled for and this one plays those windows based formats.

---

### Post by Phil Newman on 2009-10-06
O shite :( jward10 I used your code first and it downloaded all these packages and then at the end it just sat up and laughed at me :( It finished downloading and then the cursor was blinking,waiting for me to type something and I didn't know what to do :( I should have waited for your response. If I went back and did it again,what would happen? Has it been actually installed on "my pewter" or do I have to do it again and then use your code ? Betcha you're getting sick of me asking all this stuff ;) Actually I won't be here tomorrow ( doctor's appointment and some other stuff as well ) but I look forward to your help :)

---

### Post by jward3010 on 2009-10-06
A blinky cursor after apt-get did stuff is not brilliant but the great thing about apt is it's more resilient than Sylvester Stallone in the middle of a fire fight. Try this:

This will fix any broken dependencies or broken apt jobs, if thats happenend:
```
sudo apt-get install -f
```

Then run it again:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Phil Newman on 2009-10-07
[ATTACH]131075[/ATTACH] Hi again Tis me :( I tried what you said "jward" but it seems to have stumped itself for some reason :confused: I'm actually considering deleting the whole partition and starting again :( What do you think :( Can you make any sense out of the screenshot/attachment ? I'm still not sure whether anything has loaded itself on here.

---

### Post by Vaphell on 2009-10-07
there is nothing wrong in starting over if your system was not set up - not that it's so pleasant to do it over again but at least you will become more familiar with it and will learn to do some basic configuration wihout any help :-)

---

### Post by Phil Newman on 2009-10-07
> **Vaphell said:**
> there is nothing wrong in starting over if your system was not set up - not that it's so pleasant to do it over again but at least you will become more familiar with it and will learn to do some basic configuration wihout any help :-)
Hi "Vaphell" Thanks for that info :P I may just carry on with it as is for awhile and see what happens anthough I think that's probably what I'll end up doing :'(
Just a couple of questions though. How do I increase the size of the "swap file" as I have 2GB of DDR2RAM on here and I've heard that it should be 1.5 times the size of this?
Also how do you specify where you want to download a file to as I tried to download two games the other day and one seems to be invisible while the location of the other I finally found on "My Desktop" Now I had changed the background picture of that about three days before I downloaded this stuff and there was absolutely nothing on there :confused:

A quick story about meself :P I started messing about with PC's back in 1999 (Win98SP) and in that first year a friend of mine had to reformat this machine about 9 times :shock: 
This guy who was really into PC stuff said to me he'd never seen anybody lose the file "command.com" before and said I should sell it and get a bicycle instead :rolleyes:
But I said no "I'll persevere" and I did :P So here I am today wanting to start anew with "The Penguin"
Thank you to everybody here who's given me advice so far and I really appreciate it :)

---

### Post by oldfred on 2009-10-08
There is a lot of different opinions on swap. Once upon a time it was straight forward. When memory was only 256MB or  512MB you needed two times as swap. Then when memory got to 1GB swap became less important. I have heard of people with 2 or 3GB memory running without swap.
If you are using a portable you may need swap to be the same size as memory to allow hibernation. Swap is otherwise only used if you have some very memory intensive applications. 
If you do want to adjust swap size you have to use gparted from the liveCD or Gparted live cd. Nothing can be mounted when you edit partitions. The live CD may mount swap so even then you have to do swapoff to unmount it.

---

### Post by jward3010 on 2009-10-08
I agree on this one. Ubuntu sets itself up so nicely within the space you decide without problems that you shouldn't see it as a bad move. The learning and confidence you gain from it as well is invaluable.

---

### Post by jward3010 on 2009-10-08
In regards to the last error you receive (apt-get autoremove) it's because you didn't do it with sudo in front. I noticed in your text file.

---

### Post by Phil Newman on 2009-10-08
Yea I know "jward3010" :( Would it still work if I did it again? I mean installing everything you said and using auto-remove to get rid of the extra stuff :) I think I'll have to write all this down before I plunge in or I know I'm going to stuff something up. Hey I was using that GIMP editor on a couple of old photos of mine that were too bright and overexposed and that is a brilliant little app. I used to have Paint Shop Pro on here a few years back but that's so complicated to use :) Thanks again for the help.

---

### Post by Phil Newman on 2009-10-08
Thanks for that "oldfred" :) I don't think I'll bother then because this is a "Desktop" and I never use the "hibernate" function anyway. When I finish for the day,I just turn it off and unplug the modem as well.
I had a look at that "gparted" thingie and it looks like I could get myself into some sort of problem using that,however somewhere down the road,I'll want to increase the Linux partition and just keep WinXP for the odd bits n pieces perhaps.

---

### Post by Phil Newman on 2009-10-12
Ok guys :confused: I know this doesn't really belong in this discussion but I was just wondering what type of files that "Rythmbox" plays ? I tried converting some of my .wmv and .flv files to .ogg but I still couldn't open them :redface: Any suggestions ?
 And also a reply to "jward3010", I managed to get all that info installed the other day that you told me about "ubuntu-restricted-extras" but still at the end,it really didn't seem to do anything and I still can't open any music files,all of which by the way are on an external drive and I'm wondering if this has any bearing on my problem :( Thanks heaps for anyone who want's to throw their hat in the ring here with any suggestions :P

---

### Post by jward3010 on 2009-10-13
Ubuntu is set up for legal reasons not to include any proprietary codecs but basically to answer your question it plays every file possible, well in terms of audio files anyway (MP3, AAC, WMA, WAV, OGG, FLAC etc). Rhythmbox as such doesn't play them, codecs and "stuff" (pipelines) in the background called GStreamer actually does the playing with rhythmbox just a face on those background codecs.

To install those proprietary codecs you need to do two things (only really for this stuff, you wont have to do this often - it's all down to legal stuff and getting horribly sued):

1. Add the "medibuntu" repository to your list of software sources, see here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

2. Install the "restricted" package:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by oldfred on 2009-10-13
This howto discusses all the extras you can add.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Phil Newman on 2009-10-13
Thanks for that info "jward3010" and "oldfred"  :) But I went the crazy way and uninstalled "Rhythmbox",installed a different player form "synaptic manager" went back to Windows and converted all my .wmv to .ogv and now have no problems playing the files. It may have been a long way of doing it,but it seems to have worked. If I do anymore downloads I'll just convert them straight from .flv to .ogv because as I found on WinXP and I don't know if this is the same in Linux. You can't play a whole folder of .flv files but have to do it individually.

---

### Post by Phil Newman on 2009-10-13
Oooooo yea and as far as adding that "medibuntu" repository goes :( I don't know how many times I've done that and I'm still not sure it has installed properly :'(

---

### Post by jward3010 on 2009-10-14
> **Phil Newman said:**
> Oooooo yea and as far as adding that "medibuntu" repository goes :( I don't know how many times I've done that and I'm still not sure it has installed properly :'(

If the code finishes without errors then it's fine. You can also check the Administration menu > Software Sources to see if it got installed.

---

### Post by Phil Newman on 2009-10-14
Hi "jward3010" :) I checked where you said and there appears to be two packages as below :
(1) Medibunt-Ubuntu 9.04 "jaunty jackalope free-non free
(2) Medibuntu (source) Ubuntu 9.04 "jaunty jackalope" free-nonfree ( source code ) 
so that looks like it installed ok :)
Now as for the movies,they seem to be playing on Totem Movie Player 2.26.1 and I had actually converted them from .wmv to .vob :) My email program seems to work and there might be a few other small issues from time to time but for now I guess that's about it. There's a lot of stuff to using Linux I suppose and me just being a point & click Windows guy for the last ten years,I'm finding it a bit overwhelming :( Still thanks for everybody's help :)

---

