---
title: "Network sharing without samba?"
date: 2010-05-27
forum: General Help
---

### Post by Druke on 2010-05-27
[QUOTE=From the Samba site]Samba is the standard Windows interoperability suite of programs for Linux and Unix.[/QUOTE]

I have been a Linux user since 2004, but I recently moved my entire household to Ubuntu, the only "windows" in the house is my Xbox. I've always dealt with samba because I needed to do things from windows to Linux machines. But now I don't have to anymore.

Samba works great except for a few issues
[LIST]
[*]Shares sometimes have to be "reshared" everytime I login
[*]Anonymous files are a pain, have to 'sudo chmod' the files to set permissions afterwards.
[*]Appears in 'network' under 'windows netowork'
[/LIST]

I don't have to worry about samba anymore because I'm not dealing with windows. For right now I just use ssh/sftp to do inner network file transfers, all is good (all is great really). 

But for my girlfriend, it's a bit more complicated. She listens to music from her desktop to her laptop, so I we have bookmarked the ssh folder in the sidebar, but this seems to be averting the issue.

Is there anything for (network based) file sharing similar to CUPS printer sharing (holy crap CUPS printer sharing was amazing!!!!!), I'd like to have 'network shares'  just show up under networking, and work more reliably than samba (which I imagine if I knew how to configure it correctly, it'd work correctly). Things like NFS comes to mind, but I'm wanting something super simple (think CUPS sharing).

features I'm looking for:
[LIST]
[*]Shows up under 'network' in 'Places'
[*]Starts up automaticially
[*]sets permissions correctly
[/LIST]

To a lesser extent an "anonymous" setting that allows me to set up a "dropbox" folder, that assigns incoming files to a certain user/group.

I think samba can do all this, but is there a more 'native' method for this? I feel like using samba for inner ubuntu/linux file sharing is like running wine for my web browser. Perhaps my feelings are unfounded, perhaps samba started as windows/linux compatibility layer but evolved to be much more? Let me hear your thoughts/suggestions.

---

### Post by Morbius1 on 2010-05-27
> Perhaps my feelings are unfounded, perhaps samba started as  windows/linux compatibility layer but evolved to be much more?You have that in reverse. Samba was created for UNIX servers with Windows clients in the enterprise space - then Linux Servers and Windows clients in the enterprise space and now for our little home networks.
> Shares sometimes have  to be "reshared" everytime I login  Never had that problem. There was a bug in nautilus-share a while back that the share "emblem" in Nautilus would not survive a reboot but that didn't really change it to "unshared"
> Anonymous files are a pain, have to 'sudo chmod' the files to set  permissions afterwards.That's an easy fix but implementing it depends on which method of samba sharing you're using: Nautilus-share or Classic-share.

If you're interested in seeing if you can fix your current samba problems, post the output of the following commands:

```
net usershare info
sudo net usershare info
testparm -s
```If not then excuse the interruption.

---

### Post by Druke on 2010-05-27
Alright, I'll give advanced configuration a shot. I may have just had the emblem issue when it comes to shares not starting.

```
net usershare info
```
> [music]
path=/home/thebwt/Music
comment=
usershare_acl=Everyone:R,
guest_ok=n

[public]
path=/home/thebwt/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

```
sudo net usershare info
```
> no output

```
testparm -s
```
> Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


---

### Post by Morbius1 on 2010-05-27
Your using Nautilus-share and according to your share definitions:
Music - is a read only share the requires a username and password to access.
Public - is a read / writable share that allows anyone to access.

The problem is that any remote user who adds a folder or file to Public will have it's ownership set to "nobody" or if they have authenticated already for the Music share with their username.

One easy way to fix that:

from a Terminal
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = thebwt
```*[COLOR=Blue]I'm assuming that your username is "thebwt". If not then change it to the correct name.[/COLOR]*
Save smb.conf, exit gedit, and back in the terminal type either one of these commands ( sorry I wasn't smart enough to ask what version of Ubuntu you are using) :

If you're using 10.04:
```
sudo restart smbd
sudo restart nmbd
```If you're using anything earlier:
```
sudo service samba restart
```What should happen is that "force user" will act as a mask and convert the remote user to you as far as that share is concerned and all files will be saved with you as owner.

---

### Post by Druke on 2010-05-27
Assuming that 'force user' is global I can see two problems.
[LIST]
[*]In a multiuser environment (a home server in my case), all user's public folders would default to a certain user's ownership.
[*]Also in a multi user environment, would that option force all samaba transfers to be owned by thebwt? Or jsut anonymous ones?
[/LIST]

Aside from that, that fixes the basis of a large problem for our desktops (which are single user).

I'm having also having the issue of the shares not showing up in the network browser while trying to test all these changes. I get the "Windows network" folder, which holds the "workgroup" folder, which sometimes (depending on which way the wind is blowing it seems) holds "thebwt-desktop", which is empty, but sometimes (super rare) feels like showing my various shares. Notably it breaks when I'm looking at it, though I'm only looking at it while trying to fix it... so by fixing it i may have broke it worse :P :confused:

---

### Post by Morbius1 on 2010-05-27
> Assuming that 'force user' is global I can see two problems.
[LIST]
[*]In a  multiuser environment (a home server in my case), all user's public  folders would default to a certain user's ownership.
[*]Also in a multi user environment, would that option force all samaba  transfers to be owned by thebwt? Or jsut anonymous ones?
[/LIST]

- force user in this particular case is a global parameter so it will be applied to all shares. But you only have two shares - one is read only and the other is public.

- not sure what you mean by multiuser:

many local server login users - you have multiple "Public" shares? One per local login user on the server?

or many remote client users

---

### Post by Druke on 2010-05-27
server with multiple local users (myself and girlfriend will be sharing it).

The server doesn't need the public drop box, I was more learning how all this would work. I have to do this sort of thing for other people as well so I want to know what's going to happen.

perhaps it would be better to have a user group, and assign the permissions to that group?

force user works for me in my situation right now, but wouldn't be ideal if I had multiple users on one computer, who wanted to use a folder as a drop box.

---

