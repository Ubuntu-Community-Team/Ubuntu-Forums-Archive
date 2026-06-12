---
title: "XP accessing a Ubuntu Samba share"
date: 2011-08-22
forum: General Help
---

### Post by silverrope on 2011-08-22
I use an IBM S50 desktop running XP as a file and print server via Windows shares and so far all my XP and Ubuntu laptops can see and use the shares. Now I would like to move the S50 to Ubuntu and still use it as a file and print server. To test this, I have installed Ubuntu 10.04 via wubi and then I installed samba. First thing was to do the simplest case: follow the official documentation,

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

I followed it to the letter, editing the smb.conf file, creating a /srv/samba/share directory, changing the permissions, and restarting the daemons. I was able to read and write to the share with my Ubuntu laptop. Success! However, my Windows laptop can see the Samba server, but when I click on the share, "Ubuntu server (Samba, Ubuntu)" to reveal the file system, it asks for a username and password.

Any ideas on how to let XP access the Ubuntu share? Sorry as this is the most basic of questions, but I don't know what to do at this point.


```

    workgroup = workgroup
    server string = %h server (Samba, Ubuntu)
    security = user


[share]
    path = /srv/samba/share
    writeable = yes
    browseable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```

---

### Post by silverrope on 2011-08-22
Here is the log when I accessed the Ubuntu server with the XP machine.

```

[2011/08/22 17:04:45,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/08/22 17:04:45,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

```

---

### Post by Morbius1 on 2011-08-22
Please post the output of the following command:
```
testparm -s
```

That will show us how Samba is interpreting your smb.conf. The one you posted would never work.

---

### Post by silverrope on 2011-08-22
OK, here it is.

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Backups]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (S50)
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
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = No
    guest ok = Yes

[Backups]
    path = /media/My Book/Backups
    read only = No
    create mask = 0755
    guest ok = Yes

[share]
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes

```

---

### Post by Morbius1 on 2011-08-22
Unfortunately all of that looks textbook correct. 

The only thing I can think of that explains why a Linux client can access "share" and Windows client is prompted for credentials is if you have the following conditions:

* The Windows login username and the Ubuntu server login name match.
* But you created a samba password for the Ubuntu login user that differs from the Windows login password.

That's kind of confusing so let me try that again:

There's a 12 year old design flaw in Windows that has it transmit the user's login name and password when it tries to access a share even if that share is a guest share like yours. If the Samba server has no match then you can access the guest share. But if the Samba server has a match in username but a different samba password then you will be asked for a password in perpetuity.

---

### Post by silverrope on 2011-08-22
Wow! You have hit it spot on! I am temporarily testing Ubuntu on the S50 for the first time using wubi so naturally I just quickly created an account with my Windows username and password. 

I just logged into another account on a Windows machine and it accessed the files. So the lesson is I must use different username/passwords. And I learned another bit of quirkiness in the Windows/Linux interop world!

Thanks for your help.

---

### Post by Morbius1 on 2011-08-22
> So the lesson is I must use different username/passwords. And I learned  another bit of quirkiness in the Windows/Linux interop world!You don't necessarily have to have different login usernames / passwords. You can either:

* Not have a samba password at all for the Linux login user if the name matches the Windows user name.

* Have the Linux username and Linux samba password match exactly the Windows login username and password.

---

### Post by silverrope on 2011-08-22
> **Morbius1 said:**
> 
* Have the Linux username and Linux samba password match exactly the Windows login username and password.

In fact they did match exactly; so there is another problem somewhere but I will deal with that on another day. For the moment, I will just make sure the usernames do not match and continue with the test. Next, I have to see if Ubuntu can share FAT32 and NTFS folders. Plus I need to see if I can get the printers to work via Samba.

Anyway thanks again.

---

