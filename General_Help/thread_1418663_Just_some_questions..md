---
title: "Just some questions."
date: 2010-02-28
forum: General Help
---

### Post by aklo on 2010-02-28
I have xubuntu on my netbook and i want to share folders between them.

For people who use xubuntu , right clicking on a folder does not give you the "Sharing Options" Options. So i used "Share Folder" under system utilties.

Ok anyway in the dialog box, i entered my network / ip name it does not work. It only works when i specify the folder name(Videos) that is to be shared. Why?

My internal network ip address is 192.168.1.66 but when i input this, it don't work.
Same goes for entering my network address + subnet mask which is 
Network address : 192.168.1.0 
Subnet mask : 255.255.255.0

This is not really important as the shared folder is work but i'm just curious.

---

### Post by bobcollard on 2010-03-01
> **aklo said:**
> I have xubuntu on my netbook and i want to share folders between them.

For people who use xubuntu , right clicking on a folder does not give you the "Sharing Options" Options. So i used "Share Folder" under system utilties.

Ok anyway in the dialog box, i entered my network / ip name it does not work. It only works when i specify the folder name(Videos) that is to be shared. Why?

My internal network ip address is 192.168.1.66 but when i input this, it don't work.
Same goes for entering my network address + subnet mask which is 
Network address : 192.168.1.0 
Subnet mask : 255.255.255.0

This is not really important as the shared folder is work but i'm just curious.
Try Samba.

---

### Post by derrick81787 on 2010-03-01
I'm guessing that the GUI for Xubuntu probably uses Samba in the background to share files.  I don't know a lot about it though.  If Windows computers are involved in the file sharing, you should probably use Samba.  If not, I like NFS better.  It seems more natural to mount the folder on Linux than the browse network shares, and I think it's faster.  Both are pretty easy to set up because there are excellent guides out on the Ubuntu Wiki.

I don't really know the answer to your question, but if you want to learn more about file sharing on Ubuntu/Xubuntu in general, check out these links:

[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[Samba]("https://help.ubuntu.com/community/SettingUpSamba")

The guides are written for Ubuntu, so the graphical configuration steps probably won't work for you.  The command line versions will, though.

- Derrick

---

