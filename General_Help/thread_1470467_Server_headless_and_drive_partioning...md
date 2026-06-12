---
title: "Server headless and drive partioning.."
date: 2010-05-02
forum: General Help
---

### Post by jfls45 on 2010-05-02
Ok, here is  where I am at. I have the latest download of Ubuntu Server 10.04  installed.  I have not installed a gui for it. I would like to be able  to do this from command line if possible. I will be running this server  headless but I would like to be able to login remotely if necessary. My  hunch is I will need a gui to be able to log in remotely?
 
I have three Internal drives in my server. 80GB, ext4 formatted, this  has the server os loaded on it. The other two drives are 160 and 500GB  formatted ext4 as well but they are empty. I have two Ext USB drives  with all my stuff I don't want to lose. Both are formatted NTFS. So I  need help but keep in mind I am going to run the server headless, but  would like to login remotely if necessary without a gui. 

My other home computers will dual boot windows or linux, so I need to  know what is the safest and best way to format the two drives in my  server. ex4 or ntfs?  

Will I be able to run server without a gui as headless?  

I just installed Samba4 and starting down the learning curve by googling  how to set it up.  
My file sharing is simple. Nothing special within the Lan, but want to  keep hackers out from the outside world. I use Logmein on my windows  computers and may want to setup a remote login for the server at some  point. Right now my big this is setting up the drives, shares, and going  headless. I would like to be able to just turn the thing on and not  worry about it. 

thanks for all your help...

jte

---

### Post by jfls45 on 2010-05-02
Another question I have is...  If I copy files from NTFS drive to a EXT4  and then copy lets say a movie file or music, whatever, is there known problems it doesn't work or ?   Is it better to go all EXT4 partions for all drives that store files or mix as you want?  What is anyone experience?

JTE

open to all suggestions

---

### Post by srs5694 on 2010-05-03
> **jfls45 said:**
> Ok, here is  where I am at. I have the latest download of Ubuntu Server 10.04  installed.  I have not installed a gui for it. I would like to be able  to do this from command line if possible. I will be running this server  headless but I would like to be able to login remotely if necessary. My  hunch is I will need a gui to be able to log in remotely?

No, your hunch is wrong. You can log in remotely using SSH, provided you install and enable the SSH server (via the openssh-server package). There are other text-mode and GUI login protocols for Linux, but SSH is the preferred text-mode tool for most installations because it supports good encryption techniques.
 
> My other home computers will dual boot windows or linux, so I need to  know what is the safest and best way to format the two drives in my  server. ex4 or ntfs?

Whenever possible, use an OS's native filesystem(s). If a server system will be running Linux, use ext2fs, ext3fs, ext4fs, ReiserFS, JFS, or XFS. (For the brave, Btrfs is also an option, but it's still very new.) The fact that the Linux system will have Windows (or OS X or FreeBSD or Commodore 64 or whatever) clients is irrelevant, since most network servers (Samba, Apache, etc.) work on files, not on filesystems. That is, the network servers are unlikely to care what filesystem is in use, and the clients won't have a clue about that detail.

> Will I be able to run server without a gui as headless?

Yes. That's how many big Linux servers run. To do so, you'll want to shut down the GDM server by disabling its SysV init script. Try Googling "Ubuntu SysV scripts" or "Ubuntu init scripts" to find a tutorial on how to do this (I don't have a reference handy).

> My file sharing is simple. Nothing special within the Lan, but want to  keep hackers out from the outside world. I use Logmein on my windows  computers and may want to setup a remote login for the server at some  point.

If your server's clients will all be within your LAN, then your single best security measure is to set up a firewall for the entire LAN. Since you mentioned this was a home LAN, I recommend you look into a broadband router, if you don't already have one. Be sure it's properly secured -- it shouldn't forward ports unnecessarily and if it's got wireless capabilities, you should be sure it's set up with WPA2 security (not WPA and *definitely* not WEP), and preferably restrict it to respond only to your own Wi-Fi systems via their hardware addresses.

If you want remote access, as in access from outside your LAN, you'll need to forward the SSH port -- or better yet a non-standard port from the outside to the standard SSH port on your server. You configure this in your broadband router, so it's not really a Linux issue per se. This is a security risk, though, and if you do this you should ensure you use a strong password. There are other security measures you can take, but I can't really go into all the details -- whole books have been written on this topic!

> If I copy files from NTFS drive to a EXT4  and then copy lets say a  movie file or music, whatever, is there known problems it doesn't work  or ?   Is it better to go all EXT4 partions for all drives that store  files or mix as you want?

A file is just a pattern of bytes, and the filesystem just determines where those bytes get stored on the disk. Thus, assuming no bugs or hardware failures, a file won't get damaged just because you copy it from one filesystem to another. That said, different filesystems have different performance characteristics, and some filesystems are more reliable than others. Recent NTFS drivers for Linux are said to be fairly reliable, but for a Linux-only system, Linux-native filesystems are likely to be more reliable and faster than NTFS. Furthermore, NTFS on Linux has the major drawback that Linux will become unable to read it after a power failure or system crash. After such an event, the filesystem must be checked by Windows before Linux will be able to access it again.

---

### Post by jfls45 on 2010-05-03
Thank you for taking the time to answer my questions like you have. I really appreciate it. 

I was going through some of the bash and other commands for setting up the server. I 

came to the conclusion that for my needs, a simple home network (hobby really) I might be better off loading a gui for ease and comfort. Is there a way I can load a gui but then uninstall or turn it off if I so choose later?

I am still unsure how to setup the drives, go all ext4 and leave one master backup of all drives as NTFS, that way I have both. What are your thoughts on this again? 

Jeff









> **srs5694 said:**
> No, your hunch is wrong. You can log in remotely using SSH, provided you install and enable the SSH server (via the openssh-server package). There are other text-mode and GUI login protocols for Linux, but SSH is the preferred text-mode tool for most installations because it supports good encryption techniques.
 


Whenever possible, use an OS's native filesystem(s). If a server system will be running Linux, use ext2fs, ext3fs, ext4fs, ReiserFS, JFS, or XFS. (For the brave, Btrfs is also an option, but it's still very new.) The fact that the Linux system will have Windows (or OS X or FreeBSD or Commodore 64 or whatever) clients is irrelevant, since most network servers (Samba, Apache, etc.) work on files, not on filesystems. That is, the network servers are unlikely to care what filesystem is in use, and the clients won't have a clue about that detail.



