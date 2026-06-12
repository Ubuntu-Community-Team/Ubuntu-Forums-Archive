---
title: "Remote X session"
date: 2006-06-07
forum: General Help
---

### Post by randysparks on 2006-06-07
Hi

I've got an office PC running Ubuntu, and a notebook running Ubuntu. Both 6.06. 

I'm working out in the garden during nice weather on the notebook. I've been running a remote X session to the desktop PC, where my files and Evolution mail is stored, but it's slow.

I do this by booting the desktop, going outside with the notebook, and then running xinit on the notebook. Then I ssh into the office computer with the -X flag and run gnome-session. This way I get the desktop. 

I've also tried using XDMCP (ie on the notebook typing "X -query IP_address" from the command prompt) but that's slow too. In fact, it's even slower. 

VNC will probably be very slow but I haven't tried it. 

Anybody got any other ideas for quick remote X sessions?

---

### Post by ifokkema on 2006-06-07
[QUOTE=randysparks]Hi

I've got an office PC running Ubuntu, and a notebook running Ubuntu. Both 6.06. 

I'm working out in the garden during nice weather on the notebook. I've been running a remote X session to the desktop PC, where my files and Evolution mail is stored, but it's slow.

I do this by booting the desktop, going outside with the notebook, and then running xinit on the notebook. Then I ssh into the office computer with the -X flag and run gnome-session. This way I get the desktop. 

I've also tried using XDMCP (ie on the notebook typing "X -query IP_address" from the command prompt) but that's slow too. In fact, it's even slower. 

VNC will probably be very slow but I haven't tried it. 

Anybody got any other ideas for quick remote X sessions?[/QUOTE]


Did you check if it's your bandwith or your CPU which is the cause of the sluggish session? My guess is the network. IMHO, (Tight)VNC might work better, especially if you set down the colors to 16 bit max and maybe reduce the screen resolution.

---

### Post by randysparks on 2006-06-08
I wonder if there's a third way, maybe making a network share of the /home folder on the desktop and mounting the relevant home directory on the notebook. Then configuring Ubuntu on the notebook to accept the new directory as that of a user on the system.

I've no idea how fast NFS or Samba are in terms of file transfer but I've got a feeling this plan will be faster than a remote X session, especially considering that most of the actual software (GNOME, OO.org) will be running from the notebook.

---

### Post by ifokkema on 2006-06-08
[QUOTE=randysparks]I wonder if there's a third way, maybe making a network share of the /home folder on the desktop and mounting the relevant home directory on the notebook. Then configuring Ubuntu on the notebook to accept the new directory as that of a user on the system.

I've no idea how fast NFS or Samba are in terms of file transfer but I've got a feeling this plan will be faster than a remote X session, especially considering that most of the actual software (GNOME, OO.org) will be running from the notebook.[/QUOTE]

Gee, never thought of that. Sounds like a real bright idea. Since only the local user settings need to be transferred, bandwidth usage is minimized. You can mount the whole /home folder through NFS. As far as I know, it's OK if your /home folder is not empty (currently containing your user data), the contents will just temporary be unavailable if the network share is mounted.

---

### Post by Jott on 2006-06-08
I agree that your best bet is just to mount the remote files onto the notebook (that's what I did at home), but if you really want a quick remote session, try freenx.  The website is [www.nomachine.com](www.nomachine.com), instructions are pretty simple, and there's quite a bit of info on the forums about it.

good luck!

---

### Post by qrees on 2006-06-08
[QUOTE=ifokkema]Gee, never thought of that. Sounds like a real bright idea. Since only the local user settings need to be transferred, bandwidth usage is minimized. You can mount the whole /home folder through NFS. As far as I know, it's OK if your /home folder is not empty (currently containing your user data), the contents will just temporary be unavailable if the network share is mounted.[/QUOTE]
This is how it's made at my University and this is great solution. There is one STRONG server and all PC's connect to it, and mount /home folder. Sometimes there are some dalays  when saving files, but this is not very big problem :)

---

### Post by randysparks on 2006-06-09
I've got an NFS mount on the go at the moment and it's definitely the quickest way to do this. :p

---

### Post by Getwild2 on 2006-06-09
[QUOTE=Jott]I agree that your best bet is just to mount the remote files onto the notebook (that's what I did at home), but if you really want a quick remote session, try freenx.  The website is [www.nomachine.com](www.nomachine.com), instructions are pretty simple, and there's quite a bit of info on the forums about it.

good luck![/QUOTE]
I second this.  I am using FreeNX right now to connect to my desktop at home, it's very smooth and fast, not what you'd expect from a remote session.  I absolutely love it as I am on my desktop machine 6-7 hours a day (off and on) from work and no glitches.  It's over SSH too.  Here are a couple of threads I utilized in getting mine setup:

[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)
[http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx](http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx)

BTW, I have to use WinXP at work, so I'm going from a Windows box to my Dapper box.  I just run the Windows client and FreeNX server.  Good luck!

---

### Post by fergus on 2006-06-09
Don't forget the -C flag with ssh.  It adds compression which helps alot.

---

### Post by Getwild2 on 2006-06-09
[QUOTE=fergus]Don't forget the -C flag with ssh.  It adds compression which helps alot.[/QUOTE]
For FreeNX?  If so, where would I add this and how?  I'm always up for more speed!  \\:D/

---

### Post by KnottyMan on 2006-06-09
"the -C flag with ssh"

'ssh -C hostname' enables compression for the ssh connection.

---

### Post by Getwild2 on 2006-06-09
[QUOTE=KnottyMan]"the -C flag with ssh"

'ssh -C hostname' enables compression for the ssh connection.[/QUOTE]
Man I'm so sorry to keep bugging you but I'm brand new to Linux.  Which file would I add this line to?  Thanks!!

---

### Post by Lunar_Lamp on 2006-06-09
I believe he means that when you start an SSH session, instead of typing:

```
ssh *hostname*
```,

you can type:

```
ssh -C *hostname*
```

:)

---

### Post by Getwild2 on 2006-06-09
[QUOTE=Lunar_Lamp]I believe he means that when you start an SSH session, instead of typing:

```
ssh *hostname*
```,

you can type:

```
ssh -C *hostname*
```

:)[/QUOTE]
Oh I see.  Mine starts automatically, I'll just have to figure out where the command is issued from.  Thanks!!  \\:D/

---

### Post by fergus on 2006-06-09
You don't need -C with FreeNX, the nxclient and NX protocol have its own compression.  I was just pointing out, if you used 'ssh -X server' to kick a display back, add the -C because it will only speed things up.

---

