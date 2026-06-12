---
title: "Currently have 9.04 on laptop, need to go back to XP."
date: 2009-08-23
forum: General Help
---

### Post by johnnydotexe on 2009-08-23
How do I do that if it won't boot from a known-good windows disc?  It just sits at a black screen, HDD light on constant but I don't feel or hear the HDD or CD drive running.

Please do not post in this thread if you're just going to dump all over it with "omg windoze, why?"  Why?  Because after over a week I still can't establish a simple LAN between this laptop and a windows desktop, and my help thread offered no help mainly because only 1 guy responded and his instructions didn't fix the issue.   I don't have the time to waste on simple tasks that would take seconds using Windows.

---

### Post by lisati on 2009-08-23
Sometimes Windows installation disks get confused when the first partition on a disk that is found isn't in a format that Windows recognizes. 

The solution that comes to mind is to make a backup your important data, and reformat the first partition to something that Windows recognizes e.g. NTFS

---

### Post by johnnydotexe on 2009-08-23
There's no important data on this laptop, just a fresh Ubuntu 9.04 install.

How do I format the first partition?  If it were a desktop I could just hook the HDD up to my windows-desktop as a secondary and run PM8.

---

### Post by Efwis on 2009-08-23
use the live cd for ubuntu, then reformat the hdd with gparted to ntsf. next put your windows disk in and run the installation.

the problem is Windows doesn't recognize the boot loader system that Linux uses.

---

### Post by johnnydotexe on 2009-08-23
What do I go to once I'm at the Ubuntu disc-bootup menu?  I don't see anything about gparted or formatting.

---

### Post by Efwis on 2009-08-23
load the live cd in user mode, then open terminal and type
 gparted

that should start gparted for you

---

### Post by johnnydotexe on 2009-08-23
It's telling me that gparted can only be run in root mode, I loaded Ubuntu from the disc...did I do something wrong?  Kinda confused here, I've got maybe 8 hours of experience total with linux/ubuntu...

EDIT: Nvm, had to run sudo gparted.  Gonna see if I can run this software now, will update if I have any issues.

---

### Post by brons2 on 2009-08-23
> **johnnydotexe said:**
> There's no important data on this laptop, just a fresh Ubuntu 9.04 install.

How do I format the first partition?  If it were a desktop I could just hook the HDD up to my windows-desktop as a secondary and run PM8.

