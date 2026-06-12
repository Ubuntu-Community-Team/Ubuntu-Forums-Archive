---
title: "connecting linux to a windows network"
date: 2006-06-16
forum: General Help
---

### Post by maniacmusician on 2006-06-16
that's what I want to do, but i'm not really sure where to even begin. I don't think samba would suit my needs, because thats for making my linux computer a servre right? so that other windows comptuers can access services through it? 

And I don't really want remote desktop either. Just want to to set it up so that this computer (which i have Xubuntu on) can access my windows computers over the network just like windows computers access each other over a LAN. basically, i'm just looking to stream music over the network (as all my music is on my other computers) and be able to copy files, etc, without using external media. 

i'd appreciate any suggestions
thanks.

---

### Post by math on 2006-06-16
With Gnome this works out of the box. There is no need to set up anything. Places -> Network server -> Windows network.
But with xfce i dont know where to look for the windows network.

---

### Post by mlind on 2006-06-16
I reckon samba is the easiest way to go, so do like math said.

---

### Post by kscelt on 2006-06-16
I just did this recently - I just had to go to Shared Folders under the Administration Menu, and create my share in Ubuntu , and do do the equivalent in the Windows machine - worked fine with samba installed. Samba can be used to create a server as you describe, but also it is great for your purpose and mine - no muss, no fuss.

---

### Post by maniacmusician on 2006-06-16
I did as you suggested and installed samba, and set my ubuntu share in Shared Folders. I dont think i'd really have to change anything in my windows machine, as its already on the network and sharing both of its drives. now...how do i access my windows machine from xubuntu?

edit; also, when i try to access this machine from my win-xp computer, it recognizes this computer and everything, prompts me for the username and password. I enter the username that i use and the password, but it just believes that its invalid, because it just brings the prompt back up again.

---

### Post by math on 2006-06-16
according to the xfce website, xffm should have a samba network browser. so try this an you will see your winxp computer there.

---

### Post by nzruss on 2006-06-16
[QUOTE=maniacmusician]when i try to access this machine from my win-xp computer, it recognizes this computer and everything, prompts me for the username and password. I enter the username that i use and the password, but it just believes that its invalid, because it just brings the prompt back up again.[/QUOTE]

I have the same problem. Do I have to create a user (i.e the windows machine name) on the samba server, or is there a samba setting I can change (to allow all?). 

I'm behind a NAT router, so am I safe from the internet browsing my home network? ( I think I am, but am interested in any comments)

---

### Post by math on 2006-06-16
Look here [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

---

### Post by uteck on 2006-06-16
You need to set up a samba user also.  Use 'smbpasswd' to set up the user and password.  I

---

### Post by maniacmusician on 2006-06-16
[QUOTE=math]according to the xfce website, xffm should have a samba network browser. so try this an you will see your winxp computer there.[/QUOTE]

I don't understand...what am i supposed to try? how do i use xffm/the samba network browser?

---

### Post by maniacmusician on 2006-06-16
Nevermind; downloaded and installed xffm. I can see the xp machine now :) but i still can't see this computer from the xp machine

what would be the best way to create a playlist that could access music from the xp machine? I tried using Xfmedia to do it, but it loaded files that weren't music, such as pictures, and I wanted just music.

Also, is there an above-par, really good music/media player for xubuntu?

---

### Post by maniacmusician on 2006-06-16
[bump]

does anyone have  suggestions?

---

### Post by MJRehrig on 2006-06-16
[QUOTE=math]according to the xfce website, xffm should have a samba network browser. so try this an you will see your winxp computer there.[/QUOTE]

the default window manager for Xubuntu is thunar, not xffm, so it will need to be installed to be able to do that.

I would suggest doing what uteck said to do: use *smbpasswd* to create a user so that you can log into it from the win xp machine. 

