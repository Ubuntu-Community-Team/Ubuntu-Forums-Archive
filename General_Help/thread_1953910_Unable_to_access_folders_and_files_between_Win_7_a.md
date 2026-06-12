---
title: "Unable to access folders and files between Win 7 and Ubuntu"
date: 2012-04-07
forum: General Help
---

### Post by mona1972 on 2012-04-07
Hello,
 
I have Ubuntu 10 and Windows 7 Home Premium. I want to access my files and folders between the 2 OS i have. I tried the following steps:
 
1. In Win 7 I typed the following net config workstation and got the Workgroup name: WorkgroupHP
2. In Ubuntu i typed in Terminal:
sudo apt-get install system-config-samba
3. I entered WorkgroupHP in Server settings in Preferences of Samba
4. In Win 7 I enabled file sharing in Manage Advanced Sharing Settings for Home and Work 
5. I have a password protected Admin user in Win 7
6. I have shared 2 folders minimum in Win 7 with Everyone
7. In Ubuntu I ran the following command in Terminal:
sudo smbpasswd -a username  
where username is hp in both Ubuntu and Win 7 and when prompted for password I gave first the password for Ubuntu account, then I created another user in samba database with avahi as username in Unix and entered password for Win 7 account. So now I have 2 users in samba, one for my Win 7 OS and another for Ubuntu OS
8. I then clicked Add in samba and created shares in Ubuntu for Windows
 
My problem is this:
 
In Ubuntu I see WorkgroupHP in Network but it has Ubuntu shares only so i am not able to see folders that I shared in Win 7
 
In Win 7 if i type [\\ubuntu]("file://\\ubuntu") i get the error as in screenshot. 
 
Can somebody help me share my files and folders in between Ubuntu and Win 7?
 
Thanks.

---

### Post by dino99 on 2012-04-07
if both OS are on the same PC, then ubuntu can read/write on the shared partition(s) via ntfsprogs & ntfs-3g & montmanager (check they are installed via synaptic)

otherwise you need to set your network:

[https://help.ubuntu.com/11.04/ubuntu-help/nautilus-connect.html](https://help.ubuntu.com/11.04/ubuntu-help/nautilus-connect.html)
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Morbius1 on 2012-04-07
> **dino99 said:**
> if both OS are on the same PC, then ubuntu can read/write on the shared partition(s) via ntfsprogs & ntfs-3g & montmanager (check they are installed via synaptic)
ntfsprogs actually removes ntfs-3g and you will be left with a read only ntfs partition. I personally wouldn't use mountmanager on a drunken bet but that decision is up to you.

@mona1972, although you gave a very detailed post I'm still confused in certain parts - which is pretty normal for me - so if you could post the output of each of the following commands from the Ubuntu machine it might clarify things:
```
testparm -s
net usershare info --long
hostname
smbtree
```If smbtree only shows the Ubuntu machine then run smbtree this way:
```
smbtree -U username
```[COLOR=Blue]Where "username" is the Win7 user name[/COLOR]

---

### Post by mona1972 on 2012-04-21
Hi, As mentioned in second post, can you please suggest how to use ntfs progs, ntfs3g and mount manager. I would like to use the safest and easiest method to enable file and folder sharing between Ubuntu and Win 7 on same PC which I can get to know if someone kindly give me detailed steps for same. Thanks. waiting eagerly for an answer.
 
This query is for dino99 please):

---

### Post by mona1972 on 2012-05-13
Please find the output of the commands as desired. 2 things I found mentionable:
1. Both my Ubuntu and Win 7 username is hp although passwords are different. So even when I ran smbtree -U username (for Win 7 ) it listed only Ubuntu although another laptop (GSVIRK PC which is on network too) got displayed but not the Win 7 laptop partition. I have Ubuntu installed with Wubi on my Win 7 laptop itself.
2. Also I am able to access Win 7 on Ubuntu with nautilus command on Terminal but still  not able to access Ubuntu on Win 7.

Please find enlisted the results and hoping to get an early response. Thanks.

testparm -s
----------------

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Downloads]"
Processing section "[monaunix]"
Processing section "[example]"
Processing section "[chktest]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = WORKGROUPHP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    valid users = avahi, hp, nobody
    read only = No

[Downloads]
    path = /home/hp/Downloads
    valid users = hp

[monaunix]
    path = /home/hp/monaunix
    valid users = hp

[example]
    path = /home/hp/Desktop/example
    valid users = hp

[chktest]
    path = /home/hp/Desktop
    valid users = hp


net usershare info --long
----------------------------

[downloads]
path=/home/hp/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=n

[monaunix]
path=/home/hp/Documents/monaunix
comment=
usershare_acl=Everyone:F,
guest_ok=n

[example]
path=/home/hp/Documents/example
comment=
usershare_acl=Everyone:F,
guest_ok=n

[hw]
path=/home/hp/Desktop/hw
comment=
usershare_acl=Everyone:R,
guest_ok=n

hostname
--------

ubuntu

smbtree -U username
---------------------

Enter hp's password: 
WORKGROUPHP
    \\UBUNTU                 ubuntu server (Samba, Ubuntu)
        \\UBUNTU\hw                 
        \\UBUNTU\IPC$               IPC Service (ubuntu server (Samba, Ubuntu))
        \\UBUNTU\chktest            
        \\UBUNTU\example            
        \\UBUNTU\monaunix           
        \\UBUNTU\Downloads          
        \\UBUNTU\print$             Printer Drivers
WORKGROUP
    \\GSVIRK-PC

---

### Post by Morbius1 on 2012-05-13
OK, I may just have finally figured out what's going on here: 

> I would like to use the safest and easiest method to enable file and  folder sharing between Ubuntu and Win 7 on same PC which I can get to  know if someone kindly give me detailed steps for same.> I have Ubuntu installed with Wubi on my Win 7 laptop itself.> 2. Also I am able to access Win 7 on Ubuntu with nautilus command on Terminal but still  not able to access Ubuntu on Win 7.Not an expert on Wubi but I believe your Windows partition is located at /host. Linux can read a Windows filesystem but Windows cannot read a Linux filesystem nativity. I've read that you can install "drivers" in windows that can read an Linux filesystem but I would not recommend that and have no experience with it. But since Windows and Linux ( via /host ) can both access the same partition I'm not sure why you need it.

---

### Post by mona1972 on 2012-05-13
Thanks I got Windows folders through nautilus /host in Ubuntu and can copy-paste whatever info or files to windows. Thanks again

---

### Post by Mark Phelps on 2012-05-13
Just so you know ... it's  BAD idea to be updating the Win7 OS partition files and folders from inside Ubuntu.  This risks filesystem damage, and if that happens, Win7 is likely to THEN be unbootable.

If you really want to SHARE files and folders between the OSs, such that you want to be able to both read and write files, a much safer approach is to have a shared NTFS DATA partition.  That way, there's no worrying about boot-related problems.

---

