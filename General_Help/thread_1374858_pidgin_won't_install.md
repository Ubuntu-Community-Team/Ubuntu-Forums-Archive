---
title: "pidgin won't install"
date: 2010-01-07
forum: General Help
---

### Post by Spug on 2010-01-07
I recently upgraded from 8.04 to 9.10 (yeah, I know, long leap), and pidgin was uninstalled in the process, for some reason. Now I can't reinstall it. When marking pidgin for installation, Synaptic gives me the following error:

> Depends on: pidgin-data (<1:2.6.2-z) but 1:2.6.4-1ubuntu3~pidgin3.8.04 is to be installed

I see that it says 8.04 in there, so I thought I maybe had some old repositories activated, but I don't. Does anyone have a clue?

---

### Post by MelDJ on 2010-01-07
maybe you can refresh your sources by doing sudo apt-get update then try installing.
if that doesn't work, try adding the getdeb repo and get pidgin from there. See: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

---

### Post by howefield on 2010-01-08
Follow the instructions on the Pidgin website to add the repositories. 

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

---

