---
title: "Internet problem, when downloading can't access web."
date: 2010-10-11
forum: General Help
---

### Post by gencon on 2010-10-11
Note: Not upgraded yet, still using Ubuntu Lucid Lynx.

Recently I've had a strange problem with my internet connection. When downloading something I am unable to use the internet with other net clients. An example, this morning I was downloading a very large set of backup files from an online server where I store backups. The files totalled 1.5 GB and I was downloading them using a SFTP client called FileZilla - during the download I was UNABLE to access the internet using Firefox, pages did not load at all - NOT slowly, but NOT at all, the "can't find the server" message was displayed by Firefox. Likewise Thunderbird was not able to check/download email. Confirmation that no internet access (other than FileZilla) was possible was shown by trying to 'ping google.com', the response "ping: unknown host google.com". During all this FileZilla was downloading very happily and quickly and as soon as the downloads finished everything worked as normal.

The problem is not limited to FileZilla, when downloading a file with Firefox the same problem occurred. It is as if when downloading something all other net connections are put on hold including DNS lookups. In the past my internet connection might slow down as a result of downloading but I'd still be able to access the web and email just slower as a result of the download. This problem has only started happening in the last week or thereabouts.

No idea even where to start fixing this, any ideas?

Thanks all.

---

### Post by TheAnachron on 2010-10-11
Hey dude, do you have a firewall? 
Also, what kind of programs are you running while downloading?

---

### Post by gencon on 2010-10-11
I use UFW (Uncomplicated Firewall) but I've changed no settings on it since installing Lucid (soon after it was released), and this problem has only been happening for approx. a week.

Programs: Firefox, Thunderbird, Netbeans, Nautilus, Gedit, Terminal - that's about it.

---

### Post by TheAnachron on 2010-10-11
I don't know about UFW, but the other programs seem to be ok. (I use all of them as well)
Could you please provide me a list of Firefox addons you are using? 
Is there any proxy that you use?

---

### Post by lovinglinux on 2010-10-11
I doubt this has anything to do with extensions, otherwise the problem wouldn't affect other applications. I also doubt that this could be related to Firewall, otherwise you would have connection problems when not downloading.

Looks like your network is being clogged when you start the downloads. Check your router settings. Set the MTU to 1492 instead of 1500. That might help.

---

### Post by gencon on 2010-10-11
> **lovinglinux said:**
> Looks like your network is being clogged when you start the downloads. Check your router settings. Set the MTU to 1492 instead of 1500. That might help.
Thanks.

I've done that on my Ubuntu machine using this:

```
ifconfig eth0 mtu 1492
```

It made no noticeable difference - the same problem persists.

Should I be changing the settings on my actual router and not on my Ubuntu PC?

---

### Post by lovinglinux on 2010-10-11
> **gencon said:**
> Thanks.

I've done that on my Ubuntu machine using this:

```
ifconfig eth0 mtu 1492
```

It made no noticeable difference - the same problem persists.

Should I be changing the settings on my actual router and not on my Ubuntu PC?

I guess so. Is the only way I do it.  I'm not sure this will help in your case, but it helps other users experiencing connection timeout problems.

---

### Post by gencon on 2010-10-11
I changed the MTU on my router to 1492 as well, and the same problem persists. It's so strange if I am downloading a file I simply can't access the internet until the download completes (apart from the actual download connection). Why this has suddenly started happening I've no idea, all has been fine up until this last week.

Has anyone any clue what I should do?

Thanks all.

---

### Post by lovinglinux on 2010-10-11
> **gencon said:**
> I changed the MTU on my router to 1492 as well, and the same problem persists. It's so strange if I am downloading a file I simply can't access the internet until the download completes (apart from the actual download connection). Why this has suddenly started happening I've no idea, all has been fine up until this last week.

Has anyone any clue what I should do?

Thanks all.

This problem usually happens when you use a torrent client and don't limit the UPLOAD/DOWNLOAD speed. I don't know why is happening with your FTP client and Firefox download manager.

---

### Post by gencon on 2010-10-11
> **lovinglinux said:**
> This problem usually happens when you use a torrent client and don't limit the UPLOAD/DOWNLOAD speed. I don't know why is happening with your FTP client and Firefox download manager.
I have no torrent client running, nor ever.

Any other ideas anyone?

---

### Post by lovinglinux on 2010-10-11
> **gencon said:**
> I have no torrent client running, nor ever.

Any other ideas anyone?

Try to enable QoS in the router.

---

### Post by Tosho on 2011-04-11
THANK YOU, Dude! :D:popcorn:
I was wondering what's happening since I installed the Ubuntu, wasn't able to browse internet while there was any downloading. I thought it's some OS problem/config.
But what are the other settings in that QoS I add html, skype and ftp with priority is that good ? 
And is this QoS affect other OS/s in the network like Win 7 and WinXP ??

---

### Post by Tosho on 2011-04-17
bump

that doesn't work. It looks like was working when I enabled the QoS but still - cant access web when there is torrent downloading - even when the download speed is limmited to 10-20-30 kb/s.

---

