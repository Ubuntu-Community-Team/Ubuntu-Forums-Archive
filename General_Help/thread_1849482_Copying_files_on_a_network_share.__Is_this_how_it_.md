---
title: "Copying files on a network share.  Is this how it works?"
date: 2011-09-24
forum: General Help
---

### Post by nc_jed on 2011-09-24
I have a samba server in the other room, Ubuntu Server 10.10 based.  On there I have several shares.  From my laptop, I am trying to move some files around on the server's file system and it is less than speedy.

I'm curious, when I have a file manager open to the Samba share on my Xubuntu laptop and I drag files around the file manager window (one folder of >1 GB of files into another folder with many GB of files), is it somehow routing these files to my laptop (as an intermediary) before it moves the files to the other directory?

If so, how to stop?  This shouldn't be taking this long....

- ABT

---

### Post by Hugh971 on 2011-09-24
> **nc_jed said:**
>  is it somehow routing these files to my laptop (as an intermediary) before it moves the files to the other directory?

Yes, that's exactly what it's doing, the only way round it is to move the files round directly on your server, you could do this via an SSH connection from the laptop. If you install nautilus on your server you can run it from your server on your laptop via SSH. That way you will be working on the server itself instead of over the network.

---

### Post by nc_jed on 2011-09-24
> **Hugh971 said:**
> Yes, that's exactly what it's doing, the only way round it is to move the files round directly on your server, you could do this via an SSH connection from the laptop. If you install nautilus on your server you can run it from your server on your laptop via SSH. That way you will be working on the server itself instead of over the network.

yikes, no wonder why it's taking so long.  Thanks for the confirmation!

-ABT

---

