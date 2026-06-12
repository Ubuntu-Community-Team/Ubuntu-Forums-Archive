---
title: "mount and fstab problems to an NAS"
date: 2011-07-24
forum: General Help
---

### Post by MAFoElffen on 2011-07-24
Re: Ubuntu 11.04

Okay, this one is just weird.

I added an NAS to my network (Snap! Server).  For those that know me.... I have 20 drives on one of my servers, between installed and attached drives. I really didn't need more storage, but it was free.  So this is the first time I've installed a standalone NAS.

I can (sort of) mount the NAS manually from my main box (11.04) via:
```

sudo mount -t smbfs //192.168.2.107/maferr-snap /Snap -o credentials=/home/mafoelffen/.smbpasswd

```I can (sort of) mount it through fstab via:
```

//192.168.2.107/maferr-snap   /Snap       smbfs        credentials=/home/mafoelffen/.smbpasswd 0 0

```Here You might say "great"... well it is has no errors, but is only partially mounting?.  I will explain:

It doesn't show up on the gnome desktop as mounted like my other disk mounts & real "server shares" or as a folder in Places.  

After doing either of the above, I can see and read the files in that NAS via the /Snap directory through a terminal to /Snap or nautilus if I go to filesystem > /Snap.... Problem is when I check permissions on that folder from that machine, it says the owner and permissions are root(?)  Even though it says it is root, it will only let even root read , but not write... 

So the question is: 
"How to get this working and appearing as other shares, with normal access and rw rights?"  

I know, the first question I would ask someone else would be: Is it the rights and preveledges on the NAS... No- See below...

I can connect to the web server of the NAS via any browser using the same data as above...

It can connect correctly to the NAS if I do a Places > "Connect to Serverr" using the same data in the 2 attached pic's manually.  If I connect this way, I do have a desktop icon and have rw previledges... Like I said, this is weird.

---

### Post by MAFoElffen on 2011-07-24
bump

---

### Post by MAFoElffen on 2011-07-26
bump- 

Still no help or suggestions from anyone?

---

### Post by MAFoElffen on 2011-07-26
This thread has gone almost a week with no replies.  I'm going to mark this as finshed, solved, closed... Just to end it and ask in another subforum (Server Platforms).

---

