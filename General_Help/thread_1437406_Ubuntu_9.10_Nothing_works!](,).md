---
title: "Ubuntu 9.10 Nothing works!](*,)"
date: 2010-03-23
forum: General Help
---

### Post by Millnert on 2010-03-23
I'm new with Ubuntu as you can tell, so I need some assistance in this matter. NOTHING seems to be working except applications and places (unless I cannot locate the correct place to execute other files properly). For instance, I cannot find the place where to run commands (like Windows command prompt), and cannot connect to the internet to access even though Vista can. I don't know if the OS cannot recognize the drivers or what... Additionally, when I try to run my migrated documents NOTHING WORKS, media player won't open, error messages pop up, etc...


BTW I followed the instructions to dual boot properly (Vista and Ubuntu) and everything was successful I believe... 

I have a Dell Inspiron 1520 and every now and again the BSOD occurs (if that helps).

-T.M

---

### Post by Colo2 on 2010-03-23
At the top, click System

Go to Administration, and click on Hardware drivers

that will give you the option to apply system drivers if they are available.

Also do you connect via wireless or eth?

---

### Post by sendblink23 on 2010-03-23
If you are getting now an then BSOD...


Replace hard drive, I believe its already dying...   that could be the cause of nothing working for you after installing ubuntu(hard drives who are faulty tend to not install perfectly the OS) You would have similar issues like you explained... so I would replace the hard drive of your computer.


You mentioned "(like Windows command prompt)"
well.... did you go to: Applications > Accessories > Terminal   ?

Eitherway it simply sounds Ubuntu did not install correctly on your computer... and I am simply assuming it could be a faulty hard drive, since you said you get BSOD once a while ... I could be wrong.. it could also be a Bad burned copy (make sure if you did it in Windows to use ImgBurn or Infra Recorder... burn the ISO in the Lowest burning speed as possible) of your Ubuntu that you used to install it.

---

### Post by zeroseven0183 on 2010-03-23
I wouldn't recommend running commands on a Terminal this early. Try first the GUI-way of running applications.

Please help us understand more about your problem. Let's sort things out by at least enumerating the error messages, your needs, and how you installed Ubuntu (dual-boot as you mentioned).

This is the first time I heard about a BSOD in Linux

---

### Post by Millnert on 2010-03-23
Ok, thanks for pointing the location of the terminal out, I found it ;)! 

Under System>Admin>Hardware & Drivers, it searched for available drivers but none were listed; specifically "no proprietary drivers are in use on this system".

I'm trying to connect via my wireless router, it works on Vista but not on Ubuntu for some reason...(It doesn't pick up on it since when the network manager icon is clicked wireless networks and wired networks are both disconnected/grayed out)

The bsod occurs only on my vista I'd say every time I download some new software and install it (and also only when the laptop starts, kind of like a flash so I can't  read the error) but won't occur if I carry out normal activity and just shut down.

I really would like to get everything running properly but if I need to reinstall Ubuntu or any derivs. I will as a last resort :(

---

### Post by ppirilla on 2010-03-23
Wireless is sometimes tricky business in the Linux world.  Do you know what wireless card you have?

---

### Post by sendblink23 on 2010-03-23
> **Millnert said:**
> Ok, thanks for pointing the location of the terminal out, I found it ;)! 

Under System>Admin>Hardware & Drivers, it searched for available drivers but none were listed; specifically "no proprietary drivers are in use on this system".

I'm trying to connect via my wireless router, it works on Vista but not on Ubuntu for some reason...(It doesn't pick up on it since when the network manager icon is clicked wireless networks and wired networks are both disconnected/grayed out)

The bsod occurs only on my vista I'd say every time I download some new software and install it (and also only when the laptop starts, kind of like a flash so I can't  read the error) but won't occur if I carry out normal activity and just shut down.

