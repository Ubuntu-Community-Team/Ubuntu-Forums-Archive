---
title: "Can't open hard drive partitions from places menu."
date: 2011-04-03
forum: General Help
---

### Post by Tyler Kessler on 2011-04-03
Ubuntu 10.10
I would like to access the partitions of my hard drive from the Places menu. They show up there, but when I click them, the menu just closes. I can access them by navigating Places>Computer>"Drive_Name" but it would be more convenient. I was able to access them before, but something has apparently changed..

Thanks in advance for the help.

---

### Post by 311005901 on 2011-04-03
Sorry you're having problems.

Sometimes Nautilus messes up and needs to be restarted. If you open a terminal, type ```
nautilus -q
``` and retry.
If that doesn't work, try logging in and logging back out.

---

### Post by Tyler Kessler on 2011-04-03
> **311005901 said:**
> Sorry you're having problems.

Sometimes Nautilus messes up and needs to be restarted. If you open a terminal, type ```
nautilus -q
``` and retry.
If that doesn't work, try logging in and logging back out.

No luck..

---

### Post by 311005901 on 2011-04-03
I would suggest deleting your .nautilus file under /home/USER/.nautilus .

This clears out the cache and it will rebuild automatically.

---

### Post by Tyler Kessler on 2011-04-03
> **311005901 said:**
> I would suggest deleting your .nautilus file under /home/USER/.nautilus .

This clears out the cache and it will rebuild automatically.

I deleted it, logged out and back in, but it doesn't work. .nautilus showed back up, but it shows up as an empty directory.

---

### Post by 311005901 on 2011-04-03
Don't worry about your .nautilus folder being empty. It will fill up with stuff after you use Nautilus for a while.

Are you using the most recent version of Nautilus? Have you updated in a while?

---

### Post by Tyler Kessler on 2011-04-03
> **311005901 said:**
> Don't worry about your .nautilus folder being empty. It will fill up with stuff after you use Nautilus for a while.

Are you using the most recent version of Nautilus? Have you updated in a while?

Would that be accomplished through the Update Manager or through Terminal? Update Manager says I'm up to date.

---

### Post by Tyler Kessler on 2011-04-03
I just discovered that all of the locations in the Places menu (excluding Computer) are inaccessible, not just hard drive partitions. I don't know if that makes a difference or not.

---

### Post by Tyler Kessler on 2011-04-23
Upgraded to 11.04. Everything works now.

---

