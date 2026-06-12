---
title: "Connecting with a modem"
date: 2009-11-16
forum: General Help
---

### Post by BAO_Dave on 2009-11-16
Some of us live out in the sticks and do not have the option of having anything but dial-up internet, such is the case for me. Okay I could subscribe to a satellite internet provider but I refuse to pay what they want for that service.....probably why I am looking to Ubuntu as an alternative to Windows.
 
I just put together a machine from spare parts I had lying around and I need to set up the modem for dial-up internet access. I probably should state that I chose to install Ubuntu only and got rid of Windows on install. I tried to follow the tutorial on how to do that but I am stuck at step number 1 "Open > System > Administration > Network". When I open System > Administration I only have an option "Network Tools" and even if I open that the two listed devices both seem to show that they are disabled so I can proceed no further.
 
If I can get this OS to work I plan to swicth my observatory computers to Ubuntu at some point in the future so any and all help would be greatly appreciated!
 
Dave Birmingham
 
Birmingham Astronomical Observatory
Harvard MPC/H53
Thompsonville, IL
37° 56' 28.7" N / -088° 46' 18.5" W
ele. 516 ft/ 157 m
12" LX200GPS s/n 05008
ASO SuperCharge # 243-2012
Main Imager SBIG ST-402ME-C1

---

### Post by hwttdz on 2009-11-16
Can you share the walkthrough you're using to set up your network.  It's probably just that a few of the menu option names have changed.  It's likely that they're referring to system->prefs->network connections.  Of course we don't know which version of the OS you're using, that's often helpful info. I think if you edit it into your profile it gets tagged on every post you make.

As a sidenote: excited for the meteor shower?

---

### Post by BAO_Dave on 2009-11-16
Well I spent the last four days downloading Ubuntu 9.10 and I am trying to get an internet connecton set up so I can do updates.....sorry.

---

### Post by hwttdz on 2009-11-16
So you're using 9.10? 

What's the walkthrough?

Does network connections under system->preferences look like what they're talking about in the walkthrough?

---

### Post by BAO_Dave on 2009-11-16
Hey, you're talking to a Windows guy....not sure what you mean by walkthrough.

---

### Post by hwttdz on 2009-11-16
Sorry, I was using walkthrough and tutorial to mean pretty much the same thing.  If you link to the tutorial, I can take a look at it and might be able to give some suggestions about how things have changed.

---

