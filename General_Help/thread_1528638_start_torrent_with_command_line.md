---
title: "start torrent with command line"
date: 2010-07-11
forum: General Help
---

### Post by miak on 2010-07-11
Hi,

I am trying to add a torrent using command line.
My ultimate goal is to start downloading a torrent while I'm still away(use ssh client to access my computer and using command line start new torrent, so it downloads until I get back home)

It can be any torrent client, but I'd prefer transmission or ktorrent (transmission more).

Thanks,
miak

---

### Post by cj.surrusco on 2010-07-11
[_This_]("http://blog.zloether.com/2009/03/command-line-bittorrent-with.html") has some good info on that.

Google works wonders :D

---

### Post by scrooge_74 on 2010-07-11
My advice to you

Install screen and rtorrent

you can then from a terminal start screen and inside it you start rtorrent after that you can get out of that screen and close the terminal and rtorrent will still be working.

You can find some nice info [here]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

---

### Post by bodhi.zazen on 2010-07-11
I advise you use rtorrent + screen.

rtorrent + screen is perfect for what you want (ssh, command line).

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Alternately, transmission has a web interface built in. You would need to forward that port

[http://www.associatedcontent.com/article/1166282/control_your_bittorrent_downloads_remotely.html](http://www.associatedcontent.com/article/1166282/control_your_bittorrent_downloads_remotely.html)

EDIT: Popular topic I see :)

---

### Post by scrooge_74 on 2010-07-11
haha I beat bodhi in pointing kmandla's blog :P

That rtorrent solution is great and works pretty well over my own network, kids just put the torrent file in a shared folder and rtorrent takes care of everything

---

### Post by mobilediesel on 2010-07-11
scrooge_74 and bodhi.zazen appear to have the right answer. That's what I use, screen and rtorrent.

---

