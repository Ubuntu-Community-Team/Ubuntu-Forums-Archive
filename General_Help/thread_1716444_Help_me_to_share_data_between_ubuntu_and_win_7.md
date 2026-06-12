---
title: "Help me to share data between ubuntu and win 7"
date: 2011-03-28
forum: General Help
---

### Post by anhnt on 2011-03-28
I want to share data from ubuntu to windows 7 but I don't know how to do this.Can you help me?
Ubuntu 10.10 amd64 and win 7 ultimate 64 bit.
Thanks!

---

### Post by Joe of loath on 2011-03-28
What, over the network? Right click a folder and select 'share'.

---

### Post by wormyblackburny on 2011-03-28
What do you mean "share" data? If you did the dual boot install right, then your windows partition drive should appear on your desktop. In order to truly "share" files, i find it is best to create an ntfs partition and mount it permanently in /etc/fstab that way you can access the files in windows without having to download software to allow Windows to mount ext3 partitions.

---

### Post by anhnt on 2011-03-29
I mean share from ubuntu to windows.Please tell me more about this,tks!

---

### Post by Joe of loath on 2011-03-29
You still haven't clarified; do you want to do it between two computers on a network? Or between two operating systems on the same computer?

---

### Post by anhnt on 2011-03-30
I want to share on a network,i shared folder on ubuntu but can not access from windows,although i disable firewall

---

### Post by Morbius1 on 2011-03-30
> i shared folder on ubuntu but can not access from windows
Please post the output of the following commands please:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by fjgaude on 2011-03-30
Is Windows 7 a guest, virtual? Through VirtualBox or VMware?

---

### Post by CharlesA on 2011-03-30
Doesn't sound like you are virtualizing. Moved to general help.

---

### Post by anhnt on 2011-03-31
```
anhnt@anhnt-K42F:~$ net usershare info --long
[microsoft]
path=/media/Empty/Ebook/Vietnamese/Network/Microsoft
comment=
usershare_acl=Everyone:F,
guest_ok=y

[software]
path=/media/Empty/Software
comment=
usershare_acl=Everyone:F,
guest_ok=y

anhnt@anhnt-K42F:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```



Yes,I practice on virtualbox.I want to development this model with my company,but I have studing linux 2 weeks ago.

---

### Post by CharlesA on 2011-03-31
If you are testing in virtualbox, make sure you are using Bridged networking instead of NAT.

---

### Post by Morbius1 on 2011-03-31
There's actually nothing wrong with any of that so the first thing I would check is the permissions of the entire path to the shared folder. Let's take the [software] share. Check the permissions along every directory:
```
ls -dl /media
```It should come back at a minimum with:
> drwxr-xr-x```
ls -dl /media/Empty
```This should come back with:
> drwxr-xr-x```
ls -dl /home/Empty/Software
```should come back with:
> drwxrwxrwxThe other unanswered question is the one [COLOR=Blue]fjgaude [COLOR=Black]asked. Is Ubuntu the VBox host or guest. If it's the host then this should work. If it's the guest then make sure you are using Bridged mode in VBox not NAT.[/COLOR]
[/COLOR]

---

### Post by anhnt on 2011-03-31
I check my folder and change the permission on this folder:
 root@anhnt-K42F:/# chmod 644 /media/Empty/Software/
 root@anhnt-K42F:/# ls -dl /media/Empty/Software/
 drwx------ 1 anhnt anhnt 4096 2011-03-13 20:35 /media/Empty/Software/


But still can not access.I 've installed windows 7 on virtualbox and used bridged

---

### Post by Morbius1 on 2011-03-31
Edit /etc/samba/smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to [global] section:
```
force user = anhnt
```Save the file and back in the terminal type:
```
sudo service smbd restart
```Right now:
> ls -dl /media/Empty/Software/
 drwx------ 1 anhnt anhnt 4096 2011-03-13 20:35 /media/Empty/Software/anhnt is the only person who can access the folder. "force user" will convert the "guest" to "anhnt" so that he will have the same access to the share as you do.

---

### Post by anhnt on 2011-04-02
yes i do it successful,now i understand about this and very thanks to you!

---

