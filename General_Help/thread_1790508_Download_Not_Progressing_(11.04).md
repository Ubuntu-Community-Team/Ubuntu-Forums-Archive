---
title: "Download Not Progressing (11.04)"
date: 2011-06-25
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2011-06-25
I started downloading something in Software Center last night. The download was going very slowly, so I left it and went to bed. This morning, I see that the download hasn't progressed past where it was last night, about 50%. 

I'm not sure if it is related, but this happened shortly after I added natty-proposed to my update sources. I tried un-adding it. I also tried letting Software Center select the best server. Apparently, neither of these attempts can have any effect because the cache needs to be updated, which can't happen until the download is finished. I had also added this file:

Package: * Pin: release a=natty-security Pin-Priority: 990  Package: * Pin: release a=natty-updates Pin-Priority: 900  Package: * Pin: release a=natty-proposed Pin-Priority: 400



in /etc/apt so I wouldn't be prompted for software updates from natty-proposed. I tried moving it to another directory, but the download is still stuck.
What should I do?

---

