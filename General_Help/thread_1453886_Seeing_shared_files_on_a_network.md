---
title: "Seeing shared files on a network"
date: 2010-04-13
forum: General Help
---

### Post by Falc7 on 2010-04-13
Hi
I am having trouble seeing files on the network in shared folders.
I have samba installed. I run win7 though a virtual machine and it sees the files file, but when i run dolphin, network, then network again, i only see my computer there, no others.

---

### Post by Tman5293 on 2010-04-13
You must first set up samba to add it self to your windows network.

---

### Post by Falc7 on 2010-04-14
How do i do that? I don't see anything in preferences

---

### Post by Untitled_No4 on 2010-04-14
Here's how I access files on the Windows machines in our network.
1. Install smbfs (if you don't already have it):
in Konsole
```
sudo aptitude install smbfs
```
Alternatively, you can probably find it in KPackageKit and install it from there.
2. Open Dolphin and click F6 to make the path navigation editable and enter the computer you want to browse in the following format:
smb://ip.of.remote.computer/path or smb://computername/path
for instance, if I have a computer called myserver with IP address 192.168.1.1 and I want to view a folder with a share name of SharedDocs I will have to use one of the following:
smb://192.168.1.1/SharedDocs or
smb://myserver/SharedDocs

Once you put in the path and press enter you will be prompted to enter a username and password with permissions to view folders on the remote computer. This is usually the Windows domain username/password. 

You can also go to smb://computername and see which folders are shared, of course.

Here is some more extensive information about using Samba:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Falc7 on 2010-04-16
ah yes, thanks

---

### Post by Falc7 on 2010-04-18
The network i am trying to access is a work network, and now, as long as i set it to smb, it can see the shared files. But when i try and open an individual file it prompts me for a username and password, even though there isen't one. I can open the individual files just fine in windows.

---

### Post by Roasted on 2010-04-19
Are you on a domain at work? If you are on a domain at work, you log in with your username/password. Those login credentials automatically authenticate you for network share access for whatever folders you have access to, hence why you don't put the information in to view them.

However, when you're on Ubuntu, you're not on the main Windows domain at work (again, assuming you have a domain). Ultimately the username/password you're seeing could be your regular login credentials to the Windows box at work. Give it a shot. I have to do that at my place of work.

Again - this is just me assuming your work is on a domain. Some smaller places tend to stick to workgroups and local user sign-ins.

---

### Post by Falc7 on 2010-04-19
I don't think i am on a domain. There isen't anyone i can ask either, as i am probably the most technical person in this (small) office. I just stick the LAN cable in, get internet access, and can see the files on the main desktop. I don't have to put a password/username in at any time normally as i am just using my own laptop.

---

### Post by Roasted on 2010-04-19
Perhaps you need the local credentials of the computer you're trying to view the files off of.

Example:

XP box - Administrator - Password

Ubuntu box - Remotes to XP box to view files - gets username/pw box. Try the login credentials to that box, such as my above example "Administrator" + "Password".

Perhaps that's it?

---

