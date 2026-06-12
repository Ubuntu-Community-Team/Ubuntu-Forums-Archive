---
title: "samba share can not connect"
date: 2010-01-10
forum: General Help
---

### Post by linuxcss on 2010-01-10
I have setup two shares on karmic and I then try to connect with nautilus

smb://ipAddress

nautilus displays the shares and when i click on them it 
asks for the password

but its never happy with the password


But when I do the same back to a jaunty machine I do not have the problem,
and the username and passwords are identical on both machines

any help with what needs to be adjusted on the karmic machine?

---

### Post by linuxcss on 2010-01-11
anyone have a clue why shares don't work in karmic with samba?
i'm running Samba 3.4.0

---

### Post by Morbius1 on 2010-01-11
If you're trying to login to the server share by using the server users username , did you set up a "samba user" password?
There's a difference between local login user and samba user.

If your login username is linuxcss then the command to set up a samba user password is like this:

Open **Terminal**
Type [B]sudo smbpasswd -a linuxcss

[/B]It will ask you for a password to be used to authenticate.

---

### Post by linuxcss on 2010-01-15
Thanks [Morbius1]("http://ubuntuforums.org/member.php?u=982144")

that worked.

Is there any way to keep passwords automatically synced?

---

### Post by Morbius1 on 2010-01-16
Not sure what you mean by "synced".

When you're prompted for a username and password there's an option to "remember forever" if by synced you mean remembered.

---

### Post by Falkor on 2010-01-22
Hi,

I am having issue connecting to a Samba shared folder too.

I have set up Samba server on both my home Ubuntu 9.04, and the remote dedicated server with 9.10.

1)
For my home box, I modified the /etc/samba/smb.conf, only by adding info of my shared folder, as:
```

path = /home/< My system account 01 >/SambaShared/
available = yes
valid users = < My system account 01 >
read only = no
browsable = yes
public = no
writable = no

```all other settings are as default.

then:
```

smbpasswd -a < My system account 01 >
smbpasswd -e < My system account 01 >
/etc/init.d/smb restart

```After doing the above, I can connect from my Windows Explorer to the Samba folder.

2)
However, I did the same to my remote server but that didn't work.

Instead of prompting me for Samba login, I just get a pop-up saying that the \\< IP of my remote server >, couldn't be found.

(The firewall of my remote server is disabled)


Please give me some suggestions. Thanks. :KS

---

### Post by jamesisin on 2010-01-22
I don't think you need a Samba username/password.  If you connect using smb://[username]@[IP] you should be good to go.

---

### Post by Falkor on 2010-01-22
jamesisin,

Thanks for your reply.

1)
> **jamesisin said:**
> If you connect using smb://[username]@[IP] you should be good to go.

I am trying to connect from my local Windows XP, to the shared folder of my remote Ubuntu 9.10, via Windows Explorer, which I don't think it recognizes the ***smb*** command. (I tried, didn't work)

I tried that from my local Ubuntu 9.04 (from console, as I don't have desktop installed) as well, got the same result, saying it couldn't find such folder.


2)
> **jamesisin said:**
> I don't think you need a Samba username/password.

As the method in #1 didn't work for me, regarding the use of username/password, it wouldn't be necessary, with the following setting:

```

map to guest = bad user

```then whatever username/password I provide, would be ignored by Samba, and send me to the [public] shared folder (if there was one available).

As I don't seem to be able to even establish a Samba connection, and method does apply to me...


3)
I have read some discussions (including those on this forum) regarding such issue, yet most of them are actually caused by the firewall, but currently for my remote box, I have both iptables and SELinux disabled.

---

### Post by Morbius1 on 2010-01-22
Just out of curiosity what exactly does this do?
> path = /home/< My system account 01 >/SambaShared/
available = yes
valid users = < My system account 01 >
[COLOR=Blue]read only = no[/COLOR]
browsable = yes
public = no
[COLOR=Blue]writable = no[/COLOR]"read only = no" indicates that it is writeable
"writable = no" indicates that it is read only
Is the resulting share read only or writeable?

> However, I did the same to my remote server but that didn't work.
Instead of prompting me for Samba login, I just get a pop-up saying that the \\< IP of my remote server >, couldn't be found.
(The firewall of my remote server is disabled)Define "remote server" please. Is this server connected directly to the internet? Is the ip address you're using to access this server a private internal address or a public address?

---

### Post by Falkor on 2010-01-22
1)
> **Morbius1 said:**
> Just out of curiosity what exactly does this do?
"read only = no" indicates that it is writeable
"writable = no

I followed one of those articles on the web without paying attention... Indeed that setup is funny...

The article is written by _**[this guy]("http://www.razor-gator.com/obi_wan_kenobi.jpg")**_.

[SIZE=1][COLOR=LightBlue](Just joking)[/COLOR][/SIZE]


2)
> **Morbius1 said:**
> 
Define "remote server" please.


Sorry to confuse you. It is a VPS from this hosting ([link]("http://fsckvps.com/")). I try to connect from my home computer (Windows XP), to the Samba shared folder, via Windows Explorer, as this article is showing ([link]("http://www.reallylinux.com/docs/sambaserver.shtml")).


