---
title: "Gwibber will not let me add a Facebook account"
date: 2010-10-10
forum: General Help
---

### Post by finnbuntu on 2010-10-10
Hello everyone,
I was adding a Facebook account to Gwibber (2.32.0.1) and I entered my details. The authentication was OK, but there was no Add button, so I couldn't add it. Please help me with this problem (or bug).
TIA,
Finnbuntu

---

### Post by xenton on 2010-10-10
> **finnbuntu said:**
> Hello everyone,
I was adding a Facebook account to Gwibber (2.32.0.1) and I entered my details. The authentication was OK, but there was no Add button, so I couldn't add it. Please help me with this problem (or bug).
TIA,
Finnbuntu

I was having the exact same problem, just solved it, but I'm running Gwibber 2.33.0 so follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1528374&highlight=gwibber+facebook") (the 3rd post down). 

Once your on the same version as me, try what i did.

Open a terminal and type

```
sudo gedit /etc/hosts
```

and edit according to [this post on facebook]("http://www.facebook.com/topic.php?uid=2877035514&topic=13264&post=56634")

(I had an entry near the top that wasn't 127.0.0.1 I changed it so it was)

click save.

I then also removed Gwibber and Gwibber Service from ***Applications>Ubuntu Software Centre*** then I reinstalled them. Then I did a restart and went to add facebook, this time there was an add button at the end of the process! :P

Hope this helps

---