### Post by BAO_Dave on 2009-11-16
Well the tutorial I was attemping to follow is at; [https://help.ubuntu.com/9.10/internet/C/modem-connect.html](https://help.ubuntu.com/9.10/internet/C/modem-connect.html) but I can't get past stwp #1.....there is no **Unlock **to press on my system.

---

### Post by hwttdz on 2009-11-16
What about opening up a terminal and running
network-admin
you might get "network-admin: command not found", in which case do "sudo apt-get install gnome-network-admin" then try "network-admin" again.  Let me know if you have any issues with that, it should get you back on track with the tutorial (which is current).

---

### Post by BAO_Dave on 2009-11-16
Well I'm not having any luck with any of that. I didn't realize it would be so difficult to set up a modem in Linux maybe that's why it hasn't taken off so well.

---

### Post by t0p on 2009-11-16
> **BAO_Dave said:**
> Well I'm not having any luck with any of that. I didn't realize it would be so difficult to set up a modem in Linux maybe that's why it hasn't taken off so well.

Can you explain what you mean by "I'm not having any luck with any of that"?  Tell us what it is you tried, and what happened when you tried it?  For instance, if you typed commands into the terminal, paste up the output you got.

You say there is no 'Unlock' option at **System > Administration > Network**.  Can you post a screenshot of what you do see at System > Administration > Network, so we can see exactly what you are seeing?

That tutorial you're trying to follow: you say that you're stuck at "step 1"; but the very first thing it says is you need to install the gnome-network-admin package, and links to instructions to how to do it.  Have you done that?

I realize you're frustrated, but please leave the comments about "why Ubuntu hasn't taken off".  Try to understand: just because *you* are having problems, doesn't mean the problem is with Ubuntu.  Remember you are learning how to use an operating system that is completely new to you.  Be patient, and explain exactly what you are trying to do and what is happening.  The members of this forum are generally a very helpful and friendly bunch.  We'll help as much as we can.

---

### Post by BAO_Dave on 2009-11-16
Well I tried to install the gnome-network-admin package but when I followed the suggestions at, [[COLOR=#444444]http://ubuntuforums.org/showthread.p...90#post7245790[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")
I could not put any of those files in the directory that was referenced, it said I didn't have permission or something. I was able to copy the files from my USB memory stick to the Home Folder of the computer but for instance when I double clicked the admin package I got an error message, "Dependency is not satisfiable: libpolkit-dbus2 (>=0.7)". As far as doing screen shots that would be impossible since I can't get the modem set up so I can even try to use my ISP, which is something else I apparently have to set up.  I did not say that I have an **System > Administration > Network**, what I see is; **System > Administration > Network Tools**. If someone would enlighten me on how to install the gnome-network-admin package I would be most grateful. I would have assumed that being the only user on the system would have given me administrator rights to begin with but then that was just an assumption.
 
I did not mean to imply that Ubuntu has problems, geeze I have only had it installed for less than 12 hours. What I meant was that it, to me, is not very user friendly, but then I have been stuck with Mr. Gates products for many years. It just seems that setting up a modem for internet connectivity should be easier that what I have encountered. Not all of us have the luxury of DSL, LAN or other means of connecting like that.
 
I really do appreciate the help and I am more than willing to roll up my sleeves and learn.

---

### Post by BAO_Dave on 2009-11-19
Ubuntu 9.10 has turned out to be one of the worst experiences I have had in computing. Setting up a modem to gain internet access should be one of the easiest things to do with a computer and operating system.

---

### Post by hwttdz on 2009-11-19
Sorry there.  When ubuntu complains that you don't have permissions to run a system command, or edit a file in a system folder (i.e. not in /home/username) then you almost certainly need to prepend "sudo" to the command.  "sudo" gives you admin permissions for the one command.  So to install a package you need to run
"sudo apt-get install packagename", or if you want to copy a file to a directory which is owned by root, run "sudo cp file directory", to see who owns a file or a directory "ls -l".  Give installing the network manager packages a try with sudo and let us know how it goes.

---

### Post by klemes on 2009-11-19
I suggest you leave all graphical connection tools aside and try wvdial.
Its only one small file and has no dependencies so with one download you are all set.Then you have to edit only one file and that is wvdial.conf which lies in the /etc folder.You accomplish this by opening a console and
typing : sudo nano /etc/wvdial.conf.Filling the required fields should be plain forward as most are self-explanatory.I will only comment on the modem parameter which you should make it look like: modem = /dev/ttyS0  or modem = /dev/ttyS1 assuming you are using a serial modem connected in COM1 or COM2 accordingly.

Good luck and ask again if things dont get as planned.

---

### Post by ivanvajar on 2009-11-19
Don't complain about dial-up on Ubuntu. Almost all modems are winmodems, meaning that they are software modems, designed to use Windows to simulate 'traditional' modems, more than 'real' modems. klemes told you to edit /etc/wvdial.conf and the way to do it. I had many problems with dial-up and it can be solved just like klemes told you.

---

### Post by BAO_Dave on 2009-11-20
Okay I can try wvdial, I assume I can Google it. I'm not complaining about dial-up on anything, other than HughesNet or similar it's all that's available in my area, just the setting up the modem part in Ubuntu.
 
There are some assumptions being made here that I apparently don't understand, like typing : sudo nano /etc/wvdial.conf, just where I should type that in is a mystery to me unless the reference is to use terminal. I also am uncertain on where one would edit a file.
 
I did dump Ubuntu 9.10, reformatted my hard drive and reinstalled Windows. I am planning on reinstalling Ubuntu along with Windows, I think I have enough room for that or I could install it on a slave drive that has 12+GB free.
 
I have tried to download a pocket guide for Ubuntu I found but all my attempts to do so turned up to be broken zip files, at least to my WinZip 9.
 
Oh, if it matters the modem in question is a Telepath 56K Voice Faxmodem PNP on COM3, Interupt 5, Address 3E8, UART NS 16550 AN, Highest Speed 115K Baud.

---

### Post by BAO_Dave on 2009-11-20
Oaky I found the package wvdial_1.60.1+nmu2ubuntu1_i386.deb and got it copied onto a USB memory stick and then copied onto the desktop of my machine running Ubuntu. I'm not sure what to do with it next as I tried double clicking on it and it looked like it was extracting files but then I got an error message, **Error: Dependency is not satisfiable:libuniconf4.6**, and I'm not sure what that means. I would think that packages should be in a specific place, like **Windows > Program Files** so if someone would enlighten me as to where these packages should be in Ubuntu, and how to install them, I would be grateful. Also I am assuming that once I do get the wvdial package installed and run it that the machine should be connected to a working phone line?
 
I have Ubuntu installed along with Windows98, yeah it's an old machine but it's my learning platform before I go an install it on my other four machines with valuable information on them. I also found out that the Ubuntu Pocket Guide PDF will only run in Ubuntu, I was trying to install it on a Windows XP machine.

---

### Post by studmonkey on 2009-11-23
I am using Ubuntu 9.10 in a dual boot system w/ Windows Vista>Intel Pentium Dual 2.20 chip> Siemens SpeedStream 4100 DSL modem.
The modem is hardwired, no wireless.
My net hookup has performed well until a round of updates several weeks ago.  Now the modem will not connect on initial system boot until I switch it (the modem) on and off several times, even though the network connection icon shows it to be active and Auto eht0 installed (as default) and selected on the "Network Connections" screen under "Wired." 
The weird thing is that the connection on the Network Connections screen lists it as "never" used.  Huh?  How am I connected?
If I do a reboot in the middle of a session, the modem connects right away, no problems.  
Anybody else experiencing these type of problems?
Is my modem dying?
Does Ubuntu hate it now?
What gives?

---

