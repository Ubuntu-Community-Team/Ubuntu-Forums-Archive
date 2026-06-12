---
title: "can't install filezilla"
date: 2010-03-21
forum: General Help
---

### Post by newuser4 on 2010-03-21
hi all

I can't install filezilla. I've searched and written the line (sorry can't remember  what it was exactly) in terminal, but it didn't find filezilla.

I then found another thread and tried writing as shown by *aysiu* in the screen grab.

But, it got to 99% and then after ages said it couldn't finish (see screenshot).

Help a complete neewbie! ;)

ps yes I want filezilla I like it from my win xp days :D

pps plus as a newbie I think these are the things that need to work to get people off win xp :P

---

### Post by howefield on 2010-03-21
You are running Synaptic Package Manager and also using apt-get.

Run only one at a time, close one and try again.

---

### Post by _h_ on 2010-03-21
_EDIT: Beat me to it howe._[]("http://filezilla-project.org/download.php?type=client")

---

### Post by howefield on 2010-03-21
> **_h_ said:**
> EDIT: Beat me to it howe.

Don't worry about that, it happens and usually not a bad thing as it can confirm advice to the OP. :p

---

### Post by _h_ on 2010-03-21
> **howefield said:**
> Don't worry about that, it happens and usually not a bad thing as it can confirm advice to the OP. :p

I didn't even notice the Synaptic open. I saw Network Unreachable, and was about to offer up a link to the filezilla website client download. :P

---

### Post by newuser4 on 2010-03-21
Hi

still didn't work!

here's part of the info: (used: **sudo aptitude install filezilla** in terminal)

[I]Couldn't find any package whose name or description matched "filezilla"
Couldn't find any package whose name or description matched "filezilla"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

see screenshot

thanks for help

---

### Post by _h_ on 2010-03-21
```
sudo apt-get install filezilla
```

Or download it from site:

[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php)

---

### Post by megahost on 2010-03-21
better option...
places>Connect to Server
It's so much better than filezilla imo

---

### Post by newuser4 on 2010-03-21
for some reason won't connect

simply says connecting to *filezilla-project.org...* for ever.

Perhaps they have a problem with their site and I should try tomorrow? (other webpages are fine for me)

---

### Post by newuser4 on 2010-03-21
> **megahost said:**
> better option...
places>Connect to Server
It's so much better than filezilla imo

what do I put in the boxes if I try that?

---

### Post by _h_ on 2010-03-21
> **megahost said:**
> better option...
places>Connect to Server
It's so much better than filezilla imo

Except for the incredibly slow speed by the file manager.

> **newuser4 said:**
> for some reason won't connect

simply says connecting to *filezilla-project.org...* for ever.

Perhaps they have a problem with their site and I should try tomorrow? (other webpages are fine for me)

Might be a DNS routing issue, can you connect to the site through a proxy by chance?

---

### Post by newuser4 on 2010-03-21
> **_h_ said:**
> Might be a DNS routing issue, can you connect to the site through a proxy by chance?

no don't know how (I think I tried it once and got lost :p)

---

### Post by _h_ on 2010-03-21
> **newuser4 said:**
> no don't know how (I think I tried it once and got lost :p)

Go here: [http://freesurfproxy.org/](http://freesurfproxy.org/)

Put in [http://filezilla-project.org](http://filezilla-project.org) into the field and then click GO. Let me know if you see the site or not.

---

### Post by newuser4 on 2010-03-21
yes I can see it (after getting past the ads ;)

should I use it?

If so do I want filezilla client or server?

altohuh I must mention that earlier I tried to 'add on' no script to firefox and taht also wouldn't connect....

---

### Post by howefield on 2010-03-21
Filezilla is in the Universe repository, check that you have it set up in your software sources.

System > Administration > Software Sources > Ubuntu Software tab.

Or you could try gftp. Another ftp program similar to filezilla.

---

### Post by newuser4 on 2010-03-21
howefield

yes universe is ticked - I checked that earlier and just double-checked now

---

### Post by newuser4 on 2010-03-21
ok just tried to install vlc player and it couldn't find that either :-|

---

### Post by _h_ on 2010-03-21
> **newuser4 said:**
> ok just tried to install vlc player and it couldn't find that either :-|

What servers are you trying to get from? I noticed earlier you had GB tacked on, have you tried maybe another country code?

---

### Post by newuser4 on 2010-03-21
it also says both filexzilla and vlc player are not available if I search through ubunutu software centre (as shown in screen grab below)

thanks for all help

---

### Post by newuser4 on 2010-03-21
> **_h_ said:**
> What servers are you trying to get from? I noticed earlier you had GB tacked on, have you tried maybe another country code?

:KS

gold star that man!!!!!!!!!!!

I checnged the server to the second one down in the list for united states....

next second it downloaded loads of packages  (ooerr) and then after that I downloaded and installed both vlc player and filezilla in double-quick time.

so, some kind of problem with uk server

thanks a million

---

### Post by bluepicaso on 2010-06-30
I need a quick help. Here is what i did. I wanted to upgrade my filezilla from 3.3.1 to 3.3.3 but i could not do it. I downloaded tar.bz from the filezilla site. After unsuccessful hits what i did was, i extracted the tar ball and copied files from bin folder to /usr/bin/, after that evrything went wrong. Not i have copied the full extracted folder to /opt. and has added it as my custom application.

Please help me on what went wrong. I tried synaptic and terminal. but nothing worked.

---

