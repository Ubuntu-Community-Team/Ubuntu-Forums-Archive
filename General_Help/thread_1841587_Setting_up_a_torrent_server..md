---
title: "Setting up a torrent server."
date: 2011-09-09
forum: General Help
---

### Post by zalmer on 2011-09-09
Sorry if this is the wrong forum for this but I really don't know where else to put it. I am more than happy to delete it and move it to another if I need to. 

Basically what I have got is a fresh and updated install of ubuntu on a small computer im using as a file server, for my 2 mac computers and 1 windows machine. Im using utorrent on all 4 systems. What I want to be able to do is click on the magnet link / regular link and have the torrent get forwarded to my ubuntu box for downloading. I don't want to download to the server from the current box im on. I want the server to do all the heavy lifting of downloading and then it will dump it to my shared directory. So I can start 4 or 5 torrents turn of the client machine and the server will download while im away and it will be ready to be viewed over the network when I return. I have looked all over and can find nothing. Im starting to think this may not be possible. If anyone has any ideas I would really appreciate it. Thanks.

---

### Post by blueridgedog on 2011-09-09
There are lots of ways to do it.  These links might get you thinking:

[http://www.linux.com/archive/feature/137677](http://www.linux.com/archive/feature/137677)

[http://www.howtogeek.com/howto/29905/how-to-trigger-torrent-downloads-from-anywhere-with-dropbox/](http://www.howtogeek.com/howto/29905/how-to-trigger-torrent-downloads-from-anywhere-with-dropbox/)

(this one can do it with Transmission, the native torrent tool on Ubuntu and you can adapt it to not use dropbox, but a directory that is shared on the server via SAMBA)

---

### Post by papibe on 2011-09-09
I'm using transmission-daemon in my server to download all my torrents. It runs on the server, but you control it from any computer using a web interface. The only thing I would set differently from the default configuration is the download directory. I would change it to a proper place (of your choosing of course).

I highly recommend it. Check it out, and tell us if you need more details.

Regards.

Edit: Although this [guide]("http://novem-it.com/drupal6/node/5") is outdated (it is much easier in Ubuntu now) is describes the basics points. Take a look at the picture in the end: you are controlling your downloads using Firefox.

---

### Post by Cheesemill on 2011-09-09
I use Deluge on my setup.

My server runs the backend daemon, and all my other PC's connect using either the GTK or Windows frontends, you can also access it using a WebUI if you wish.
[URL="http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient"]
Deluge thin client setup.[/URL]

---

### Post by JebusWankel on 2011-09-09
I set one of these up this summer. I recommend using deluge. You can run the deluge daemon deluged on your file server and then install the gui frontend on your other computers. Then you can get the torrents running with just one click. I don't know about magnet links, those would probably work too.

You can also set up the server to run the web interface like I did so I can check on my torrents even when I'm away from home. Also, that web interface works with a fantastic android app called transdroid, which I highly recommend. Also I used mediatomb for streaming my files and this script [http://mroach.com/rss_fetch.html]("http://mroach.com/rss_fetch.html") to automatically download .torrents from an rss feed.

---

### Post by zalmer on 2011-09-09
Thanks everyone for your input I think blueridgedog's 2nd link is closest to what I want to get done with a bit of tinkering It should work thanks a lot guys.

---

### Post by Pariah819 on 2011-09-09
I also have been meaning to get a torrent server up and running for a while now (ever since I put a media server in my basement).  I guess since I stumbled on to this thread I have no reason to wait anymore.  Thanks for the info guys!

---

