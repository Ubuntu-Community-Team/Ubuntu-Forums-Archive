---
title: "Automatic mirroring of large files over spotty connection"
date: 2009-07-15
forum: General Help
---

### Post by mgchan on 2009-07-15
I have a small file server (Popcorn Hour A-110) which is NFS, Samba, and FTP capable. It's connected to a wireless router in client mode to my network. However, it is separated by my main network by a couple walls and thus has somewhat spotty network performance; it drops connection randomly.

I'd like to have that small server mirror a few folders on my main Ubuntu server, but I do have this problem of large files. I rip my favorite movies to my main server (which is also running XBMC in my home theater) and I would like to set it up so those moves are automatically copied (either immediately or intermittently) to the Popcorn Hour. So far, I've been using VNC into my XBMC machine and just using an FTP client to send things over, which will then autoresume files when it gets disconnected. 

Is there any way to automate this process? Will rsync resume files if it gets disconnected? Obviously if I just use something like cp, it will start copying, get to maybe 70%, drop connection and try again, and I'm not sure if it would ever complete.

---

