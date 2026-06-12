---
title: "Home Media Server possible with Ubuntu"
date: 2010-05-19
forum: General Help
---

### Post by cooldudeny on 2010-05-19
Hi Everyone, 

I am planning to use my Acer AX 1300 as a media server for my home, since i have like 3 latops and a PC. I think it is time now for me to build a media server to keep everything in one place. 

what i am looking for is a light weight OS along with that i am looking for  file sharing,Media Sharing,Automatic Back up on PC as well as Mac. 

Will ubuntu be able to help me achieve this and if yes then how ? my pc will be stand alone and will run on wifi to connect to the home network. I can not connect it to a monitor all the time. 

Looking forward for some advice on this

---

### Post by NCLI on 2010-05-19
> **cooldudeny said:**
> Hi Everyone, 

I am planning to use my Acer AX 1300 as a media server for my home, since i have like 3 latops and a PC. I think it is time now for me to build a media server to keep everything in one place. 

what i am looking for is a light weight OS along with that i am looking for  file sharing,Media Sharing,Automatic Back up on PC as well as Mac. 

Will ubuntu be able to help me achieve this and if yes then how ? my pc will be stand alone and will run on wifi to connect to the home network. I can not connect it to a monitor all the time. 

Looking forward for some advice on this

1) Use SSH for filesharing
2) I'd use PS3MediaServer for media sharing.
3) rsnapshot for backup.
4) I'd really recommend using a physical connection for the server.

---

### Post by earthpigg on 2010-05-19
+1 to ssh. check out sshfs. 

why 'lightweight'? is this desktop a p4 or something?

---

### Post by philinux on 2010-05-19
Moved to General Help.

---

### Post by mb_webguy on 2010-05-19
"Lightweight" is a relative term...  Ubuntu is certainly lighter than Windows 7/Vista, though. and can be run with no graphical desktop environment, which can further free up system resources.

Files can be shared many ways.  On a local network, folders can be shared just as they can be on Windows.  There are lots of other options, however, such as ftp and ssh (the latter of which is very secure and is capable of a lot more than just file transfers).

There are also several UPnP media servers available, including MediaTomb and PS3 Media Server.  I highly recommend PS3 Media Server (whether your UPnP media player is a PS3 or not) as it has quite a number of nice features that many of the others don't.  If you need a web interface to control the media server, however, go with MediaTomb.  It's quite easy to set up and use, and has all of the basic features you'd expect from a UPnP server, including on-the-fly transcoding.

There are a number of file backup and synchronization tools available including Unison and Grsync, though if you want it to be automated, you can't do much better than a simple script using the rsync command and scheduled with cron.  This does require some small amount of knowledge of using the terminal, but can be done in about three or four commands all together, and once it's set, you can forget about it.

