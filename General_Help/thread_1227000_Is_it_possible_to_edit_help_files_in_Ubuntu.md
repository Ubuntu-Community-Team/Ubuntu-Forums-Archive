---
title: "Is it possible to edit help files in Ubuntu?"
date: 2009-07-30
forum: General Help
---

### Post by rocket16 on 2009-07-30
Hello to all. My new customized Version of Ubuntu is nearly ready, but I wish to edit the Help Files, so that the people here (most of whom are novice in Computing, and Windows OS Users) could understand working in Ubuntu a bit better. Further, here English is not the first language of the people. So, I would like to rewrite the Help files to the standard of the dwellers here. What is the procedure then? Thanks all.

---

### Post by rocket16 on 2009-07-30
Thanks to anyone, who would like to help.

---

### Post by rocket16 on 2009-07-30
And sorry for using up too much space, but I need another information. That is, like Windows XP and Vista, which are found in Starter, Basic, Home-Premium, Ultimate, Business and Professional Edition, I also would like to create many editions of Ubuntu, such as Ubuntu Ultimate (which will include all packages, regardless of use), Ubuntu Educational Edition (for Childern, after adding some packages with Edubuntu), Business edition (mainly Financial Softwares) etc. But, unlike Windows Vista, I would like to include them all, packed up within a single DVD. In that DVD, I wish to include many Installation Choices, like Ultimate, Educational, Business etc. I wish to make it in a way, that there will be plenty f Packages in the disk, but for each Installation option, only specific packages will be install. In Ultimate, all will be installed. I think such a move, shall popularise Ubuntu to a tremendous extent. So, how may I do that? Thanks for any help.

---

### Post by rocket16 on 2009-08-01
Any help indeed?

---

### Post by Bucky Ball on 2009-08-01
You have a lot of re-writing to do. Open a terminal and type:

locate help

There's all your help files. Open them in your favourite text editor and away you go.

As for your custom editions, you need to turn them into ISO files and then burn them all to a bootable disk with a menu for selection of which version you want to install (or perhaps run 'Live'?). Putting all the ISOs on a DVD is easy, writing code to boot the disk and a install menu I know nothing about.

---

### Post by rocket16 on 2009-08-01
Thanks for your help!

---

### Post by rocket16 on 2009-08-01
Thanks!

---

### Post by Bucky Ball on 2009-08-01
Try:

```
dir /usr/share/gnome/help
```Not sure if they are in the same place in 9.04 and this isn't all of them but the ones for Gnome at least.

---