Yes. That's how many big Linux servers run. To do so, you'll want to shut down the GDM server by disabling its SysV init script. Try Googling "Ubuntu SysV scripts" or "Ubuntu init scripts" to find a tutorial on how to do this (I don't have a reference handy).



If your server's clients will all be within your LAN, then your single best security measure is to set up a firewall for the entire LAN. Since you mentioned this was a home LAN, I recommend you look into a broadband router, if you don't already have one. Be sure it's properly secured -- it shouldn't forward ports unnecessarily and if it's got wireless capabilities, you should be sure it's set up with WPA2 security (not WPA and *definitely* not WEP), and preferably restrict it to respond only to your own Wi-Fi systems via their hardware addresses.

If you want remote access, as in access from outside your LAN, you'll need to forward the SSH port -- or better yet a non-standard port from the outside to the standard SSH port on your server. You configure this in your broadband router, so it's not really a Linux issue per se. This is a security risk, though, and if you do this you should ensure you use a strong password. There are other security measures you can take, but I can't really go into all the details -- whole books have been written on this topic!



A file is just a pattern of bytes, and the filesystem just determines where those bytes get stored on the disk. Thus, assuming no bugs or hardware failures, a file won't get damaged just because you copy it from one filesystem to another. That said, different filesystems have different performance characteristics, and some filesystems are more reliable than others. Recent NTFS drivers for Linux are said to be fairly reliable, but for a Linux-only system, Linux-native filesystems are likely to be more reliable and faster than NTFS. Furthermore, NTFS on Linux has the major drawback that Linux will become unable to read it after a power failure or system crash. After such an event, the filesystem must be checked by Windows before Linux will be able to access it again.

---

### Post by srs5694 on 2010-05-03
> **jfls45 said:**
> I came to the conclusion that for my needs, a simple home network (hobby really) I might be better off loading a gui for ease and comfort. Is there a way I can load a gui but then uninstall or turn it off if I so choose later?

Yes. In fact, it's hard to install Ubuntu without the GUI. You can install it, configure it, and then either leave it running (it'll consume some RAM but otherwise do no harm) or disable it by shutting down GDM. You can then re-enable it by starting up GDM. You can use text-mode remote access with or without the GUI running locally. You can even use GUI remote access without the GUI running locally.

> I am still unsure how to setup the drives, go all ext4 and leave one master backup of all drives as NTFS, that way I have both. What are your thoughts on this again?

The only common reason to use NTFS in Linux is if the disk in question will eventually be used by Windows. If it's a removable disk or if you dual-boot to Windows, using NTFS may make sense. Even then, FAT and ext2/ext3 are viable alternatives, and are preferable in some cases. (There is a Linux FAT filesystem check utility, dosfsck, for instance, although FAT can't handle files larger than 4GiB; and of course ext2/ext3 are native Linux filesystems, so if you mainly use the disk in Linux and just occasionally need access from Windows, installing a Windows ext2/ext3 driver may make more sense than using NTFS.) If the disk will be used from Linux alone, there is ***no advantage*** to using NTFS. (OK, OK, somebody will post about some improbable scenario in which using NTFS from Linux makes sense, but I guarantee that will be for some highly specialized purpose.)

---

### Post by jfls45 on 2010-05-03
Point me in the right direction regarding remote access without the gui running locally.  Do I need to have the gui installed although it's not running to remote access?

Another question, do I need to have Samba for my hobby network I'm doing. Is there program that comes with the basic files that will work fine for what I need?

Sorry I have so many questions.

Jeff

---

