---
title: "Ubuntu living with windows"
date: 2011-08-27
forum: General Help
---

### Post by nothingspecial on 2011-08-27
These are questions about ubuntu coexisting with windows. I'm not asking for windows support.

I have installed windows on one computer. It will dual boot with ubuntu but half of the time it will run windows.

The computer in question happens to be the one the printer is connected to. If I share the printer from windows will the other computers in the network (all running various *buntus) pick it up? Or am I better off moving the printer to my 10.04 server and configuring cups (obviously if I do that the windows 7 computer has to be able to use it)?

The computer has a large data partition formatted ext4. I believe that there is software for windows that can read ext4. Am I better off formatting the partition ntfs or leaving it as it is. The partition contains data with various permissions for various users. I know that this will go out of the window if it becomes ntfs. Or if I leave it ext4, how will writing to it from windows effect the permissions? What is my best strategy here? I have plenty of space on spare dives to have two copies of the data, which would be an extra backup.

Thankyou.

---

### Post by nothingspecial on 2011-08-27
> **jackjwalt said:**
> virtual machine allows you to work in parallel desktop i e in ubuntu as well as in windows

I know, but windows in a virtual machine wasn't doing the business performance wise which is why I have installed it to the hard drive. And I need the printer accessible to the network so even if I did claim it in a virtual linux while windows is running the question remains.

---

### Post by saltmarshlamb on 2011-08-27
You should be able to do it either way,

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)
> 
The computer has a large data partition formatted ext4. I believe that there is software for windows that can read ext4I'd not want to write to the linux partitions from windows - ext2ifs used to work with ext2/3 not sure about ext4, there's ext2read that'll read ext4. 

You might be better off if you can do so to backjup and change it to ntfs ... 

[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)
[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

---

### Post by Richard Wordingham on 2011-08-27
Simple file permissions can be shared when you use ntfs-3g to read and write the NTFS volume from Linux.  I used the ntfs-3g support program usermap.exe on Windows to help set up the translation table UserMapping (most simply located in the partition's top level directory) to convert between Linux and Windows users and groups.

I don't know how to get the ACLs to work.  The options in my /etc/fstab table for the NTFS partition read rw,nosuid,nodev,windows_names,permissions,inherit,acl, but from Ubuntu I don't see the Windows ACLs and they certainly don't work.  Possibly I need a better version of ntfs-3g than 1:2010.3.6-1ubuntu1.

---

### Post by SeijiSensei on 2011-08-27
CUPS enables the Ubuntu clients to print to a Windows printer.  You'll have the option of selecting the printer with an smb://server/printer URL.  Use the printer's IP address for "server" if you have name resolution issues.

Writing to ext4 from Windows is still not supported, but the ext2/3 Windows driver will support reads.  If you want full read/write support, you should reformat to ext3.

If you move the printer to a Ubuntu machine, you'll need to run Samba to make the printer visible to Windows clients.

---

### Post by nothingspecial on 2011-08-27
Thanks very much for the information.

So the printer will not be an issue, I'll just leave it where it is.

As for the data. I have it backed up on the server. I think I'll just use another drive to mirror it for windows. At the moment I'm thinking of using the backup on the server as a "sort of" cloud. I know how to use rsync to do that from the ubuntu installation. And I'm sure there is a way of getting windows and the linux server talking. The only issues will be permissions..........

........hang on 

.......... how does this sound? The windows machine uses the "backup" data on the server which is rsynced with the data on the Ubuntu installation? Is that do-able? You "share" directories from the server with accounts on the windows installation so that each user can only access/change the stuff they are supposed to. Then script something to apply the correct linux permissions to the new/changed stuff on the server before syncing it back with the Ubuntu installation......... if you see what I mean....... or am I talking nonsense?

---

