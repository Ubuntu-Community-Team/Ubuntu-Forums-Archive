---
title: "partition question"
date: 2012-01-26
forum: General Help
---

### Post by mr.farenheit on 2012-01-26
its been awhile since i've done a multi boot on a single system and was thinking about installing an rpm based distro alongside ubuntu, main question, do i need to create a separate partition for install or can i just simple run them alongside each other?

---

### Post by MG&amp;TL on 2012-01-26
Separate partition. In two words. Short of virtualisation, wubi (neither of which applies to you), you always have to partition to run two OSs alongside.

---

### Post by mr.farenheit on 2012-01-27
thanks, good to know. i was curious because some times during an ubuntu install it would locate the primary partition and ask me if i wanted to run them alongside each other. i was planning on running fedora and didn't know if it would work the same way.

---

### Post by MG&amp;TL on 2012-01-27
> **mr.farenheit said:**
> thanks, good to know. i was curious because some times during an ubuntu install it would locate the primary partition and ask me if i wanted to run them alongside each other. i was planning on running fedora and didn't know if it would work the same way.

Ahh...you were talking about logical vs primary partitions?

In which case, any linux distro will happily install alongside another ina primary partition, they just need different logical partitions.

I thought you meant on-the-same partition. My bad. :)

---

