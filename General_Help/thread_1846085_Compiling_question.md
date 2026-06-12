---
title: "Compiling question"
date: 2011-09-18
forum: General Help
---

### Post by smcrossman on 2011-09-18
Okay...background I have a desktop running Ubuntu 11.04 64 bit, and a netbook running 11.04 (largely Kubuntu at the moment) & Win 7 dual boot.  I am adding a NSS to my system....basically an external hard drive that hooks into my gateway (modem/router) designed for automatic backups and file storage. The Windows install went fine (of course...the CD is for windows/mac).  The website provides opensource download for use.  Largely it seems to be based on something called curl (which I have discovered is already fully installed on my system).  

So the issue:  I have the directory set up with access. I extract the tar.bz2 using the proper code. Fine so far.  It gives me everything in src.rpm.  Okay fine...so my question is....have I successfully unpacked the source archive? I know rpm isn't going to run on my system. I can't get autogen.sh or automake or any of those to run (but I am truly not good with compiling). 

Do I use alien or something else to convert the .src.rpm into regular .src? and then how do I put it back into a "package" so that I can compile it?

I suspect there is an easier option (such as an existing program to do basically the same thing in Linux) but I stilll need to include the Windows 7 stuff too.

NSS Drive is a Seagate FreeAgent GoFlex Home 1TB.  

I like the Seagate Dashboard and the Seagate Shares set up seems fairly user friendly. But it's all fairly useless if I cant access it with linux as well as windows.  I know that I will have to go with a cross-system backup tool to set up automatic backups, so I haven't even looked a thte Memeo that came with the software.

If you need to see the source link or source here is the webpage:

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=gpl&vgnextoid=02d819e56cdee010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=gpl&vgnextoid=02d819e56cdee010VgnVCM100000dd04090aRCRD)

Basically....1) do I need to use alien to get from .rpm to general .src?
2) Then how do I get ./configure to run with such a huge package? Or will one of the package managers install it for me if I get it out of .rpm?

---

### Post by grayraven on 2011-09-18
Hey smcrossman,

Normally, the src.rpm file is just a source package. These are similar to the src.deb package files. You should be able to use alien to convert them.

However, I downloaded the file for the GoFlex Home, and expanded it. The packages all seem to be the src packages for a basic Linux systems. I believe in this case it is for a RedHat Enterprise Linux 6 system. Is there a specific package in the collection that you are trying to build?

Cheers,

James

---

### Post by smcrossman on 2011-09-18
Actually I've been wondering about the huge number of files.

The Installation DVD (with 5 languages) has the driver, the Seagate Dashboard, The Seagate Share, and Memeo Instant Backup softwares.  The first one gives you a graphical overview of the 3 partitions on the drive...public, personal,backup and the files on whichever you choose to look at.  The 2nd gives a graphical interface to take the files from the first 2 partitions and create shares  for others on the network.  

Basically samba/nmbd-smpt/ssh only in a really simple pretty gui.  Of course somewhere in that software it also allows for wireless connection to each share and access over the internet. (Okay that is part of the others as well...but way beyond my skill level. 

Basically the problem is that so far I haven't been able to "see" or "access" the network drive except with windows which has the software packages installed.  I have the IP address and am working to add it as a host but I still am not getting it mounted, so I thought the software might be easier....

Of course one difference between external storage and a network drive is that the network drive has some form of operating system in order to do processes and jobs that a basic external drive doesn't.  Basically...would the short version be to hook it up to the desktop, format it (its currently NTSF) and install a version of server or such on it?  Keeping the 3 partitions for the filesystem and backups.

I guess I'd better do a better job of reading through all those files and see if anything seems like one of the software packages I'd like to use, as well as start searching the opens source listings for something as well.

Thanks for the help....I was just baffled at the amount of files/directories and totally lost at how it would all install as one package.

---

### Post by grayraven on 2011-09-19
Hey smcrossman,

I just want to make sure I am clear on what you are saying. The DVD you refer to is the Windows/Mac installation. The driver and listed utilities are the ones that are installed on the Windows/Mac client machines.

While this doesn't solve the problem, you might be able to mount the shares using the IP of the device and the share name. I am thinking they are SMB/Samba shares. So, you should be able to use smbmount to mount them. Once installed the man page gives some good examples of the commands. Since it is a network share, the drive format should not matter.

I am parsing out the known packages from that file to see what unknowns are left. Maybe one of them is an installation for the utilities.

Cheers,

James

---

### Post by smcrossman on 2011-09-19
Sounds like you understand correctly.  Thank you for the help!  I assigned it a domain name to keep from getting myself confused, and IF I recall correctly on the desktop under network this morning it listed Windows network, Zanazoo smb and of course the host Needle.  I couldn't actually access either smb due to mounting issues....but I haven't gone in to fully set up Samba or ssh (which is what the Zanazoo is kicking out on) since I was hoping that the provided software would save me the time/trouble. 

If/when I get home again (sitting along side of  road waiting for gasoline delivery) I'll look at the Samba and the ssh setup and what I have left to do.  Samba I'm very familiar with ssh not so much.  I did find a slew of automated backup packages in the repositories last night, but not any really for the shares or using it for basic file storage....then again that is what the networking programs really do.  I haven't tried smbmount...but will research taht while I am sitting here waiting! Thanks!

---

### Post by srs5694 on 2011-09-19
I concur with grayraven that the package to which you've linked is not software for you to run on your own computer; it's probably the source code to the OS that runs on the device itself. As such, it will be useless to you unless you're trying to compile custom software for that device.

From your description, it sounds like the device might support SMB/CIFS, which Linux should be able to mount. If you're having problems, you might try smbclient as a diagnostic tool, which you can use like this:

```

smbclient //hostname/sharename

```

If it connects, smbclient supports ftp-like commands (put, get, ls, and so on), so you can check basic operations. If you can't get in, you might at least get a helpful error message.

If the device doesn't support SMB/CIFS, you'll need to figure out what protocol it does support. There should be documentation somewhere that describes this, or as a last resort, you could try a port scanner -- but only try a port scanner on your own personal network, not on an employer's network, since many workplaces forbid their use!

---

### Post by smcrossman on 2011-09-22
Thanks. On my list of things to do int he next couple of days. Yesterday my entire internet access to my system was out....still trying to clean up odds & ends there.  At themoment the NSS isn't even attached. Hopefully it will be again by this evening.  I will definitely use the smbclient for diagnostic (new to me, but good learning!) I'm also trying to make sure I did all the set up steps for samba. So I'll be running through that diagnostic as well to ensure that the issue isn't in my existing system.

---

### Post by smcrossman on 2011-09-25
Currently the NSS drive is showing up as SFTP File Transfer on GoFlex under Network.  So it isn't actually smb....although I thought samba supported ftp....do I need to install SSH Server onto the NSS?  What is the best way to do that?  Off to do more reading & research on external and remote drives.....

---

### Post by grayraven on 2011-09-25
Hey smcrossman,

You may not need to install it on the NSS if it is showing up as a sftp connection. You might be able to access it using SSH from your Linux machine. I think the sftp command line is similar to the ssh command line. Let me know if this helps.

Cheers,

James

---

