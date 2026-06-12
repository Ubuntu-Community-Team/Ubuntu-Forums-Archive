---
title: "Can't Get Windows 7 to Show Ubuntu Network"
date: 2012-02-28
forum: General Help
---

### Post by johnsmoke on 2012-02-28
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Recently I got a new laptop with Windows 7 (needed it to run playon). I have my desktop PC upstairs running Ubuntu 11.04 and I can access the Windows 7 files off the network no problem on it. Now what I'd really like to do is access the files from my Ubuntu desktop machine that's upstairs on the Windows 7 laptop that I have downstairs... 
I've tried enabling the folder that I want for sharing: rt-clk>sharing options> enable sharing etc.... but no matter what when I go down and look for the network on the Windows 7 laptop, it just isn't showing up. I don't quite understand why. I can access the Windows 7 network on my Ubuntu machine upstairs, but for some reason my Ubuntu network will not show on the Windows 7 machine. Is there anything that I can do to correct this? I even tried "Samba" to enable file sharing and connect to "Workgroup" on my Ubuntu and still the network does now show up on Windows 7. I have sharing enabled on both systems.
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by efflandt on 2012-02-28
By default **smbclient** is installed, but not the **samba** server.  Did you install samba?

The workgroup setting in /etc/samba/smb.conf applies to both client and samba server.

---

### Post by johnsmoke on 2012-02-29
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]At first I just tried to set the share options in the folder, but it said the service wasn't installed, then it installed it for me. Since that didn't work, I tried Samba, snagged it from Software Center and gave that a shot, but still no dice.
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Morbius1 on 2012-02-29
> At  first I just tried to set the share options in the folder, but it said  the service wasn't installed, then it installed it for meWhat it installed was samba.

Please post the output of each of the following commands:
```
hostname
testparm -s
net usershare info --long
smbtree
```

---

### Post by johnsmoke on 2012-02-29
> **Morbius1 said:**
> What it installed was samba.

Please post the output of each of the following commands:
```
hostname
testparm -s
net usershare info --long
smbtree
```


Thanks for the offer to help, I appreciate it. Here are the responses to the commands you requested: 

**hostname**

johnsmoke-desktop
[B]

testparm -s[/B]

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = WORKGROUP-NEW
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers



**net usershare info --long**

Looks like it just goes back to the original cmd line of this when I type the above command: johnsmoke@johnsmoke-desktop:~$


**smbtree**

WORKGROUP-NEW
    \\JOHNSMOKE-DESKTO        johnsmoke-desktop server (Samba, Ubuntu)
        \\JOHNSMOKE-DESKTO\IPC$               IPC Service (johnsmoke-desktop server (Samba, Ubuntu))
        \\JOHNSMOKE-DESKTO\print$             Printer Drivers
johnsmoke@johnsmoke-desktop:~$

---

### Post by Morbius1 on 2012-03-01
> **hostname**

johnsmoke-desktopYour desktop is invisible to the network becasue it's hostname is 2 characters too long for Samba.

The easiest way to fix this [COLOR=Blue]for samba purposes[/COLOR] is to use a samba config file to make it shorter:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - under the workgroup line:
```
netbios name = johnsmoke-desk
```[COLOR=Blue]*It doesn't have to be that exact name but it has to be 15 characters or less in length.*[/COLOR]

Save smb.conf and then back in the terminal restart the samba services:
```
sudo service smbd restart
``````
sudo service nmbd restart
```[COLOR=Blue]*Note: Every time you restart samba the network has a fit so wait a few minutes and then see if you can connect to your share.*[/COLOR]

I should also note that based on your output you have no shares defined anywhere so although your Win7 machine might now be able to see the Ubuntu machine there is nothing for it to connect to.

As a test you could open up Nautilus and right click on one of your home folders like Documents. Then select "Sharing Options", click on all the boxes, select "create share", allow it to modify permissions and then see if Win7 can access the "documents" share on your Ubuntu machine.

---

### Post by johnsmoke on 2012-03-05
Morbius1, it worked! Thanks so much for your info! I can now access my files on my main PC (the Ubuntu one) from my Windows laptop that I have hooked up downstairs! THANKS! :)

---

### Post by DocHoss on 2012-05-01
EDIT: Problem solved.  Used a much simplified smb.conf from here: [Official Samba 3.5.x HOWTO]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

I'm having the same problem.  I know this thread is old but this is the exact problem I'm having.  I have Ubuntu Server 11.10 running and I'm on a Windows 7 laptop that can't see the server at all.  Here are my outputs from the above commands:

hostname
THEBOSS

testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
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
        idmap config * : backend = tdb
        force user = bo

[homes]
        comment = Home Directories
        valid users = %S
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[share]
        comment = Test
        path = /home/bo/test
        read only = No
        create mask = 0755
        guest ok = Yes

I get no output from the net usershare command.  And when I do smbtree it prompts for a password, but does nothing when I input my password.  Any help on this one?

---

