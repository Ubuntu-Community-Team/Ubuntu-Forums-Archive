---
title: "Ubuntu 6.x &amp; 5.x Doesn't Work On My PC"
date: 2006-06-04
forum: General Help
---

### Post by LoungeLover on 2006-06-04
It's terribly strange and frustrating that my Ubuntu 5.x Breezy Badger Live CD and my Dapper 6.06 Desktop and Server CDs will not work on my HP Pavilion 8562 Intel PIII 500 PC.  They all will start the install process but then crash at various points of installation.  (Let me also add that FreeBSD doesn't run on my PC either.  This is 3 Unix/Linux apps now!)

However, my Ubuntu 5.x Breezy Live CD for PPC runs perfectly on my Power Mac Dual G5.  What is going on here???  This is honestly making me want to buy an old PPC Mac to install Ubuntu on so that I can really learn how to use it. 

Much of the errors I'm seeing in my i386 install CDs (5.10 and 6.06) reference not being able to read files from the CD.  On the 6.06 Dapper Desktop CD, it's not able to work with either of my video cards.  I've tried using 2 different video cards - NVidia TNT Vanta 8MB and ATI Mach 32MB. I'm not using them in the PC at the same time, however. I'm swapping them to test.

I will mention that I'm burning all of my CDs on my Power Mac, as that's my primary machine.  My PC is just a machine for playing with software on.

What do you suggest I do regarding none of my i386 Ubuntu CDs installing the app or running the Live version on my PC?  

Also, how do I perform an MD5 checksum to see if my i386 downloads are corrupt or not?  I do perform burn verifies and so far, all have been verfied as good burns.

Thanks.

---

### Post by Chickenmonger on 2006-06-04
Whenever I download a Linux distribution via HTTP or FTP, I usually check the download by getting the BitTorrent file, and pointing it at the file I downloaded via HTTP or FTP. The BitTorrent program will check the integrity of the file, and automatically redownload corrupted parts.

As I don't have a Mac with OS X, I can only research methods to check the md5 sum. A page I found claims: 'To check a file's md5 checksum, simply open a Terminal window and type the following command: "md5 /path/to/the/file". Then, press return and compare the string returned with the one displayed on the download page.'

Have you considered the integrity of your CDROM drive? I had Pentium 1s from 1995 that still work, but have gone through three or four CDROM drives. Maybe it's not reading correctly?

---

### Post by LoungeLover on 2006-06-04
Chicken, you may be on to something with the integrity of my CDROM drive.  Duh!  I didn't even consider that, but luckily, my PC has a newer, HP CD-RW drive that I installed about a year after I bought it.

I'm trying the 6.06 i386 Desktop CD now in the other CD drive....it moved a lot faster on install and it's gotten further along than where I was hanging up before.

