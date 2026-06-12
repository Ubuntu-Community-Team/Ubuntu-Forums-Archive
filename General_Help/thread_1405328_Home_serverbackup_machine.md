---
title: "Home server/backup machine"
date: 2010-02-12
forum: General Help
---

### Post by ChrisML123 on 2010-02-12
Hey guys. Would really appreciate some help here. My situation is: I have built a home file server/backup machine. Its an Atom dual processor, with 2gb of ram, and a 1.5tb hard disk.

My needs are:
[LIST]
[*]Ability to do automated backups of laptops and pcs in the house to the server.
[*]Ability to do on demand (as in log into web interface or something and say "backup now") backups
[*]Ability to access backed up files on server: so files stored as network accessible files, rather than one massive encrypted blob.
[*]Ability to stream media files off the pc.
[*]Ability to access files through ftp, when away from the LAN
[/LIST]

That's pretty much it. I don't need multiple full backups of each machine, just one current one.

Thoughts appreciated. At the moment I have a blank pc, and a copy of ubuntu server on a dvd. I need your recommendations to get further.

Bless,
[Chris Lowry]("http://allaboutchris.co.uk")

---

### Post by jken146 on 2010-02-12
Read the server guide: [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)
See in particular the sections on remote administration, security, fileservers, backups (the backup section is more concerned with making things like the 'blobs' you mentioned, but it does contain instructions on using cron to automate things).

See also: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

As for streaming, the best solution will depend on the client devices you have. Using FTP or Samba on your clients to accesss the files you want might be simplest. Or, you might want to have a constant stream of music coming out of your server, so you'd look at mpd perhaps. It depends on what exactly you want to achieve.