3)
Again, as you can see in my previous post, I have only added the definition of my shared folder, and everything else is as default. That works for my home Ubuntu box, yet it doesn't for my VPS.


4)
Since my current issue with the Samba of my VPS, is that I can't establish the connection with it, I followed this guide for doing the troubleshooting ([link]("http://samba.org/%7Etpot/articles/multiple-interfaces.html")), yet couldn't get it to work.

From ifconfig, my interfaces setup is as:

```

lo    127.0.0.1

eth0    127.0.0.1

eth0:0    < My public IP >

```Thanks for your help.

---

### Post by Morbius1 on 2010-01-22
VPS is above my pay grade ( if you're familiar with that expression ) I'm afraid. My first guess would have been the firewall but you posted that it's disabled. 

Sorry, I have nothing to offer.

---

### Post by jamesisin on 2010-01-22
I would not use a Samba share via a public IP.  If you must use Samba from a non-local server, consider using VPN to make that server local so you can use a private IP address.

---

### Post by Falkor on 2010-01-22
Morbius1,

Yup, most common cause that I have seen is the firewall settings.

Setting up VPS is above my level too, but using it, is the same as a normal Ubuntu server.
______________________________________________



> **jamesisin said:**
> I would not use a Samba share via a public IP.  If you must use Samba from a non-local server, consider using VPN to make that server local so you can use a private IP address.

jamesisin,

Thanks for your reply.

( I read some of your previous posts regarding your Samba setup. :) )

I mainly need to setup the Samba server on my VPS, because I am using a KVMoverIP, to install Windows 2008 on another dedicated server. I need to mount the .iso file of Windows 2008, as a virtual media, but as the uplink of my home DSL is slow, so I uploaded the .iso file to my VPS, as it has a 10 mbps uplink.

I have never tried VPN before, but I will check it out to see if I can use it for mounting a vritual media.
______________________________________________



I have been doing troubleshooting by following this guide:

- [http://samba.org/~tpot/articles/multiple-interfaces.html]("http://samba.org/%7Etpot/articles/multiple-interfaces.html")

and everything is fine until I get to this part:
```
nmblookup -B 127.0.0.1 server
```which returns the following result:
```

querying B on 127.255.255.255
name_query failed to find name B
querying 127.0.0.1 on 127.255.255.255
name_query failed to find name 127.0.0.1
querying server on 127.255.255.255
name_query failed to find name server

```:confused:

---

### Post by linuxcss on 2010-02-08
earlier Morbius suggested

'If you're trying to login to the server share  by using the server users username , did you set up a "samba user"  password?
There's a difference between local login user and samba user.

If your login username is linuxcss then the command to set up a samba  user password is like this:

Open **Terminal**
Type [B]sudo smbpasswd -a linuxcss

[/B]It will ask you for a password to be used to authenticate.



Well, something now is broken,

I had a couple of virtual machines that were accessing shares on this host ubuntu 9.10 karmic system.
And now one of them can not authenticate. However it can still authenticate to a jaunty share with the same username and password.

This was working after i did Morbius suggestion of:  'sudo smbpasswd -a linuxcss',
but now I have discovered after not using it for about a week it not longer works, The only thing that comes to mind that might have broke this is that I have applied updates to the system via update-manager and am now running kernel 2.6.31-19-generic-pae.

Does anybody have a clue what else I can try to fix my problem.

thanks

---

### Post by Merlinson on 2010-02-08
I'm not going to pretend I know anything, but I followed the tips in this thread and now my shares on all my computers, including windows can all see each other automatically.

Good luck.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Morbius1 on 2010-02-09
I have only dealt with a kernel update once with VirtualBox and it was a very long time ago - like Version 2 or maybe even earlier - but don't you need to rebuild the kernel module when the kernel is updated?

*vboxdrvr setup* or something like that - sorry don't remember the specifics. 

If I understand your description correctly, you can access a remote server but not the local VBox host machine. You may need to reinstall the Guest additions as well.

Sorry if this is incoherent ( more incoherent than usual for me at least ;)), I'm trying to remember all this without the aid of my notes.

---

### Post by dmizer on 2010-02-09
> **Falkor said:**
> 
```

path = /home/[COLOR="Red"]< My system account 01 >[/COLOR]/SambaShared/
available = yes
valid users = [COLOR="Red"]< My system account 01 >[/COLOR]
read only = no
browsable = yes
public = no
writable = no

```

The red highlight means that the only user allowed to access the share is whatever username you use to log into that samba server.

> **jamesisin said:**
> I would not use a Samba share via a public IP.  If you must use Samba from a non-local server, consider using VPN to make that server local so you can use a private IP address.
I wanted to take the time to really emphasize this. Samba is meant for use ONLY on a trusted network. It is not hardened and it can easily be cracked. Bots are constantly out there looking for samba connections, and I strongly suggest that you disable that ASAP and keep it disabled until you can figure out how to use something like VPN or ssh.

---

