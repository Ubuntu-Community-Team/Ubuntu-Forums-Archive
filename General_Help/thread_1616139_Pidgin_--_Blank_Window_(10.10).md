---
title: "Pidgin -- Blank Window (10.10)"
date: 2010-11-07
forum: General Help
---

### Post by gh4ever on 2010-11-07
Hi,
I'm running Pidgin 2.75 on Ubuntu 10.10, and suddenly one day Pidgin started showing a blank buddy list....
Pidgin always starts normally, but then after about 5 minutes, the buddy screen and any chat windows that are open turn blank...is there any way to fix this, or am I going to have to switch to Empathy?
The weird thing is that for about 4-5 days after upgrading Pidgin worked perfectly, but then it started having this issue...I don't recall updating Pidgin, but I don't remember....
So far I've tried using the Pidgin PPA to get a more current version of Pidgin (which is why I have 2.75), but it still doesn't work...any help, comments, or ideas would be greatly appreciated!
Attached is a picture of what it looks like.

---

### Post by gh4ever on 2010-11-08
Bump.

---

### Post by lkjoel on 2010-11-08
Try this in a Terminal window:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
You may have already done this.
Do this every day.
This command will completely update your system (including kernels)

---

### Post by gh4ever on 2010-11-08
Just did what you said and it looks like it just updated chromium and did nothing to Pidgin....
Some additional information: When I'm already talking to someone, it freezes, and if I try to open Pidgin from the taskbar, it shows up blank like in the screenshot.

---

### Post by gh4ever on 2010-11-09
Bump.

---

### Post by gh4ever on 2010-11-10
Any ideas at all?

---

### Post by gh4ever on 2010-11-11
Solved by uninstalling Pidgin, backing up /etc/purple/prefs.xml and ~/.purple and then deleting them, and then finally reinstalling Pidgin.

EDIT: Actually, I think it's caused by the gfire plugin...when I reinstalled it, Pidgin stopped working, but then when I reuninstalled it, Pidgin worked again.

---

### Post by lkjoel on 2010-11-11
> **gh4ever said:**
> Solved by uninstalling Pidgin, backing up /etc/purple/prefs.xml and ~/.purple and then deleting them, and then finally reinstalling Pidgin.

EDIT: Actually, I think it's caused by the gfire plugin...when I reinstalled it, Pidgin stopped working, but then when I reuninstalled it, Pidgin worked again.
Glad to know that you got it working again!

---

### Post by h1ll39 on 2010-11-20
I'm having the same issue in 10.04 and have the gfire plugin... Will have to try the purple thing and see if it works. Thanks.

---

### Post by gh4ever on 2010-11-20
I don't think it was the purple thing that fixed it, I'm 99% positive it was me uninstalling the gfire plugin. And no problem! Glad I could help.

---

### Post by h1ll39 on 2010-11-21
Does anyone know how to fix this without just removing the problem :(? I want to talk to my friends on xfire. I've tried reinstalling, the purple fix thing above, i upgraded to the newest version (I think it's the newest version)... idk what else to do.

---

### Post by gh4ever on 2010-11-22
I'm not really sure...you can check around for a different version of gfire. Maybe there's a PPA or something where there's a more updated version? Ask me if you need any more help!

---

### Post by Rumpanzle on 2010-12-05
I'm still having this problem (10.04-64 on i7-870, pidgin 2.7.7, gfire 0.8.3). Disabling a protocol isn't really solving it, just avoiding. I'm using the gfire and pidgin ppa's.

---

### Post by gh4ever on 2010-12-05
Again, I'm not really sure if there's a solution and what it is...I never use xfire anymore so I'm fine with just disabling it. Maybe you can try filing a bug report somewhere? Maybe on Pidgin's launchpad (or gfire if they have one?) I really don't know where you'd go for this issue...sorry :(.

---

### Post by rld on 2010-12-22
Found this thread through Google, and I'm having this problem on my netbook with 10.10 and my desktop with x64 10.04. Sometimes Pidgin will crash with no error message at all, not even while running it from a terminal. If Gfire is disabled or uninstalled, everything will work flawlessly.

Apparently the Ubuntu repos have a quite old version of Gfire. I just downloaded and updated it today and the Ubuntu version is 0.8.3-0ubuntu1, while the latest stable version on the [Gfire official page]("http://gfireproject.org/download/") is 0.9.2. There is also a Launchpad PPA for Ubuntu which contains stable and SVN versions, I guess I could try that and see how it works out: [https://launchpad.net/~gfire/+archive/gfire](https://launchpad.net/~gfire/+archive/gfire)

---

### Post by gh4ever on 2010-12-22
Alright, if it does anything, post back on this thread so people that need to use gFire'll know what to do :).

---

### Post by rld on 2010-12-23
Well, I've been using the stable ppa version and so far so good, no blank windows yet :D

I guess it works at least for me on my netbook, I've yet to try it on my desktop with 10.10 to make sure it's only gfire's fault.

---

### Post by gh4ever on 2010-12-23
Alright! Let us know how it goes!

---

### Post by rld on 2010-12-25
Well, I'm still having occasional crashes while having one Xfire account enabled which is only solved by doing 'killall pidgin', so that kind of sucks. The only real solution right now is having no Xfire accounts enabled or uninstalling gfire altogether. At least for me that is.

---

### Post by gh4ever on 2010-12-26
That's what it's been like for me, too.
Hey, does anyone know whether or not this thread should be marked as solved? This issue was solved for me by disabling gfire, but for other people (who actually still use xfire), this doesn't solve the issue.

---

