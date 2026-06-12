---
title: "Installede edubuntu package, want normal logo back"
date: 2006-06-29
forum: General Help
---

### Post by Ketrel on 2006-06-29
I installed the edubuntu package so I could get all the tools that it does without manually installing them all.  After I did that, I noticed that some of the branding images have changed such as when I shut down and boot up.

I was wondering how I can get those back to the default for a normal ubuntu installation.

---

### Post by no1wantdthisname on 2006-06-29
```
sudo update-alternatives --config usplash-artwork.so
```
and select usplash-default.so.

---

### Post by Ketrel on 2006-07-12
according to the system, I'm now using the default, however I'm still getting Edubuntu splash screens

---

