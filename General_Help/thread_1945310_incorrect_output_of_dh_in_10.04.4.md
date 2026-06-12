---
title: "incorrect output of dh in 10.04.4"
date: 2012-03-22
forum: General Help
---

### Post by serp2002 on 2012-03-22
Hallo!

When i use dh -h in console it show me incorrect information. 

For example i have /home partition. Size of /home is 500Gb. I have approx 400Gb of my files on it partition, but when i input df -h in console, it tells me:

99% available free space.

On other hand, i have few servers on 8.04.4 and 10.04.4 and on it all fine.

from wich source df got information about free space?

---

### Post by dcstar on 2012-03-23
> **serp2002 said:**
> Hallo!

When i use dh -h in console it show me incorrect information. 

For example i have /home partition. Size of /home is 500Gb. I have approx 400Gb of my files on it partition, but when **i input df -h in console**, it tells me:

99% available free space.

On other hand, i have few servers on 8.04.4 and 10.04.4 and on it all fine.

from wich source df got information about free space?

Post the output.

---

### Post by serp2002 on 2012-03-23
Sorry, i found problem.
It's buggy localization, columns in output of command is shifted.

---

