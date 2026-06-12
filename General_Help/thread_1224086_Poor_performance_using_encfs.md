---
title: "Poor performance using encfs"
date: 2009-07-27
forum: General Help
---

### Post by azzid on 2009-07-27
Hi,

With a small fetish for being paranoid it was only natural for me to implement the following the other day: [https://wiki.ubuntu.com/EncryptedHomeFolder]("https://wiki.ubuntu.com/EncryptedHomeFolder").

It works real nice in most cases, but when I add a new item to my bittorrent client the whole machine gets really really slow. Like it will take a minute or two to open a new tab in firefox or so.

Is there some smart/easy way to give the UI higher priority so that I can sacrifice a little bit of I/O for the general user experience?

Also I find the poor performance a tad bit weird, because none of the hardware resources get maxed out, this is how the system monitor looks:
[ATTACH]122567[/ATTACH]

Sincerely,
Mattias

---

### Post by azzid on 2010-10-07
I just found the command **ionice**, it seems to be able to limit the implications of my ioissue.

Doing the following from the command line improved my desktop performance:
```

# ps aux | grep -i tran[s]
user   1930  0.3  0.7 443752 65332 ?        Sl   Oct06   3:28 transmission -m
# ionice -p 1930
none: prio 0
# ionice -c 3 -p 1930
# ionice -p 1930
idle

```

---

