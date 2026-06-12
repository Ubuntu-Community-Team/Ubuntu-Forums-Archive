---
title: "Starting MySQL from a launcher?"
date: 2010-07-27
forum: General Help
---

### Post by Dngrsone on 2010-07-27
I am running Ubuntu 10.4LTS AMD-64 on an HP Pavilion DV4Z-1200 with (currently) with 2GB RAM.

I installed LAMP for use in a WordPress local installation.

The latest update (I got it on the morning of 26th July) did something to the MySQL daemon so that it no longer starts on boot.

This is fine, I don't load up WordPress all the time and I don't need the resource load.  However, I would like to be able to call MySQL up on-demand, as it were, using the launcher I am using to open up the WordPress blog, or through its own launcher, if it is possible.

Can anyone help me?

---

### Post by Dngrsone on 2010-07-31
Wow, three days and only 30 views... I sure know how to write a title, huh?

Maybe if I just shorten it a bit, I will get some kind of response.

---

### Post by WorMzy on 2010-07-31
Well, you know the command to start MySQL, right? I believe that it's
```
sudo service mysql start
``` on Lucid.

So you can right-click on the panel and create a new "Application in terminal" with that command. Or you can try creating a graphical sudo prompt by using "gksu service mysql start" with a normal application launcher.

---

### Post by Dngrsone on 2010-07-31
Thank you.  That is exactly what I need.

---