You can do that with laptop hard drives as well, go buy one of those universal hard drive connector thingys that plug into a USB port.  I got one at Fry's, but I'm sure that other retailers carry them.  This is the one that I have:  [http://www.apricorn.com/product_detail.php?type=family&id=39](http://www.apricorn.com/product_detail.php?type=family&id=39)

You can also use something like Darik's Boot and Nuke (DBAN) to completely zero out your hard drive.  [http://www.dban.org/](http://www.dban.org/)

This being said...if Windows were so easy, why are you at a **Ubuntu** forum looking for help to get it reinstalled?  There's nothing special about Linux that makes it impossible to install Windows back over it.  It sounds more like a problem with your CD drive or your CD.

I once had a box that I could not reinstall Windows back onto no matter how hard I tried, but it installed Ubuntu 9.04 just fine and is running as we speak.  It had some oddball ALI chipset in the motherboard, maybe that had something to do with it.  But, I  digress.

---

### Post by johnnydotexe on 2009-08-23
See above posts for reasons why my known-good windows disc wouldn't install, a disc I used 2 weeks ago to install windows on this laptop, before deciding to try out ubuntu.

---

### Post by cmost on 2009-08-23
It's really sad when people make their first tentative steps into the world of Linux but then run back to Windows at the very first sign that "OMG!!  Something is different!!!"  I'm not sure what problem you were having connecting your Ubuntu system to a Windows network, but I'm sure the problem can be sorted quite easily.  I have several Linux systems talking to a Linux server emulating a Windows domain and there are no problems.  That being said, Gnome is NOT as intuitive in this area as KDE.  My recommendation is to use smb4k (sudo apt-get smb4k).  This fantastic little utility acts like Windows' 'My Network Places' on steroids.  It will allow you to easily mount any available Windows shares with ease.  Check it out before putting back on the shackles that is Microsoft Windows.  Good luck!  :P

---

### Post by johnnydotexe on 2009-08-23
> **Efwis said:**
> use the live cd for ubuntu, then reformat the hdd with gparted to ntsf. next put your windows disk in and run the installation.

the problem is Windows doesn't recognize the boot loader system that Linux uses.

gparted would only let me format the first/biggest of the three partitions...wouldn't let me delete/edit/resize/etc the other two smaller partitions.  I reformatted the first/biggest one in NTFS, rebooted, tried to boot from windows disc and I'm having the same issue.  Sitting at blank screen, apparently no activity from disc drive or HDD.

---

### Post by johnnydotexe on 2009-08-23
> **cmost said:**
> It's really sad when people make their first tentative steps into the world of Linux but then run back to Windows at the very first sign that " OMG!!  Something is different!!!"  I'm not sure what problem you were having connecting your Ubuntu system to a Windows network, but I'm sure the problem can be sorted quite easily.  I have several Linux systems talking to a Linux server emulating a Windows domain and there are no problems.  That being said, Gnome is NOT as intuitive in this area as KDE.  My recommendation is to use smb4k (sudo apt-get smb4k).  This fantastic little utility acts like Windows' 'My Network Places' on steroids.  It will allow you to easily mount any available Windows shares with ease.  Check it out before putting back on the shackles that is Microsoft Windows.  Good luck!  :P

Over a week, two different threads on this forum...and still can't establish the most simple LAN between this laptop and a windows-desktop.  Drivers are installed by default and work, the hardware is all 100% operational.  It should work by default and doesn't.  Hours upon hours of searching the web, changing settings, etc...still nothing.  No thanks @ that, I very much prefer my XP Pro over this.

---

### Post by brons2 on 2009-08-23
> **johnnydotexe said:**
> See above posts for reasons why my known-good windows disc wouldn't install, a disc I used 2 weeks ago to install windows on this laptop, before deciding to try out ubuntu.

Maybe you scratched it since then.

I repeat my suggestion to use DBAN to wipe the drive if you really want to wipe it out.  You can even do a DoD compliant wipe if you really want to be thorough (I suggest just zeroing out all the sectors which takes much less time).

---

### Post by SunnyRabbiera on 2009-08-23
Well what was you issue with LAN?
We could help you if you just have some patience, what were you trying to do?

---

### Post by sandyd on 2009-08-23
> **SunnyRabbiera said:**
> Well what was you issue with LAN?
We could help you if you just have some patience, what were you trying to do?

hes trying to attach one end of the network cable to ubuntu and the other end to windows. or rather, thats what it sounds like hes trying to do. 

while doing this, you gotta set a static ip for each computer, point the dns servers properly and everything. i had to do the same thing before (but between windows/windows) i bought a router.

unfortunately, most people in this forum have a router/hub of some kind. this is why 99.9% of people can't answer his question.

I simply advise him to go to the closest electronics store and get a router, wired or not. its not too expensive.

---

### Post by johnnydotexe on 2009-08-23
No scratches, this disc is flawless...and so is the other XP Pro disc I have.  Tried both, no go.

Can I run the suggested software with no OS installed?  I deleted the main Ubuntu partition already...

> **SunnyRabbiera said:**
> Well what was you issue with LAN?
We could help you if you just have some patience, what were you trying to do?

I have a cat5 crossover cable connecting my ubuntu-laptop to my windows-desktop.  I get online with the windows-desktop by tethering my Alltel Blackberry Pearl and using the Alltel Axcess software.  On the windows-desktop, internet sharing is on with an IP set to 192.168.0.1 and a Netmask of 255.255.255.0 in the TCP/IP properties.  I have sucessfully gotten online this way with an xBox, and 4 windows-laptops.

On this ubuntu laptop, the connection will work sometimes and won't work other times.  When it doesn't work, or I disconnect it and attempt to reconnect...it won't work until the windows-desktop is rebooted for some unknown reason.  When it does work, it stays working until I disconnect it or reboot the ubuntu-laptop.

Here's the recent thread on it...

[http://ubuntuforums.org/showthread.php?t=1244724](http://ubuntuforums.org/showthread.php?t=1244724)

I booted from the Ubuntu liveCD, ran gparted and formatted the first/biggest partition to NTFS so Ubuntu probably doesn't exist on the HDD anymore.  I'm completely fed up with not being able to get that LAN working so I can get online when I'm home, since my desktop has internet connection priority over the laptop here.  Away from home, tethering and wireless work great on the laptop but that wasn't enough for me.

---

### Post by brons2 on 2009-08-23
Yes, you can run DBAN with no software installed.  You boot it from floppy or CD.  You do know how to burn a CD from an iso file I assume at any rate...?

I suggest using version 2.0 even though the DBAN page says it's beta, it has better hardware compatibility with SATA drives and such.

One other thing, there are routers out there that are specifically intended for sharing phone company cell data networks such as what you are using, so you don't have to do that contorted network setup.

---

### Post by johnnydotexe on 2009-08-23
> **brons2 said:**
> Yes, you can run DBAN with no software installed.  You boot it from floppy or CD.  You do know how to burn a CD from an iso file I assume at any rate...?

I suggest using version 2.0 even though the DBAN page says it's beta, it has better hardware compatibility with SATA drives and such.

I'll give DBAN a try, and yes I am capable of burning an ISO to disc. :)

I'm running Ubuntu from the disc again and it's showing the 71.66GiB partition as empty/NTFS, and the two 2.86GiB partitions as still extended/linux-swap and locked so I'm unable to touch those.  Still won't boot from the Windows disc, so hopefully DBAN does the job.

---

### Post by sandyd on 2009-08-23
you just need to be more patient.


[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
if your going to be roaming anyways, why is your desktop a piority?
instructions to share your net connection from ubuntu -> windows provided on the above link.

---

### Post by sandyd on 2009-08-23
> **johnnydotexe said:**
> I'll give DBAN a try, and yes I am capable of burning an ISO to disc. :)

I'm running Ubuntu from the disc again and it's showing the 71.66GiB partition as empty/NTFS, and the two 2.86GiB partitions as still extended/linux-swap and locked so I'm unable to touch those.  Still won't boot from the Windows disc, so hopefully DBAN does the job.
right click on the swap. select unmount/swapoff
done. 
delete it.

---

### Post by johnnydotexe on 2009-08-23
> **carlee said:**
> you just need to be more patient.


[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
if your going to be roaming anyways, why is your desktop a piority?
instructions to share your net connection from ubuntu -> windows provided on the above link.

I'm home a lot, and since my main computer with all my stuff is the windows-desktop, it's usually online a lot.  I wanted to be able to be online with the windows-desktop and the ubuntu-laptop while at home, to do certain tasks and etc.  I am connecting online with the windows-desktop and wanting to share to the ubuntu-laptop, not vice versa as the link you posted instructs on.

I'm not mobile often, but there are the rare times I'm away from home and a laptop with mobile net comes in handy, I had that area covered because Ubuntu by default recognized the hardware and pretty much did all the setup work for me...same for the ethernet, but apparently there was a problem somewhere that I never could figure out.

That link you posted, I have read before.  They don't cover my means of getting online, and seem to center around sharing the net from an ubuntu system to an ubuntu or otherOS system.  It's also somewhat difficult for me to understand, networking isn't one of my strongsides.

---

### Post by SunnyRabbiera on 2009-08-23
> **carlee said:**
> you just need to be more patient.


[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
if your going to be roaming anyways, why is your desktop a piority?
instructions to share your net connection from ubuntu -> windows provided on the above link.

Just keep in mind some things do need terminal sometimes, but this sort of thing is getting better each day.
More GUI's are being developed so less terminal.
Personally i cannot give any real device as i dont run windows LAN networks or anything of that sort.

---

### Post by johnnydotexe on 2009-08-23
I think it may be a few more years before I'm ready to make the full switch from XP to linux, as linux just isn't ready to fill those shoes.  Sure it's a great OS, very reliable and very secure...but let's be honest, it's not as complete or compatible as Windows.  I hate windows as much as anyone else, but it works and does what it's told to do without issue(most of the time, lol).  Not everyone that is used to Windows wants to jump in to a completely new OS that requires setting up the simplest things, and having to deal with the terminal and all those commands...it's a pretty scary concept, I was rather intimidated the first time I ran Ubuntu.  I felt like I needed several degrees just to use it.

EDIT:  I right clicked the swap partition and chose "swapoff" and then deleted per the above instructions, then was able to delete the other partition and then resize the main NTFS partition.  Windows boot installation is now working.  Thank you for the help!

I'm still going to get that DBAN software, as it may come in handy when repairing customer computers.  Having a variety of software that can boot from disc is a lifesaver, especially something like DBAN.

---

### Post by brons2 on 2009-08-23
DBAN is great when someone wants assurance that their disk is completely wiped.  Run the DoD 5220 compliant wipe and it will wipe each sector and then overwrite it 7 times with random data.

---

### Post by johnnydotexe on 2009-08-23
> **brons2 said:**
> DBAN is great when someone wants assurance that their disk is completely wiped.  Run the DoD 5220 compliant wipe and it will wipe each sector and then overwrite it 7 times with random data.

That is awesome.  Can't wait to try it now, haha.  Thanks. :)

---

### Post by cmost on 2009-08-23
> **johnnydotexe said:**
> I think it may be a few more years before I'm ready to make the full switch from XP to linux, as linux just isn't ready to fill those shoes.  Sure it's a great OS, very reliable and very secure...but let's be honest, it's not as complete or compatible as Windows.  I hate windows as much as anyone else, but it works and does what it's told to do without issue(most of the time, lol).  Not everyone that is used to Windows wants to jump in to a completely new OS that requires setting up the simplest things, and having to deal with the terminal and all those commands...it's a pretty scary concept, I was rather intimidated the first time I ran Ubuntu.  I felt like I needed several degrees just to use it.

You said it correctly in your first sentence:  "I think it may be a few more years before I'm ready to make the full switch from XP to Linux..."  I take issue, however, where you go on to say that Linux is not ready to fill XP's shoes and several other quotes from your rant above.  My assessment is that YOU are not ready for Linux; not the other way around.  This is evident by your mad rush to return to Windows at the slightest obstacle.  Even though people have offered to help you set up your network, you're dead set on returning to Windows.  Go back to Windows and enjoy your software fees, battles with malware, and servitude to Microsoft.  When you're ready to open your mind and actually LEARN something new, then open source will be waiting.  :confused:

---

### Post by lisati on 2009-08-23
Are "dual boot" or "wubi" options? That way you can have both XP and Ubuntu on your system, learning Ubuntu and figuring things out while still having XP there if needed.

---

### Post by johnnydotexe on 2009-08-23
I am very open minded.  If I wasn't, I wouldn't have done a full/non-dual install of Ubuntu in the first place.  I took quite a big dive in to this, and so far I am severely displeased.  This isn't a matter of patience, patience went out the window when 1 week passed with no help on my "LAN isn't establishing" thread.  I shouldn't even have to make a thread, it's a freaking LAN which is just as easy as placing a new folder on your desktop.  I wanted to try something new, and went with Ubunutu which did not deliver.

No, linux is NOT ready to fill the shoes that Windows has left.  If it was, then please explain to me why a majority of PC owners on this planet are using...dun dun dunnnn...a windows OS?  Don't tell me that Gates held a gun to their head and forced them, or that "it came with their pc and they don't know any better" because any of them could get online, any of them could be aware that there are other OS choices out there.  Linux may be more secure, it may be more reliable. it may be less bulky...but like I stated above, the completeness, ease of use/user friendliness and compatibilities are still in favor of Windows.  Plus as long as the terminal / complicated commands and etc are involved, people will continue to shy away from the linux OS.  The first time I viewed a walk-through on setting up a small home network with ubuntu, I seriously though I needed to attend college for several years to understand 90% of what was in the thread...and I've been working on and around computers for numerous years, and make a living from working on computers.

I am by no means a Microsoft fanboy, don't twist what I've said...I HATE windows, I would love nothing more than to make the switch to another OS.  At this time I refuse to spend hours, days or even weeks to do something like establish a frickin' LAN between two computers when I can do it quickly on windows.  Maybe in a few years I'll be on here saying how superior Ubuntu is, but right now I honestly can not say that because it would not be completely true.  Though Ubuntu is way better in numerous areas, it's still not at the point where the average joe like me could make an easy transition from windows.  It's not *ready* yet, notice I said *yet*.

---

### Post by slakkie on 2009-08-23
You are not ready. If you are unable to format a drive I am more then willing to believe that you cannot understand on how to setup a LAN. It is not rocket science.

---

### Post by johnnydotexe on 2009-08-23
> **slakkie said:**
> You are not ready. If you are unable to format a drive I am more then willing to believe that you cannot understand on how to setup a LAN. It is not rocket science.

I have a week of very-little experience with Ubuntu/Linux, of course I won't know how to format a linux partition.  Don't come in my thread and tell me that means my knowledge in other fields suffers, it's rude.  I work on and drive hondas, you don't know how to chip and tune a p28 ecu so I'm going to criticsize you for it, ok?  I mean that makes about as much sense as what you just did to me, am I right?

Anyways, no, I am not ready to switch from Windows to Ubuntu because Windows has more to offer me at this time, and does what I need it to do.  I am not ready because Ubuntu is not ready, plain and simple.  If I have to make sacrifices in regards to my time, sacrifice compatibility with hardware and software I like to use, etc...then the OS is NOT READY in my eyes.

Setting up a LAN is not rocket science, but so far Ubuntu has made it look that way to me.  I just reinstalled XP on the laptop, and established a LAN with shared internet and file sharing in less than an hour...but it takes a week to still fail at establishing a LAN on Ubuntu, something Ubuntu should have suceeded at out of the box.

Since you're so quick to tell me what I don't know, that I can't do this and that...please, stop by the following thread and tell me what the issue was with the LAN.  I'd like to see your solution to the problem, heck I'll re-install Ubuntu back on the laptop just to try your solution...if I haven't done whatever method it is already, which is unlikely considering I've spent a week or more on that problem. 

[http://ubuntuforums.org/showthread.php?t=1244724](http://ubuntuforums.org/showthread.php?t=1244724)

[B]EDIT:  If an admin/moderator could lock this thread, that would be greatly appreciated.
[/B]

---

### Post by slakkie on 2009-08-24
1) Configure your network - not via network manager (see link in my sig)
2) install smbfs (sudo aptitude install smbfs)
3) sudo mkdir -p /mnt/my_windows
4) Edit your fstab
```

\\thewindowsserver\share /mnt/my_windows  cifs user,uid=<youruser>,gid=root,credentials=/home/<youruser>/.smb,iocharset=utf8,codepage=unicode,unicode,noauto 0  0

```
5) The credentials file .smb in your homedir contains the following
```

username=my_username
password=supersecret

```
6) sudo mount /mnt/my_windows
7) cd /mnt/my_windows

