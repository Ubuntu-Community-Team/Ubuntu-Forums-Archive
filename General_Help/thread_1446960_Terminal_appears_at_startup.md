---
title: "Terminal appears at startup"
date: 2010-04-04
forum: General Help
---

### Post by Speedcuber on 2010-04-04
Hi, 

Every time I log in, a terminal appears on my screen. Previously, I attempted to embed a terminal as part of the desktop but I have deleted all the scripts and packages used, yet the terminal still appears. It is not an embedded terminal, but it does not have the panel at the top. It appears as a window on the lower panel of my screen. Is there anyway to stop this from appearing, so I can then attempt to start over with embedding a terminal in the desktop?

Thank you

---

### Post by RedSingularity on 2010-04-04
Have you checked your startup items to make sure that terminal is not listed there?

---

### Post by Speedcuber on 2010-04-04
Terminal is not in my start-up applications or in my rc.local file--I really do not know where it is coming from.

---

### Post by sisco311 on 2010-04-04
Xfce Menu -> Settings -> Session and Startup & make sure that the *Automatically save session on logout* is not selected.

Rename/Remove the ~/.cache/sessions directory. Log out and log back in.

---

### Post by Speedcuber on 2010-04-04
> **sisco311 said:**
> 
Rename/Remove the ~/.cache/sessions directory. Log out and log back in.

Hey, thanks! That worked!

---

### Post by sisco311 on 2010-04-04
> **Speedcuber said:**
> Hey, thanks! That worked!

You're welcome!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

---