I really would like to get everything running properly but if I need to reinstall Ubuntu or any derivs. I will as a last resort :(



You mentioned it pretty clear there: "and also only when the laptop starts, kind of like a flash so I can't  read the error "

I assume its definitely a Hardware issue(no reinstalling of any OS can fix this), ... since i do not have your laptop in my hands to do some tests... there isn't an exact way to figure out the exact issue....   it could be hard drive, it could rams, it could be the motherboard, it could be your bios or it could be the video card(or onboard graphics) ...     certainly you need to take the laptop to repair(or to check if it needs repair)

If your laptops hardware was perfectly fine, you would never have any random BSOD on starting up your computer.

---

### Post by Millnert on 2010-03-24
The wireless card I have is a piece of crap 802.11g.

If the underlying hardware on my laptop is the problem, does anyone know how to properly install Ubuntu despite the bsod on vista OS issue?

Also, what is the best way to completely clear up the Ubuntu partition and its loader so I can start this installation over or via another method?

---

### Post by zeroseven0183 on 2010-03-24
For your network controller, please post the output of ```
lspci | grep -i net
```You will need an MBR Recovery Tool to correct your Windows boot after wiping off Ubuntu if that's what you plan. But if you have the Windows Vista installation disc, then you're good to go. Follow the instruction below as per [http://www.raymond.cc/forum/linux/9367-how-to-remove-ubuntu-linux-from-dual-boot-tutorial.html](http://www.raymond.cc/forum/linux/9367-how-to-remove-ubuntu-linux-from-dual-boot-tutorial.html).

> 
 1. Boot PC with Windows Vista installation disc.
2. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
3. Click Repair your computer.
4. Click the operating system that you want to repair, and then click Next.
5. In the System Recovery Options dialog box, click Command Prompt.
6. Type Bootrec.exe, and then press Enter.
7. Delete Ubuntu Partition

This will also overwrite GRUB with Windows boot loader.


Be sure to backup all you data from that partition before deleting it.

By the way, how did you install Ubuntu in the first place? Did you use Wubi (install inside Windows)?

---

### Post by gordintoronto on 2010-03-24
See this wonderful article:
[http://www.networkworld.com/news/2005/041105-windows-crash.html](http://www.networkworld.com/news/2005/041105-windows-crash.html)

---

### Post by eriktheblu on 2010-03-24
> **Millnert said:**
> 
and cannot connect to the internet to access even though Vista can.
Probably your wireless card not being recognized. If you can connect to the internet by another means (ethernet rarely has problems) I recommend doing a system update. Go to system>administration>update manager. There is a good chance that will fix your wireless connection issue.

> I don't know if the OS cannot recognize the drivers or what... Most generic drivers are included on the CD, but sometimes you will need specialty drivers. Many of them are available through the Hardware drivers application, but internet is required. For everything else, a google search normally will point you in the right direction.

> Additionally, when I try to run my migrated documents NOTHING WORKS, media player won't open, error messages pop up, etc...
For your media, I think [this](https://help.ubuntu.com/community/RestrictedFormats) may be your answer. 

As for your documents, are they MS office documents? I've never had any issue with powerpoint, excel, or word formats (2003 or 2007). Of course I have always had the restricted extras package installed first.

---

### Post by Millnert on 2010-03-24
**2 zeroseven0183** How did I install Ubuntu? First I dled the Ubuntu ISO image [here]("http://www.ubuntu.com/GetUbuntu/download") and and then followed this tutorial [here]("http://www.pctipsbox.com/how-to-dual-boot-vista-with-ubuntu/").

The output of the network controller command was:
'03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100BASE-TX (rev02)'
'0C:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (revo02)'

I do have the Vista re-installation disc but is using this method easier as opposed to using FDISK/MBR method and then simply deleting the Ubuntu partition?

**2 gordintoronto** Concerning the article on resolving crashes, does it apply in my case since I'm using Vista (the 'getting started' requirements on p.1 doesn't list vista)?

**2 eriktheblu** When I open the update manager it searches but then notifies me that '*An error occurred \n the details are provided: W:failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg) could not resolve 'us.archive.ubuntu.com*' (and some more lines of similar nature)'.

For the media thing, I can only use Vista to access that site and since I cannot save the file (Firefox doesn't recognize the apt extension), I have no way to apply this to Ubuntu... The .doc documents do work however :) (I guess I haven't tried opening it previously).

Additional info.
-Anytime I use Ubuntu and browse around/check out the system and applications, and then Restart or Shutdown to boot with Vista, I get the bsod. It says Stop 0x0000007B (I had to change the on error settings) . Searching more closely resembles a hardware problem...:(
-I CAN navigate through Vista (from Ubuntu) and open some files of the following format: .doc, pdf, .jpg, and .zip.
-I CAN'T open .mp3 files (it says the required software to play is not installed>then if I hit search it says no packages w/requested plugins found 'requested plugins are -MPEG-1 layer 3 decoder'). That is using both Movie Player and Rythmbox.
-There are some ntuser.dat files in the 'media/OS/users/(my name)/directory I don't know what they mean but if I try to open it says 'could not display <the path to file> this file is of an unknown type'.

This process is quite frustrating but my primary goal is to get the internet working and music playing.

---

