---
title: "being monitored"
date: 2011-01-18
forum: General Help
---

### Post by themutt22 on 2011-01-18
hey guys i have a few questions.... i have ubuntu 10 on my computer at work. now im going to admit ive never been the keen user of ubuntu or linux for that matter. ive always had it but never used it extensively. and the obvious question pops up since i finished all my assignments for this week at work-could my computer be monitored and how do i find out if it is. i noticed that its got teamviewer installed but other than that-no clue. is there a quick and easy way to find out??? thanks!

---

### Post by nerdy_kid on 2011-01-18
it is probably not, but you could do this:

```

sudo apt-get install nmap

```
and then
```

nmap localhost

```
and see what spits out.  That is a port scan of your computer, and if the "bad guys" have installed a monitoring program it should show up there.  Just post the output and I'll tell you if there are any unusual ones.  Then, if you want to, run

```

sudo ufw enable

```

to enable Ubuntu's firewall, which is disabled by default.  Note that by enabling it you can cause some things to not work, such as Samba (windows shares), ssh, etc.

---

