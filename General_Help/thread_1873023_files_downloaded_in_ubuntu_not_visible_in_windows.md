---
title: "files downloaded in ubuntu not visible in windows"
date: 2011-10-31
forum: General Help
---

### Post by Vlownage on 2011-10-31
Hey everybody,

I'm new here to the forum, because i'm having the following problem:

I have a laptop (Asus N53S) and i'm dual booting with both windows 7 and ubuntu. In ubuntu I recently installed qbittorrent for downloading. But i'm experiencing the following problems:

Most importantly, files downloaded in qbittorrent are normally accesible in ubuntu, but i can't find any trace of the map in windows.

When a download has finished, and i start qbittorrent at a later time, it says the download has to start from 0 again in stead of being finished. 

So i hope you can help me find a practical solution. I'm not a star at being a linux-expert or working with commandlines. I can copy and enter them and occasionaly understand what it does but that's it :P Should i perhaps just use a different torrent client? Is this a known problem (google didn't resolve).

Thanks in advance for your responses!

Vlownage

---

### Post by goldshirt9 on 2011-10-31
A - Windows wont see your linux o/s.
  but you could try [http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/](http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/)

cannot help with  qbittorrent as i use deluge but look in your settings.
if you have then await a more gifted person than me :D

---

### Post by satanselbow on 2011-10-31
> **Vlownage said:**
> 
I'm new here to the forum, because i'm having the following problem:


Welcome aboard ;)

> **Vlownage said:**
> Most importantly, files downloaded in qbittorrent are normally accesible in ubuntu, but i can't find any trace of the map in windows.

 
The filesystems usually used by ubuntu cannot be read by windows. If you want to use the downloaded files in Windows you will have to copy them across to your windows disk - or move them to a NTFS shared partition.


> **Vlownage said:**
> 
When a download has finished, and i start qbittorrent at a later time, it says the download has to start from 0 again in stead of being finished. 


This can happen (on any torrent client, on any platform) for a couple of reasons.

1) Have you checked the "move completed to folder" in qbittorrent?
2) You have purposely moved the completed torrent files - but have also enabled "automatically load torrent files from folder".
3) ... I'll think about that one...

> **Vlownage said:**
> 
So i hope you can help me find a practical solution. I'm not a star at being a linux-expert or working with commandlines. I can copy and enter them and occasionaly understand what it does but that's it :P Should i perhaps just use a different torrent client? Is this a known problem (google didn't resolve).


I like qbittorrent - does exactly what it says on the tin ;) I think you might have tweaked something accidently :D

> **Vlownage said:**
> 
Thanks in advance for your responses!


No problem :D

---

### Post by jmacx81 on 2011-10-31
I have mine setup to dump in a folder that is on my windows partition that way I can use my songs or movies on either side.

---

### Post by TBerk on 2011-11-01
[http://ubuntuforums.org/showthread.php?t=1870339&highlight=qbittorrent]("http://ubuntuforums.org/showthread.php?t=1870339&highlight=qbittorrent")

Possibly you are having the same problem I am having;

When you add a torrent in qbittorrent it adds itself to the list just fine but once you activate it for downloading/seeding it will look like it has been removed (or deleted) from that same list of torrents.

Meanwhile, if you look at the Up/Down speeds you can see activity, and stopping all active torrents will re-enable the ability to 'see' the disappear'd torrents.

Does this match your experience?


TBerk

---

