---
title: "Java Web Start Problems"
date: 2009-10-15
forum: General Help
---

### Post by cincinnatus on 2009-10-15
I used to be able to launch a certain Java Web Start application, but now it won't work. It gives me a message saying "Unable to launch the application", and then if I click on "Details" it gives me this:
```
CouldNotLoadArgumentException[ Could not load file/URL specified: /home/***/.java/deployment/cache/6.0/21/6152f355-7b90e1b9]
at com.sun.javaws.Main.launchApp(Main.java:268)
at com.sun.javaws.Main.continueInSecureThread(Main.java:219)
at com.sun.javaws.Main$1.run(Main.java:107)
at java.lang.Thread.run(Thread.java:619)
```

How do I make it work again?

---

### Post by cincinnatus on 2009-10-16
I think this happened because I installed SCIM, using [this guide]("https://help.ubuntu.com/community/SCIM"). Or at least it happened *after* I installed SCIM. And I can't figure out how to get SCIM to work either. Does SCIM have anything to do with Java? I don't really know what I'm doing...

Help!

---

