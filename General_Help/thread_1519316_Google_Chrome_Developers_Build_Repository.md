---
title: "Google Chrome Developers Build Repository"
date: 2010-06-28
forum: General Help
---

### Post by Klaw117 on 2010-06-28
Does anyone know the repository for the developers version of Google Chrome? The installation adds the repository for the stable build and my developers build version isn't updating itself, so I would really appreciate it if someone could tell me what the repository is.

---

### Post by Coplen on 2010-06-28
[http://build.chromium.org/buildbot/snapshots/](http://build.chromium.org/buildbot/snapshots/)

---

### Post by warfacegod on 2010-06-28
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by Klaw117 on 2010-06-28
Thanks a lot guys.

---

### Post by warfacegod on 2010-06-28
Sure thing. If that link is what you were looking for you could mark this thread as Solved under Thread tools so that someone else can benefit as well.

---

### Post by Klaw117 on 2010-06-28
Oh wait, I just noticed these repositories are for Chromium, not Google Chrome. Will they still work?

---

### Post by CoreyB. on 2010-06-29
> **Klaw117 said:**
> Oh wait, I just noticed these repositories are for Chromium, not Google Chrome. Will they still work?

Chromium is Chrome, but without the built-in updater (Ubuntu manages that on it's own) and usage tracking (Google keeps track anonymously of what you are doing).  So think of Chromium of Chrome, but better! :guitar:

---

### Post by Klaw117 on 2010-06-29
> **CoreyB. said:**
> Chromium is Chrome, but without the built-in updater (Ubuntu manages that on it's own) and usage tracking (Google keeps track anonymously of what you are doing).  So think of Chromium of Chrome, but better! :guitar:
So are you saying to just get rid of Google Chrome and install Chromium instead? That didn't really answer my question of whether or not the repositories will still work. I'm guessing they don't since the version numbers on my Windows and my Ubuntu partitions are different. The Chrome version in Windows is 6.9.447.0 dev while the version in Ubuntu is 6.0.437.3 dev and I can't update it in the Update Manager.

---

### Post by warfacegod on 2010-06-29
Everything I've just read indicates that the chrome/chromium ppa is one and the same. Apparently the two names are totally interchangable and frankly it looks like a source of serious confusion.

---

### Post by Klaw117 on 2010-06-29
> **warfacegod said:**
> Everything I've just read indicates that the chrome/chromium ppa is one and the same. Apparently the two names are totally interchangable and frankly it looks like a source of serious confusion.
In that case, I'll just keep Chrome on, wait a few days/weeks and see if it updates after a while. If not, I'll just go to Chromium since I don't like having a browser that won't update. Thanks for clearing this up.

EDIT: Ok, it turns out that Google's repository ([http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main) will actually update the developers and most likely beta (I only use the developers version, so I'm not 100% sure about the beta) versions of Google Chrome as well even though it says "stable" in the repository. Therefore, you don't need the Chromium repository in order to update Google Chrome.

---

