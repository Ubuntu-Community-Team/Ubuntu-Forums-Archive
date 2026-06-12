---
title: "change permissions in ubuntu on folders/files"
date: 2011-11-02
forum: General Help
---

### Post by rflores2323 on 2011-11-02
I wanted to change permissions on my external drives that are mounted however I have tried by sudo nautilus and then going to gui and permissions and changing it however it does not let me.

I ran the ls -l and get
drwx------ 1 xbmc xbmc

the gui shows below.


owner xbmc
folder access create and delete files
file access ---

Group xbmc
folder access none
file access ---

others
folder access none
file access ---

how can I change it so that everyone has permission to access the drive and folders/files inside of it. I am trying to get plexmedia server running and I cant see my drives via the webpage manage to add it to my source to be able to stream my content.

I want to change the "others" access so that I can access all my drives on the /media path to get read and write for all my folders from anywhere.

---

### Post by rflores2323 on 2011-11-02
Any help please?

---

### Post by Rhizoid on 2011-11-02
Is this an external which is being auto-mounted on a folder in /media?

What is the filesystem type?

---

### Post by rflores2323 on 2011-11-02
> **Rhizoid said:**
> Is this an external which is being auto-mounted on a folder in /media?

What is the filesystem type?

yes this is an external drive being automouted.  

you can see my drives that are mounted here (external drives are #18,19,20) [http://paste2.org/p/1754386](http://paste2.org/p/1754386)

---

### Post by Rhizoid on 2011-11-02
> **rflores2323 said:**
> yes this is an external drive being automouted.  

you can see my drives that are mounted here (external drives are #18,19,20) [http://paste2.org/p/1754386](http://paste2.org/p/1754386)


It's an NTFS partition - *nix permissions aren't applicable.

---

### Post by Rhizoid on 2011-11-02
Sorry - just read your first post properly.  You want to share your external drive with the network?  Is that right?

---

### Post by rflores2323 on 2011-11-02
so I cant change the permission so that "others" can have read/write/execute?

---

### Post by rflores2323 on 2011-11-02
> **Rhizoid said:**
> Sorry - just read your first post properly.  You want to share your external drive with the network?  Is that right?

well I already have samba installed and the drives are being shared that way.

The problem I am having is that I cannot access the files on my plex linux server to be able to stream over the internet.

---

### Post by Rhizoid on 2011-11-02
For a local user the permissions are applied when the filesystem is mounted - so the group and others permissions are a little redundant.

However for network users it's different.  I'm not sure there's a way to apply the permissions you want in a plug and play fashion but you can share the mounted filesystem with the network like this:

First make your mount point (if you haven't already).  I prefer to keep these as simple as possible so avoid spaces in the mount point name.

```
sudo mkdir /media/external
```

Now find the UUID of the external device.

```
sudo blkid
```

Next edit the fstab

```
gksudo gedit /etc/fstab
```

You need to put the following line somewhere in the fstab file - make a new line right at the bottom if you prefer - replace anything inside { } curly brackets with your own information.

```
UUID={the number from sudo blkid} /media/external ntfs _netdev 0 0
```

To test the mount works and display the permissions, use this:

```
sudo mount -a; ls -l /media
```

Let me know how that works out ;)

Cheers,

---

### Post by Morbius1 on 2011-11-02
Please post the output of the following commands so we can see how you samba shares are set up:
```
testparm -s
net usershare info --long
```Probably the fastest way to resolve this issue is to add a line to your smb.conf:
```
force user = your-user-name
```Where you put that line depends on what method you used to create the share. The output of the 2 commands above will tell us that.

---

### Post by rflores2323 on 2011-11-02
> **Morbius1 said:**
> Please post the output of the following commands so we can see how you samba shares are set up:
```
testparm -s
net usershare info --long
```Probably the fastest way to resolve this issue is to add a line to your smb.conf:
```
force user = your-user-name
```Where you put that line depends on what method you used to create the share. The output of the 2 commands above will tell us that.

```
xbmc@xbmc-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Elements]"
Processing section "[Expansion Drive]"
Processing section "[ext drive 2]"
Processing section "[Kids Movies 3]"
Processing section "[Kids TV Show3]"
Processing section "[Movies 3]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = XBMC SMB
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = xbmc
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast host lmhosts wins
    os level = 33
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[Elements]
    path = /media/Elements
    read only = No

[Expansion Drive]
    path = /media/Expansion Drive
    read only = No

[ext drive 2]
    path = /media/ext drive 2
    read only = No

[Kids Movies 3]
    path = /home/xbmc/Desktop/Kids Movies 3
    read only = No

[Kids TV Show3]
    path = /home/xbmc/Desktop/Kids TV Show3
    read only = No

[Movies 3]
    path = /home/xbmc/Desktop/Movies 3
    read only = No
xbmc@xbmc-desktop:~$ net usershare info --long
[kids movies 2]
path=/media/ext drive 2/Kids Movies 2
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/tv shows is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/kids movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[kids tv show3]
path=/home/xbmc/Desktop/Kids TV Show3
comment=
usershare_acl=Everyone:F,
guest_ok=y

[xbmc back drops]
path=/home/xbmc/Desktop/xbmc backdrops
comment=
usershare_acl=Everyone:F,
guest_ok=y

[kids tv shows]
path=/media/ext drive 2/Kids TV Shows
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/freeagent drive_ is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/elements___ is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/xbmcmovies 2 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[elements]
path=/media/Elements
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/kidsxbmc movie 4 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/movies 4 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[ext drive 2a]
path=/media/ext drive 2
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/tv shows 4 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[kidsmovies 3]
path=/home/xbmc/Desktop/Kids Movies 3
comment=
usershare_acl=Everyone:F,
guest_ok=y

[ext drive 2]
path=/media/ext drive 2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[xbmc backdrops]
path=/home/xbmc/Desktop/xbmc backdrops
comment=
usershare_acl=Everyone:F,
guest_ok=y

[movies 3]
path=/home/xbmc/Desktop/Movies 3
comment=
usershare_acl=Everyone:F,
guest_ok=y

[tv shows 2]
path=/media/ext drive 2/TV Shows 2
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/kidstv shows 4 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/movies 5 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[documents]
path=/home/xbmc/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/my music is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[music videos]
path=/home/xbmc/Desktop/Music Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[xbmc movies 2]
path=/media/ext drive 2/XBMC Movies 2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[downloads]
path=/home/xbmc/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/freeagent drive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[public]
path=/home/xbmc/Public
comment=
usershare_acl=Everyone:F,
guest_ok=n

[kids movies 3]
path=/home/xbmc/Desktop/Kids Movies 3
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/xbmcmainmovie is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/xbmc mainmovie is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/elements__ is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/kidstv shows is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[intros]
path=/home/xbmc/Desktop/Intros
comment=
usershare_acl=Everyone:F,
guest_ok=y

[expansion drive]
path=/media/Expansion Drive
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/kidsmovies 2 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
xbmc@xbmc-desktop:~$ 

```

---

### Post by Morbius1 on 2011-11-03
You've got a lot of shares there and your configuration might just work although unless you had a unique networking issue I would change this line:
    > security = SHAREBack to the default:
```
security = USER
```But the biggest problem I see at the moment is this line:
>      encrypt passwords = NoChange that to:
```
encrypt passwords = Yes
```Since all your shares seem to be guest shares and you set your guest account to be xmbc I think the encrypt passwords change should do it.

Don't forget to restart samba after you make any changes to smb.conf:
```
sudo service smbd restart
```

---

