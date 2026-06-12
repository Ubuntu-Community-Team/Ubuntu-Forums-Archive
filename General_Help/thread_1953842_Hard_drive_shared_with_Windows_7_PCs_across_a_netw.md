---
title: "Hard drive shared with Windows 7 PCs across a network?"
date: 2012-04-07
forum: General Help
---

### Post by kaitco on 2012-04-07
I have a desktop and two laptops. The desktop is connected to a router through a wired connection and my four external hard drives are all connected to it. The two laptops and the desktop were all connected on the same home network and the laptops could view and run files on the hard drives connected to the desktop. 

I installed Ubuntu via Wubi on the desktop two days ago, but the laptops are both still running Windows 7 and neither laptop can see the hard drives connected to the desktop that now runs Ubuntu.

I am sure there is a way connect all three PCs on the same network so that they can share the same drives, but I've not yet found this information, so any assistance (even links to other threads or wikis) with this would be appreciated.

This is my second attempt at trying Ubuntu, but I am very much the novice in this regard. The other PCs in the house are very dependent on this network for the drive sharing and switching back and forth between Windows and Ubuntu is not a viable option.

Many thanks!

---

### Post by lmarmisa on 2012-04-07
Have you defined some shared folder (using Samba) on your desktop?.

Have you defined your own workgroup in Windows for sharing files?.

Have you tested the communications among the three computers using ping?.

---

### Post by kaitco on 2012-04-07
> **lmarmisa said:**
> Have you defined some shared folder (using Samba) on your desktop?.

Have you defined your own workgroup in Windows for sharing files?.

Have you tested the communications among the three computers using ping?.

No for the first and the third. I had a workgroup created on Windows and was able to share files within the workgroup with no issue between all three computers. Do I need to create a new workgroup on Ubuntu? Should I create a new workgroup on one of the laptops?

I'm not familiar with either Samba or Ping. Is there any documentation that describes what I'm trying to accomplish? Normally, I can find all the information I need by just searching for it, but I'm not even sure what to ask or for what I should be searching.

---

### Post by lmarmisa on 2012-04-07
> **kaitco said:**
> No for the first and the third. I had a workgroup created on Windows and was able to share files within the workgroup with no issue between all three computers. Do I need to create a new workgroup on Ubuntu? Should I create a new workgroup on one of the laptops?

I'm not familiar with either Samba or Ping. Is there any documentation that describes what I'm trying to accomplish? Normally, I can find all the information I need by just searching for it, but I'm not even sure what to ask or for what I should be searching.

Create a new folder named test on your Desktop. Select it and right button Sharing Options.

The system will propose to install some Samba packages. Continue with the installation and restart your session.

When the packages are installed and a new session is started, select the folder again and Sharing Options. Tick Share this folder and optionally Allow others to create and delete files on this folder. That is all for sharing a folder.

The standard workgroup in Samba is WORKGROUP. If you need to change it, open a terminal and edit the file smb.conf typing this command:

```

gksudo gedit /etc/samba/smb.conf

```Search Global settings and workgroup and define your new WORKGROUP identifier.

Save & Exit.

Finally, type this command:

```

sudo service smbd restart

```

Try to check if you are able to access the shared folder test from your Win7 machines.

---

### Post by kaitco on 2012-04-07
Okay, I followed each step to install Samba and the other options and I've renamed my homegroup to same one as the Windows laptops, but I'm still unable to see the Ubuntu desktop in the homegroup on either laptop. 

I remember when I set up my network on Windows there was a security key required to add PCs to the homegroup. Would something like that be necessary here?

Many thanks for your help!

---

