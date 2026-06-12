---
title: "About wifi in Linux"
date: 2011-01-28
forum: General Help
---

### Post by Uvunter on 2011-01-28
Hello.

I'm using Linux Mint 10 with wifi connection. It works very well thanks to an user who explained to me how to have connection.

So, I write in a terminal:

```
lsmod | grep rt2
```

and the result was:

```
rt2870sta 405890 1 
crc_ccitt 1351 1 rt2870sta
```

So, I've blacklisted it, I've restarted the system, and the USB started working. I've configured my network, restarted the system again, and you know the rest :D

But this is not what I want to say. Well, if that worked in Linux Mint, I suppose that it will work in another distro, as Fedora, openSUSE or Slackware. What do you think?

I've seen this tutorial: [http://ubuntuforums.org/showthread.php?t=1342593]("http://ubuntuforums.org/showthread.php?t=1342593"), and I ask this because it's easier to blacklist a module than to compile a new kernel module :oops:

Maybe I'll change my distro.

---

