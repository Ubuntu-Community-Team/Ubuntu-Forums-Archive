---
title: "Software centre empty ?"
date: 2011-06-05
forum: General Help
---

### Post by Bruv on 2011-06-05
I have been using Software centre tonight, just having look around to see what I might need.
It appeared to hang and so I rebooted, then when I went back it seemed to hang again so I went to Synaptic and chose to re-install, hoping to repair anything that may have been broken.

Now when I load the program there is nothing there to see.

Help please

---

### Post by wildmanne39 on 2011-06-05
> **Bruv said:**
> I have been using Software centre tonight, just having look around to see what I might need.
It appeared to hang and so I rebooted, then when I went back it seemed to hang again so I went to Synaptic and chose to re-install, hoping to repair anything that may have been broken.

Now when I load the program there is nothing there to see.

Help please
Hi try this command
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by Bruv on 2011-06-06
That did the trick, thank you very very much

---

### Post by wildmanne39 on 2011-06-06
> **Bruv said:**
> That did the trick, thank you very very much
Hi, your welcome,would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

