---
title: "ram almost completely eaten after update"
date: 2009-12-04
forum: General Help
---

### Post by slackthumbz on 2009-12-04
The most recent updates to karmic unr has had a somewhat deleterious effect on my system. The initial amount of ram used after boot has doubled. The machine in question is a relatively old netbook with only 512MB of RAM. I suspect the cause for this is the replacement of sreadahead with ureadahead although I can't be sure. 

Is there any way I can disable the readahead service altogether so that I can test this hypothesis?

---

### Post by slackthumbz on 2009-12-04
*bump*

This is rather disappointing. I can now only launch a couple of programs at a time otherwise what little RAM I have left is used and the system starts swapping like crazy, causing just about everything to grind to a halt. This makes me a sad panda.

---

### Post by Ancanus on 2009-12-04
> **slackthumbz said:**
> The most recent updates to karmic unr has had a somewhat deleterious effect on my system. The initial amount of ram used after boot has doubled. The machine in question is a relatively old netbook with only 512MB of RAM. I suspect the cause for this is the replacement of sreadahead with ureadahead although I can't be sure. 

Is there any way I can disable the readahead service altogether so that I can test this hypothesis?

Open your System Monitor (System -> Administration -> System Monitor) and tell which process is consuming your memory.

I believe that readahead only runs during booting so it should not be the culprit.

---

### Post by slackthumbz on 2009-12-04
I've already done this, I ran top and switched the sort field to memory and nothing appears to be out of the ordinary yet, almost all my memory is being used.

---

### Post by slackthumbz on 2009-12-04
A curious one this, it appears that rather than doing a straight restart it required a full shutdown and manual boot. After that it works fine. I can only guess that somehow the RAM cache isn't cleared properly when using the restart option from the system menu... Verry odd :s

---

