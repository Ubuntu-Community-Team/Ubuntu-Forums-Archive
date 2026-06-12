---
title: "Hard drive problem"
date: 2011-08-06
forum: General Help
---

### Post by ruseriousb511 on 2011-08-06
Hey guys, 
          First let me apologize if this is in the wrong place but I wanted to post here to get as much help as possible, feel free to move to the correct forum if need be.

I was just checking out the info on my hard drive and I found that my disk has a problem and I have no idea how to fix it or if this is why my upgrades for Ubuntu will not work. 

There is one filesystem volume in my harddrive that is a 30gb linux 0x83 partition type. it says partition bootable and this is where my problem comes in, on my SMARTdata disk security I am getting this problem here :

ID : #5 -

Attribute :  Re-Allocated Sector Count 

Count of re-mapped sectors, When the hard-drive finds a read/write/verification error it marks the sector as "re-allocated" and transfers the data to a special reserved area (spare area)

Assessment : Warning
Normalized : 100
Worst : 100
Threshold : 5
Value : 1507517 sectors
Type : Failure is a sign of imminent disk failure (pre-fail) 

All other ID's and attributes are fine and I have an option of a refresh or a self-test and the self-test says it came back "O.K."    Is this a problem with my pc or is it the Linux partition ? How can I fix it ?

I JUST got this pc and I am freakin out because I dont want it to crash because its freakin sweet but I have no idea what this means or how to fix it.

Can someone PLEASE help me !!!! I will even send you some money via pay-pal if we can get this fixed, I CANNOT have this pc fail on me and I cannot install any other OS's at the moment and need to know if this is why.  

PLEASE HELP, Im freakin out guys.:?:  :icon_frown:

---

