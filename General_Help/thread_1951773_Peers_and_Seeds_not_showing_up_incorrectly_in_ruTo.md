---
title: "Peers and Seeds not showing up incorrectly in ruTorrent V3.4"
date: 2012-04-03
forum: General Help
---

### Post by osc1882 on 2012-04-03
So here is a snapshot of what I am dealing with: [http://i.imgur.com/4w4Kq.jpg](http://i.imgur.com/4w4Kq.jpg)
I installed rtorrent / ruTorrent a few days ago using this guide / script: [http://forums.rutorrent.org/index.php?topic=608.0](http://forums.rutorrent.org/index.php?topic=608.0)
Everything seems to be working pretty great so far but the issue of Peers and Seeds not showing up correctly.
What is interesting is if I am not connected to anyone at all at the time then is shows the seeders and peers as zero but if I am connected to anyone at all it shows both the seeders and peers as the same number. That is if I am connected to 38 peers and 2 seeders then it shows both the number of seeders and the number of peers as 40. But If I click on a torrent and then go to the tracker tab as you can see in the above picture then you can see the actual number of peers and seeders for that torrent.
All of the torrents are on a private tracker and none of the torrents are new.
Does anyone have any idea? I am wanting to switch to rtorrent completely but I feel like I need to understand this problem before I start to move everything over.
Thank you for your time.

---

### Post by Rodney9 on 2012-04-03
I alwas found Deluge worked faster, it is in the Software Center.

[http://dev.deluge-torrent.org/wiki/About](http://dev.deluge-torrent.org/wiki/About)

Deluge is a full-featured, multi-platform, multi-interface BitTorrent client using libtorrent-rasterbar in it's backend and featuring multiple user-interfaces: GTK+, web and console.

It has been designed using the client-server model with a daemon process that handles all the bittorrent activity. The Deluge daemon is able to run on headless machines with the user-interfaces being able to connect remotely from any platform.

You may want to install this package to use Deluge in classic mode, which means the daemon and the GTK+ user-interface are linked together.

---

### Post by osc1882 on 2012-04-03
I was just leaving Deluge as I normally got some pretty wierd errors with it and I am looking to run a very large number of torrents and rtorrent normally does for better with that from what everyone says. Plus ruTorrent has a search, I know that sounds like a small deal but when you have a huge number of torrents running being able to search for a torrent does help alot.

---

### Post by pyroscope on 2012-04-04
You don't need ruTorrent (or any web UI) to be able to search.

[IMG]https://pyroscope.googlecode.com/svn/trunk/pyrocore/docs/videos/rtcontrol-curses.gif[/IMG]

Also [http://youtu.be/Bv-oajBgsSU](http://youtu.be/Bv-oajBgsSU)

What you're likely comparing here is d.peers_connected / d.peers_accounted vs. t.scrape_complete / t.scrape_downloaded / t.scrape_incomplete, and those are simply very different values.

---

### Post by osc1882 on 2012-04-05
Thanks for the help pyroscope? I'm glad you love your rtorrent with out a gui but I would like a gui myself. Do you have any idea how to get rutorrent to display that accual number of people connected to the torrent?

---

### Post by pyroscope on 2012-04-05
Well, you cannot display what you don't have in xmlrpc or don't even get from the tracker (not all trackers deliver swarm size data). If you want the scrape values in the table, then rewrite the plugin code to issue the matching get command instead of what's used right now.

---

