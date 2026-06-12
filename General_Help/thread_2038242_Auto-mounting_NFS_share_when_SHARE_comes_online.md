---
title: "Auto-mounting NFS share when SHARE comes online"
date: 2012-08-06
forum: General Help
---

### Post by borcenty on 2012-08-06
Hey,

I got myself a home server with Ubuntu 12.04 on top. Basing on the articles on this forum I managed to configure the NFS connection between home server and my laptop. I also edited the /etc/fstab to have it all mounted while booting.

My question is:

What's the best way to auto-mount NFS shares? I sometimes turn off my home server and it happens that laptop (nfs source) is offline and home server can't mount nfs shares from the laptop. Is there any smart way to auto-mount the share when my laptop comes on-line? I was thinking about a short script in cron, every 5mins, which would check the mounts and mount any new shares.

Any other options?

Thanks!
borcenty

---

### Post by borcenty on 2012-10-02
UPDATE: I got rid of NFS and used SMB instead (default file sharing in Ubuntu). Seems to work easier in my case.

---

