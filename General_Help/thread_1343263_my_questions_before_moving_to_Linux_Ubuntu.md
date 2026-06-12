---
title: "my questions before moving to Linux Ubuntu"
date: 2009-12-01
forum: General Help
---

### Post by MKVCrazy on 2009-12-01
Hi, I am convinced after reading that Ubuntu is faster, safer and more user friendly or modifiable (I like doing things my way) than Windows 7 Ultimate 64-bit which I am currently operating with. But the reason why I post this thread is just to get the info links of quick infos if you don't mind answer to my questions because I can understand that you might probably have answer these questions multiple times but again as I said since I like doing things my way I also like making sure that it'll work according to my situations. So here it goes ...

For my home computer,
I would like to run some windows apps because I am always chatting/talking with my friends on messengers such as Google Talk or Windows Live Messenger. So I will list the softwares I am most like to use if I ever switch to Ubuntu. So I need to know if they'll work. Also will there be performance decrease if another program is used to run the following windows apps?

MeGUI (a media converter)
RipBot264 (a media converter)
Google Talk
VZOChat
Windows Live Messenger
Mozilla Firefox
JDownloader (JAVA based file download manager)

Well, there are many more I want to use but I don't think it's worth listing all of them here unless someone requests but is there a link/place where I can read the limitations of programs like WINE? How many are there like WINE that allow me to run Windows apps. Can I still get viruses? I am guess yes since it'll become able to read windows exe files but I'm still not 100% sure.

Last question, I am also planning to use an Ubuntu OS on one of my dedicated servers and I can't find one with Ubuntu Desktop 64-Bit (only 32-Bit there) but I only found Ubuntu Server 64-Bit. How differ are they on the performance? Server has 4GB DDR2 RAM. Should I still bother with finding Desktop 64-Bit? Because I am not planning to use the server for hosting. I am planning to use it as my home computer but it has faster speed and more storage space (1TB).

Regards,
MKVCrazy

---

### Post by jbrown96 on 2009-12-01
64-bit tends to be about 5-10% faster but has about 5% memory overhead. If you can run 64-bit, do it. There aren't any drawbacks. 


As far as the Windows applications. They may work in Wine, but I would try to find native Linux apps. Handbrake (download from their website) is a very good media converter. There are several IM programs available, and as far as I know, they can get on the Windows Live network. Firefox is natively supported in linux and comes installed by default. There are also several download managers (kget is one, but you may want to find a Gnome app). 

Viruses aren't a problem with Wine. You have to understand that Wine does not work with many programs. It's primarily designed for games, and your mileage will vary. Search for the Wine AppDB, and you can see if your specific programs are supported.

---

### Post by adaucourt on 2009-12-01
> **MKVCrazy said:**
> Hi, I am convinced after reading that Ubuntu is faster, safer and more user friendly or modifiable (I like doing things my way) than Windows 7 Ultimate 64-bit which I am currently operating with. But the reason why I post this thread is just to get the info links of quick infos if you don't mind answer to my questions because I can understand that you might probably have answer these questions multiple times but again as I said since I like doing things my way I also like making sure that it'll work according to my situations. So here it goes ...

For my home computer,
I would like to run some windows apps because I am always chatting/talking with my friends on messengers such as Google Talk or Windows Live Messenger. So I will list the softwares I am most like to use if I ever switch to Ubuntu. So I need to know if they'll work. Also will there be performance decrease if another program is used to run the following windows apps?

MeGUI (a media converter)
RipBot264 (a media converter)
Google Talk
VZOChat
Windows Live Messenger
Mozilla Firefox
JDownloader (JAVA based file download manager)

Well, there are many more I want to use but I don't think it's worth listing all of them here unless someone requests but is there a link/place where I can read the limitations of programs like WINE? How many are there like WINE that allow me to run Windows apps. Can I still get viruses? I am guess yes since it'll become able to read windows exe files but I'm still not 100% sure.

Last question, I am also planning to use an Ubuntu OS on one of my dedicated servers and I can't find one with Ubuntu Desktop 64-Bit (only 32-Bit there) but I only found Ubuntu Server 64-Bit. How differ are they on the performance? Server has 4GB DDR2 RAM. Should I still bother with finding Desktop 64-Bit? Because I am not planning to use the server for hosting. I am planning to use it as my home computer but it has faster speed and more storage space (1TB).

Regards,
MKVCrazy

MeGUI (a media converter)
RipBot264 (a media converter)
**USE AVIDEMUX, DEVEDE**

Google Talk
**USE PIDGIN/EMPATHY**

VZOChat
Windows Live Messenger
**USE PIDGIN/EMPATHY**

Mozilla Firefox
**AVAILABLE IN LINUX**

JDownloader (JAVA based file download manager)
**USE FIREFOX PLUGINS - DOWNLOAD STATUS BAR**

Yes viruses exist for all platforms!

You can always install virtual machine with-in linux if you want access to windows if you want a wine alternative

---

### Post by AlanR8 on 2009-12-01
So long as you're not a main stream PC gamer you should be able to make the transition easily. Use an Xbox for games.

My son, when he was 16 asked me to put Linux on his PC and never looked back, he has an Xbox.

Bought him a MacBook Pro when he went to uni......Doze, not is this establishment, apart from the wife and I have plans......

---

### Post by oldsoundguy on 2009-12-01
> **adaucourt said:**
> MeGUI (a media converter)
RipBot264 (a media converter)
**USE AVIDEMUX, DEVEDE**

Google Talk
**USE PIDGIN/EMPATHY**

VZOChat
Windows Live Messenger
**USE PIDGIN/EMPATHY**

Mozilla Firefox
**AVAILABLE IN LINUX**

JDownloader (JAVA based file download manager)
**USE FIREFOX PLUGINS - DOWNLOAD STATUS BAR**

Yes viruses exist for all platforms!

You can always install virtual machine with-in linux if you want access to windows if you want a wine alternative

Download manager .. I use FlashGot in FireFox