Done

---

### Post by johnnydotexe on 2009-08-24
1. In your single post that you linked in your sig...the first walk-through is how to set up wireless which I don't need to do since Ubuntu handles that automatically out-of-the-box.  Plus the addition of Wifi-Radar covers that just in case NM decided it didn't want to.  I tested and confirmed the functionality of wireless.  The second link, the method you used, seems to be pointed at using multiple networks.  I use one network for wired ethernet, that being the cat5 crossover cable connection to my windows-desktop.

2. If I need internet to install that, not possible.  I need the wired ethernet working in order to get online here at home.

3. Haven't tried yet.

4.  Not sure what an "fstab" is or how I edit it.  Not even sure what I do with that code, either.

5. Don't know what file you're talking about, or what it should contain.  Not even sure what username/password should be in there.

6. Haven't tried yet.

7. Haven't tried yet.

I'm currently re-installing Ubuntu from the liveCD, but doing the dual-boot this time instead of the full install.  Now that people are actually offering to help me out with advice I haven't already used, I figured it was worth a second shot because I really want to like Ubuntu.

EDIT:  Step 1 in the network configuration that you used in your sig, can't do it.  No net = no getting new software.

---

### Post by slakkie on 2009-08-24
> **johnnydotexe said:**
> 1. In your single post that you linked in your sig...the first walk-through is how to set up wireless which I don't need to do since Ubuntu handles that automatically out-of-the-box.  Plus the addition of Wifi-Radar covers that just in case NM decided it didn't want to.  I tested and confirmed the functionality of wireless.  The second link, the method you used, seems to be pointed at using multiple networks.  I use one network for wired ethernet, that being the cat5 crossover cable connection to my windows-desktop.


