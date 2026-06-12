---
title: "Remotely move files"
date: 2012-08-25
forum: General Help
---

### Post by bcdudley on 2012-08-25
I am looking for some type of interface (preferably web server) that will allow me to remotely move files from one predefined directory to a list of several other predefined directories within my network. Renaming the files while moving will be a huge bonus. The files are very large (from 1mb to 20Gb) so some type of queuing will almost be required. The originating server will be an Ubuntu server and the destination will be a Windows server. I need to be able to provide some type of security as I will want this available on a public web server. 

Lastly, I would like something simple to understand so that my significant other can use it without needing to take computer classes.

Any suggestions?

Thank you.

---

### Post by TheFu on 2012-08-25
rsync over ssh. Be certain you setup ssh-keys for the trust between the different systems.    **man rsync **to learn more.

You can use a CGI web interface to launch your script(s) on demand, but I can't recommend allowing anyone to use the web interface with dynamic inputs. Too much of a security risk. Setting up a secure web interface for this is not easy. Heck, the people who make web interfaces to manage system have security issues, what chance to you and I have to do it correctly?

Or you can schedule the copies to happen automatically on any schedule you want via cron.  **man crontab** to learn more.

If you are dealing with media files, then** rsync is fine.**  If you are dealing with virtual machine disk images, then there are better methods that are much more efficient - Hint: you won't be sending the entire huge file every time.  Setup a good backup method.

The easiest way to prevent your SO from having issues is to completely automate this stuff.  It isn't hard.  Learn a little bash scripting.  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) is the best reference I know.

---

### Post by andymurn on 2012-08-25
rsync is fine for backups and scheduled stuff. If you are moving pictures, movies, documents, etc you could try a WebDAV server with Apache and get a web interface client to easily access it. There are lots of web clients to choose from and you can even get desktop clients. For easily transferring files within your network I suggest running SAMBA as well.

---

### Post by bcdudley on 2012-08-25
Thanks for the suggestions. I would love to automate this if I thought it would be possible. The type of files that I would be moving will vary and include various different types of media. It may include entire folders or single files. Depending on what it is will determine which location it would go to. I like to keep my media organized and I think that would be very difficult to do with an automated script.

I think the WebDav stuff may be the way to go. I found AjaXplorer and I am looking at a couple others.

I had also thought about trying to write my own program, but I really don't have enough experience. I am decent with vb.net, but that apparently does not translate to web skills, lol.

Thank you.

---

### Post by TheFu on 2012-08-26
Things that work are not always a good idea. WebDAV has been plagued with security problems across all platforms.  I'm just sayin'.  I deployed WebDAV a few yrs ago. It was hacked. Never again.

I've automated transfers for TV and movie recordings, so I know this is possible, but only you know your needs.  The main thing is to get the files moved to the correct file system. That takes time.  Moving the files into the correct folder structure after that is just 1 change to a file pointer - nearly instantaneous.

vb.net doesn't translate anywhere else.  Bash scripting can be as easy or complex as you like.  It is basically like PowerShell, but without all the really-long-names-for-all-the-commands.  To me, PowerShell looks like bash.

Have you considered using NFS to mount storage from your different machines locally? Then the relocation of files over the network just looks like a local file move/copy.  

There are tools to handle media for XBMC from BT and usenet - sickbeard comes to mind.  I only have recordings - downloading media from BT and usenet is illegal where I live. Recording TV and movies is perfectly legal here, so I have built up a fairly large collection off premium cable channels over the years.

If you can describe the media and the programs you are trying to organize it to be used in, perhaps someone can suggest an already created tool?  Most file reorganization needs have been programmed.   Doing a search on freecode.com can't hurt. That wheel has probably already been invented.

---

### Post by SeijiSensei on 2012-08-26
If you just want to provide a graphical program to manage a remote filesystem, I'd tunnel X over SSH and launch the remote's copy of Nautilus or Dolphin:

```

$ ssh -X root@remote
# dolphin &

```

Now you'll see dolphin (or nautilus if you use GNOME) appear on your local machine.  There are [other file managers]("http://www.linuxlinks.com/article/20081224191928555/FileManagers.html") available for Linux.  I've used [Krusader]("http://www.linuxlinks.com/article/20070923091440325/Krusader.html") from time to time as well.

---

### Post by Lars Noodén on 2012-08-26
Because you're working with pre-defined directories, another way, in addition to the ssh -X method mentioned by SeijiSensei, would be to use [SSHFS](https://help.ubuntu.com/community/SSHFS).  Then you could use dolphin or nautilus locally.  SSHFS is easy to set up and allows the remote directories and their contents to be accessible as if they were local.

---

### Post by TheFu on 2012-08-26
Over a WAN, using **ssh -X** is painful. Using something like VNC (inside an ssh or VPN tunnel) or NX would be better if a GUI is needed.

SSHFS will be painful if the remote directories are on the WAN, but if they are both local, then it is an easy method.  OTOH, if they are local, just setup NFS between all the machines.  NFS is much more efficient than any other network file system, IMHO.  It should never be used over a WAN, however.

---

### Post by SeijiSensei on 2012-08-26
> **TheFu said:**
> Over a WAN, using **ssh -X** is painful. Using something like VNC (inside an ssh or VPN tunnel) or NX would be better if a GUI is needed.

I haven't found that to be the case.  YMMV.  If I run a remote file manager over X, only that application's display will be sent down the wire.  Using a remote desktop client sends the entire desktop.

> SSHFS will be painful if the remote directories are on the WAN, but if they are both local, then it is an easy method.  OTOH, if they are local, just setup NFS between all the machines.  NFS is much more efficient than any other network file system, IMHO.  It should never be used over a WAN, however.

If I have two remote shares mounted with SSHFS or NFS and want to copy a file from one to the other, the file will first come down to my client from the source share then be copied up to the target share.  That's much slower than running a file manager on the remote server and copying files directly on the remote machine.  That is the equivalent of using "cp" in a shell on the remote.

---

