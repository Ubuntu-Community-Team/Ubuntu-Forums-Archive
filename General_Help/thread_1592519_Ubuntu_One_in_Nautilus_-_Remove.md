---
title: "Ubuntu One in Nautilus - Remove?"
date: 2010-10-10
forum: General Help
---

### Post by isecore on 2010-10-10
Hi, just upgraded to Maverick from Lucid about two hours ago. Just discovered that there's an ugly and annoying Ubuntu One "toolbar" or whatever at the top of my Pictures folder. As far as I've noticed it also appears in the Music folder. Not sure if it's anywhere else.

How do I remove it? I don't use Ubuntu One and I want it gone. Thanks in advance!

---

### Post by howefield on 2010-10-10
Try Nautilus > File > Ubuntu One > Hide Ribbon. 

Just to say, that this will do only that - hide the ribbon, the ubuntuone-syncdaemon will still be running.

To remove Ubuntu One if you don't plan on using it try,

```
sudo apt-get purge ubuntuone-client
```

---

### Post by isecore on 2010-10-10
Thanks mate, I really should have looked more closely. I'm fine with it running, just as long as it's hidden. Appreciate the help.

Considered removing it all, but got lots of complaints about various dependencies so I'll leave it in place.

> **howefield said:**
> Try Nautilus > File > Ubuntu One > Hide Ribbon. 

Just to say, that this will do only that - hide the ribbon, the ubuntuone-syncdaemon will still be running.

To remove Ubuntu One if you don't plan on using it try,

```
sudo apt-get purge ubuntuone-client
```

---

### Post by Mrmental on 2010-10-11
Thanks mate.
Got to say - one of the reasons I like Ubuntu is the lack of preloaded crapware. Take heed, Canonical.

---

