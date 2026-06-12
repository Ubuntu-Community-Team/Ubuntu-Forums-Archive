---
title: "Update/SOftware Help!"
date: 2011-06-02
forum: General Help
---

### Post by ddavid82 on 2011-06-02
When i go to the software center or update manager and try to tell it to install something, the authentication window pops up and shakes back and forth and disappears, even if i click it before. To go around this i have been using terminal to install any programs i want with apt-get or apt-cache search to find them but i do not know how to do this with updates. This is really inhibiting my use of ubuntu please tell me how to fix it. I am running 11.04 Ubuntu

---

### Post by akand074 on 2011-06-02
> **ddavid82 said:**
> When i go to the software center or update manager and try to tell it to install something, the authentication window pops up and shakes back and forth and disappears, even if i click it before. To go around this i have been using terminal to install any programs i want with apt-get or apt-cache search to find them but i do not know how to do this with updates. This is really inhibiting my use of ubuntu please tell me how to fix it. I am running 11.04 Ubuntu

```
sudo apt-get upgrade
```

will update all your packages that have a new version

---

### Post by ddavid82 on 2011-06-02
Thanks, that was really fast! It updated but is there a way to fix the authentication pop-up?

---

### Post by akand074 on 2011-06-02
> **ddavid82 said:**
> Thanks, that was really fast! It updated but is there a way to fix the authentication pop-up?

Probably... I don't know how though, it's never happened to me. I find issues like that just tend to go away for me without me doing anything :S. Perhaps someone else might have had this issue. I always recommend you try to make your thread title as detailed as possible about your issue. You'd be more likely to get someone who actually knows how to fix it or has had the issue before to actually find it and read it.

---

### Post by iclestu on 2011-06-02
try these

```
sudo dpkg --configure -a
```
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
```

---

### Post by itzmeharish on 2011-09-21
This did not solve the problem for me. Im also having the same problem of "authentication window pops up and shakes and goea away". Please suggest some thing so that ill recover it and use ubuntu efficiently.

---

