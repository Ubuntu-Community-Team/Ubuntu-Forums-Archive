---
title: "How to Run Terminal Commands Synchronously ?"
date: 2010-04-30
forum: General Help
---

### Post by Jonah Bron on 2010-04-30
I've tried to google it, but couldn't find anything.  I've created a bash shell script, to open a few graphical programs.  Trouble is, the next one doesn't start until I close the first one.  How can I just skip to the next program?

Thanks!

---

### Post by viralmeme on 2010-04-30
> **Jonah Bron said:**
> I've tried to google it, but couldn't find anything.  I've created a bash shell script, to open a few graphical programs.  Trouble is, the next one doesn't start until I close the first one.  How can I just skip to the next program?

Thanks!

Put an ampersand in between the commands.


$gpicview &  galculator

---

### Post by Jonah Bron on 2010-04-30
Sweet, thanks!

:popcorn:

---