No, there are no virus files in the wild for Linux and there is no ANTI VIRUS program for Linux as a stand alone as it is not needed.  AV is needed if you are to act as a server to protect any Windows machines on that server .. and to screen any FORWARDED eMail  (bad idea in the first place, copy/past/send is a better idea!)
AV is also a good idea if you are running Windows programs in any form (in VM/Wine/dual boot/whatever) to protect those areas.  A Virus  will not migrate to your Linux nor to your boot sector.

---

### Post by jakslev on 2009-12-01
Hi MKVCrazy, 

I am sure you will be happy with Linux. Ubuntu is a good distribution that is updated and vibrant with a new exciting version coming out every 6 months. 

I understand that you are worried about loosing the "good old" programs that you have gotten accustomed to with Windows.  

I have the same situation - e.g. I need to use Adobe Illustrator and Photoshop professionally and at present there is nothing that matches these products on the open source market (a few years and I am sure that situation will have changed). 

What I have done to use these "work programs" is installing a virtual machine. Not being sure if you are familiar with what that is I will spend a few lines explaining. 

I am using a program called Virtual Box from Sun System, that allows me to run Windows (and many other operating systems) as if they were installed on my computer. Virtual Box provides a virtual machine where you can install your Windows and any windows programs you would like. Then with a few clicks you have them running in full screen with no trace of Ubuntu and full share-ability between the two "worlds". It is VERY easy to set up; and once installed it takes no time booting Windows as a slave system. As I said I run Adobe Illustrator with absolutely no lag or other problems!

As for the programs you mentioned below, that are not programs that you are only using now-and-then:

MeGUI (a media converter)
RipBot264 (a media converter)
YOU WOULD PROBABLY FIND VERY GOOD AND CLEAN ALTERNATIVES IN THE OPEN SOURCE COMMUNITY. OTHERWISE INSTALL UNDER VIRTUAL BOX!!

Google Talk
VZOChat
Windows Live Messenger
SURE ALL THESE CLIENTS ARE SUPPORTED BY PIDGIN, AND YOU CAN BE LOGGED IN TO ALL ACCOUNTS AT THE SAME TIME. FURTHERMORE IT WILL INTEGRATE WITH YOUR MAIL PROGRAM EVOLUTION. 

Mozilla Firefox
OF COURSE. THIS IS AN OPEN SOURCE PROJECT. 

JDownloader (JAVA based file download manager)
NOT SURE WHAT IT DOES.. BUT I JUST TESTED AND IT IS ALSO OPEN SOURCE. 

Sorry for the yelling... ;o)

As for the server and 64/32-bit discussion I am no expert! However, I run 64-bits on all computers (basically because I am a bit weird). I do know that running 64-bit will cause you some more.. challenges when installing software (e.g. it took some simple commands to get Skype 32-bit to run on my 64-bit system). 

All in all I am sure you will be very happy on Ubuntu, and you will be happy with the many new features you will find here.

HaHa just realized a lot of other people answered :o) There you go! A very active community that will support you.. Try and call Microsoft!!!

---

### Post by jakslev on 2009-12-01
> **oldsoundguy said:**
> Download manager .. I use FlashGot in FireFox

No, there are no virus files in the wild for Linux and there is no ANTI VIRUS program for Linux as a stand alone as it is not needed.  AV is needed if you are to act as a server to protect any Windows machines on that server .. and to screen any FORWARDED eMail  (bad idea in the first place, copy/past/send is a better idea!)
AV is also a good idea if you are running Windows programs in any form (in VM/Wine/dual boot/whatever) to protect those areas.  A Virus  will not migrate to your Linux nor to your boot sector.

Let's not be too cocky.. with the virus and internet security issues. 
At some point there will be vira for Linux as well.. 
And you still need to take care of who is snooping on your computers and trying to hack you. 

There are several security systems for linux out there and even a virus guard (though I am not sure it has ever caught anything :p )

---

### Post by MKVCrazy on 2009-12-01
I appreciate your replies.

About to use Firefox's plugin, I never liked any browser built-in download managers, they're always not giving me full speed. I use JDownloader for a reason and its great features that you can't find on other apps. I did some search a few mins ago and I found that WINE is only able to run windows application and not the windows OS. If I want to do converting videos should I dual boot using VMware instead of using WINE? How might their performances differ? I don't want to do if any of them is going to use a LOT of CPU resource and slow up my computer.

EDIT

Will the PIDGIN allow me to use voice/webcam chat in VZOChat, WLM or Google Talk? I just want to hear something while I am at it. I read on the internet that it's not fully support or something about the audio but the thread ended. No final answer :\

About VirtualBox, yes that sounds very very sweet. I can't even wait to test out the Ubuntu! :D

---

### Post by audiomick on 2009-12-01
> **MKVCrazy said:**
>  dual boot using VMware instead of using WINE? 

