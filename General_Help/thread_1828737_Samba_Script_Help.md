---
title: "Samba Script Help"
date: 2011-08-19
forum: General Help
---

### Post by Barajqial on 2011-08-19
I seem to be having a bit of trouble with a script I've been working with to add users to an Ubuntu file server.  So what I've been using  is a text file in the format:
```
Username UserGroup Userpass
```and feeding it into this script:

```
#!/bin/bash
#
# Ensure that root is running the script.
##
WHOAMI=`/usr/bin/whoami`
if [ $WHOAMI != "root" ]; then
echo "You must be root to add news users!"
exit 1
fi
#
clear
NEW_USERS="/home/empire/Desktop/users.txt"

cat ${NEW_USERS} | \
while read USER GROUP SMBPASS ; do
   
   groupadd -f ${GROUP} #2> /dev/null
   echo Group ${GROUP} added
   useradd -g ${GROUP} -s /bin/true ${USER}

   #(echo $SMBPASS; echo $SMBPASS) #| passwd --stdin ${USER} > /dev/null
   echo Added user ${USER}

   smbpasswd -L -a ${USER} #-w ${SMBPASS} > /dev/null
   (echo {$SMBPASS}; echo ${SMBPASS}) #| smbpasswd -as ${USER}
   echo User added to samba ${USER}
   smbpasswd -L -e ${USER}
   echo User Activated ${USER}
   echo -e "${USER} = ${USER}" >> /etc/samba/smbusers
done

```So the Script runs through the text file just fine and the user gets created and added where it needs to(both as an ubuntu user a samba users and into smbusers).  The Problem I'm having is that some of these users work and can connect to the shared drives no problem, but others cannot.  This seems to be rather erratic in which users can and cannot access them.  Any thoughts or helpful ideas would be awesome.

Oh BTW this is on a 10.04 LTS  system

-bar

---

### Post by Barajqial on 2011-08-24
Hey guys anyone have any ideas, I don't know enough a bout scripting to get this to work right

-Bar

---

### Post by papibe on 2011-08-24
Could you post the result of:
```
$ sudo testparm
```
Regards.

---

### Post by Barajqial on 2011-09-01
Hey sorry been busy with stuff Thanks for your reply here is the results of testparm

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[EmpVol1]"
Processing section "[AlwanColorServer]"
Processing section "[ArtDies]"
Processing section "[Empire]"
Processing section "[Proofs]"
Processing section "[EMail]"
Processing section "[PLANT]"
Processing section "[Backups]"
Processing section "[Users]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = WOKRGROUP
    server string = 
    map to guest = Bad User
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    smb ports = 139
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[EmpVol1]
    path = /media/EmpVol1
    valid users = admin, @Eng
    write list = admin
    read only = No
    create mask = 0777
    directory mask = 0777
    browseable = No
    browsable = No

[AlwanColorServer]
    comment = Alwan Colors
    path = /media/EmpVol1/AlwanColorServer
    valid users = deb, mrowlands, admin, @ArtDept
    write list = deb, mrowlands, admin, @ArtDept
    read only = No
    create mask = 0777
    directory mask = 0777

[ArtDies]
    comment = Art Dies
    path = /media/EmpVol1/ArtDies
    valid users = deb, mrowlands, admin, @ArtDept
    write list = admin, @ArtDept
    create mask = 0777
    directory mask = 0777

[Empire]
    comment = Empire's Directory
    path = /media/EmpVol1/Empire
    valid users = admin, @ArtDept, @Eng, @Sales, @DieShop, @SA, @Plant
    write list = admin, @ArtDept
    create mask = 0777
    directory mask = 0777

[Proofs]
    comment = Die Proofs
    path = /media/EmpVol1/Proofs
    valid users = deb, mrowlands, admin, natem, @ArtDept
    write list = admin, natem, @ArtDept
    create mask = 0777
    directory mask = 0777

[EMail]
    comment = EMail Storage
    path = /media/EmpVol1/EMail
    valid users = deb, mrowlands, admin
    write list = admin
    create mask = 0777
    directory mask = 0777

[PLANT]
    comment = Plant Folder
    path = /media/EmpVol1/PLANT
    valid users = deb, mrowlands, admin
    write list = admin
    create mask = 0777
    directory mask = 0777

[Backups]
    comment = Sams folder
    path = /media/EmpVol1/Backups
    valid users = admin, @DieShop, qc
    write list = admin, @DieShop, qc
    create mask = 0777
    directory mask = 0777

[Users]
    comment = Users Backup Folder
    path = /media/EmpVol1/Users
    valid users = admin
    write list = admin
    create mask = 0777
    directory mask = 0777

```

Again sorry it took so long.

Any idea what the correct syntax is to answer the password prompt in the script is, could that be my issue?

Thanks,
    -bar

---

### Post by papibe on 2011-09-01
A few questions:

Are you using useradd and groupadd aware that they are low level utilities? (instead of the common adduser and addgroup). Not that it is wrong, but just curious.

Are you using NIS? Do you have it set in /etc/nsswitch.conf?

If not, why are you using @groupname instead of just +groupname. I ask this because I see that you are making the effort to create the groups locally, so you can use them directly. Note that if NIS is not configure, this is not important because they will default for the local groups.

Regards.

---

