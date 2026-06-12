---
title: "opening files in deluge via termal"
date: 2009-08-13
forum: General Help
---

### Post by Cyked on 2009-08-13
Anyone know if this is possible?  I googled around and could only find info regarding deluge opening files automatically.  

I'd like to be able to run a command to open a file in deluge from terminal if that is possible.

---

### Post by alexlafreniere on 2009-08-13
Are you talking about a .torrent file? I would try something like this:

```
deluge yourTorrent.torrent
```

I don't have much experience with Deluge, so that may not be the exact command for it. I usually just use Transmission.

---

### Post by credobyte on 2009-08-13
If Deluge is your default torrent client:
```
open movie.torrent

```

---

### Post by Cyked on 2009-08-13
> **alexlafreniere said:**
> Are you talking about a .torrent file? I would try something like this:

```
deluge yourTorrent.torrent
```

I don't have much experience with Deluge, so that may not be the exact command for it. I usually just use Transmission.

This worked.  Thanks!

---

### Post by Cyked on 2010-06-01
Stupid follow up question after all this time.  If I am logged in as the user running deluge and open the file in terminal it works fine (i.e. sitting in front of the computer).

Any idea if I can do this via putty to open a .torrent file since deluge is already running?

Anyone?  I 'll post the error I get when I get a chance.  If I "deluge yourTorrent.torrent" when logged in locally and in terminal it works, but not over putty.

---

