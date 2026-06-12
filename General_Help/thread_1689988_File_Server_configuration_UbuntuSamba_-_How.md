---
title: "File Server configuration Ubuntu/Samba - How??"
date: 2011-02-17
forum: General Help
---

### Post by SSA-Ed on 2011-02-17
I am an Ubuntu rookie, but very experienced in windows. I am re-using an older PC and want to make it a file server (my Win2k died). I loaded Ubuntu & Samba and started searching for help as I can't quite seem to get it done. Today I found this link:
                 [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

which seemed helpful until I tried to edit the samba config file (smb.conf) - it's read only. So I looked up how to change the files attributes, but as it is owned by the root, no joy yet again.

Perhaps over the last week of flailing, its time to re-load and start over. But if I had a little help maybe it won't be so frustrating. I'll load Ubuntu on a small sata-2 SSD and once loaded, I'll add a sata-2 @TB drive which will be shared.

Q1: I have the latest 10.04, is there anything I should change in the defaults that are loaded?
Q2: How should I format the share drive? (NTFS on a win PC, DOS?)
Q3: Does anyone have a list of the s/w I should 'get' (Get Software, Provided by Ubuntu) to be able to help me make Samba a Win file server?

Thanks, Ed

---

### Post by mr_luksom on 2011-02-18
Do you need samba? I found it more trouble than its worth.

Personally, I find NFS much easier:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

And if you need Windows access, you can install Unix Tools for Windows:

[http://www.astroarch.com/wiki/index.php/Setting_up_Windows_Services_For_UNIX_(SFU)_NFS](http://www.astroarch.com/wiki/index.php/Setting_up_Windows_Services_For_UNIX_(SFU)_NFS)

---

### Post by WannabeFantasma on 2011-02-18
Do you have a 10.04 server? (with no gui?)

I made a samba server myself recently (still on 9.04 but can't be that different) I can connect to it from any pc in my LAN.

I change the smb.conf file by typing 
"sudo vim /etc/samba/smb.conf" in the command line, pressing insert makes you type text inside it. (Sudo makes you open it as "Root")

when you changed everything needed; you press escape and type :wq!

you can use nano instead of vim too.


2: The drive can just be formatted as EXT3/4 I can acces my file server on a Vista machine.

---

### Post by mastablasta on 2011-02-18
> **SSA-Ed said:**
>  
which seemed helpful until I tried to edit the samba config file (smb.conf) - it's read only. So I looked up how to change the files attributes, but as it is owned by the root, no joy yet again.

 
to get temporary root privilages you need to use sudo command in the terminal.
 
if you are using desktop you can try
 
gksudo gedit [yourfilename]
 
editor will open the file with root privileges.

---

