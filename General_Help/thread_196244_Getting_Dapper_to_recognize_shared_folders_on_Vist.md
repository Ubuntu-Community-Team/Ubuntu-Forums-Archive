---
title: "Getting Dapper to recognize shared folders on Vista"
date: 2006-06-13
forum: General Help
---

### Post by Varth on 2006-06-13
Hello all.

My family broke the computer again, and I need to format and reinstall Windows on it. (It's not my computer, so I don't have a choice of which OS runs on it). Normally I'd follow my usual routine for this: Make a shared folder on my own computer, boot the family computer with a live CD, and back up everyone's files over the network to my computer. And it always works like a charm. But this time, there's one difference: my computer is running the Vista beta (I know, boo and all that).

Now, when I boot the family computer with the Dapper Live CD, it won't let me access any of my shared folders in Vista when I try to mount them. Whenever I mount one and try and open it, it starts asking me for a username and password:

[IMG]http://img149.imageshack.us/img149/1093/screenshotauthenticationrequir.png[/IMG]

Whenever I tried to transfer to my computer while it was running XP I also got this dialog, but I could access the folder anyway by pressing Escape.I never set a password for the folder in the first place, so I don't understand why it's prompting me foe one. I've tried entering my login information for the Vista computer, as well as trying to log in as the live CD user, nothing happens except for the password dialog popping up again. No matter what I put in, it just keeps popping back up until I cancel, at which point it says "The contents of this folder cannot be displayed; Sprry, couldn't display all of the contents of "Desktop".

As for the Vista machine, I've set sharing restrictions at their loosest, so I don't know what's up.

Can anyone help me out?

---

### Post by Varth on 2006-06-14
Bump.

How come no one ever replies to my threads? Could some please help me out?

---

### Post by florizs on 2006-06-14
I'm not shure, but Vista uses the new windows file sharing system SMB 2.0 while  Samba supports SMB 1.
this could be the problem.
There is a backwards compatability feature in Vista, but I can't help you out on that since I'm not familliar in with Vista.

---

### Post by longinus on 2006-06-15
I got this login msg some times when conecting to normal XP shares. I don't when that happened, or why, but I just entered the administrator login (not the user), more than once sometimes. And it worked..

I also have Vista running, but it's on the same computer as Ubuntu, so I can't try sharing between them. BUT another XP machine can access my Vista shares.

I would recomend to install a simple FTP server on Vista, like Filezilla server... and conect to it from ubuntu... It's probably faster than samba anyway.

Edit: Vista is VERY paranoid about security... you need to tell if the network is private, etc. It has the firewall up, and everything else like restricted mode in IE. So I wouldn't be surprised if this is some bug of the over protection of Vista.

---

### Post by jongkind on 2006-06-15
My experience with Samba is that best results for accessing shared network folders is via Nautulus. E.g. let's assume that the IP adress of the Windows computer is 192.168.1.101. In that case you can access the Windows computer by entering its IP address in the address bar of Nautulus as follows: smb://192.168.1.101/

---

### Post by nemesa on 2006-06-16
I have the same problem. I can reach shared folders on Vista via XP. It shows me the password dialog, but on XP, it's accept the correct password, while on Ubuntu discard it...

:(

---

### Post by foureight84 on 2006-11-21
yep. i am having the same problem. and the same goes with trying to connect to a linux shared folder from vista. i can't do it. arg this is annoying. i'm going back to xp. vista is not worth my trouble; although it is more stable than xp (so far).

---

### Post by UMDGaara on 2006-11-24
Same problem here, only I'm using Edgy. Any ideas beyond SMB 1.0 vs 2.0 incompatibility?

MOSTLY UNRELATED NOTE: XBMC on xbox is also unable to connect to my Vista shares, I assume for the same 1.0/2.0 problem. I had to set up ccXsteam to share media to it but I'd rather use SMB to move files around if possible.

---

### Post by z600 on 2007-02-11
I'm having the same problem too! :( Any ideas on how to get this working? I initially assumed it was the vista firewall but it's not. I access my printer through a windows box. It worked fine when I had XP but now its unaccessible with vista.

---

### Post by z600 on 2007-02-13
Has anyone found a solution to this problem?

---

### Post by z600 on 2007-02-13
I found that I could mount a share on Vista via the usual mount command.

eg. sudo mount -t smbfs -o username=username,password=password //VISTA_BOX/share ubuntu_mount_dir

It still does  not work through the "Places->Connect to Server..." dialog.

---

### Post by FaytlND on 2007-02-16
I have found the same.  I can mount the Vista shares via command line and FSTAB, but no go when trying to connect via the "Connect to..." dialog.  No big deal, I guess.  Command line is just as easy (and FSTAB even easier).

---

### Post by z600 on 2007-02-18
That's cool for shares but not for shared printers. Does anyone know how to mount a shared Windows Printer on Ubuntu via command line?

---

### Post by sawjew on 2007-03-22
I had the dame problem and managed to get printer sharing working by installing LPD print services on Vista and then share it using CUPS.

I followed this guide here [http://www.frogmorecs.com/arts/configure-lpdsvc.html]("http://www.frogmorecs.com/arts/configure-lpdsvc.html") and modified it slightly to suit the differences with Vista.

The main difference is that it is no longer called "print services for Unix" but something like "LPD print services" (I'm not in front of Vista at the moment so I am not sure).  The other thing to note is that you don't need to start the service, it is started automatically after installation.

The only other thing is on your windows printer under sharing options for the printer you need to disable bi-directional printing or it will just make noise and won't print.

I used this guide here [http://adrianus.wordpress.com/2007/02/06/howto-add-right-click-menu-to-mount-smb-shares-in-ubuntu-edgy/]("http://adrianus.wordpress.com/2007/02/06/howto-add-right-click-menu-to-mount-smb-shares-in-ubuntu-edgy/") to set up my file sharing and it works easier than nautilus.  The file sharing problem is not a samba problem but a nautilus one and hopefully it will be fixed soon.

hope this helps.

---

### Post by bigdave146 on 2007-07-16
Has anyone found a fix for this yet ?

Dave

---

### Post by mikex on 2007-08-24
I seem to have run into the same thing. I shared out a folder on Ubuntu and I can see it on Vista, and it pops up a box asking for a name and password. However, it won't accept anything I type in as valid.

---

### Post by sawjew on 2007-08-24
The issue you're having is different one, it's the other way around.  You need to add a samba user with a username and password or just allow anyone access to your samba shares.  If your on a home network and not concerned about the other users on your network having access to your files the easiest way is to allow all users access.

The way to do this is;

[LIST=1]
[*]open a terminal
[*]enter the following code;
```
sudo gedit /etc/samba/smb.conf
```
[*]Under the heading "Authentication" at about line 91 you will see

```
security = user
```

[*]change this to

```
security = share
```

[*]then enter the following in the terminal
[/LIST]
```
sudo /etc/init.d/samba restart
```

You should then be able to access your shares with no password.

---

### Post by mikex on 2007-08-24
Sorry, I just did those steps and still won't let me in. Still asks for a user name and password. I re-booted and no-go.

Plus, I don't see why the user setting won't work. If I want to see the share on linux, and log in using my own user name and password, which is what the user setting is for, why wouldn't it work anyway - that is what i was doing. I know my user name and password, it rejects them.

---

