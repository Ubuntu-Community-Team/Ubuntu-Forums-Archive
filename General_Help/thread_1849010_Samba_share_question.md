---
title: "Samba share question"
date: 2011-09-23
forum: General Help
---

### Post by hrturner on 2011-09-23
Hello Everyone. As of lately I have been getting use to Ubuntu (came from fedora) as such I have been finding things to install and learn how to use. First project was a terminal server which went surprisingly well, so wondering what I could use at work, I tried to come up with another project. Having messed with samba in fedora I figured what the heck lets give it a whirl! So everything is setup and works great from my user name (hrturner). I can access the share from anywhere on work's network and from a machine running Windows or Linux.

So where is the problem you ask? I have another user called "image" who I want to be able to access the same share that my "hrturner" login can. So I added the user "image" to the server and then to the smb.conf file. However I still can't authenticate the user "image" to the share (even though hrturner works on the same share). 

Any thoughts? I was thinking it was a group permission thing so I added all but the adm and admin groups to the user "image" that "hrturner" has but it still doesn't work.

---

### Post by Morbius1 on 2011-09-23
> So I added the user "image" to the server and then to the smb.conf file.
So you added a new local user and you included him to the valid users of the share but you didn't mention if you added him to the samba password database:
```
sudo smbpasswd -a image
```

---

### Post by hrturner on 2011-09-23
Oops, Sorry forgot to mention that part as well. Yes I did run that command. Tried it again just to be certain but I still get the same issue. Error message I receive states that the network path could not be found but when I use the username "hrturner" it connects.

---

### Post by hrturner on 2011-09-23
I double check the file permissions on the folder they are set to 755. So I would think that would mean others could read the share but not write to it?

---

### Post by Morbius1 on 2011-09-23
Why not post the output of the following commands so we can see how these shares are set up:
```
testparm -s
```
```
net usershare info --long
```

You may not get anything from the second command.

---

### Post by hrturner on 2011-09-23
Here is the output of the first command:
```

root@ubuntultsp:/media/samba# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Images]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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

[Images]
    comment = McKesson Images
    path = /media/samba/Images
    valid users = hrturner, image
    read only = No


```

As you said, the second command returned nothing.

Also here is what the log files say is happening when I try to connect from another PC as the image user. 

```

[2011/09/23 10:21:13,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2011/09/23 10:21:17,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service Images, path /media/samba/Images

```

---

### Post by Morbius1 on 2011-09-23
Well, that's not good because everything looks like it's factory fresh and ready to go. If /media/samba/Images has a mode of 755 the remote user will not be able to write to the share but he should be able to access and read the share.

Are both remote users ( hrturner and image ) trying to access this share from the same client machine?

It could be that the entire path to the share is not allowing anyone but hrturner to gain access. By that I mean:

/media/samba has to be 755 and even
/media has to be 755

My "logic" here is that maybe /media/samba is owned by hrturner and has permissions of 700. hrturner would have access to the subfolder but no one else.

---

### Post by hrturner on 2011-09-23
Ah, did not think to try that. I will check those permissions and respond back.

---

### Post by hrturner on 2011-09-23
Morbius, you were right. I changed /media/samba to 755 and now my "image" user can see the share! I guess I didnt go far enough up the tree when I was checking permissions!

Thank you for letting me bounce ideas off you.

---

### Post by nightshadowfx on 2011-09-24
ok I have samba question I am trying to set it up to were me and a friend can access each other on his home network. we are both running ubuntu 11.04 the only difference on both is i am running 32bit and he is running 64bit. when i run the sudo smbpasswd -a command  I get this for both.

david@nightshadowfx:~$ sudo smbpasswd -a gary
New SMB password:
Retype new SMB password:
Failed to add entry for user gary.

that is when I try to add him. we see each other on the network and can get into each other but can not open up any folders shared. I have the folders setup to have read and write permissions on them. Any possible help would be great. thank you in advance.

---

### Post by Morbius1 on 2011-09-24
> david@nightshadowfx:~$ sudo smbpasswd -a gary
New SMB password:
Retype new SMB password:
Failed to add entry for user gary.Adding a samba user is a 2 step process - just like Windows:

[1] Add a user account to nightshadowfx.

There's 2 ways to do this. You can go to Administration > Users and Groups and add him that way or you can do it this way:
```
sudo useradd -s /bin/true gary
```This will create a gary account on your machine that has no home directory and no logon capability to your physical machine ( unlike the "Users and Groups" method ). If the only reason for adding gary is to share files I would recommend this way of doing it.

[2] Then add gary to the samba database:
```
sudo smbpasswd -a gary
```

---

### Post by nightshadowfx on 2011-09-24
thank you that did the trick.

---

