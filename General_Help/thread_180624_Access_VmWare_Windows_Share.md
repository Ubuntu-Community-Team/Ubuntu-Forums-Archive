---
title: "Access VmWare Windows Share"
date: 2006-05-22
forum: General Help
---

### Post by seth0x2b on 2006-05-22
Hey guys.
I just setup VmWare , installed WindowsXp and is works great.
I need to setup a network connection between Ubuntu and windows.I have one shared folder(R/W) on the guest Windows machine and I need to access it from Ubuntu.
I have searched the forum but I could only find how-to's on how to setup a shared folder on Linux and access it from Windows. I want to  do it the other way around.
Any info in appreciated.Thanks

Cheers

---

### Post by Kethinov on 2006-05-22
**sudo apt-get install smbfs** then in your **/etc/fstab** write a line like this:```
\\vmware_computer_netbios_name\share_name /media/vmwindows smbfs user,uid=your_ubuntu_username,username=your_windows_username,password=your_windows_password 0 0
```Then **sudo mkdir /media/vmwindows** and **cd /media** then **sudo mount vmwindows**

You will then have access to your Windows share.

You could alternatively setup a Samba share on your Ubuntu box and mount that from Windows, which I think is easier and is what I do, but is potentially less secure if you don't want people to access your Ubuntu box using Windows Networking.

---

### Post by ousooner919 on 2006-05-23
I use VMWare Workstation 5.5, and there's a "Shared Folders" option under your advanced config options for the VM itself. Once you set it up, it will automatically share whatever folders you specify under a "\\.host\<share-name-you-configured>". No need to set up Samba yourself (unless you just want to, of course).  :-)

---

### Post by ousooner919 on 2006-05-23
Or, you could be an idiot like me and post directions you probably already have found...I misread your initial request. My sincere apologies. The samba option is better for what you need.

---

### Post by seth0x2b on 2006-05-23
ousooner919: You're not an idiot :) .That is actually the method I opted for since it's soooo easy to setup.I created a folder in my Ubuntu home directory called "share" and I access it via "\\.host\Shared Folder\share" from Windows.I did a map network drive so it's all fine and dandy.

Kethinov: Creating samba shares was my first option, but I don't want to have any (samba) open ports on Ubuntu...

2 new questions now:
a) Are the any chances that files that I save from windows in the shared folder to get corrupted or something like that?!
b) My IP is set via DHCP, and the internet connection works excellent on linux, But how do I exactly setup the virtual Windows machine to access my linux box if I were to..let's say...install apache with my website on Ubuntu and I would want to access it from windows?!

Thanks alot!
Cheers

---

