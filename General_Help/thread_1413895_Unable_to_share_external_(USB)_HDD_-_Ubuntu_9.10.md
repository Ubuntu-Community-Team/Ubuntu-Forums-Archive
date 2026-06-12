---
title: "Unable to share external (USB) HDD - Ubuntu 9.10"
date: 2010-02-23
forum: General Help
---

### Post by Mike BFD on 2010-02-23
An external USB hard drive (NTFS-formatted) is easily mounted and accessible at the Ubuntu laptop it's connected to. However, all attempts to share it (for network access from another Ubuntu machine) failed.

The best description of the problem is already posted here: [https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-April/011972.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-April/011972.html)
I have the very same problem.

Searching forums (this and others) showed several similar questions but no effective answer!

Any ideas??

Thanx in anticipation,
Mike

---

### Post by Mike BFD on 2010-02-23
...Has anybody have the same problem??

I really wander what I can do with it! Samba (referred to as a solution in the most of forums) is ineffective...

---

### Post by cjhabs on 2010-02-23
I share my ntfs drives between Ubuntu machines using NFS - it is much faster than Samba.

You will need to install nfs server and client support from the repos.

---

### Post by Mike BFD on 2010-02-23
NFS? A few more details if you don't mind?

---

### Post by ubunterooster on 2010-02-23
get the following packages for server: nfs-common, nfs-kernel-server, and portmap

then enter: "sudo /etc/init.d/nfs-kernel-server status" in the terminal.

---

### Post by ubunterooster on 2010-02-23
above directions are for server computer,will give client info later. nfs (network file system) allows complete integration, as far as allowing one computer to even use drivers compiled on another. It will do the job for regular files as well.

---

### Post by ubunterooster on 2010-02-23
also for server, i.e. host, you will likely want "share-admin" unless you would rather do it all via terminal. [if you want to do it all via terminal, I can help w/ that, too]

on the client, install "nfs-common"

Please post when you have completed the above steps. :)

---

### Post by cjhabs on 2010-02-24
Thanks for following up for me - I am only on the board sporadically.

---

### Post by ubunterooster on 2010-02-24
HOST.
go to system>admistration>shared folders. In the dropdown menu "share through" choose "UNIX nfs".
In the "allowed hosts" enter the ip address of the client.

---

### Post by ubunterooster on 2010-02-24
CLIENT:
sudo mount -t nfs 192.169.1.2/media/nameofsharedhdd

replace above IP address w/ the one for the host.

---

### Post by Mike BFD on 2010-02-25
> **ubunterooster said:**
> HOST.
go to system>admistration>shared folders. In the dropdown menu "share through" choose "UNIX nfs".
In the "allowed hosts" enter the ip address of the client.
Hmmm... I'm stupid))
In my system>administration there's nothing about sharing!
How can I get to those settings in some other way??

---

### Post by Morbius1 on 2010-02-25
The reason you can't access the external - NTFS partitioned USB drive share is because it mounts with you as owner and with read / write permissions to you only. The remote user isn't you so even though you may have set up samba to allow guest access guest still isn't you.

The easiest fix - if your still interested in the samba method - is to do the following:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = your_ubuntu_user_name
```Save the file, exit gedit, and back in the termnal type: **sudo service samba restart**

---

### Post by ubunterooster on 2010-02-25
> **Mike BFD said:**
> Hmmm... I'm stupid))
In my system>administration there's nothing about sharing!
How can I get to those settings in some other way??

[NFS is faster and (some debate this) more secure.]

Or right-click a folder, and select sharing options...you may wish to stick all folders inside a "main" folder.

---

### Post by Morbius1 on 2010-02-25
Come to think of it you never stated which samba method you're using - there are two and they're configured in two different places. Again, only if you interested in the samba method , post the output of these three commands which will tell us which method you're using and how you're using it:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

---

### Post by ubunterooster on 2010-02-25
@ morbius: in "force your-ubuntu-user-name" is this server username or client username you refer to?

---

### Post by Morbius1 on 2010-02-25
You're right that was somewhat incoherent wasn't it?:redface:

It's the local server user login name.

---

### Post by Mike BFD on 2010-02-25
2 ubunterooster:

The problem is, an external USB HDD doesn't offer any "sharing options" on right-click. At all! And unfortunately, I have no idea how to "mark" it in NFS config file.

2 Morbius1:

Well, the output is the following:
(net usershare info)
info_fn: file /var/lib/samba/usershares/share is not a well formed usershare file.
info_fn: Error was Path not allowed.

[public]
path=/home/mike/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[! collectables]
path=/media/WD Elements/! Collectables
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/a_shared is not a well formed usershare file.
info_fn: Error was Path is not a directory.

(sudo net usershare info)
-- no reaction. at all. like
mike@newhomeone:~$ sudo net usershare info
mike@newhomeone:~$ 

(testparm -s)
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Processing section "[WD Elements]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = sys
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
    force user = mike
    guest ok = Yes

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

[Public]
    path = /home/mike/Public
    read only = No

[external hdd]
    comment = our external hdd
    path = /srv/samba/share
    read only = No

[WD Elements]
    path = /media/WD Elements
    read only = No

---

### Post by Morbius1 on 2010-02-25
(1)
> 2 ubunterooster:

The problem is, an external USB HDD doesn't offer any "sharing options" on right-click. At all! It does and it must have for you once also or else you would not have been able to create this:
> [! collectables]
path=/media/WD Elements/! Collectables
comment=
usershare_acl=Everyone:F,
guest_ok=yBTW, I'm not 100% sure but I don't think that will work because of the "!" in there. 

(2) As I said, there are two different methods of samba and you're using both at the same time and on the same target directories.

You need to get rid of one or the other. The Nautilus-shares are all guest = ok, but your "classic samba" shares all require authentication.

Which do you want: allow guests or require username and password to access?

---

### Post by Mike BFD on 2010-02-25
In my present case - pretty simple actually - I need just to allow unlimited access to my comp's folders (first of all, that "WD Elements" HDD) from another LAN comps.

That's all. I see that I maybe mixed different methods - no experience in Linux yet, gentlemen!

However, it doesn't matter to me what to use - Samba, NFS or anything else, I just need to make my folders visible over the network.

The network is small and "hungs" on a wireless router with built-in DHCP server, there's no need of any "additional authentication" of users for I know all of them))

---

### Post by Morbius1 on 2010-02-25
I would like to make a suggestion:

I'm assuming that /media/WD Elements is the USB NTFS drive.

**gksu gedit /etc/samba.smb.conf**

Put a # in front of each line for this share:
> 
[COLOR=Blue]#[/COLOR][WD Elements]
    [COLOR=Blue]#[/COLOR]path = /media/WD Elements
    [COLOR=Blue]#[/COLOR]read only = No     Save the file and issue the **sudo service samba restart**

Now see if you can go to /media/WD Elements and Right-Click > Sharing options.

If you can then click on all three of the boxes and select "Create Share"

---

### Post by Mike BFD on 2010-02-25
...Guys, I would HIGHLY appreciate a short - but "readable to a fool" - step by step instruction)) I'm a complete "green rookie" in Linux - and all my experience in terminal commands is limited to "old good DOS times"... But please, it was 20 years ago!!)))))

---

### Post by Mike BFD on 2010-02-25
**2 Morbius1:**

Hmmm... That was THE instruction. It works now. Thank you!
If ever in Finland, I'm buying you beer man))

---

