---
title: "Anyone know of a good beginners guide to xargs"
date: 2011-07-06
forum: General Help
---

### Post by CaptainMark on 2011-07-06
Just like the title says im looking to get to know xargs better but cant find any "xargs for dummies" guides.

---

### Post by TeoBigusGeekus on 2011-07-06
If you want to use it with find, what's wrong with the exec option?

---

### Post by nothingspecial on 2011-07-06
xargs isn't just for find, although the internet would have you believe that.

There's nothing to it really.

command | xargs command

It takes the output of one command and uses that as the arguments for another command.

What don't you understand?

---

### Post by CaptainMark on 2011-07-07
i was looking for something that could teach me more than that, i understand it can be a very powerful tool if used properly

---

### Post by gmargo on 2011-07-07
Start with the **xargs(1)** man page.

---