Have a look at the docs (the server guide and [https://help.ubuntu.com](https://help.ubuntu.com)), use your google-fu and ask for help when you run into specific problems. Have fun!

---

### Post by lukeiamyourfather on 2010-02-12
> **ChrisML123 said:**
> 
[LIST]
[*]Ability to do automated backups of laptops and pcs in the house to the server.
[*]Ability to do on demand (as in log into web interface or something and say "backup now") backups
[*]Ability to access backed up files on server: so files stored as network accessible files, rather than one massive encrypted blob.
[*]Ability to stream media files off the pc.
[*]Ability to access files through ftp, when away from the LAN
[/LIST]


All of this is possible. Are you comfortable working in the terminal or is this your first experience with Linux? Are the other hosts Linux or another operating system?

---

### Post by ChrisML123 on 2010-02-13
Other hosts are windows machines.

I am not mega comfortable using the terminal, and have just decided to add xfce to my ubuntu-server configuration.

Have tried to install backuppc, and got some errors, that I couldn't work round.

Now trying out rsnapshot.

However, I really think backuppc was exactly what I wanted, so if you wanted to help me through that I'd appreciate it!

---

### Post by Girya on 2010-02-13
> **ChrisML123 said:**
> Other hosts are windows machines.

I am not mega comfortable using the terminal, and have just decided to add xfce to my ubuntu-server configuration.

Have tried to install backuppc, and got some errors, that I couldn't work round.

Now trying out rsnapshot.

However, I really think backuppc was exactly what I wanted, so if you wanted to help me through that I'd appreciate it!

Backuppc is what I use. post the errors and I'll  try to help you. What tutorial did you use?

Were you able to install backuppc and got errors when you backedup or was it problems with installation?

---

### Post by pirateghost on 2010-02-13
what problems are you having with installing backuppc?

do note that your last 3 criteria items are not actually functionality of backuppc, except that you can:
access the backed up files via the backuppc webpage and download any of those files you want or even multiples.  That kind of takes care of items 3 and 5
item 4 is not doable with backuppc, but why do you need to stream media files that are backed up?  backups are not meant to be used as live files.  they are backups

another note: get DeltaCopy for your windows machines to do backups of them to backuppc.  it rocks

---

### Post by Roasted on 2010-02-13
I'm in a similar situation, but kind of reversed.

You seem to work in a Windows household with one Ubuntu server acting as a server.

I'm in a Windows household with my personal desktop being Ubuntu and my personal desktop acting as the backup server.

What I did is I simply installed Samba and shared out 1 directory per user, and applied permissions accordingly so only that user can access their folder. Then I set up Syncback SE, a free windows sync program, to link up to their share. Then I set up a scheduler with that program, which automatically syncs their stuff to my computer every morning at 3 am.

---

### Post by Mykle87 on 2010-02-13
I got an Ubuntu linux server at my college house and I have my parent's (windows xp), my sister (mac os x), and my girlfriend (mac os x) backup to it over the Internet. I wasn't too comfortable with the command-line at first but I have gotten so much more comfortable especially after following step-by-step guides. For Windows, I recommend using [cwrsync]("http://www.itefix.no/i2/node/10650"). It is a command-line tool that allows you to use rsync, which is a command-line, unix backup utility built right into Ubuntu Server to backup files easily and can be scheduled automatically. Once you setup a backup script with cwrsync, you can use windows task scheduler to backup however often you want. Good luck with the backup server.

---

### Post by Mykle87 on 2010-02-13
I might as well try and help you out with these other bullet points too...

> [LIST]
[*]Ability to stream media files off the pc.
[/LIST]

If you are using another computer, as long as you have Samba installed on Ubuntu server, you can easily share whatever folder has your media and point your other windows machines to it. Here is a really [simple tutorial]("http://www.debuntu.org/guest-file-sharing-with-samba") on how to setup samba. If you are streaming to an xbox or ps3, you can use [ushare]("http://ubuntuforums.org/showthread.php?t=632428"). It works really well on both xbox and ps3 (I just hate that xbox and ps3 don't stream mkv).

> [LIST]
[*]Ability to access files through ftp, when away from the LAN
[/LIST]

If you want to access your files over the Internet, I would recommend using SFTP, which is ftp over ssh. If you have ssh installed (which it should be by default?), then just open port 22 (by default) and connect from anywhere you have Internet. I use this fairly often and it gives me piece of mind knowing it is encrypted.

---

### Post by pirateghost on 2010-02-13
> **Mykle87 said:**
> I got an Ubuntu linux server at my college house and I have my parent's (windows xp), my sister (mac os x), and my girlfriend (mac os x) backup to it over the Internet. I wasn't too comfortable with the command-line at first but I have gotten so much more comfortable especially after following step-by-step guides. For Windows, I recommend using [cwrsync]("http://www.itefix.no/i2/node/10650"). It is a command-line tool that allows you to use rsync, which is a command-line, unix backup utility built right into Ubuntu Server to backup files easily and can be scheduled automatically. Once you setup a backup script with cwrsync, you can use windows task scheduler to backup however often you want. Good luck with the backup server.
why use a commandline only tool in windows when there is a perfectly good GUI solution called DeltaCopy?

---

### Post by jken146 on 2010-02-13
> **Mykle87 said:**
> If you want to access your files over the Internet, I would recommend using SFTP, which is ftp over ssh. If you have ssh installed (which it should be by default?), then just open port 22 (by default) and connect from anywhere you have Internet. I use this fairly often and it gives me piece of mind knowing it is encrypted.
You'll need to install **openssh-server**

---

### Post by Roasted on 2010-02-13
> **pirateghost said:**
> why use a commandline only tool in windows when there is a perfectly good GUI solution called DeltaCopy?

+1

And SyncToy
And SyncBack SE
And a dozen more I'm sure...

---

### Post by pirateghost on 2010-02-13
> **Roasted said:**
> +1

And SyncToy
And SyncBack SE
And a dozen more I'm sure...

DeltaCopy uses rsync and works great to backup to a backuppc server, which was the point i was trying to make.  But yeah, there are about 5 million apps in windows to perform backups/file synchronizations with

---

### Post by van_Zeller on 2010-02-13
Hello,

I'm right now doing the exact same thing as the original poster.

Here's what I've done so far:
1. Got an old PC
2. installed Ubuntu, (normal desktop edition), openssh server, vsftpd, samba, inadyn, xbmc.
3. Set up a dyndns account. Set up port forwarding on ports 22 and 21.
4. Shared the home folder over smb.

Right now I can:
1. Access the server over ssh (Yay!)

But right now I can't: 
a. access the server over ftp
b. Set up my computer to make backups over the local network

I want to use unison or grsync. However on these services, I don't know how to set up the destination folder so that it points to my home server, via the home network. Can anybody help me with this?

Also, I can't seem to be able to log in to the home server over the internet, using ftp. It says "host not found", but if I ping my dyndns, everything is fine...Help?

---

### Post by Mykle87 on 2010-02-13
> **pirateghost said:**
> why use a commandline only tool in windows when there is a perfectly good GUI solution called DeltaCopy?

I didn't know about DeltaCopy. Thanks for the recommendation :) I will look into it. I have read so many great reviews on rsync here in the forums that I wanted to give it a shot for myself. Plus, it was dead simple to setup on OSX since it is built right in.

---

### Post by pirateghost on 2010-02-13
> **Mykle87 said:**
> I didn't know about DeltaCopy. Thanks for the recommendation :) I will look into it. I have read so many great reviews on rsync here in the forums that I wanted to give it a shot for myself. Plus, it was dead simple to setup on OSX since it is built right in.
DeltaCopy is just a gui wrapped around rsync made for windows.  its extremely easy to setup and use and will run as a service so you dont ever have to worry about it

---

### Post by Mykle87 on 2010-02-13
> **pirateghost said:**
> DeltaCopy is just a gui wrapped around rsync made for windows.  its extremely easy to setup and use and will run as a service so you dont ever have to worry about it

Definitely looks like a neat little tool. I will definitely use it in the future when I need to backup Windows machines to my linux server.

---

### Post by cjhabs on 2010-02-13
For accessing vsftpd do you have 
listen_address &#8212; Specifies the IP address on which vsftpd listens for network connections.
configured - and the default data port is 20 according to the docs. 
ftp_data_port &#8212; Specifies the port used for active data connections when connect_from_port_20 is set to YES.

The default value is 20.

---

### Post by ChrisML123 on 2010-02-13
Ok, so I couldn't get backuppc to run, because it was looking for nmblookup:

```
2010-02-13 20:43:15 $Conf{NmbLookupPath} = '/usr/bin/nmblookup' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

I definitely had samba installed, and yet nmblookup wasn't there. In the end I followed this advice - [http://ubuntuforums.org/showthread.php?t=1228002]("http://ubuntuforums.org/showthread.php?t=1228002") - and created an nmblookup from scratch. 

Now terminal tells me things are happy:

```
boss@boss:~$ sudo /etc/init.d/backuppc start
 * Starting backuppc...                                                  [ OK ]
```

But I'm stuck. How do I access backuppc? Can't seem to get there in a browser, or any other way! 

I appreciate the other options given, but I'm needing something server based, not client, that copes with computers being turned on and off, and has an option for users to log into a web interface and say "backup now", for example just before leaving the house for the office, and needing to be able to access a file off the server later. Obviously happy to try other options if this doesn't work, but help appreciated for getting BackupPC to work first!

Bles,
[Chris Lowry]("http://allaboutchris.co.uk")

---

### Post by meethead on 2010-03-22
Thank you ChrisML123!!! That totally did the trick :) Listen, I'm a complete *nix noob, but I also had the same problem - not being able to access backuppc via browser. I was able to sort it out by using the ip ([https://xxx.xxx.xxx.xxx/backuppc](https://xxx.xxx.xxx.xxx/backuppc)) instead of the server name (backuppc used the name, which I don't have configured correctly, and prepended http:// even though I'm running [https://)](https://)) - could this be it for you as well?

Cheers, HTH!

---

### Post by ChrisML123 on 2010-03-22
In the end, BackupPC couldn't do quite what I needed - I need a store of network accessible files, which BackupPC can't do.

However, I seem to be having luck with rsync at the moment.

Bless,
[Chris]("http://allaboutchris.co.uk")

---

### Post by rgotten on 2010-04-12
> **Roasted said:**
> 
What I did is I simply installed Samba and shared out 1 directory per user, and applied permissions accordingly so only that user can access their folder. .

i have the same setup with SAMBA..how can you apply permissions so only the user cann acces there folders and not everybody

---

