---
title: "Google Chrome and Chromium crash on start up in 11.10"
date: 2012-01-05
forum: General Help
---

### Post by imcoma on 2012-01-05
I'm using Google Chrome on a desktop running Ubuntu 11.10. I've been using Chrome for a year or two and through several Ubuntu upgrades with no problems. A couple months after upgrading to 11.10, I noticed that Chrome started to crash occasionally, generally when I had multiple tabs open.
I tried uninstalling Chrome, and installing Chromium, and now Chromium crashes just seconds after startup. I've tried uninstalling, then purging it, and reinstalling it. Same problem. Google searches have helped me little.
I'm at a loss. I'd tried to switch back to Firefox, but I can't even find a way to export my bookmarks from Chrome to Firefox.
I currently have the google-chrome-stable package installed, and am having the same problem.

Any ideas?

---

### Post by rjf1 on 2012-01-05
> **imcoma said:**
> I'm using Google Chrome on a desktop running Ubuntu 11.10. I've been using Chrome for a year or two and through several Ubuntu upgrades with no problems. A couple months after upgrading to 11.10, I noticed that Chrome started to crash occasionally, generally when I had multiple tabs open.
I tried uninstalling Chrome, and installing Chromium, and now Chromium crashes just seconds after startup. I've tried uninstalling, then purging it, and reinstalling it. Same problem. Google searches have helped me little.
I'm at a loss. I'd tried to switch back to Firefox, but I can't even find a way to export my bookmarks from Chrome to Firefox.
I currently have the google-chrome-stable package installed, and am having the same problem.

Any ideas?

I had that problem with Chromium/Chrome. After I started getting the daily Chromium builds the problem went away. You can check out the daily builds here: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by imcoma on 2012-01-05
> **rjf1 said:**
> I had that problem with Chromium/Chrome. After I started getting the daily Chromium builds the problem went away. You can check out the daily builds here: [https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")

I removed google-chrome-stable and added the PPA for Chromium daily builds that you suggested. I installed Chromium from their archive aaand...same problem.

I start Chromium. The browser opens and looks fine for a moment. Sometimes I have to click on a link or two before it crashes. Sometimes not.

Still flustered.

---

### Post by rjf1 on 2012-01-06
Try deleting the chromium folder (it's inside your home folder's .config folder) before running Chromium.

---

### Post by imcoma on 2012-01-06
> **rjf1 said:**
> Try deleting the chromium folder (it's inside your home folder's .config folder) before running Chromium.

I've deleted my chromium folder before running chromium, but it doesn't change the situation.
This is odd though: I can open chromium and run searches and click on links and load pages, but the second I try to load twitter.com, or log into chromium sync, chromium is gone.
Is the crash related to pages with log-in forms?

---

### Post by rjf1 on 2012-01-06
> **imcoma said:**
> I've deleted my chromium folder before running chromium, but it doesn't change the situation.
This is odd though: I can open chromium and run searches and click on links and load pages, but the second I try to load twitter.com, or log into chromium sync, chromium is gone.
Is the crash related to pages with log-in forms?

Yes -- that's what used to happen to me -- it was ok on pages that I didn't need to sign into, but would immediately crash on pages as soon as I (or it automatically) started to sign in -- don't remember if it was only on pages that used my google account, but may have been.

---

### Post by nedkov on 2012-01-10
Somebody with solution for this problem? I hate other browsers and i don't want to use it.

---

