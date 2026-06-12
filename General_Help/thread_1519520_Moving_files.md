---
title: "Moving files"
date: 2010-06-28
forum: General Help
---

### Post by =ChAoS= on 2010-06-28
Hi guys firstly i would like to say great forum and i will be reading a lot from past threads.
 
Secondly i am a complete linux noob and thats what as brought me here :p
 
Myself and a mate recently rented a dedicated server to run various things, shoutcast, teamspeak, and a seedbox to name but a few. I had Ubuntu 8.04 LTS installed as the whole server thing is also new to me so my thinking was that a desktop environment would be better suited while i learned the ropes.
 
I have gained access to it using NX (no machine) as well as putty from my windows 7 desktop. 
 
I'm in the process of looking around the web to try to get certain things running before i get more involved with linux (who knows i might replace windows on my desktop someday) and so i hope someone can point me in the right direction. 
 
As for installing the things i want theres loads of tutorials on various sites related to the particular programs so not really any problems there but the first thing i would like to acheive is a simple file swap from my desktop to the remote server.
 
Could someone please point me to the correct solution or a tutorial explaining how this is achieved or what is needed?
 
Also when i go to Computer -> File system and click properties its showing 3.5 gig installed and 15 gig available but System Monitor shows 888.5 GiB so do i need to format more drives/partitions or create folders as it's a terabyte drive?
 
Sorry for the really noob questions and please bear in mind all answers need to be in "numpty language" :lolflag:
 
Thanks =ChAos=

---

### Post by lukeiamyourfather on 2010-06-28
What operating system are you using on your desktop? If its Linux then use scp to copy files between your desktop and the server. Otherwise setting up an FTP server is probably the best way to transfer files between the desktop and server. See the link below for partitioning a disk.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

If you search there's plenty more information about formatting and partitioning disks. Cheers!

---

### Post by pricetech on 2010-06-28
There's an NX Client for Linux as well from NoMachine.

I don't recommend FTP because of its inherent insecurity. Use SCP instead.  From your Ubuntu box you can simply click Places - Connect to Server, choose SSH as the protocol, and type in the IP of your remote server to establish a secure connection.

WinSCP works well for me under windows to accomplish the same connection.

---

### Post by lukeiamyourfather on 2010-06-28
> **pricetech said:**
> There's an NX Client for Linux as well from NoMachine.

I don't recommend FTP because of its inherent insecurity. Use SCP instead.  From your Ubuntu box you can simply click Places - Connect to Server, choose SSH as the protocol, and type in the IP of your remote server to establish a secure connection.

WinSCP works well for me under windows to accomplish the same connection.

Good call, or use SFTP to keep it secure. Cheers!

---

