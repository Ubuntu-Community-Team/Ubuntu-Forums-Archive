---
title: "Samba slow on Windows clients, any alternative?"
date: 2011-12-25
forum: General Help
---

### Post by stoneattic on 2011-12-25
I guess this is really a many part question.  I have a small LAN with a Ubuntu file server and 4 client PCs, three running WinXP Pro and one running Win7 Home.  Samba is surprisingly (to me) slow, particularly on the Win7 machine.  It's not hardware related because downloading from Apache is instant on the same files that take 30sec or longer on Samba.  I've spent a lot of time searching and tweaking on both the server and client end but noticed no real improvement.  

I've experimented with NFS, but none of the client OSes natively support NFS.  I've experimented with various add on clients but have not have much luck.

Any suggestions?  Is there yet another way to serve files on my Ubuntu server?

---

### Post by dcstar on 2011-12-25
> **stoneattic said:**
> I guess this is really a many part question.  I have a small LAN with a Ubuntu file server and 4 client PCs, three running WinXP Pro and one running Win7 Home.  Samba is surprisingly (to me) slow, particularly on the Win7 machine.  It's not hardware related because downloading from Apache is instant on the same files that take 30sec or longer on Samba.  I've spent a lot of time searching and tweaking on both the server and client end but noticed no real improvement.  

I've experimented with NFS, but none of the client OSes natively support NFS.  I've experimented with various add on clients but have not have much luck.

Any suggestions?  Is there yet another way to serve files on my Ubuntu server?

[http://wiki.samba.org/index.php/Samba_Troubleshooting#Slow_file_transfer_-_especially_smaller_files](http://wiki.samba.org/index.php/Samba_Troubleshooting#Slow_file_transfer_-_especially_smaller_files)

I have just dome some benchmarks on my test 10.04 server with Samba shares on EXT3 & NTFS filesystems copying a single 697.3 MB ISO file on a 100mb LAN:

Ubuntu 10.04 to Ubuntu 10.04 (NTFS) Samba share: 85s
Ubuntu 10.04 to Ubuntu 10.04 (EXT3) Samba share: 78s

Windows XP to Ubuntu 10.04 (NTFS) Samba share: 99s
Windows XP to Ubuntu 10.04 (EXT3) Samba share: 98s

Vista to Ubuntu 10.04 (NTFS) Samba share: 69s
Vista to Ubuntu 10.04 (EXT3) Samba share: 67s
Vista to XP (NTFS) share: 66s

The Vista transfers basically maxed out the 100mb LAN link, and the others weren't that far behind. Using NTFS on the Linux box slows down writes compared to EXT3 by about 10% on the first creation of the file, the reads were about the same.

Windows 7 to Samba can (apparently) be improved by turning off the 128bit encryption on the Windows 7 box.

---

### Post by stoneattic on 2011-12-26
Thanks for the reply.  I tried adding:

```
large readwrite = no
```

to the global section, per the link you provided, and restarted samba, but didn't see any change.  The file system for the shares are EXT2 and I had already disabled 128bit encryption previously.

It's not just through put while copying, but populating folders, opening and saving documents, pics, mp3s, etc, is ridiculous.

My samba shares have never been particularly fast over wireless connections to XP, but now with the Win7 machine it is pretty much unusable.  

My options may come down to either trying to install XP on the new laptop, or switching to a windows server.  Neither is a particularly appealing choice since I would have to try to find XP drivers for the new hardware.

I was doing more testing and I can open these same files from other Windows PCs instantly.  As much as I hate to do it I may have to go to a Windows OS on the server.  This is really depressing.   :(

---

### Post by stoneattic on 2011-12-30
Well after wiping the OS and installing 11.10 and reconfiguring everything I still had the same symptoms.  Fast ftp and HTTP but slow Samba.  After just about giving up in frustration for the evening I was looking at the routers and just for kicks plugged the server directly into the router that the Windows PCs were plugged into.  Success! Instant Samba response on the Windows PCs. 

It's a home network:

Cable modem---Vonage VT2442 router---Linksys WRT54GS router

Originally the server was plugged into the VT2442 and the Windows PCs into the WRT54GS.  Now that everything is plugged into the WRT54GS the Samba speed is good.  So although I'm not sure what the problem is, it's not the Samba, but something with one of my routers.  I need to figure out what's going on, but I pretty much got everything working now.

---

