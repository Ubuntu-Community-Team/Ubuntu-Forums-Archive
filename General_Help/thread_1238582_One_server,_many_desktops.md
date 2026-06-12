---
title: "One server, many desktops"
date: 2009-08-12
forum: General Help
---

### Post by Innu on 2009-08-12
I have a server and many desktops/laptops.

What I want to do is that I'll create some users at the server. And all the other computers should be able to log in using it.

My first idea was that I'll mount the server /home directory with the sshfs. Then add users to /etc/passwd one by one.

Not sure if it works like this.

Are there better ways?

---

### Post by starcraft.man on 2009-08-12
I think what you want is a thin client server set up. See this [wiki]("https://help.ubuntu.com/community/ThinClientHowto"). The article is unsupported, just read the intro and then go to ltsp link, that seems to be up to date. I'm not a server admin, so I can't answer any problems. Seem fairly comprehensive though in terms of documentation.

---

### Post by zzzBrett on 2009-08-12
> **Innu said:**
> I have a server and many desktops/laptops.

What I want to do is that I'll create some users at the server. And all the other computers should be able to log in using it.

My first idea was that I'll mount the server /home directory with the sshfs. Then add users to /etc/passwd one by one.

Not sure if it works like this.

Are there better ways?

This may help:
[http://ubuntuforums.org/showthread.php?t=509618](http://ubuntuforums.org/showthread.php?t=509618)

---

### Post by HermanAB on 2009-08-12
The common UNIX way is to NFS mount the user home directories.

---

