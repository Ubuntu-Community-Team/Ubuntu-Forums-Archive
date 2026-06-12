---
title: "Installing on a computer with little or no internet."
date: 2010-10-01
forum: General Help
---

### Post by Cityscape on 2010-10-01
Hi all. I live in northern Canada. I am not in a high speed internet zone but use an alternative method which I pay lots of money to get high speed. However I am restricted to 5 GB of traffic per month.

Now I have to computers running Ubuntu. So for example, if I want to install TuxPaint on my first PC then I would go to the software center and it would download then install the software for me. Now if I wanted to install the same program on my second computer it would download it again. The problem is that this would download twice as much from the internet. **Is there any way that I can save internet bandwidth by using the download files from my first computer to install the program on my second computer?**

Similarly, can I only download updates once but install them on both computers?

Thanks for your time,
Adam  ^_^

---

### Post by gandaran on 2010-10-01
> **Cityscape said:**
> Hi all. I live in northern Canada. I am not in a high speed internet zone but use an alternative method which I pay lots of money to get high speed. However I am restricted to 5 GB of traffic per month.

Now I have to computers running Ubuntu. So for example, if I want to install TuxPaint on my first PC then I would go to the software center and it would download then install the software for me. Now if I wanted to install the same program on my second computer it would download it again. The problem is that this would download twice as much from the internet. **Is there any way that I can save internet bandwidth by using the download files from my first computer to install the program on my second computer?**

Similarly, can I only download updates once but install them on both computers?

Thanks for your time,
Adam  ^_^
yes, just copy the downloaded packages from /var/cache/apt/archives to the other computer, put them in the same place then install normally just like you would install a package or updates.

---

### Post by btindie on 2010-10-01
Take a look at [AptProxy]("https://help.ubuntu.com/community/AptProxy") and [Apt-Cacher]("https://help.ubuntu.com/community/Apt-Cacher-Server"), also the [Package Management category]("https://help.ubuntu.com/community/CategoryPackageManagement") of the Ubuntu documentation.

---

### Post by sikander3786 on 2010-10-01
You can also try APTonCD.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

