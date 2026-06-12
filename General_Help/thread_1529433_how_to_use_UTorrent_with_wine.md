---
title: "how to use UTorrent with wine?"
date: 2010-07-12
forum: General Help
---

### Post by ultimatedell on 2010-07-12
hi guys i'm a bit of a noob when it comes to ubuntu. i can accomplish all of the tasks i need to i.e word processing and easy stuff like that but i am trying to use Utorrent now and i need to use wine. i have successfully created the lancher i think cause it has the glass of wine as the icon. the only problem is that when i double click it IT DOES NOTHING!!! this is my code.
```
wine "/home/zac/utorrent.exe/NOINSTALL"
``` 

any ideas?

also can u change ur name on this forum cause i created this account years ago when i learned about Ubuntu but never used it till now.

thanks in advance 

UltimateDell

---

### Post by kukker32 on 2010-07-12
why you want to use &#8595;torrent with wine??

install ktorrent using the ubuntu softwarecenter
ktorrent is similar to utorrent and does the same... just made for ubuntu

---

### Post by hawthornso23 on 2010-07-12
Transmission works just fine. Generally speaking a native linux application is MUCH better than a windows application running in wine.

---

### Post by lovinglinux on 2010-07-12
You don't need to use uTorrent in Wine. There are several excellent open source native BitTorrent clients. I like Ktorrent and Deluge a lot, but recently I switched to qBitTorrent, which is the fastest torrent client I ever used and looks a lot like uTorrent.

BTW, uTorrent Linux version will be available soon.

---

### Post by giddyup306 on 2010-07-12
I don't know why *anyone* would want to use UTorrent or BitTorrent.  UTorrent was bought out by BitTorrent Inc, and it is a closed-source program.  Although it doesn't say it on Wiki anymore,  BitTorrent Inc is partners with # 20th Century Fox, # Comedy Central, Lionsgate Films, MTV,  Paramount,   Spike TV, Warner Brothers, New Line Cinema and Manga Entertainment.   Some of these companies are members of the RIAA and MPAA.

I took this screenshot today.  Really the only reason why they might have bought the company is so that they can monitor people's computers.  Why else would they care?   

EDIT:  This is a smaller version of my IP blocker.

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/bittorrent-1.png[/IMG]

---

### Post by lovinglinux on 2010-07-12
> **giddyup306 said:**
> I don't know why *anyone* would want to use UTorrent or BitTorrent. ...

Would you mind posting large images attached instead of inline?

---

### Post by giddyup306 on 2010-07-12
> **lovinglinux said:**
> Would you mind posting large images attached instead of inline?

No problem.  I just thought I'd save the site some bandwith by upping them to my Photobucket. ;)

---

### Post by WorMzy on 2010-07-12
I wouldn't install ktorrent unless you're using kubuntu. Installing 100MB of libs just to use a torrent client seems redundant to me.

I, personally, recommend deluge. It can be run as a daemon, and you can use a GTK client or a web client. It has a blocklist for blocking IPs, a scheduler to control when you want to download automatically, and plenty of other good features.

---

### Post by lovinglinux on 2010-07-12
> **giddyup306 said:**
> No problem.  I just thought I'd save the site some bandwith by upping them to my Photobucket. ;)

Thanks. Large images mess with the forum layout and is annoying to read the post.

I don't know about photobucket, but imageshack has a thumbnail template for forums.

---

### Post by GregoryMA on 2010-11-20
We get there are other bittorrent clients that may be easier to use in Ubuntu but that's not what this person asked.  They asked for help setting utorrent up with wine.  Can anybody give them some advice?

---

### Post by WorMzy on 2010-11-20
I doubt they're still interested four months on, please don't needlessly bump topics.

---

### Post by nasweef on 2011-01-07
Do you want to install utorrent with wine, or just want to use utorrent in ubuntu?
If what you want is to use utorrent in ubuntu, its simple
1. Download linux version of utorrent
2. Extract the tar
3. Run utserver (double clicking will do)
4. Go to [http://localhost:8080/gui/](http://localhost:8080/gui/) in ur browser for the gui

The whole thing is there at [http://geekztips.blogspot.com/2011/01/utorrent-in-ubuntu.html]("http://geekztips.blogspot.com/2011/01/utorrent-in-ubuntu.html")

---

