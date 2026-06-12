---
title: "nautilus does not change smb.conf"
date: 2009-11-22
forum: General Help
---

### Post by plum7500 on 2009-11-22
When I enable sharing on a folder in Natilus (mouse right click on folder, properties->share), I don't see the file /etc/samba/smb.conf changing. Is the smb.conf file for each user stored in another location?

---

### Post by sefs on 2009-11-22
> **plum7500 said:**
> When I enable sharing on a folder in Natilus (mouse right click on folder, properties->share), I don't see the file /etc/samba/smb.conf changing. Is the smb.conf file for each user stored in another location?

All users of the same computer use the same smb.conf as far as I know.

---

### Post by plum7500 on 2009-11-22
> **sefs said:**
> All users of the same computer use the same smb.conf as far as I know.

Thanks for the reply. It seems that my videos folder is being shared when I do this:


root@haf:~# smbclient -L localhost
Enter root's password: 
Domain=[MHOME] OS=[Unix] Server=[Samba 3.4.0]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    videos          Disk      
    IPC$            IPC       IPC Service (haf server (Samba, Ubuntu))
    dropbox         Disk      
    pictures        Disk      
Domain=[MHOME] OS=[Unix] Server=[Samba 3.4.0]

    Server               Comment
    ---------            -------
    HAF                  haf server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    MHOME                  HAF


I manually added the following to the /etc/samba/smb.conf. As changing the properties for the folder using the GUI had no effect.

[videos]
        path = /home/john/Videos
        available = yes
        read only = no
        guest only = yes
        guest ok = yes
        browseable = yes
        public = yes


I did the following to test the smb.conf which seems ok to me:

root@haf:~# testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[videos]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = MHOME
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

[videos]
    path = /home/john/Videos
    guest only = Yes
    guest ok = Yes

However my videos directory is not seen by my Windows Vista computers.

---

### Post by sefs on 2009-11-22
Here is how I setup Samba when I have ufw enabled. Note if you do not have ufw enabled just ignore the ufw parts.

ufw is the firewall and I also install gufw as the front end to ufw.


1) Installing samba ...
------------------------

```

sudo apt-get install samba-tools
sudo apt-get install system-config-samba
sudo apt-get install smbfs
sudo apt-get install samba
sudo apt-get remove libpam-smbpass

```

At this point I have a fresh install of samba so the smb.conf is a virgin one with no manual changes made by me. That's important.

I remove libpam-smbpass because I want my smb user passwords to be different than my linux user password, otherwise libpam-smbpass will try to sync them.  Annoying.

2) Configuring UFW to work with samba
---------------------------------------
then edit /etc/default/ufw

and change this line...

```

IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"

```

to this line ...

```

IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

```

Next issue these commands to the firewall changing the IP's below to the IP's of your network. I mentioned gufw earlier but its just easier to cut and paste some commands into a terminal.

```

sudo ufw allow proto tcp to any port 135 from 192.168.1.0/24
sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24

```

3) Other files that you may need
------------------------------------------
You may need these extra packages....
libgnomevfs2-extra
libgnomevfs2-bin
gvfs-fuse
gvfs-bin

...but i suspect they may already be installed.

At this point samba should now be configured correctly on the linux workstation.  Note that I have not touched smb.conf nor do I need or intend too.

4) Configuring Users and Shares
----------------------------------
To configure shares simply go in your Ubuntu menu system to...
System -> Administration -> Samba 

I am too lazy for screen shots so I will just say what i do.

When the samba gui opens...

go to 

Preferences -> Server settings
1) set your workgroup
2) set your description 

Next ...
Preferences -> Users
1) Add a user (unix username, windows username, samba password, confirm samba password).  These will be the users that access your shares.  So for instance we will set up a user called myuser.

Next ..
File -> Add Share
1) note that this dialog has two tabs. Basic and Access.
2) In the Basic tab select the directory you want to share...give it a share name, and check the boxes writable and visible.
3) go to access tab and select "only allow access to specific users" and select from the users you would have added to access this share.

And that's basically how I set up samba on my machine with no need to fiddle with smb.conf

Now I can browse my linux shares from any computer that will pop up a box that I just give it the username (myuser for example) and password I would have set up for this user and share.

---

### Post by plum7500 on 2009-11-22
Thanks, that did it. ;)

Strange, Samba worked when Karmic was first installed using Nautilus. It was broken after applying the automated updates.

---

