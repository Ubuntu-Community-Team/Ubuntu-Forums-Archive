---
title: "Trouble installing Java"
date: 2010-03-10
forum: General Help
---

### Post by nickguletskii on 2010-03-10
Sorry if it has been solved before, but I am having problems installing Java runtime on karmic. The problem is: jre depends on the bin, and the bin depends on the jre package... Anyway to solve that? Should I try forcing? :(

I can't get Ubuntu to connect to the internet, so I downloaded the deb packages and put them on a USB stick.

---

### Post by scouser73 on 2010-03-10
Here you go, the advice on the website will show you how to set up the latest version of Java: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by nickguletskii on 2010-03-10
> **scouser73 said:**
> Here you go, the advice on the website will show you how to set up the latest version of Java: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Thanks, I will try that. Paradox: this package requires another package that requires this package.

---

### Post by 3rdalbum on 2010-03-10
> **nickguletskii said:**
> Thanks, I will try that. Paradox: this package requires another package that requires this package.

It seems like a paradox, but it's not really. It means that both packages should be installed at the same time.

```
sudo dpkg -i package1.deb package2.deb
```

You can specify multiple packages to be installed simultaneously, or a whole directory's worth:

```
sudo dpkg -i *.deb
```

---

