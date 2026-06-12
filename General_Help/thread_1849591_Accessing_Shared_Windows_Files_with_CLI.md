---
title: "Accessing Shared Windows Files with CLI"
date: 2011-09-24
forum: General Help
---

### Post by davec51 on 2011-09-24
I'm frustrated by an inability to operate as root, so I'm learning to do things from the CLI as much as possible. Today's question, after becoming root with "su." how do I access files on a shared Windows XP computer? I have tried many variations of the "mount" command with no luck.

---

### Post by haqking on 2011-09-24
> **davec51 said:**
> I'm frustrated by an inability to operate as root, so I'm learning to do things from the CLI as much as possible. Today's question, after becoming root with "su." how do I access files on a shared Windows XP computer? I have tried many variations of the "mount" command with no luck.

you should not enable the root account there is no need to.

we use sudo or gksudo please read [**ROOTSUDO**]("https://help.ubuntu.com/community/RootSudo")

which looking at your previous threads you should already know as it has been said before when you have said similar things

and it depends how your windows shares are setup, i presume you are using samba.

so look at cifs or smbfs

---

### Post by patryk77 on 2011-09-24
sudo apt-get install smbc

Has been a long time since I used it, but it has a very simple interface (it looks like it's out of MS-DOS 3.0 but hey, it works)

[IMG]http://freshmeat.net/screenshots/c3/03/c303050adf2d7ed32fcfa579caaf8592_medium.jpg?1237052622[/IMG]

---

### Post by davec51 on 2011-09-24
Haqking: I'm not asking what the root account is or how to get admin privileges. This time I simply want to know how, once in a terminal as root, what commands I need to access my shared files. Is there an easy answer to that question?

---

### Post by haqking on 2011-09-25
> **davec51 said:**
> Haqking: I'm not asking what the root account is or how to get admin privileges. This time I simply want to know how, once in a terminal as root, what commands I need to access my shared files. Is there an easy answer to that question?

either the post above yours ^

or like i said cifs or smbfs.

If you do things as root then good luck ;-)

---

### Post by JRV on 2011-09-25
Try this: 

nautilus smb://WINDOWS_HOSTNAME/SHARE_NAME

You do not need to be root.

---

### Post by Morbius1 on 2011-09-25
Just to be clear about this root cannot access a remote share using the normal methods ( i.e., gksu nautilus smb://.... ). It's a "fuse" thing.

The only way to access it as root is old-school:

[1] Install the following package:
```
apt-get install cifs-utils
```If you are using an older version of Ubuntu it's:
```
apt-get install smbfs
```[2] Mount the remote share:
```
mount -t cifs -o username=user-name,password=secret,dir_mode=0777,file_mode=0666 //server/share /local-mount-point
```

---

### Post by capscrew on 2011-09-25
You certainly can access a SMB share with the CLI.  You can't do much but you can access it.  Try```
smbclient //NETBIOS_NAME/SHARE_NAME
```

You can do this as a mortal user or as root.  See the man pages for the capabilities of smbclient```
man smbclient
```

---