VM ware is not a dual boot. It is a virtualisation. Read this:
[http://en.wikipedia.org/wiki/Virtualisation](http://en.wikipedia.org/wiki/Virtualisation)

Dual boot is when you have two OSs installed, and run one or the other.
[http://en.wikipedia.org/wiki/Dual_boot](http://en.wikipedia.org/wiki/Dual_boot)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

> How might their performances differ?
I don't want to do if any of them is going to use a LOT of CPU resource and slow up my computer.

I don't have any experience with virtualisation yet, but as I understand it the main limiting factor is how much RAM you have. If you have enough to provide the guest system with enough and still have enough left over for the host, I believe that performance can be very good.

---

### Post by lykwydchykyn on 2009-12-01
> **MKVCrazy said:**
> Hi, I am convinced after reading that Ubuntu is faster, safer and more user friendly or modifiable (I like doing things my way) than Windows 7 Ultimate 64-bit which I am currently operating with. 

I think it's better to have the mindset that you are about to move to a totally different computing experience, rather than just a faster/safer/whiter/brighter version of Windows 7.  

Trying to get Windows programs running in WINE is one of the biggest things that frustrates new Linux users and often sends them running back to Windows.  It's much better to forget your laundry list of Windows apps and just approach this system for what it has to offer itself.  

Give it a month or so. If you can't find a good workable replacement for the apps you mention (apart from firefox, which runs natively in Linux), then try them in WINE, but be prepared for some frustration.

---

### Post by gordintoronto on 2009-12-01
> **MKVCrazy said:**
> I appreciate your replies.

About to use Firefox's plugin, I never liked any browser built-in download managers, they're always not giving me full speed. I use JDownloader for a reason and its great features that you can't find on other apps. I did some search a few mins ago and I found that WINE is only able to run windows application and not the windows OS. If I want to do converting videos should I dual boot using VMware instead of using WINE? How might their performances differ? I don't want to do if any of them is going to use a LOT of CPU resource and slow up my computer.

EDIT

Will the PIDGIN allow me to use voice/webcam chat in VZOChat, WLM or Google Talk? I just want to hear something while I am at it. I read on the internet that it's not fully support or something about the audio but the thread ended. No final answer :\

About VirtualBox, yes that sounds very very sweet. I can't even wait to test out the Ubuntu! :D

Converting video is a strong point of Linux!  Convert your videos using a Linux program.

Voice and webcam chat is a weak point.  I use Skype under Ubuntu for videoconferencing.  It appears to require a reasonably modern (fast) computer.  I have not found a way to use voice and webcam on MSN.  I don't use the other chat systems you mentioned.

---

### Post by camaron1 on 2009-12-01
> I don't have any experience with virtualisation yet, but as I understand it the main limiting factor is how much RAM you have. If you have enough to provide the guest system with enough and still have enough left over for the host, I believe that performance can be very good.
If you have 3 gigas of ram (but more better), a half-decent graphic card, a multi-core processor and a free copy of Windows do give it a go.

---

### Post by NFblaze on 2009-12-01
double post

---

### Post by NFblaze on 2009-12-01
Just want to let you know that JDownloader is available in Linux.

Although, I have been unsuccessful in installing it. Though, there have been others who have. 


Also, alternatives for your other options are:

MeGUI (a media converter)    --------------> Handbrake or FFMpeg with GUI
RipBot264 (a media converter)--------------> Handbrake

Google Talk ------> Pidgin
VZOChat ----------> Pidgin

Windows Live Messenger -----> aMSN or Pidgin

Mozilla Firefox - Natively Available in Linux.

---

### Post by MoebusNet on 2009-12-01
Please allow me to recommend that you download a Ubuntu Live-CD image, burn it to a CD, then boot from it to try out Ubuntu with your hardware before you commit to a full install. You can save yourself a lot of time and aggravation by using Ubuntu (from the Live-CD) first before making any changes to your hard drive. It's kinda like taking a new car for a test drive before buying it.

If you don't have a CD or DVD drive, you can always download an Ubuntu image to install to a USB flash drive, but I don't have any experience doing that.

Don't get in a rush, get used to how Ubuntu does things before you commit to wiping out your Windows install. If you'll get used to Ubuntu first, then you'll be more confident about committing to Ubuntu. But once you do get used to Ubuntu, I confidently predict you'll enjoy the OS and the community supporting it.

Some recommended reading:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Best of luck!

---

### Post by jakslev on 2009-12-02
> **MKVCrazy said:**
> I appreciate your replies.

About to use Firefox's plugin, I never liked any browser built-in download managers, they're always not giving me full speed. I use JDownloader for a reason and its great features that you can't find on other apps. I did some search a few mins ago and I found that WINE is only able to run windows application and not the windows OS. If I want to do converting videos should I dual boot using VMware instead of using WINE? How might their performances differ? I don't want to do if any of them is going to use a LOT of CPU resource and slow up my computer.

EDIT

Will the PIDGIN allow me to use voice/webcam chat in VZOChat, WLM or Google Talk? I just want to hear something while I am at it. I read on the internet that it's not fully support or something about the audio but the thread ended. No final answer :\

About VirtualBox, yes that sounds very very sweet. I can't even wait to test out the Ubuntu! :D

Dear MKVCrazy, 

I very much agree with the two other responders. You will, when you start using Ubuntu, realize that a lot of the programs you were used to in Windows have counterparts that are working fine or evene better under Linux. 

I personally use Pidgin, because it allows me to sign-in to several instant messaging accounts (mainly MSN, Google Talk and my Facebook chat); and provides a clean no-nonsense interface. At present they do not support webcam and audio, but I believe you might be able to tweak it to do. In either case it is probably going to be supported within the next 12-18 months. My girlfriend uses aMSN, which is a clone of the normal MSN (with a few extra features). Here the webcam and audio is supported out of the box. Otherwise you can use Skype where the webcam and audio seems to work. 

Virtualbox is a virtualization machine - just as Virtual Ware. VirtualBox is supported by Microsoft-Arch-Enemy Sun Systems; and I found it very simple to use for a newbie. Sun Systems are also the people that will supply you with your Microsoft Office alternative - namely Open Office. It is true as someone else mentioned - virtualization takes RAM (I have 8, and that makes my Illustrator experience perfect as I have allocated 2 to the virtual machine).  

When I switched from Microsoft to Linux, I started with installing a dual-boot system. With a dual-boot you get two separate systems with FULL access to processor and graphics card. Only down part is that you have to split your hard disk in two. 

It is VERY important that when you start this test, you try to use Linux for as much of the daily things as possible. You will not fall in love with or appreciate the potential of the system; if you continue using Windows to surf the internet and write e-mails; and only log in to Linux when you want to do something that might take some tweaking (e.g. ripping a movie). You need to get the feel for the system! 

Otherwise running it from a cd or usb stick to see how the system looks is something you should do today. 

Good luck

---

### Post by jakslev on 2009-12-02
> **gordintoronto said:**
> Converting video is a strong point of Linux!  Convert your videos using a Linux program.

Voice and webcam chat is a weak point.  I use Skype under Ubuntu for videoconferencing.  It appears to require a reasonably modern (fast) computer.  I have not found a way to use voice and webcam on MSN.  I don't use the other chat systems you mentioned.

Hi GordinToronto, 

Trt aMSN. That works perfectly with video and audio. Visit: [http://www.amsn-project.net](http://www.amsn-project.net) for more info. 

jakslev

---

### Post by MKVCrazy on 2009-12-02
@jakslev

aMSN seems good. I've got 3 computers at home and one in the sky. I will try the Ubuntu Live-CD today hopefully, I need to find a free CD/USB stick :).

The system specs I am going to be testing on is below:
Intel Quad Core Q6600
4GB DDR2 RAM
1TB SATAII HDD

By the way, must the windows that I am going to install in VirtualBox be in CD/DVD? Can't it be in .ISO or something because it's a server and I can't go to the datacenter since it's about an ocean away from my home.

---

### Post by MKVCrazy on 2009-12-02
By the way, what is good for connecting to Ubuntu Server from a Windows 7 machine? I prefer something graphical if there's any but of course I care about securities and performances on speed. I have always been using Remote Desktop Connection on my Windows 7 to connect to my Windows 2003 server but Windows Server licenses are a pain in the a**. :( (Everything related to Microsoft is a pain in the a**, really.)

I am looking at the NoMachineNX. Will that work with Ubuntu? I've used it with Fedora 8 or something a few months back. I connected to my Fedora online pc from Windows XP fine. I am not sure how I am going to access to my Ubuntu and install the server version of NX so I can connect to it using my home Windows 7 PC.

---

### Post by 3rdalbum on 2009-12-02
The "ME" in "MEgui" stands for "MEncoder". MEncoder is a native Linux command-line program. So, definitely no need for dual-booting or Wine just to convert videos.

As far as voice and video goes, there is slowly being some progress made on this front. Linux itself is fully capable of it (you can do it today with Skype, on the Skype network), but nobody previously has taken the time to implement it for normal IM protocols like MSN and AIM.

The Meebo instant messenger ([www.meebo.com](www.meebo.com)) can do voice and video on any IM network. It does it through the Tokbox service, so the person on the other end will be prompted to open a URL that will give them access to Tokbox. Actually it's good incentive to get them to use Meebo as well; not only will it consolidate all their chat programs into one web browser window, but they can do seamless voice and video with you and other Meebo users.

EDIT: Ubuntu Server does not contain a GUI. You'll need to install the openssh-server on Ubuntu Server, and then install an SSH client such as PuTTY on Windows. This will enable you to get a command-line login remotely. If you are planning on installing a GUI onto Ubuntu Server (or using Ubuntu Desktop as a server, they'd be the same thing) then you can use any VNC client to log into your server's currently-running desktop.

---

### Post by adaucourt on 2009-12-02
> **oldsoundguy said:**
> Download manager .. I use FlashGot in FireFox

No, there are no virus files in the wild for Linux and there is no ANTI VIRUS program for Linux as a stand alone as it is not needed.  AV is needed if you are to act as a server to protect any Windows machines on that server .. and to screen any FORWARDED eMail  (bad idea in the first place, copy/past/send is a better idea!)
AV is also a good idea if you are running Windows programs in any form (in VM/Wine/dual boot/whatever) to protect those areas.  A Virus  will not migrate to your Linux nor to your boot sector.

Read 1st two paragraphs from Kaspersky Labs:
[http://www.internetnews.com/dev-news/article.php/3601946](http://www.internetnews.com/dev-news/article.php/3601946)

---

### Post by MKVCrazy on 2009-12-02
Ok let me summarize about the server part, correct me if I'm wrong.

> Ubuntu Server comes with OpenSSH-Server and I'll have the login infos when I receive the server infos from the hosting.
> Then I login to the server using SSH Client like PuTTY which is commandline and use that commandline to install either Ubuntu Server GUI or Ubuntu Desktop GUI.
> Then I install NoMachineNX Server from PuTTY since there's no server app in the GUI.
> I use the NoMachineNX Client on my windows PC to connect to that Ubuntu Server/Desktop GUI

Then what about the commandline version of the Ubuntu? I just leave it or it's running as long as I run the GUI version of Ubuntu? I am a little confused between the Ubuntu GUI and non-GUI.

Thanks for your patience guys, I am new to non-GUI stuff.

EDIT:

So now will I be running two OS'es? Ubuntu Server (one without GUI) and Ubuntu Server or Desktop GUI?

---

### Post by ed-koala on 2009-12-02
As far as viruses and Wine is concerned, this is not a problem as long as you **NEVER RUN WINE AS ROOT**!

I yelled that because it's that important. Unless you give Wine root privileges, it can't harm your system even if you install a windows virus infected file.  The absolute worst that can happen is it'll affect stuff in your .wine directory.  It will not hose your Ubuntu or affect system files at all.

---

### Post by Some Penguin on 2009-12-02
> **ed-koala said:**
> As far as viruses and Wine is concerned, this is not a problem as long as you **NEVER RUN WINE AS ROOT**!

I yelled that because it's that important. Unless you give Wine root privileges, it can't harm your system even if you install a windows virus infected file.  The absolute worst that can happen is it'll affect stuff in your .wine directory.  It will not hose your Ubuntu or affect system files at all.

Does the phrase "privilege escalation" mean anything to you?

---

### Post by ed-koala on 2009-12-02
Actually, no. Care to enlighten me? I was under the impression what I said was correct, and at worst you might have to wipe and reinstall wine and all your wine programs.

---

### Post by MKVCrazy on 2009-12-02
Please review my steps :\

---

### Post by jakslev on 2009-12-02
> **MKVCrazy said:**
> @jakslev

aMSN seems good. I've got 3 computers at home and one in the sky. I will try the Ubuntu Live-CD today hopefully, I need to find a free CD/USB stick :).

The system specs I am going to be testing on is below:
Intel Quad Core Q6600
4GB DDR2 RAM
1TB SATAII HDD

By the way, must the windows that I am going to install in VirtualBox be in CD/DVD? Can't it be in .ISO or something because it's a server and I can't go to the datacenter since it's about an ocean away from my home.

Sure no problem with using an ISO file to install in Virtualbox

---

### Post by jakslev on 2009-12-02
> **MKVCrazy said:**
> By the way, what is good for connecting to Ubuntu Server from a Windows 7 machine? I prefer something graphical if there's any but of course I care about securities and performances on speed. I have always been using Remote Desktop Connection on my Windows 7 to connect to my Windows 2003 server but Windows Server licenses are a pain in the a**. :( (Everything related to Microsoft is a pain in the a**, really.)

I am looking at the NoMachineNX. Will that work with Ubuntu? I've used it with Fedora 8 or something a few months back. I connected to my Fedora online pc from Windows XP fine. I am not sure how I am going to access to my Ubuntu and install the server version of NX so I can connect to it using my home Windows 7 PC.

The VNC protocol i supported natively in Ubuntu. I would use VNC for windows to connect :)

---

### Post by Some Penguin on 2009-12-02
Escalation of privileges refers to... well, literal escalation of privileges, just like it sounds.   In a normal Unix-y environment with the user/group model and omnipotent root, the extreme case is where an ordinary user account manages to act as root.   There are intentional, legitimate ways to happen (the 'sudo' mechanism) but there also (generally unintentional) vulnerabilities that get discovered from time to time where unprivileged users interacting, possibly quite indirectly, with privileged code can improperly gain privileges they shouldn't have had.

Sometimes, this happens in badly-written packages which are fairly rare, or in ways that are difficult to exploit.  Sometimes, this happens in ways that can only be exploited by somebody who already has an ordinary user account (local access).   Sometimes, these can be trivially exploited remotely by people who don't have *any* local account -- this usually means occurs through a buffer overflow where arbitrary executable code gets dumped on the stack along with a fake call stack or through executing requests that have been poorly sanitized (if at all).

See [http://www.cr0.org/misc/CVE-2009-2692.txt](http://www.cr0.org/misc/CVE-2009-2692.txt) for one example.  This particular case affected all Linux kernels from 2.4.4-2.4.37.4, and 2.6.0-2.6.30.4 -- released between *May 2001 and August 2009* -- and allowed non-root local users to assume root privileges.

Basically, the lesson here is that having a user/group model with various security mechanisms does not mean that you can assume that the model is actually properly implemented, or that there is complete separation (there can't be, in general, because it'd be rather limiting if non-privileged code couldn't ever interact with privileged code such as the kernel.)  Wine, being written by people, is not immune to improper or perhaps even subtly malevolent coding practices, or in vulnerabilities in related packages -- run Wine on top of a vulnerable kernel or the like, and it is not entirely impossible that malware could be written which would trigger those bugs.  This is really not that different from any other operating system.

Of course, a real paranoid might be running OpenBSD or, if they had to run Linux, SE Linux.

---

### Post by oldsoundguy on 2009-12-02
> **adaucourt said:**
> Read 1st two paragraphs from Kaspersky Labs:
[http://www.internetnews.com/dev-news/article.php/3601946](http://www.internetnews.com/dev-news/article.php/3601946)

Look at the DATE
Look at the vagueness of the content.
And remember that Kaspersky is trying to sell AV programming.
Then realize that thus far, all of the virus files that have been written for Linux that have escaped to the wild are SERVER virus files (they do not have an effect ON the computer, just on what passes THROUGH the computer .. just as I mentioned .. they target WINDOWS computers.
Not saying there will never be a virus file that targets the desktop user .. never say never .. but, unless that user is running in ROOT, (something Ubuntu has managed to avoid), the chances of INSTALLING a virus is about as good as Rush Limbaugh voting Democrat.

---

### Post by ed-koala on 2009-12-02
Ok, granted, such things are possible.  But the likelihood of anything actually happening to your system while running Ubuntu is pretty remote. I've been using Ubuntu for a long time now without any firewall or antivirus protection and have had zero trouble.

I still maintain Wine is safe, at least as far as your system is concerned, so long as you never run Wine as root.  Any malware you might pick up under a Wine install should be confined to Wine.  However, running Wine as root would be foolish and begging for trouble.

---

### Post by JKyleOKC on 2009-12-02
> **MKVCrazy said:**
> By the way, must the windows that I am going to install in VirtualBox be in CD/DVD? Can't it be in .ISO or something because it's a server and I can't go to the datacenter since it's about an ocean away from my home.Yes, they can be in ISO form; the VirtualBox settings dialogs let you choose between physical drives or specific ISO files, and you can change without shutting down the program.

---

### Post by MKVCrazy on 2009-12-02
Alright, I am sorting everything in my head and so far so good. But I came up with another question which might make me stuck. I was reading on the internet that you can set the as much as you want for the VirtualBox but I didn't see if I can set like below

Let's say total RAM on server is **12GB DDR2**.

Give Linux Ubuntu - **2GB**
Give Windows XP Pro/Home from VirtualBox - **10GB**

Is that possible? Setting the virtual one higher than the root? Will converting in virtualbox faster then?

EDIT

I've decided to higher the server specs a little when I realize RAM matter and I have experienced systems with 2GB and find it not so fast. So getting more RAM.

---

### Post by jakslev on 2009-12-02
> **MKVCrazy said:**
> Alright, I am sorting everything in my head and so far so good. But I came up with another question which might make me stuck. I was reading on the internet that you can set the as much as you want for the VirtualBox but I didn't see if I can set like below

Let's say total RAM on server is **12GB DDR2**.

Give Linux Ubuntu - **2GB**
Give Windows XP Pro/Home from VirtualBox - **10GB**

Is that possible? Setting the virtual one higher than the root? Will converting in virtualbox faster then?

EDIT

I've decided to higher the server specs a little when I realize RAM matter and I have experienced systems with 2GB and find it not so fast. So getting more RAM.

If you go over 65% VirtualBox will complain and warn you that your main system might be suffering. If you hit 85% it down-right refuses. At least on my system. However, most likely you wont need nearly that amount. I have allocated 2 GB to my Windows VirtualBox and it runs Photoshop and Illustrator fine. As far as I am aware these are very RAM consuming programs, so I would imagine that you won't need to allocate more than 4GB RAM if you wanted to be on the super safe side...

But give it a try - otherwise the alternative could be to boot into Windows XP at dual-boot.. That way you would have full access. 

However, as someone else mentioned before, by going to Linux you are using a different system and it would, in the long run, be a bad idea to be too stuck on old Windows programs.

---

### Post by MKVCrazy on 2009-12-02
@jakslev

Yes I too think it's a bad idea to touch any thing related to "Windows" especially on server relate things as we need servers to be a lot faster than our normal old computers. Well I guess I should try the RAM limit until I find my best taste then.

A couple days ago I was running 4 heavy programs, Photoshop CS4, MS PowerPoint, A Banner Creator, plus converting some youtube videos for my iPod Touch on my Windows 7 Ultimate with 2GB RAM (but 64-Bit OS). It hanged for 8 hours and I thought it's still proceeding the converting and trying to run all the programs till end but they were just completely "STUCK". Nothing was being done. I found out after I did hard reboot from the power button and turned it back on. I was pretty disappoint about that as I was hoping Windows 7 will be the fastest and least hangs of all OS'es like Vista, 2003 (besides XP). Then this Linux Ubuntu thing poped into my head :D when I went to internet and saw the huge amount of Windows Server License.

---

### Post by gordintoronto on 2009-12-02
> **jakslev said:**
> Hi GordinToronto, 

Trt aMSN. That works perfectly with video and audio. Visit: [http://www.amsn-project.net](http://www.amsn-project.net) for more info. 

jakslev

Thanks, Jakslev,

I'm still using Jaunty, so I don't have the latest version of Amsn.  When I went to the Amsn site and selected Download/Linux, it provided a "package" file which is not associated with any application, and the link "Please follow the instructions to install the package." gives a 404.

---

### Post by adaucourt on 2009-12-03
> **MKVCrazy said:**
> By the way, what is good for connecting to Ubuntu Server from a Windows 7 machine? I prefer something graphical if there's any but of course I care about securities and performances on speed. I have always been using Remote Desktop Connection on my Windows 7 to connect to my Windows 2003 server but Windows Server licenses are a pain in the a**. :( (Everything related to Microsoft is a pain in the a**, really.)

I am looking at the NoMachineNX. Will that work with Ubuntu? I've used it with Fedora 8 or something a few months back. I connected to my Fedora online pc from Windows XP fine. I am not sure how I am going to access to my Ubuntu and install the server version of NX so I can connect to it using my home Windows 7 PC.


[LIST]
[*]PuTTY
[*]You can also install Webmin on the server box and access via web
[/LIST]

---

### Post by MKVCrazy on 2009-12-03
Thanks to all who replied, I have all the info I need to get an Ubuntu server :) Let's see how goes and when I find myself later Lol. Thanks for your patience on answering my newbie question too.

---

### Post by adaucourt on 2009-12-03
> **MKVCrazy said:**
> Ok let me summarize about the server part, correct me if I'm wrong.

> Ubuntu Server comes with OpenSSH-Server and I'll have the login infos when I receive the server infos from the hosting.
> Then I login to the server using SSH Client like PuTTY which is commandline and use that commandline to install either Ubuntu Server GUI or Ubuntu Desktop GUI.
> Then I install NoMachineNX Server from PuTTY since there's no server app in the GUI.
> I use the NoMachineNX Client on my windows PC to connect to that Ubuntu Server/Desktop GUI

Then what about the commandline version of the Ubuntu? I just leave it or it's running as long as I run the GUI version of Ubuntu? I am a little confused between the Ubuntu GUI and non-GUI.

Thanks for your patience guys, I am new to non-GUI stuff.

EDIT:

So now will I be running two OS'es? Ubuntu Server (one without GUI) and Ubuntu Server or Desktop GUI?

[FONT=Arial]Ubuntu server doesnt come with open-ssh installed you must install it with :
```
sudo apt-get install openssh-server
```

You can then login to your ubuntu server via SSH using PuTTY

Ubuntu Server does not include a GUI(Graphical User Interface) and Ubuntu Desktop does, although you can install a GUI support on Ubuntu Server by issuing this command:
[/FONT][FONT=Arial]```
sudo apt-get install ubuntu-desktop
```

You don't need NoMachineNX to connect to a remote Ubuntu box.  You can use tsclient (with xvnc4viewer) 
installed from another Ubuntu box, or VNC from a Windows box.  This is of course if you wish to connect 
remotely in a graphical nature as opposed to the terminal (PuTTY).

Sitting at the machine you will now be able to login to the GUI and have a pretty desktop vs. text

Hope this clears things up!
[/FONT]

---

### Post by bdalzell on 2009-12-03
A lot web based downloading can be done from the command line with the command line program wget. There are also GUI front ends for  wget such as GWGet or Gnome Transfer Manager. If they are not installed when you set up your Linux system it is easily to acquired them using the add-remove application found when you click on Applications in the Panel and then go down to the bottom of the menu to Add/Remove.

One of the reasons Linux is resistant to malware is that there is not much written for it, while another reason is that a lot of open source applications are kept in official repositories so that when you fetch one to add it, you have confidence that it is a safe application.

When you use Applications>Add/Remove you have to type in your user password before the system will fetch a new application and install it.

I have been running Ubuntu for 4 years now and yet to have a virus. On the other hand I have to help remove some piece of malware or anther from my roomate's Windows computer every couple of months. The OSX MAC that is the third computer here has not gotten viri either. But OS X has as an underpinning a Unix operating system that is very similar to Linux in the way it implements permissions and handles users.

---

### Post by jakslev on 2009-12-04
> **gordintoronto said:**
> Thanks, Jakslev,

I'm still using Jaunty, so I don't have the latest version of Amsn.  When I went to the Amsn site and selected Download/Linux, it provided a "package" file which is not associated with any application, and the link "Please follow the instructions to install the package." gives a 404.

No need to go to their actual website. You should find aMSN in the repositories using Synaptics Package Manager (System - Administration - SPM). 

If you somehow does not find itin SPM (which you will) you can find it on Sourceforge here: [http://sourceforge.net/projects/amsn/files/amsn/0.98.1/amsn-0.98.1-1.tcl85.x86.package/download](http://sourceforge.net/projects/amsn/files/amsn/0.98.1/amsn-0.98.1-1.tcl85.x86.package/download). 

Cheers, 

jakslev

---

### Post by gordintoronto on 2009-12-04
> **jakslev said:**
> No need to go to their actual website. You should find aMSN in the repositories using Synaptics Package Manager (System - Administration - SPM). 

If you somehow does not find itin SPM (which you will) you can find it on Sourceforge here: [http://sourceforge.net/projects/amsn/files/amsn/0.98.1/amsn-0.98.1-1.tcl85.x86.package/download](http://sourceforge.net/projects/amsn/files/amsn/0.98.1/amsn-0.98.1-1.tcl85.x86.package/download). 

Cheers, 

jakslev

Thanks for your efforts.  However, the version in the Jaunty repository is not the latest one, and Sourceforge offers me a "package" file.  I have no idea what to do with a "package" file.

---

### Post by Frogging101 on 2009-12-04
There are a bunch of issues with Windows Live Messenger audio chat in most of the linux messenger programs.

---

### Post by audiomick on 2009-12-04
> **MKVCrazy said:**
> 

Then what about the commandline version of the Ubuntu? I just leave it or it's running as long as I run the GUI version of Ubuntu? I am a little confused between the Ubuntu GUI and non-GUI.

Thanks for your patience guys, I am new to non-GUI stuff.

EDIT:

So now will I be running two OS'es? Ubuntu Server (one without GUI) and Ubuntu Server or Desktop GUI?

I think no one has answered this yet.

A non GUI Linux is a GUI linux without the GUI installed. A GUI Linux is a  non GUI linux with a GUI installed.

---

### Post by MKVCrazy on 2009-12-04
> **audiomick said:**
> I think no one has answered this yet.

A non GUI Linux is a GUI linux without the GUI installed. A GUI Linux is a  non GUI linux with a GUI installed.
You're making it more complicated Lol. Are you saying yes I am going to be having two OS'es running at the same time or NO, I won't be? I've installed it on my home computer and so far  I AM STUNNED by the effects and speeds of Linux/Ubuntu!

Now I just need to make a decision for my server whether I should take their ready-to-go Ubuntu Desktop 8.XX 32Bit or get the Ubuntu Server 9.04 64Bit and install the Ubuntu Desktop 9.04/9.10 64Bit myself.

---

### Post by JKyleOKC on 2009-12-04
> **MKVCrazy said:**
> Are you saying yes I am going to be having two OS'es running at the same time or NO, I won't be?No, you won't be. There'll only be a single OS running.

The difference is that the GUI, which is actually a suite of programs separate from the OS itself, won't be taking up any space on your drives if you install the non-GUI version. You can install a GUI version, and then disable the GUI from starting, to get essentially the same action as the non-GUI version.

Personally, I install a GUI version (Xubuntu) which has an interface I find simpler than the one in the Ubuntu or Kubuntu versions, and let the GUI run anyway. It makes life simpler for me and with a modern set of hardware doesn't incur any noticeable performance penalty...

---

### Post by judge jankum on 2009-12-04
As far as security, I've hit "warez" sites "porn" sites" and every site posted anywhere that had a virus or trojan just putting Ubuntu through hell lol! And nothing has touched it so far...
I have a puter set up just to test it...And I have to hell and back.....And I'm on it right now with no virus, no trojan and no malware.....No money either, but that's another story lol!!!

---

### Post by chronus_aurelius on 2009-12-05
I use Virtualbox to cover my legacy hardware with windows xp.  I recommend Virtualbox which is free as a way to transition into Linux.  I also dual-boot, but the problem with dual booting is that it takes about 5 minutes to do, and then you start dreading having to reboot.  I have stayed away from Wine during my decade use of Linux because everybody seems to be having to teak things to get then to work, and that is not a trip I recomend for a new user.

With virtualbox, you can easily get your printer, scanner and other hardware to work with their original software, and it works out-of-the-box, no teaking.

Since we are in a time where we are starting to do everything on the Internet, I can assure you, you can do 99% of your daily task using Linux.  the 1% being, as other replies suggest, gaming (non-flash gaming that is) and some types of DRM (Digital Rights Management) media.

---

### Post by MKVCrazy on 2009-12-05
Thanks Kyle, now I now understand it better. I think of it as a person which is the OS and when the person is naked that means it's non-GUI and when clothes on it becomes GUI but still one person (one OS) :)

And yes I agree, chronus. I can see most of what I do could be done easily on Linux except those media stuff and other non-win stuff. I'm also planning to install VirtualBox when I get what I need first installed.

By the way, can you catch virus through VirtualBox? Will it destroy your computer if virus was caught through the windows program being ran in VirtualBox? Or the virus won't get out too far beyond VirtualBox? Cuz I gotta ask this since I am not planning to install any AV yet.

---

### Post by ed-koala on 2009-12-05
Yes, your virtual windows can catch viruses. No, they cannot go beyond that. All you need to do to stop problems is take a snapshot of your virtual machine at a point where you have it set up as you like, then if you get zapped by a virus, just restore to the snapshot and you're good to go.

---

### Post by hallu on 2009-12-05
> **MKVCrazy said:**
> 
JDownloader (JAVA based file download manager)


jdownloader is available for linux

---

### Post by 3rdalbum on 2009-12-05
> **gordintoronto said:**
> Thanks for your efforts.  However, the version in the Jaunty repository is not the latest one, and Sourceforge offers me a "package" file.  I have no idea what to do with a "package" file.

When you say a "package file", do you mean that the filename ends in ".package"?

If that's what you mean, then just run that file. It's an Autopackage; when you run it, it brings up a GUI that installs the program and its dependencies.

---

### Post by Nixie Pixel on 2009-12-05
I always advise dual-booting if you're a gamer, and already have Windows to play your games on.

Trying to get the current games to run in Wine is painful...

---

### Post by MKVCrazy on 2009-12-05
> **ed-koala said:**
> Yes, your virtual windows can catch viruses. No, they cannot go beyond that. All you need to do to stop problems is take a snapshot of your virtual machine at a point where you have it set up as you like, then if you get zapped by a virus, just restore to the snapshot and you're good to go.
What do you mean by "snapshot"? To me that means to take a screenshot in to an image format which helps nothing except I can see the screenshoted desktop. :confused:

---

### Post by amauk on 2009-12-05
A snapshot, in reference to virtual machines, is a copy of the virtual machine at a particular time

VM managers, like virtualbox, etc, allow you to take snapshots of VM's and then later revert back to particular snapshots

---

### Post by MKVCrazy on 2009-12-05
> **amauk said:**
> A snapshot, in reference to virtual machines, is a copy of the virtual machine at a particular time

VM managers, like virtualbox, etc, allow you to take snapshots of VM's and then later revert back to particular snapshots
Got it, thanks a lot. I'll try it tomorrow.

---

### Post by JKyleOKC on 2009-12-05
> **MKVCrazy said:**
> What do you mean by "snapshot"? To me that means to take a screenshot in to an image format which helps nothing except I can see the screenshoted desktop. :confused:Nope, in a virtual machine, a snapshot is much like the Windows System Restore feature. However the snapshot is a total backup of the whole virtual machine, including all the disk files and memory. Thus when you restore a snapshot later, it wipes out everything that has happened since the snapshot was taken.

If you've read about doing a disk image of a Windows system, such as with Norton's Ghost or the Acronis True Image program, the snapshot of a virtual machine is the same thing -- only easier and faster.

---

### Post by gordintoronto on 2009-12-05
> **3rdalbum said:**
> When you say a "package file", do you mean that the filename ends in ".package"?

If that's what you mean, then just run that file. It's an Autopackage; when you run it, it brings up a GUI that installs the program and its dependencies.

"Run" the file?  Nautilus says there is no application associated with a .package file.  I had never heard of an "autopackage" before.

I googled it, and installed Autopackage, then removed the old AMSN and installed the new one.  When I run it, I get the message: "There's a problem loading a module of aMSN (TkCxImage): couldn't load file "utils/TkCximage/TkCximage.so":  utils/TkCximage.so: wrong ELF class: ELFCLASS32

I guess this version of aMSN is for people who know what an ELFCLASS is.

---

### Post by jakslev on 2009-12-06
> **gordintoronto said:**
> Thanks for your efforts.  However, the version in the Jaunty repository is not the latest one, and Sourceforge offers me a "package" file.  I have no idea what to do with a "package" file.

Hi GordinToronto, 

Most of the software that is in Ubuntu is NOT the latest version of the software. The team behind Ubuntu checks the software to see what is stable etc. to minimize the amount of errors experienced by us end-users. That's why you will see that the repository file is an older version than the one you find on the developers sourceforge website. 

If you choose the file from the sourceforge website it will not be updated automatically through the update manager. I would therefore advise you to use that file - unless there is a specific feature in the latest version of aMSN that you need. 

Should you want to use the file I would download it into a folder under your user account (f.i. /home/user/.aspecialamsn/ - the initial period making the folder invisible in normal view). The cd your way into the folder with terminal. Here you will use the sh [filename] command to install the file (could also be that it will work with install. depending on the filename).

Cheers. 

jakslev

---

### Post by gordintoronto on 2009-12-06
> **jakslev said:**
> Hi GordinToronto, 

Most of the software that is in Ubuntu is NOT the latest version of the software. The team behind Ubuntu checks the software to see what is stable etc. to minimize the amount of errors experienced by us end-users. That's why you will see that the repository file is an older version than the one you find on the developers sourceforge website. 

If you choose the file from the sourceforge website it will not be updated automatically through the update manager. I would therefore advise you to use that file - unless there is a specific feature in the latest version of aMSN that you need. 

Should you want to use the file I would download it into a folder under your user account (f.i. /home/user/.aspecialamsn/ - the initial period making the folder invisible in normal view). The cd your way into the folder with terminal. Here you will use the sh [filename] command to install the file (could also be that it will work with install. depending on the filename).

Cheers. 

jakslev

I appreciate that you are trying to help.  However, the version of amsn from the repositories does not meet my need for audio, video and text chatting.  I can do it with Skype, but I would prefer to do it through the MSN connection.  (My wife is on an extended trip to China, and we videoconference almost every day.)

---

### Post by jakslev on 2009-12-07
> **gordintoronto said:**
> I appreciate that you are trying to help.  However, the version of amsn from the repositories does not meet my need for audio, video and text chatting.  I can do it with Skype, but I would prefer to do it through the MSN connection.  (My wife is on an extended trip to China, and we videoconference almost every day.)

That's weird - I installed it from the repository and my partner she uses it almost daily with video and audio.. She is using version 0.98.1...

jakslev

---

### Post by gordintoronto on 2009-12-07
> **jakslev said:**
> That's weird - I installed it from the repository and my partner she uses it almost daily with video and audio.. She is using version 0.98.1...

jakslev

Thanks, my primary computer is running Jaunty, which does not have that version in the repository.  I have an older computer with Karmic, and it now has the latest Amsn.  In the audio and video setup, everything works very nicely.  Now to see what happens when my sweetie logs on.

---

### Post by jakslev on 2009-12-08
> **gordintoronto said:**
> Thanks, my primary computer is running Jaunty, which does not have that version in the repository.  I have an older computer with Karmic, and it now has the latest Amsn.  In the audio and video setup, everything works very nicely.  Now to see what happens when my sweetie logs on.

Gotcha.. you might have problems with the firewall. Somehow the video/audio ports are blocked on my computer (suspect they have been switched off in connection with either NFS or SAMBA extensions).. But that should be easily amended...

---