### Post by pqwoerituytrueiwoq on 2011-08-06
i would back up anything worth keeping
if it is under warranty tell them the hdd is failing smart
if you want a to see what it says about the hdd with another application here are some in addition to the disk utility
```
 sudo smartctl --all /dev/sda
```also there is this one
[http://www.hdsentinel.com/hard_disk_sentinel_linux.php](http://www.hdsentinel.com/hard_disk_sentinel_linux.php)
extract it to your desktop and run this command
```
cd ~/Desktop/;sudo ./HDSentinel -r
```
there will be a full report on your desktop

---

### Post by ruseriousb511 on 2011-08-07
yeah i did a little research on it and its not good. I will definitely try those other methods, and the laptop is NOT under warranty still. Its about 3 years old and I was curious if there is any to know how long it may last ? Is there a way to backup the Linux/Ubuntu OS so that I can install them on the new HDD when I replace it ? I have about 5 Linux OS's on discs and the  Linux kernel automatically installs and updates with those doesnt it ? Still unsure about how some of this works, there is a lot to learn about this whole Linux thing and my hdd failing doesnt help. Thanks for your suggestions.

---

### Post by pqwoerituytrueiwoq on 2011-08-07
i would do it asap
you can use gparted to copy the partitions (that is what i tend to do) there are more efficient ways i am not familiar with
you will still need to fix the mbr or reinstall grub after copying to the new drive
a new hdd is under 50$ USD unless you want a big one
you can go cheap and get a re-certified drive but if you have to return it the shipping will eat your savings
edit may be worth checking the serial number on the drive to see if the manufacture covers it

```
sudo smartctl --all /dev/sda | grep "Serial Number"
```
[http://websupport.wdc.com/warranty/serialinput.asp?custtype=end&requesttype=warranty&lang=en](http://websupport.wdc.com/warranty/serialinput.asp?custtype=end&requesttype=warranty&lang=en)
[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Test_with_SeaTools_and_Submit_Return&vgnextoid=0df7edc52f0fc010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=Test_with_SeaTools_and_Submit_Return&vgnextoid=0df7edc52f0fc010VgnVCM100000dd04090aRCRD)
[http://www.samsung.com/in/support/warranty/hddWarrantyCheck.do?page=HDD.WARRANTY.CHECK](http://www.samsung.com/in/support/warranty/hddWarrantyCheck.do?page=HDD.WARRANTY.CHECK)
[http://www.hitachigst.com/portal/site/en/support/warranty/](http://www.hitachigst.com/portal/site/en/support/warranty/)

---

### Post by ruseriousb511 on 2011-08-07
what is mdr and grub ?

I didnt install any of this stuff, it was on here when i got the laptop, so i dont know what that is or where to find it for re-install. I am worried about the linux kernel though so that i can still run linux after i get the new one. 

do i just back that up or is it a new download on the new hdd ?

---

### Post by ruseriousb511 on 2011-08-08
I am getting ready to get a new harddrive in my laptop since this is going out, I found one at a local shop and since I dont know how to do this I am going to let the guy at the shop do it (for a pretty penny) and he does not know about the Linux system. 

He wants to install the original Windows XP Professional, should I let himn do this and then install the Linux that I want ? Could I have him install windows xp pro. and then install an Ubuntu distro and get the Linux Kernel when I install the new Ubuntu ? 

Or can I backup the LInux kernel and/or Ubuntu ?

Or should I just buy the hard drive and do it myself by a set of  instructions somewhere, No matter what happens I want the Linux EKernel and distros back.r 

What is the best way to go about doing this ? There is not a whole lot to transfer or back up since the pc was pretty clean when I got it. I just want to make sure I get the  Linux back.

Please help with suggestions and/comments on the best way to do this, and also if you can please insert a link on how to install a hard drive and get the OS on it, I do not want to pay this guy over $100 to it if I can do it myself.

Thanks guys, I really appreciate  the help and support.

---

### Post by anselm on 2011-08-08
Do a search on clonezilla it will do a image of your old hard drive, once you get the new one you can copy the image to your new hard drive and wont have to reinstall anything.

---

### Post by pqwoerituytrueiwoq on 2011-08-08
just go watch a 5 minute howto youtube video
XP takes over 1hr to install ubuntu takes about 10 min or less
see the difference in "on the clock time"
just have him leave the drive black, just plug it in for you if you are afraid to touch it

---

### Post by ruseriousb511 on 2011-08-09
What I want to do is install windows xp pro (that came with the pc) and Linux partitioned side by side, would I be able to do that by myself with these how to videos and software downloads ?

Any links/advice/suggestions/help would be great as I am not tht pc literate but I think I could do this, because I am not a complete idiot either.

Thanks guys for help and support.

---

### Post by dabl on 2011-08-09
> **ruseriousb511 said:**
> What I want to do is install windows xp pro (that came with the pc) and Linux partitioned side by side, would I be able to do that by myself with these how to videos and software downloads ?

Any links/advice/suggestions/help would be great as I am not tht pc literate but I think I could do this, because I am not a complete idiot either.

Thanks guys for help and support.

You can do it.  Here's your guidance:  [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Blasphemist on 2011-08-09
> **ruseriousb511 said:**
> What I want to do is install windows xp pro (that came with the pc) and Linux partitioned side by side, would I be able to do that by myself with these how to videos and software downloads ?

Any links/advice/suggestions/help would be great as I am not tht pc literate but I think I could do this, because I am not a complete idiot either.

Thanks guys for help and support.

This site has very good installation instruction for dual boot of windows and ubuntu. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Ubuntu has a very good installation program that you should be able to understand and use. Do you have windows installation media? If not and if having windows is important to you, you will need to learn about and use cloning software. 

The mbr is the master boot record and a simple way of describing it is that it is a step in taking the boot process from the computers bios (basic input output system) chip to running on the hard drive. Grub, actually Grub2 these days, is the grand unified boot loader. It presents a menu that allows a user to make boot process choices. In a windows and ubuntu dual boot configuration it is what presents the choice of windows or ubuntu. You could say that Grub2 takes over the boot process from the initial program loader (IPL) in the mbr and boots the environment of your choice.

---

### Post by ruseriousb511 on 2011-08-09
One more problem, for the windows xp pro install I have the product key but I dont have the cd for it. I also cannot look it up on the hard drive because the original owner installed linux/ubuntu OVER the windows xp adn all files. 

Any ideas for that ?

---

### Post by ruseriousb511 on 2011-08-09
ok, is the mbr and grub instructions part of that link for the dual install instructions you gave me ? I havent looked at it yet because I am trying to find how to get the windows xp pro software, I need the os and start-up/ boot disc right. Is that one and the same or is it 2 seperate discs ?

---

### Post by Blasphemist on 2011-08-10
The link I posted to Herman's site includes all of the detail you should need. It's focus is not a tutorial on the mbr and grub but it does provide all of the detail on that normally needed.

I don't remember detail of what win xp cd's you need or should try to get. What requirements do you have that require windows? Most all people don't really need windows. Sure some people have some thing they do that makes them think it is required but that's less and less true these days. Again, please be specific about what you do that you think will require windows.

If you can get past a windows requirement you can do a very straightforward install of ubuntu and be up and running very quickly. I think this would really help especially give that you don't know for sure that the hard drive is failing.

---

### Post by ruseriousb511 on 2011-08-10
That is true, I dont need windows for anything in particular, I just wanted to put it on there as a "just in case' type thing. I think what I may fo is go ahead and get the hard drive and put Linux/Ubuntu on it. Then if I decide to at a lter time and date I can add the windows to it later right ?

---

### Post by ruseriousb511 on 2011-08-10
do i need drivers or anything for linux like i would for windows ?

---

### Post by ruseriousb511 on 2011-08-10
do i need the iso, tar, and text or just iso ? What do i need to download from there exactly ?

---

### Post by ruseriousb511 on 2011-08-10
that last is for gparted sorry

---

### Post by Blasphemist on 2011-08-11
Sorry, I've been tied up so to speak. I know you may already have ubuntu installed, up and running. 

Yes, there will be options later for adding windows. That isn't however the easiest windows install. I just think that to wait now for a way to install windows for no real need would be waste of your time. 

About the only driver that may not come with the ubuntu install or it's first updates might be for a printer. That said, I need a cd for my printer (epson workforce 40) for windows but it's plug and play with ubuntu.

You just need to download and burn to installation media the iso. That is a disc image file. Installation media can be a cd or a usb stick. Unetbootin is a free and easy way to make a usb for using. There is plenty of documentation on how to burn a cd.

You can choose try ubuntu when you boot the installation media and then run gparted. That is a good thing to do. It helps you to use the live installation media to ensure your hardware is supported "out of the box" by ubuntu by using it and in the process you get your partitioning done.

---

### Post by ruseriousb511 on 2011-08-11
sweet, I think I am going to get the hard drive in the next day or two anyway.

Thank you for you help and suggestions.

---

### Post by ruseriousb511 on 2011-08-11
i have downloaded some files since I got this laptop and when I do they wont run, I keep getting this error message here :

Archive:  /home/temp/Downloads/7zip.exe
[/home/temp/Downloads/7zip.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/temp/Downloads/7zip.exe or
          /home/temp/Downloads/7zip.exe.zip, and cannot find /home/temp/Downloads/7zip.exe.ZIP, period.


Does anyone know what this means ? Or how to fix it ? 

I have about 3-4 downloads I need but I cannot run them because of this, that is onw reason why I want to get windows as well. So i can download and run some of the stuff I need.

What is this ?

---

### Post by pqwoerituytrueiwoq on 2011-08-11
```
sudo apt-get install p7zip-full unrar
```
then you can open 7zip files and winrar files
check the software center before google

---

### Post by ruseriousb511 on 2011-08-11
what about the others like the driver software (scanner) that I need ? I can get it to download but I cannot run it. 

I also downloaded an iso burner to make an iso bootable but I cannnot run it.

I tried a crucial.com system scanner so I could see exactly what ram upgrade kit I needed but I cannot get ANY of them to run. 

why and how can i get them to run ?

---

### Post by pqwoerituytrueiwoq on 2011-08-12
assuming you are using what you have in your sig (HP Compaq Presario X-6000)
you need DDR2 400 2x1GB (200 pin)
the ram you need is no-longer manufactured your best bet is ebay
if you mean scanner like what is on a printer applications->graphics->simple scan

---

### Post by Blasphemist on 2011-08-12
Files with an exe extension are windows executables. They are executable files written to be used in windows only. The previous post told you how to install in ubuntu the capability to open files created with 7zip but 7zip is a windows zip utility. The crucial scanner is also a windows executable.

There are many programs for creating, opening and using compressed files in linux. As posted earlier, you'll see options in the software center. As for the memory scanner, I haven't looked for one to use in linux. If you have any question about which memory type you need, please post your make and model of pc here and we'll be happy to take a look at it's specs for you and tell you which you need. Memory vendors will also be very willing to do that for you. You could also google for a utility to check for you in linux, I just didn't do that. I just look at the vendor's specs when I need to buy memory and the last time I bought memory my vendor did the same to be sure I was right.

The software center in ubuntu has many thousands of titles available that really will provide for nearly all needs. And there are thousands of other software titles not in the software center but it is recommended to use the software center whenever possible so that all updates will be covered by one process.

---

### Post by ruseriousb511 on 2011-08-12
Ok so I installed wine but it was the beta, and I want to uninstall it and install the regular and for some reason it wont let me uninstall wine OR install anything else. 

Im starting to not like Linux/Ubuntu now because of stuff like this, yes im a newbie but wow, why does this stuff have to be so difficult. Do i need to install an uninstallation something to do it or install another program to install something else ? 

This is getting ridiculous, go ahead and say it, "what an idiot" but what gives ?

I dont know much about what is on here and how it was done because I didnt install it. All i know is what i know from messin around on here and what you guys say. 

What all do i need to be able to run .exe programs and to be able to install and uninstall stuff. Also what is the best backup program ? I think if I install a fresh Linux distro I may be able to do more because I dont know much about this one.

also you put in commands by hitting alt,ctrl+F7 right ? It says : "ubuntu login" there
what is my login or do i need it ?

Thank you for your time and patience with me.

---

### Post by ruseriousb511 on 2011-08-12
so i think i did something wrong, for some reason I cannot install from the software center anymore, I can look anything up but i cannot actually instaall from there, I am haveing to use the synaptic package manager to install anything.

I guess it doesnt matter I am getting ready to reinstall a new hard drive anyway but what gives ? I just like to know

---

### Post by pqwoerituytrueiwoq on 2011-08-12
> **ruseriousb511 said:**
> so i think i did something wrong, for some reason I cannot install from the software center anymore, I can look anything up but i cannot actually instaall from there, I am haveing to use the synaptic package manager to install anything.

I guess it doesnt matter I am getting ready to reinstall a new hard drive anyway but what gives ? I just like to know
we will need a error message or at last a description of exactly what is not working

---

### Post by ruseriousb511 on 2011-08-13
there is no error message at all, thats the thing. For some reason I just cant install or remove from the software center.

I go to click the install or remove tabs and it does nothing. It lights up the tab but nothing happens, no prompts for installation or removal. Its like the tabs are dead, or dont work.

If i go to synaptic package manager though i can do whatever i need to. Not sure why it did that all of a sudden but no big deal, Im more worried about getting this new hard-drive and getting everything installed correctly. 

I have everything now i think, i just need to go pick up the hard drive and i think i am good to go. I have 5-6 linux distros on live cd's and ready to go for when i do get the hard drive put in.

Also I dont have much on this pc in the way of files and such so I dont really need a back up disc to install because i am going fresh from the new hard drive, starting from scratch so, wish me luck and any more suggestions o pre-install of a hard drive would be useful.

 Is there anything you guys can think of that I may need to do before a fresh install of windows xp pro (maybe) and/or linux on a new hard drive ?

---

