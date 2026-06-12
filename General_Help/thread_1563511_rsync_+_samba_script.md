---
title: "rsync + samba script"
date: 2010-08-29
forum: General Help
---

### Post by neon401 on 2010-08-29
Hi.

I'm using Deluge (torrent client) and it has an option to execute a command whenever a torrent finishes.
What I would like it to do is to sync the torrent folder on the Linux box with my Windows PC mounted with smbfs.

This is how I do it right now:

```
sudo rsync -parv /mnt/wd/Torrent /mnt/samba
```
'/mnt/wd/torrent' is where the torrents get saved after completion and '/mnt/samba' is the Samba mount.

Now I'm a Linux newb, so how do I put this in a simple script?

Also, as you can see, I need to run the command with sudo. If I don't, I get a "Permission denied" error. How do I get around this?


Thanks in advance, and apologies for my bad English.

---

