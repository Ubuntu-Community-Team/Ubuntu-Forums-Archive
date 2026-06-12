---
title: "Multiple user configuration for rutorrent/rtorrent"
date: 2009-09-17
forum: General Help
---

### Post by Jorsher on 2009-09-17
There isn't *too* much documentation on this subject, so I was hoping to get some information from you all :D

I've followed directions from multiple tutorials on multiple rtorrent UIs hoping to find a solution, but haven't had any luck.

I did read:
[http://ubuntuforums.org/showthread.php?t=1119482](http://ubuntuforums.org/showthread.php?t=1119482)

I attempted what was there and still am having the problem...

**The problem:**
If I go to mysite/user1 or mysite/user2, it displays the same torrents in rutorrent.  If I'm on user2's page, whenever I go to settings it shows settings from user1's rtorrent.rc.

If user1 does not have rtorrent running, mysite/user2 will not load properly.

Apparently, when I go to the user2 webpage, it's loading the webpage from user1.

I have checked rtorrent on each user, and it's displaying the torrents properly.

I have set different rtorrent.rc files for each user, differen't paths for their session, different scgi ports, etc.  They each have their own rutorrent web directory and the settings are configured.

For some reason, going to mysite/user2 seems to be directing to mysite/user1, so I think it's something I'll need to configure with the apache server.

I've tried mysite:scgi_port/user, and the page won't load.

Any ideas?

Questions?

Help!

---

### Post by mothra13 on 2009-09-20
Man, I am on a debian box and I am having the exact same problem, i thought it was an issue with the SCGIMount property in apache2.conf but when I added more it didn't work, but it is possible I have the syntax wrong for multiple SCGI ports.  

Good luck to you and if you find anything please ping me about it.

---

### Post by mothra13 on 2009-09-20
Hey, I hope you get this but if you go to the rutorrent site and grab the RPC plugin, download it and decompress it to your /rtorrent/plugins/ folder, it should fix it.

---

