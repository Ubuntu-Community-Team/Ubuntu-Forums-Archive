---
title: "Samba"
date: 2011-01-28
forum: General Help
---

### Post by Hippytaff on 2011-01-28
I know I could just try it or google and find out but I have limited time (wife, kids, work bins to take out etc etc) so I know I can rely on the good people here to just say yes or no. (and give extra advice ;-) )

Can windows read files from a home file server with an ext4 file system?

or do I have to partition the drive with the server (ext4) and an ntfs partition with the files on?

I guess yeas and no are out of the question now because I or'd :?

---

### Post by QLee on 2011-01-28
When files are transferred over the network a network protocol is used, it doesn't matter what filesystem type the file resides on.

---

### Post by wormyblackburny on 2011-01-28
Just so I understand here: You are setting up a Ubuntu server in your house and want it to serve files to your Windoze computers correct? And you are worried that since the files are stored on ext4 makes them incompatible.... The answer is: Yes and No. 

Yes, Windows by defailt can't read ext filesystems. However, there are programs that will let Windoze mount ext filesystems. This is especially useful when you have a dual boot machine (although, I prefer to use Ubuntu to go in and move files between the Windows/Ubuntu partitions).

As for what you are wanting to do, yes you are correct that you will need to install/configure Samba if you want to share files with your Windows computers. Here is a pretty good tutorial for using the GUI tools in 10.10: [URL="http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-"]http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-
[/URL]

---

### Post by Hippytaff on 2011-01-28
cheers both, the wife insists on windows so it has to be accessible for her machine...thank god shes not a mac monkey

---

### Post by QLee on 2011-01-29
[QUOTE=Hippytaff]cheers both, the wife insists on windows so it has to be accessible for her machine...thank god shes not a mac monkey[/QUOTE]

Over the network, just like the filesystem on which the file resides, the operating system used doesn't matter. If the file is shared over the network, it is shared, assuming the client system has an application that can read and operate on the file.

---

