---
title: "how to mount to a hidden directory"
date: 2011-03-12
forum: General Help
---

### Post by UncleBoarder on 2011-03-12
I want my data volume to mount to /.data

Possible?

I can hear you already... Why would I want to do that?

My data volume is on my server and it contains data for Ubuntu, CentOS, and Windows... and at the root it has folders for each OS.  I want the .data mounted (or NFS shared) to all my computers and then I'll make a link to the appropriate platform directory pointing to /data.

That gives me a /data directory that matches each OS... AND it gives me a hidden parent directory that let's me access all my data directories from any computer.

I think you can see that I can't do it in reverse, I can't mount /data and then link /.data.  It doesn't accomplish the same hierarchy.

---

### Post by Krytarik on 2011-03-13
Why shouldn't it work?! Just try it! Nice plan, btw..

---

### Post by UncleBoarder on 2011-04-17
Never got it to work.  Instead I just mounted to /mnt/data and then created symlinks of /data for each OS.

---

