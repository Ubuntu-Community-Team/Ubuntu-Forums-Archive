---
title: "Make files automatically inherit permissions of shared folder"
date: 2011-10-02
forum: General Help
---

### Post by wgilthorpe on 2011-10-02
Hello all.  I need a bit of help.  I have set up a ubuntu file server for my home that shares my movies, music, etc. with all the machines in my home.  It is working almost perfectly, except for the fact that when I add a new album to my shared music folder or a new video to my shared video folder, I have to run chmod 777 on whatever new file(s) have been added.  I have read about scripts using chron to take care of this, but is there a more elegant way or some built in tool to do this that I have not come across yet?  I have a couple of ideas of my own, but they all seem clunky.  I would like to get feedback from the community before I implement anything.  Thanks

---

### Post by Morbius1 on 2011-10-02
All we need to know now is what you are using to share the folders. Samba?

If it is Samba please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by ajgreeny on 2011-10-02
I am not too sure about using shared folders on a server, but normally to make all files added to a folder follow the folders permissions, you would need to run ```
sudo chmod 2777 path/to/folder
```The 2 in front of the 777 makes all files take the same permissions as the folder itself.

---

### Post by dave01945 on 2011-10-02
> **ajgreeny said:**
> I am not too sure about using shared folders on a server, but normally to make all files added to a folder follow the folders permissions, you would need to run ```
sudo chmod 2777 path/to/folder
```The 2 in front of the 777 makes all files take the same permissions as the folder itself.

all the 2 will do is make any new files created take the same group as the directory it won't affect any other permissions

---

### Post by prodigy_ on 2011-10-02
> **wgilthorpe said:**
> I have to run chmod 777
777 is almost always a security hole in the long run and it's a good indication that you're doing something wrong. Just saying.

---

### Post by wgilthorpe on 2011-10-02
Here are the results of the commands that you asked for Morbius1:

```
will@media-server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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

``````
will@media-server:~$ net usershare info --long
[music]
path=/home/will/raid/Music
comment=
usershare_acl=Everyone:R,MEDIA-SERVER\will:F,
guest_ok=n

[videos]
path=/home/will/raid/Videos
comment=
usershare_acl=Everyone:R,MEDIA-SERVER\will:F,
guest_ok=y

[public folder]
path=/home/will/raid/Public Folder
comment=
usershare_acl=Everyone:F,
guest_ok=y

```I am not too concerned about security as this is not an outside facing server.  Really all it does is act as a print server and NAS.  Also, I just noticed as I am typing this that my music share (which was giving me trouble this morning on my only remaining windows box) has guest_ok=n which may be part of my problem.  Also, thanks for all of the speedy feedback.

---

### Post by Morbius1 on 2011-10-03
I'm confused as to why you feel the need to chmod 777 everything in the shared folders on the server. All of your shares except "Public" are read only to the remote guest. There's something I'm missing in your description of the problem.

What I would suggest is the following:
edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
force user = will
```Save smb.conf and run the following command:
```
sudo service smbd restart
```NOTE: Every time you restart samba the network has a fit so you need to wait a few minutes for things to settle down before trying to access anything.

When the remote guest gains access he will be converted to you for these shares so assuming "will" can access these things in MEDIA-SERVER locally so will everyone else.

---

