---
title: "Move encrypted home, make it home of multiple installations"
date: 2011-11-21
forum: General Help
---

### Post by Mappenz on 2011-11-21
Hi,

my old Ubuntu installation doesn't boot anymore. I installed a new ubuntu on a new partition. The old home is encrypted. I successfully accessed and backed it up. I set up a empty partition.

I found a few differing instructions on moving a encrypted home to a new partition, but theres a slight difference. I want to move the old home to the new Partition and make it the home of my new installation as well as the home of a installation I intent do do after the encrypted home is in its own partition.

---

### Post by mike555 on 2011-11-21
Not a good idea, different operating systems should not share a /home ......... too many hidden config files.
  that said, you could make a "backup" partition for all , but only backup your doc's and music (not whole home folder).

---

### Post by Mappenz on 2011-11-21
Good to know. Maybe thats why the second installation didn't log in after i tried. Then maybe i did something else wrong.

Would it work to backup the encrypted home of the broken installation. Reinstall and copy home back?
I still would like to have home on a separate partition but i could try this later.

---

### Post by mike555 on 2011-11-21
Actually having /home on a separate partition is not a good idea , it makes your hard drive work harder because the arm is going back and forth more ...... better to just use rsync and backup your important stuff to separate partition.

---

### Post by Mappenz on 2011-11-21
Thats interessting too. I read multiple times that a separate homepartition was a good thing.

---

### Post by Habitual on 2011-11-21
> **Mappenz said:**
> Thats interessting too. I read multiple times that a separate homepartition was a good thing.


+1 for separate /home and the time it SAVES when re-installing.

---

### Post by mike555 on 2011-11-21
Many people think a separate /home is good , because most people don't backup and when they have problems they are at a loss, but if you backup like everyone should it's better for your computer not to use separate /home ...

 besides reinstalling using your old /home is installing your old problems into the new install, most config files are in /home (hidden)and they often are the cause of trouble.

---