If you are looking for a good media player that can handle network drives... I would use Rhythmbox.  It is very good, and I would consider it a good iTunes replacement (although it still isn't quite as good as iTunes)

---

### Post by CameronCalver on 2006-06-16
r u trying to share a folder from linux to windows or share from windows to linux

---

### Post by nzruss on 2006-06-16
[QUOTE=CameronCalver]r u trying to share a folder from linux to windows or share from windows to linux[/QUOTE]


Both. Id like to share folders (music) on my XP machine with my Dapper laptop, 

And access files Breezy machine from XP. 

(I also want share the printer that is connected to the XP machine, but will be happy with files at this point.. )

---

### Post by maniacmusician on 2006-06-16
I'm trying to do the same thing. As of right now, I'm able to see my XP machine from my xubuntu machine. I manually mounted it in fstab using the info at the link that someone posted in this thread earlier. But I still havn't gotten my xp machine to be able to see this computer. 

Well, technically speaking, it can *see* it, but when I type in the username and password i'm using, it doesn't work. I already used smbpasswd, did nothing for me...

---

### Post by bforbes on 2006-06-16
[QUOTE=maniacmusician]I'm trying to do the same thing. As of right now, I'm able to see my XP machine from my xubuntu machine. I manually mounted it in fstab using the info at the link that someone posted in this thread earlier. But I still havn't gotten my xp machine to be able to see this computer. 

Well, technically speaking, it can *see* it, but when I type in the username and password i'm using, it doesn't work. I already used smbpasswd, did nothing for me...[/QUOTE]

Can you do it from the Dapper box? Where 'sharename' is the name of the share you want, and 'username' is the username you set up with smbpasswd:
```

smbclient //localhost/sharename -Uusername

```
Then enter the password you set using smbpasswd. Note that 'username' also has to be a valid linux user on your box as well.

EDIT: You also have to be logged in to the terminal as the user 'username' in order to execute the above command.

---

### Post by maniacmusician on 2006-06-16
I tried what you said, that doesn't work either. Here's how it went:
```

maniacmusician@MusicStation:~$ smbclient //MusicStation/maniacmusician -maniacmusician
Unrecognised protocol level aniacmusician
Password:
session setup failed: NT_STATUS_LOGON_FAILURE
maniacmusician@MusicStation:~$ 

```

could it be because my username and sharename are the same?

edit: also, 
[QUOTE=MJRehrig]the default window manager for Xubuntu is thunar, not xffm, so it will need to be installed to be able to do that.
[/QUOTE]

what do you mean? I have thunar and xffm both installed. The problem is that when i use any function of xffm, such as fstab mount, find utility, etc, it starts up xffm-deskview which changes my desktop. I dont want that because it is a pain to have to manually kill xffm-deskview each time. Is there any way i can get it to not start but still use fstab mount manager?

---

### Post by bforbes on 2006-06-17
It should be:
```

smbclient //MusicStation/maniacmusician -Umaniacmusician

```

---

### Post by maniacmusician on 2006-06-17
```

maniacmusician@MusicStation:~$ smbclient //MusicStation/maniacmusician -Umaniacmusician
Password:
session setup failed: NT_STATUS_LOGON_FAILURE
maniacmusician@MusicStation:~$

```
still doesn't work. 

Interestingly enough [i did this by accident]:
```

maniacmusician@MusicStation:~$ smbclient //MusicStation/maniacmusician -maniacmusician
Unrecognised protocol level aniacmusician
Password:
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]
smb: \>

```

If you'll notice, it's without the U, and for the password, I didn't type anything; just hit enter. Does this mean that if I go onto my xp box, fill in nothing for username, nothing for password, i'll be able to get in as "anonymous"? I'll go try it...

edit: as expected, it does not work. I'm going to bed...i hope someone has come up with something by tomorrow morning...

---

### Post by bforbes on 2006-06-17
Post the [maniacmusician] section of /etc/samba/smb.conf, maybe something's going on there. Also, check that the port is open. Get nmap and do as root:
```

nmap -sS localhost

```

---

### Post by maniacmusician on 2006-06-17
```

[maniacmusician]
path = /home/maniacmusician
available = yes
browseable = yes
public = yes
writable = yes

```

nmap: 
```

maniacmusician@MusicStation:~$ sudo nmap -sS localhost

Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-06-17 12:58 EDT
Interesting ports on localhost (127.0.0.1):
(The 1671 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.336 seconds

```

---

### Post by bforbes on 2006-06-17
Port 139 is open, that's good. Smb.conf seems fine, but try my settings just in case:
```

[shared]
        comment = SharedStuff
        path = /home/bforbes/shared
        read only = Yes
        case sensitive = no
        guest ok = yes
        msdfs proxy = no
        force user = bforbes

```

Some of those things probably aren't necessary, but try it and then remove unwanted settings one by one. Remember, you have to kill smbd and restart it when you change smb.conf.

---

### Post by maniacmusician on 2006-06-17
It won't let me kill smbd from xfce task manager (it says "Couldn't KILL the task with ID 4475")...and there's two instances of it running. when i type in smbd into terminall, it says "aborted" but the tasks remain in xfce. I also rebooted, but no effect...i still can't log into this machine from my xp box.

---

### Post by bforbes on 2006-06-18
Type
```

sudo killall smbd
sudo smbd

```
That reboots samba.

---

### Post by Abhi Kalyan on 2006-10-20
hi, just trying to figure out all this stuff, cause am facing with the smae problem.
Any idea on how to use
Places
Connect to server?
hope this might helps us all!

---

### Post by Abhi Kalyan on 2006-10-24
Hi!maniacmusician
something happened, 
Am able to connect to my share by using the IP address after installing 
linneighbourhood
Search for smb in synaptic and you get this.
once there install this with dependencies and then 
use the IP of the system to whihc you want to connect.
It worked for me though,
Could you please help if it works for you too?
Thank you

---

### Post by maniacmusician on 2006-10-24
sorry, I don't use xfce anymore so I dont have this problem. I've switched to KDE, and with that, I just installed samba, and used Konqueror to browse my windows shares; it just worked.

---

### Post by tronica on 2006-10-24
for anyone who cares, if you just use the built in network browser it works but doesn't let you play movies, music from that network computer. so you need to mount that share on that computer. very easy

first open the terminal, and type

> cd /mnt

> sudo mkdir Share

> sudo chmod 777 Share

> sudo mount -t cifs //ipaddressofshare/sharename /mnt/Share -o user=usernameofthatcomputer,pass=passwordofshare

then just browse to /mnt/Share, there you go, hope it helps someone.

---

### Post by Abhi Kalyan on 2006-10-25
Tronica- Thank you a tonne,
It works like wild,
This did help not one but - 150 users!!!
Cheers,
Thank you Once again
Sincerely
Abhi Kalyan

---

