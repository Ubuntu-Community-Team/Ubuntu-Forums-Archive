---
title: "Can't browse MSHOME ( Windows shares ) !"
date: 2009-07-08
forum: General Help
---

### Post by credobyte on 2009-07-08
[COLOR=DimGray]Samba configuration: [http://linosun.id.lv/files/smb.conf](http://linosun.id.lv/files/smb.conf) ( updated & working )[/COLOR]

```
dainis@credobyte:~$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                           [ OK ] 
dainis@credobyte:~$ 
```The problem is that .. I can't access MSHOME and Windows machine can't access my Samba shares ( tough, sees shared folder ).
Any ideas ? :roll:

---

### Post by swerdna on 2009-07-08
> **credobyte said:**
> Samba configuration: [http://linosun.id.lv/files/smb.conf](http://linosun.id.lv/files/smb.conf)

```
dainis@credobyte:~$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                           [ OK ] 
dainis@credobyte:~$ 
```The problem is that .. I can't access MSHOME and Windows machine can't access my Samba shares ( tough, sees shared folder ).
Any ideas ? :roll:

Check you've allowed samba "folder sharing service" in System --> Administrtaion --> Services Settings.

Check MSHOME is in the windows box (probably is).
.
Add a Linux user dainis to the Linux Samba user database and supply those creds from the windows box when asked.

These are better to match winxphome operating system:
>     name resolve order = bcast host wins lmhosts

    wins support = no


FFI see here: [Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by credobyte on 2009-07-08
Hm, weird ! I still can't access them .. tried various configurations and everything is up and running ( yesterday it worked like a charm ) :(

---

### Post by Jebtrix on 2009-07-08
That is weird, you haven't installed Firestarter by any chance? Dumb question but ya neva know. That will cause that issue with defaults.

---

### Post by credobyte on 2009-07-08
> **Jebtrix said:**
> That is weird, you haven't installed Firestarter by any chance? Dumb question but ya neva know. That will cause that issue with defaults.

No, I haven't ! The best part is that, when I try to browse Samba from my Winxp box, it says "Windows 2000 server" :o What the hell that means ? How Ubuntu/Samba can be threated as Win2k ?

---

### Post by t4thfavor on 2009-07-08
Its just telling you it thinks the Ubuntu server is a Win2K server because thats probably what the default is in the config file, or that is the version of windows samba they were "copying" when the developers wrote the ubuntu samba daemon.

Its a bit of a PITA, but if you type "smbpasswd" on the commandline, you may be able to set the password, and then login remotely. I know my samba server didn't work all that well until I found that command.

---

### Post by Arup on 2009-07-08
Have you tried typing the location in nautilus, open up nautilus and click on go>location and type smb://19x.xxx.xx.xx and see if it works, the network tab has never worked for me.

---

### Post by credobyte on 2009-07-08
> **Arup said:**
> Have you tried typing the location in nautilus, open up nautilus and click on go>location and type smb://19x.xxx.xx.xx and see if it works, the network tab has never worked for me.

Yes, I've tried it ! Still gives only a welcome message ( "unable to mount windows share" ).

---

### Post by swerdna on 2009-07-08
Can you repair the link to your smb.conf -- I get this message:> Failed to Connect. Firefox can't establish a connection to the server at linosun.id.lv.

---

### Post by credobyte on 2009-07-08
> **swerdna said:**
> Can you repair the link to your smb.conf -- I get this message:
  
Somebody left me without an electricity ( link is up and running ) :roll: Anyway, I removed my "custom" configuration file and replaced with what samba gives by default - works like a charm ( tough, I'm not really sure why I can access WinXP on MSHOME while Samba is on WORKGROUP ).

---

### Post by swerdna on 2009-07-09
> **credobyte said:**
> Somebody left me without an electricity ( link is up and running ) :roll: Anyway, I removed my "custom" configuration file and replaced with what samba gives by default - works like a charm ( tough, I'm not really sure why I can access WinXP on MSHOME while Samba is on WORKGROUP ).

That's becasue the default for smb.conf names the workgroup as WORKGROUP. Have a look, you'll see it. edit the file so it says: ```
workgroup = MSHOME
```

FFI on that and more tweaks should you need them --> [How to Edit, Backup and Restore Samba's Configuration File]("http://ubuntu.swerdna.org/ubulanprimer.html#smb.conf")

---

### Post by credobyte on 2009-07-09
> **swerdna said:**
> That's becasue the default for smb.conf names the workgroup as WORKGROUP. Have a look, you'll see it. edit the file so it says: ```
workgroup = MSHOME
```FFI on that and more tweaks should you need them -- [on this link]("http://ubuntu.swerdna.org/ubulanprimer.html#smb.conf")

Ok, thnx for your help ( bw, website looks pretty solid :) ).

---

