---
title: "firefox troubles connecting to my bank"
date: 2010-02-15
forum: General Help
---

### Post by gustengroda on 2010-02-15
Dear forum members,
I have some problems with my web browser. I use it to connect to my web based bank. It has been working out fine until I installed a deb package with came with a more secure login method (using some kind if USB dongle).

The dongle-stuff didn't work out and I removed the package "dpkg -r packagename".

My trouble now is that when I browse to the log-in page of my bank it get stuck connecting to some server. I guess some part of that plug-in or whatever software I installed is remaining. As a consequence I cannot use my bank (with the old login way either). Firefox just freezes.

Well, I tried to remove whatever firefox is "apt-get remove --purge firefox". Works fine but firefox is still functional after I removed it. 

Another clue is that the issue persists when I log in as another user, hence it is not a personal setting.

Any advice is apreciated!

---

### Post by gustengroda on 2010-02-15
Some things to add. I managed to remove firefox
apt-get remove --purge firefox-3.5

Still after re-installation the problem persists.
In opera I have no issues.

Please advice me how to wipe out any corrupt settings.

---

### Post by lovinglinux on 2010-02-15
> **gustengroda said:**
> Some things to add. I managed to remove firefox
apt-get remove --purge firefox-3.5

Still after re-installation the problem persists.
In opera I have no issues.

Please advice me how to wipe out any corrupt settings.

Start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and start it. If that works, then you could copy only the settings you need from the old profile to the new one.

---

### Post by gustengroda on 2010-02-15
I tried to create a new profile. The same happends with a fresh one.
I also noticed that firefox does not end propoerly nowdays (=after I install that deb package). When I shut down my computer there is a dialoge stating stating that firefox hasn't ended.

suggestions welcome!

---

### Post by lovinglinux on 2010-02-15
Try [this](http://lovinglinux.megabyet.net/?page_id=220#Web-sites-keeps-loading-but-never-show-up-2) and [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-(grey)-frequently-2).

> **gustengroda said:**
> I also noticed that firefox does not end propoerly nowdays (=after I install that deb package). When I shut down my computer there is a dialoge stating stating that firefox hasn't ended.!

Open the System Monitor and kill *firefox-bin*.

---

### Post by gustengroda on 2010-02-15
I updated the settings as described for ipv6 and the security items. Still I have the same troubles.

---

### Post by lovinglinux on 2010-02-15
> **gustengroda said:**
> I updated the settings as described for ipv6 and the security items. Still I have the same troubles.

Have you installed the software provided by your bank again?

---

### Post by gustengroda on 2010-02-15
No. I didn't. The thing is that everything worked fine with the old log-in method. I just want to get back to where I were... :/

---

### Post by lovinglinux on 2010-02-15
> **gustengroda said:**
> No. I didn't. The thing is that everything worked fine with the old log-in method. I just want to get back to where I were... :/

Perhaps you should contact your bank IT department.

---

### Post by mkvnmtr on 2010-02-15
Perhaps you should remove the .moxilla file in the home directory. It will then be regenerated. You will loose your bookmarks if you do not save them.

---

### Post by lovinglinux on 2010-02-15
> **mkvnmtr said:**
> Perhaps you should remove the .moxilla file in the home directory. It will then be regenerated. You will loose your bookmarks if you do not save them.

The OP already done that.

---

### Post by gustengroda on 2010-02-16
I did some further investigations and it turns out that there are two pieces of software. one driver for the dongle and a utility called nexus personal. When I uninstall nexus personal things work to some extent. I can use the dongle without USB cable connected which gives me some limited access to the bank.

Using chrome browser instead of firefox gives the same bahaviour.

I read some forums (in swedish) and someone posted an email from the bank that basically said that ubuntu 9.04 works fine but there is something bogus in the combination of 9.10, firefox, nexus personal and the driver.

any clues?

---

