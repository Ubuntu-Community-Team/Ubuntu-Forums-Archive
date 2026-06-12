---
title: "gdebi package isntaller"
date: 2012-06-05
forum: General Help
---

### Post by freefixkorma on 2012-06-05
hi there i am sorry i bug with this questions i was trying to use gdebi package installer but every time i open it it freezes or the window open but cant access any of the options can i open it in terminal i will appreciate . how to open in terminal thanks guys
running on ubuntu 12.04 

freefix

---

### Post by snowpine on 2012-06-05
You can open gdebi from the terminal with:

```
gksu gdebi
```

If it crashes then there will be error messages in the terminal to help you troubleshoot.

You can also install a package named "foo" directly from the terminal with:

```
sudo dpkg -i foo.deb
```

In general however, you do not need to download .debs from the internet and install them with gdebi or dpkg, because thousands of trusted applications can be easily installed through the Software Center. :)

---

