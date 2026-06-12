---
title: "Keep Torrent Client Running After Logout?"
date: 2011-02-10
forum: General Help
---

### Post by steevven1 on 2011-02-10
I currently use Deluge for torrents, and I have many torrents which I would like to keep seeding 24/7 on my desktop computer. This machine is on 24/7, and has many users, both locally (using the standard Ubuntu GUI on a monitor, keyboard, and mouse hooked to the actual machine) and remotely (via ssh). My point is that this is a multiuser system. I am the administrator/have root access.

Anyway, the point is, I would like to run a BitTorrent client on this system without having to have any user logged in just to sustain it. Currently, the only way I know of keeping BitTorrent active at all times is to log in locally via the GUI, turn on Deluge, and then hit "lock screen," protecting my session and allowing others to log in locally as well while I'm gone (via "Switch User"). It is a big drain on system resources to have me logged in all the time (especially with a GUI).

I think I have explained the problem...Is there a solution? I use Deluge and like it, so I'd like to stick with it, but if there is a better option for this purpose, I am willing to switch.

Thanks.

---

### Post by Vaphell on 2011-02-10
use command line torrent client like rtorrent
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

what to do to keep it running after logout?
[http://ubuntuforums.org/showthread.php?t=817712](http://ubuntuforums.org/showthread.php?t=817712)

---

### Post by steevven1 on 2011-02-11
Wow, this worked like a charm, and I really like rtorrent! Thanks!

---

