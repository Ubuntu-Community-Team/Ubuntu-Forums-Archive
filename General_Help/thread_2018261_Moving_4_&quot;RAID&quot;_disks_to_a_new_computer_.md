---
title: "Moving 4 &quot;RAID&quot; disks to a new computer - How to make sure it works?"
date: 2012-07-06
forum: General Help
---

### Post by Navigateur on 2012-07-06
Thinking in terms of the future, let's say I buy 4 external disks, set them up with Ubuntu software raid 1+0. Then later after some usage I want to stick them on a new computer - how do I ensure they work immediately?

If I just plug them into the fresh computer, will they automatically know how to relate to each other REGARDLESS of which order of external slots I plug them into? Or do I have to be careful to plug them in a certain port order?

If neither of these are guaranteed to work, then what steps must I take to ensure I get the Ubuntu up and running just as before? Please treat me as someone who needs all the steps and possibilities you know of.

---

### Post by greenfruitsalad on 2012-07-07
although it isn't strictly plug and play, you will be able to reuse your md raid array on other computers. raid partitions contain identifiers which tell mdadm what array they are a member of and which order they are in. it is literally a matter of 2-3 commands to attach and mount it on another machine.

---

