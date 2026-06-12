---
title: "Customize run-level settings"
date: 2009-10-23
forum: General Help
---

### Post by gunksta on 2009-10-23
I think I am running into a upstart related issue. The problem is, I don't really understand how to tweak out upstart.

I have the postgre server installed on my laptop. I only use it when I'm away from the office and need to do some SQL work. Otherwise, I use the much faster server sitting next to my desk! I only use the postgres server once every couple of months (on the laptop). Because this is a laptop and I want to keep the start-up as lean/fast as possible.

Thus, I want to disable the postgres server from starting when I boot my laptop.

I browsed over to /etc/rc2.d and I can see a linked file called S19postgresql-8.4 (I'm running Karmic, although this isn't a Karmic specific question). This is clearly the script to start/stop postgres.

According to the README, I should be able rename this file to K19postgresql-8.4 and then run "update-rc.d script defaults" to reset the start order/dependencies.

But, I get an error when I try to run the script, because . . . . 

> update-rc.d: /etc/init.d/script: file does not exist

which is true.

So, how do I got about disabling postgres without breaking anything, while leaving enough behind that it's real easy to reset things to the default when I want to?

---

### Post by gunksta on 2009-11-17
bump.

While Upstart is a really neat tool, it's pretty danged complicated. If someone could throw me a link to a For Dummy's guide, I just want to be able to leave postgres installed on this machine, but not turned on automatically when my laptop starts.

Thanks

---

### Post by Aubergines on 2009-11-17
I've always done it the manual method, everything in rcX.d are simply symlinks to start up scripts in /etc/init.d.

You can simply delete /etc/rc2.d/S19postgresql-8.4 to prevent the script (or link) from running at boot time.

You can then manually start it whenever you need it by typing
```
sudo /etc/init.d/postgresql-8.4 start
```
If one day you want to postgres to boot at start up again just recreate the link with
```
sudo ln -s /etc/init.d/postgresql-8.4 /etc/rc2.d/S19postgresql-8.4
```

---

### Post by gunksta on 2009-11-17
Thanks! That's exactly what I was looking for.

---