However....It's stuck right now at "Setting Up ICE Socket Directory..."  It's been on that screen about 8 min now.  :(

I'm also using the "RC" versions of 6.06 Desktop and Server, which seems different than the current download versions, as they don't have RC in their name.  So, I'm going to re-download, do the MD5 checksum (found a Mac OS X MD5 checker) and re-burn.

---

### Post by PapaWiskas on 2006-06-04
Two things to consider, 1 you have already dealt with and that is the CDROM....

The 2nd thing that happened to me, and I am not saying this is your problem but I pulled out my hair for 2 months.  The IDE controller on the motherboard was flaked out, it would do strange things to my CDRom and my slave drives.  So the possibility that something is kinda flaked on your motherboard is possible.  Especially if you got a new CDRom.

---

### Post by LoungeLover on 2006-06-04
I appreciate that info Papa, as I hadn't thought of that.

What I've done since my last reply is, downloaded a fresh 6.06 i386 Desktop iso, performed the MD5 checksum (checked out fine), burned it to CD and verified a good burn.

What I'm getting now when I boot from the CD and after the Ubuntu install screen disappears is:

> Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?  <Yes> <No>

If I don't select an answer within about a minute, or if I select YES, both take me to this prompt after giving a date, time, some Ubuntu credits and a bash message listed all over the screen:

**ubuntu@ubuntu:~$**

If I hit ENTER, that prompt just moves all over the bottom of the screen, like this: 

[INDENT]**ubuntu@ubuntu:~$**[/INDENT]
[INDENT][INDENT][INDENT]**ubuntu@ubuntu:~$**[/INDENT][/INDENT][/INDENT]

I'm clueless on what to do at this point.

---

### Post by PapaWiskas on 2006-06-04
now it sounds like you are having a video driver issue.  If you are using a nvidia or ati card you might have to do some research on what to do, there are some people here that could definetly help you out if you could give some more information such as what kind of video card you have, and other system information, the more info you can give people here, the quicker they can help you out.

You are almost there, so just hold tight and someone should be able to help you out.

---

### Post by LoungeLover on 2006-06-04
k, cool...I really think this has been the root of many of my issues outside of the CD drive.

I checked the **Dealing with problems with the Xserver** sticky here and tried the **dpkg --configure -a** command and saw a message that I needed to be a superuser to run it.

I then tried the **dpkg-reconfigure xserver-xorg** command and got a message that I needed to be logged in as "root" to run it.

---

### Post by eqisow on 2006-06-04
First of all, put your nVidia card in if it's not already there. If you still have a problem after that, we will install the binary nvidia drivers and reconfigure X. You can do that with the following:

```
sudo apt-get install nvidia-glx linux-restricted-modules-386
sudo nvidia-xconfig
sudo dpkg-reconfigure xserver-xorg
```

When you run that last command, you will be presented with a configuration wizard. Leave everything at the default value unless I tell you to alter it.

You will want to make sure you select 'nvidia' at the driver selection.

When you are asked about your monitor and presented with a Simple, Medium, Advanced selection, choose medium if you know your monitors max resolution and refresh. If you don't know this information choose simple. Either way, select the appropriate setting for your monitor and continue.

*NOTE: When running **dpkg-reconfigure xserver-xorg**, Spacebar makes selections and Enter confirms those selections*

Edit: sudo means super user do, and gives temporary root privilidges. This was why the commands wouldn't run before. :)

Edit again: Your password will be the login password you chose during install, just fyi.

---

### Post by LoungeLover on 2006-06-04
eqisow - I'll try that now, as I currently have the ATI Mach 32 video card installed.

if I need to run those commands, where/how do I run them and do I need to be logged in as root?  I'm a newb so I'm not sure on where to run certain commands.


Thanks!

---

### Post by eqisow on 2006-06-05
Whenever it drops you at **ubuntu@ubuntu:~$**, like you said it did before, you enter the commands there. Don't worry about logging in as root, sudo will take care of it.

Also, I forgot to mention in my last post, that after you follow those steps you will need to run **startx** to start the graphical environment again.

P.S. - Your switching graphics cards because ATI has shitty Linux support. Be sure to yell at them if this frustrates you. ;)

---

### Post by LoungeLover on 2006-06-05
[QUOTE=eqisow]P.S. - Your switching graphics cards because ATI has shitty Linux support. Be sure to yell at them if this frustrates you. ;)[/QUOTE]

You've got that right and they will hear about it!  ;)

---

### Post by LoungeLover on 2006-06-05
I'm getting ahead here, finally, thanks to you all!

Ok, now I've loaded the Ubuntu GUI desktop and preparing to start the installation, as I want to install it to the HD.

My Sony LCD monitor is now showing the Information message "Out of range 1280 X 768" smack dab in the middle of the screen!  This is my monitor's highest resolution.

I'll see how far I can get with the HD install...

---

### Post by LoungeLover on 2006-06-05
I performed an install with the server CD I had burned, as doing the install from the desktop CD was awfully slow.

It seemed to install fine and now I'm sitting at a prompt showing:  **username@ubuntu:~$**.

I typed those 3 commands and given by eqisow and saw this message: 
> 
Reading package lists...Done
Building dependencies...Done
Package nvidia-glx is not available but is referred to by another package
This may mean that the package is missing, obsoleted, or is only available from another source
Package nvidia-glx has no installation candidate

I then typed startx at my prompt and saw > -bash: startx: command not found

I'm sitting at my prompt again **username@ubuntu:~$**.  This PC is not connected to the Internet yet if those commands were supposed to download packages.

---

### Post by eqisow on 2006-06-05
ermm, server CD? The server CD is meant for servers. It comes with no kind of GUI at all. You can connect the computer to a network and do **sudo apt-get install ubuntu-desktop**, or you can use the Alternate CD to install. The Alternate CD is a text based installer. That's what you want if the Desktop CD wasn't working well.

P.S. - Yes, one of those commands was supposed to download a package, but we should be able to get things working without that package. You will, however, need to do something about having a server install. ;)

P.P.S. - It just occured to me that with a PIII 500 Ubuntu may be unbearably slow anyway. If the system has > 256MB RAM, you may be OK. Otherwise, I wouldn't even bother with it on this computer. Xubuntu could be worth a try though, it uses a very lightweight XFCE environment.

---

### Post by LoungeLover on 2006-06-05
Ok, that makes sense.  I'll re-install with the Alternate CD.

I will be an Ubuntu guru yet huh?  :)

---

