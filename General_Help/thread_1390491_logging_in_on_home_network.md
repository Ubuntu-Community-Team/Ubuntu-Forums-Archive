---
title: "logging in on home network"
date: 2010-01-25
forum: General Help
---

### Post by killiekosmos on 2010-01-25
I've got 3 machines on my home network.  

PC1 is Win 7 wired to router
PC2 is ubuntu 9.10 wired to router
PC3 is XP connected wirelessly to network.

I managed to edit smb.conf to change the name of my network from default NETWORK to its real name.  Each machine can see the others on the network.

The ubuntu box (PC2) can browse PC3 (XP) and copy files etc
Problems are:


[LIST=1]
[*]Trying to connect from ubuntu (PC2) to Win 7 (PC1) I get asked for password but none are accepted
[*]trying to connect from PC3 or PC1 to ubuntu (PC2) I get asked for a password but none work.
[/LIST]
I'm really stumped by this.  the Ubuntu box can access the XP box but not the other way round and no other access works from any other box.

The XP box has no passwords.

Ubuntu box is dual boot.  If I boot it into XP then everything seems OK (can access all devices and network print from all devices).  This leads me to suspect i need to chasnge something in ubuntu.

Please, has anyone any suggestions to remedy this?  In basic steps please as I'm a newcomer to ubuntu.

Thanks

---

### Post by cariboo on 2010-01-25
To connect to the Windows 7 computer, you need to enter the username and password for the Win 7 computer.

Windows systems, only know how to connect to other Windows systems. You need to install and setup samba in order to fool the Windows computers into thinking they are connecting to an other Windows system.

Have a look [here]("https://help.ubuntu.com/community/SettingUpSamba"),for a Samba setup guide.

---

### Post by n0dix on 2010-01-25
Note that window$ S.O doesn't communicate with any linux distro (resembles the case of any window$ system can't read/write any partitions of linux). You will need a software or something in window$ to communicate.

---

### Post by audiomick on 2010-01-25
There is a lot of info here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by killiekosmos on 2010-01-26
Thanks for the comments.  I had samba installed (and change the name of my workgroup so each machine can 'see' the others.  As Ubuntu can see and browse my XP machine I assume that the appropriate software is in place.  The difficulites are:

(1) any win machine being asked to log on to ubuntu machine - but none of the username/psswords are accepted.
(2) same thing happens from Ubuntu to Win 7.

It seems to me that I need to change some settings in ubuntu and/or Win 7 to get everthing communication.

Any further suggestions?

Thanks

---

### Post by killiekosmos on 2010-01-27
bump, still totally stuck

Can access XP box from ubuntu no problem and XP box from Win 7 no problem but any other way asks for username and password but none work.

Any help out there?

Thanks

---

### Post by polki@mac.com on 2010-01-28
Maybe you need to set a smbpasswd for the user, then you should be able to use the shares on the Ubuntu puter from the XP machine at least. I think it's:

sudo smbpasswd -a theusernametoadd

For more info just type "man smbpasswd" in the terminal.

---

### Post by Ugluk on 2010-01-28
Check this thread: [http://ubuntuforums.org/showthread.php?p=6120780](http://ubuntuforums.org/showthread.php?p=6120780)

---

### Post by 3rdalbum on 2010-01-28
In Windows, you may need to specify the computer name and share name rather than just try and "browse" for the share. Even if you can see it in front of you.

I'm not sure exactly how it's done on Windows, but in Ubuntu you'd tell the file manager to go to:

smb://computername/sharename

---

### Post by killiekosmos on 2010-01-28
Thanks for the suggestions.

I edited the registry on the XP machine and change the lma setting to "1".  

When trying to access the Win 7 machine I got asked for a password - entered my username and password on the Win7 box and got in!

The ubuntu box is dual boot so I started it in XP and edited its registry too.  I also managed to access the Win7 box.

So far so good.

Then tried to access the ubuntu box (booted into XP) from either XP or Win 7 and got asked for a password (but there are no user accounts on this box?)  Rebooted it into ubuntu and tried again, still wants user accounts.

I'm really, really stumped!

Any more suggestions, please?

---

### Post by Morbius1 on 2010-01-28
Have you created any shares on the ubuntu box?

Post the output of the following commands from the Ubuntu box please:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

---

### Post by killiekosmos on 2010-01-29
Thanks, that's tonights's tasks
 
Cheers

---

### Post by killiekosmos on 2010-01-29
[B]Here is what I get by running those comments - does this help?


net usershare info[/B]


**sudo net usershare info**
[sudo] password for colin: 
[desktop]
path=/root/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=y

** testparm -s**
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = AVALON
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by doas777 on 2010-01-29
> **killiekosmos said:**
> 
Then tried to access the ubuntu box (booted into XP) from either XP or Win 7 and got asked for a password (but there are no user accounts on this box?)  Rebooted it into ubuntu and tried again, still wants user accounts.

I'm really, really stumped!

Any more suggestions, please?


you have to provide a usename and password that exists on the ubuntu box, and you will likely have to have run smbpasswd for that user. there has to be an account on your ubuntu box, as the setup will not allow you to continue until you make one.

also if you are allowing guests via "usershare allow guests = Yes", you probably need to comment out "map to guest = Bad User", or map it to a real account.

---

### Post by Morbius1 on 2010-01-29
Here's my take on all this:

(1) You're allowing guest access on your only share so you don't need to set up any smbpasswd on the server.

(2) You need to keep "map to guest = Bad User" intact.  When any client identifies itself to the server it will be be viewed by the server as a "Bad User" and the ubuntu default "map to guest = Bad User" will convert all clients to "guests". 

(3) The reason you're constantly being asked for a password is not a samba issue it's a linux file permissions issue:
> [desktop]
path=/root/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=yYou're sharing /root/Desktop ( BTW, no disrespect, but have you lost your mind ;)). /root/desktop has permissions of 755 and it's parent /root has permissions of 700. You will never get in as a guest.

This is what I would do. I would create a new directory and share that one. For example:

Open **Terminal**
Type **sudo mkdir /GuestShare**
Type **sudo chmod 777 /GuestShare**

Go back in Nautilus and "unshare" /root/Desktop, then share /GuestShare.

---

### Post by killiekosmos on 2010-02-08
I found the solution on another thread - delete Windows Live ID login assistant!!!

---