I have a headless (meaning it doesn't have an attached monitor or keyboard) media server running Ubuntu right now, and it's great.  I use ssh and VNC to control it through a remote desktop (which I can do over the internet as well as over my LAN), I use Deluge to download media from the internet and Avidemux and Handbrake to clean it up or convert it if necessary, I share the media on the local network using Samba (i.e. Windows' shared folders), and I stream the media to my PS3 and other UPnP clients using PS3 Media Server.  I was previously using a Windows 7 machine using shared folders, TVersity, and Windows Remote Desktop, but the current setup is much more secure and versatile.

---

### Post by 3rdalbum on 2010-05-19
I have an Atom-based home server, that does similar tasks to yours (except for the backing up). That's plenty of processing power; it's equal in processing power to an **old** P4. Serving files doesn't take up hardly ANY processing power, and your operating system doesn't add much overhead when it's doing virtually nothing.

I use Samba for the file sharing and I have some boxes that plug into my TVs and into the network, that can browse Samba shares and play videos from them. I also have Mediatomb running for my audio files, but I could easily extend it to the videos if I had a PS3.

I'd also advise against using wifi to connect the server to the router and clients. Put the server in the same room as the router and connect it via an Ethernet cable. Nothing sucks more than having to plug a keyboard, mouse and monitor into your server because the wireless has disconnected while serving three movies to different areas of the house, just to unmodprobe the driver and reinsert it and reconnect.

In terms of "Can Ubuntu do xyz as a server", the answer is usually Yes. Ubuntu is a very versatile server platform even if you just stick to the repositories.

---

### Post by NeddyDownUnder on 2010-05-19
I think Ubuntu is great for what you want to do. I just setup a media server for myself at home... I'm relatively new to Ubuntu but with a bit of effort and a lot of Google-ing and searching through the Ubuntu documentation site I have a headless media server running Ubuntu Server Edition. The box I run it on is an old P4 that a friend was going to throw away... 

I have installed on it:

Mediatomb - UPnP server (but I'm going to check out ps3MediaServer after reading the other posts in this thread...)

Firefly (mt-daapd) - for sharing music
  
Deluge - for torrents (with a network folder that I just drop torrents in and then the server downloads them during off-peak time)

SSH - for remote access

Netatalk - Apple file sharing (if you use Windows machines you could install Samba)

Webmin (webmin_1.510_all.deb) - Web based server admin


I also installed acpid so that I could power down my headless server with just the power button...

I'm really happy with my setup and I would highly recommend you setup one for yourself... You may want to just install the desktop edition if your intended server has enough resources to do so and you don't want to setup a 'Command Line' system. 

Good luck and enjoy.

---

### Post by cooldudeny on 2010-05-19
Thank you for so many good replies not i need to ask one more question as of now. i might have more later ;) 

Can i access the server using the web interface from anywhere on the internet ?

---

### Post by cooldudeny on 2010-05-19
> **NCLI said:**
> 1) Use SSH for filesharing
2) I'd use PS3MediaServer for media sharing.
3) rsnapshot for backup.
4) I'd really recommend using a physical connection for the server.

see i will love to use the physical connection for the server but unfortunately the way outlets are setup in my home it is difficult for me to put the server next to the router because of the noise issues. 

Does anyone else exp with using server via wifi ?

---

### Post by NeddyDownUnder on 2010-05-19
> **cooldudeny said:**
> Thank you for so many good replies not i need to ask one more question as of now. i might have more later ;) 

Can i access the server using the web interface from anywhere on the internet ?

Just edited my post and added 'Webmin' to my installed packages, I forgot about it. It makes it a little easier to manage the server, but really I do the vast majority of my server administration via SSH.

As for using a wireless connection for your server... I have never tried using my server via wireless, but I have tried using a few clients wirelessly.  My PS3 would not stream over wireless, I assume this is because the streaming software on the PS3 is not that great. I can stream via a wireless connection to my Mac (150 megabit connection) when the clips I want to stream are Web Optimized. 

In my opinion a wireless connection will probably cause you a few headaches, but if that's what you need to do then give it a go. That's the beauty of Linux, you can usually make things work with enough effort.

Good Luck.

---

### Post by AoDZelda on 2010-05-22
Thanks. This has answered some of my questions that I have had also. I will figure out what I need hardware spec wise, and get back here for some more help.

---

### Post by earthpigg on 2010-05-22
> **cooldudeny said:**
> see i will love to use the physical connection for the server but unfortunately the way outlets are setup in my home it is difficult for me to put the server next to the router because of the noise issues.

get an Atom CPU - those don't even need fans. at least the one in my netbook doesn't. hell, no reason you couldn't get a cheap used netbook off of craigslist, plug an external hard drive into it, and use that as your server.

---

### Post by SFSDCris on 2010-05-24
How do you get around situations in which Ubuntu requires input during the boot process?

I have no keyboard or monitor attached to this media server.

I currently have a situation where if there is a problem, ubuntu stops on boot and asks which system I want to run, 

Secondly, if there is a disk problem, it requires I run a disk check to hit 'y' a bunch of times to approve attempted fixes. 

For a headless, keyboardless media server this is impossible. 

Ideally auto-rebooting after a power failure, auto-attempting to fix disk problems, reporting once ubuntu booted.  Have you done this?

---

