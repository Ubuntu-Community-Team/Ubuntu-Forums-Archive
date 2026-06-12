---
title: "Transmission &amp; file sizes (newbie)"
date: 2009-09-11
forum: General Help
---

### Post by irishbreakfast on 2009-09-11
In the bottom status bar of the Transmission window I can see the "Total Transfer" for the selected torrent. What I would like to know is why this number disagrees with the number given in the main part of the window.

In my case:
The main part of the window --
[INDENT]Name of file
846.8 MB of xx GB (n%) - zzz time remaining[/INDENT]

The status bar --
[INDENT]Total Transfer: Down 1.5GB[/INDENT]

Thanks

---

### Post by wobin77 on 2009-09-11
probably the total of inbound / outbound. Not only inbound...

---

### Post by irishbreakfast on 2009-09-11
Thanks, I should have added the full info:

the full status bar is 

Down: 1.5 GB   Up: 1.2 GB  xx down speed  yy up speed

---

### Post by wobin77 on 2009-09-11
It could also be that the total download is more because a large amount of data is rejected by your torrent. Normally you can see this (total dl, - % rejected) somewhere in your bittorrent client.

---

### Post by irishbreakfast on 2009-09-11
Thanks. I can't find anything in the GUI for Transmission, nor in the Transmission Forum about this. And a very quick google didn't help.

I just don't know if this is a problem. At what point do I consider the reject ration too high. If so, is there anything I can do anyway?

---

### Post by wobin77 on 2009-09-11
It's no problem. But i think it's rather a high value of rejected data... 
There's little you can do about it. It's downloaded data, but which you don't need. The exact explanation of this, i don't know. 
You should check from which peer it's downloaded and block that peer.

---

### Post by irishbreakfast on 2009-09-11
What a good idea. I would like to try that. 

But I can't find anything in Transmission that flags rejected data and the source. I downloaded the transmissioncli via Synaptic and that too doesn't have 'reject' option. Oh well, maybe it is in the latest version.

And besides this, my first journey, into the world of torrents will be postponed till next calendar month so my family has some bandwidth.

Thanks for all your help.

---

### Post by P4man on 2009-09-11
Rejected frames are .. rejected automatically. It doesn't show in the interface AFAIK, its part of the protocol. IT can be because some seeders have bad data (possibly deliberately trying to corrupt the torrent). 

Although the explanation could also be a lot simpler, perhaps you downloaded something else previously? Also, there is overhead to be taken in to account. Its quite normal to download 1GB you would have 1.2 or more gigabyte network traffic (which is what your ISP charges you for). Also the upload you did has a download overhead component to it.. For every frame you upload, you have to receive a request, receive acknowledgement and what not.

---

### Post by wobin77 on 2009-09-11
try µtorrent...  

@P4man: Indeed, couldn't explained it better! Lot's of 'seeders' want to ~TryToMessUpTorrents~..

---

