---
title: "Specifying a range"
date: 2010-05-21
forum: General Help
---

### Post by aabrego on 2010-05-21
Hi:

I'm running some shell script and need to include a range of number. I have been able to do so for two digit numbers (example 15 to 19) using:

... 1[5-9].

However, if I need to do it for a three digit numbers (220 to 260) this function does not work:

... 2[20-60].

Is there a way to do it?

Antonio

---

### Post by coslo on 2010-05-21
Yes, with bash you can specify integer ranges this way: {m..n}. In your example you would use {220..260}. That's pretty powerful!

---