I've changed it so you can read the whole thread. 
For more information regarding the interfaces file:
man interfaces (you can type this in google or in a terminal).

> 
4.  Not sure what an "fstab" is or how I edit it.  Not even sure what I do with that code, either.


/etc/fstab

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

You put that code in your fstab and then you can mount/umount partitions. See also man mount, man umount, man fstab.

> 
5. Don't know what file you're talking about, or what it should contain.  Not even sure what username/password should be in there.


Login to your windows for samba... unless you have guest login enabled.

Also for network configuration under Linux:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking)

The issue is you need to read some documentation, with Windows it is the same, but since you are used to it, you can figure it out and do without the reading.

Linux is new to you, so you need to do some digging and reading before you will understand it and get comfortable. After a while you start to get the hang of it and you will do this with ease. There is a learning curve, and you have just started, in the beginning it will take you longer then on Windows, but that will change.

---

### Post by johnnydotexe on 2009-08-24
[http://support.microsoft.com/kb/951446](http://support.microsoft.com/kb/951446)

Check out that article, I think that may actually be the problem I'm having.  I'm dual-booting XP Pro SP3 + Ubuntu 9.04 on the laptop and both OS's are seeing the LAN and using the ICS from the windows-desktop...once I can get the connection to not work, I'll stop/restart the firewall/ics per that article to see if it fixes the problem.  If it does, that article applies to me and at this time there is no actual fix, just a work-around that has to be done each time the connection fails.

I did, however, use the method that you used.  I don't think it works, probably messed up somewhere along the line when following the instructions.  I'm still having to use the Auto eth0 connection in Network Manager.

What I used-
[http://ubuntuforums.org/showthread.php?t=124153](http://ubuntuforums.org/showthread.php?t=124153)

---

### Post by jheaton5 on 2009-08-24
> **cmost said:**
> You said it correctly in your first sentence:  "I think it may be a few more years before I'm ready to make the full switch from XP to Linux..."  I take issue, however, where you go on to say that Linux is not ready to fill XP's shoes and several other quotes from your rant above.  My assessment is that YOU are not ready for Linux; not the other way around.  This is evident by your mad rush to return to Windows at the slightest obstacle.  Even though people have offered to help you set up your network, you're dead set on returning to Windows.  Go back to Windows and enjoy your software fees, battles with malware, and servitude to Microsoft.  When you're ready to open your mind and actually LEARN something new, then open source will be waiting.  :confused:

What he said.

---

### Post by fadeyt on 2009-09-11
honestly im with this guy on going back to xp cuz what i need from a computer has nothing on linux im so displeased on some levels but on otheres im very pleased but at 19 who cares right i just dont like all the things on linux the music programs dont work for what i need so im just going to go back to windows so i can furthur my music production

---

### Post by wobin77 on 2009-09-11
Just installed Ubuntu at work, the windows network just works right out of the box. I even configured my first 'windows-network printer'. No problems at all. 

Really glad i switched to linux.

---

### Post by oboedad55 on 2009-09-11
> **fadeyt said:**
> honestly im with this guy on going back to xp cuz what i need from a computer has nothing on linux im so displeased on some levels but on otheres im very pleased but at 19 who cares right i just dont like all the things on linux the music programs dont work for what i need so im just going to go back to windows so i can furthur my music production

I tried to read this, but got a migraine. I think I kind of got that you like Windows, so you should use Windows. This is an Ubuntu help forum for the most part although some people will indulge you and try to convince you that you should like something you don't. However, if using Windows is causing this lack-of-punctuation problem you might want to try something else. Like BeOS, for example.

---

### Post by fadeyt on 2009-09-13
ok so i followed all of these steps i dont know what i am doing wrong i used dban and when i put the windows disk in i got an error saying something like no reconizable hard drive so then i tryed the gpartion one and deleted the paritions and got the smae thing so i nuked it agian what am i doing wrong please help i just want windows and i feel like im doin somethin wrong

---

