---
title: "Cannot open Software Center"
date: 2010-10-24
forum: General Help
---

### Post by 16spendl on 2010-10-24
Hello!

I seem to have a problem with software center, it says "starting ubuntu software center" for about 10 seconds, then it closes. It was opening before, but now it wont. 

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 48, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 33, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 50, in <module>
    from  appdetailsview_gtk import AppDetailsViewGtk as AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py", line 45, in <module>
    from appdetailsview import AppDetailsViewBase
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 30, in <module>
    from purchasedialog import PurchaseDialog
  File "/usr/share/software-center/softwarecenter/view/purchasedialog.py", line 25, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: /usr/lib/libgnutls.so.26: symbol gcry_cipher_setkey, version GCRYPT_1.2 not defined in file libgcrypt.so.11 with link time reference
]
```
This is what I get in terminal when I try to open it. Also I think that this problem might be conflicting with other programs. I have tried many things, such as reinstalling python, libcrypt, and software center.

Please help if you can!

- Scott Pendleton
Thank you! :popcorn:

---

### Post by sikander3786 on 2010-10-24
Hi and Welcome to the forums :popcorn:

Try updating from the terminal and again start software center.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by 16spendl on 2010-10-24
> **sikander3786 said:**
> Hi and Welcome to the forums :popcorn:

Try updating from the terminal and again start software center.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Thanks for the reply!

Yes I have already done that, still I have a had no results. Seems that Python is acting up, don't know why though haven't use it that much.

---

### Post by sikander3786 on 2010-10-24
Is it Ubuntu or Mint? Which version?

---

### Post by 16spendl on 2010-10-24
I am using Ubuntu 10.10 Maverick

---

### Post by sikander3786 on 2010-10-24
In most cases, changing the update servers from Software Center > Edit > Software Sources and disabling any third party PPAs from Other Software tab solves the problem.

[http://ubuntuforums.org/showthread.php?p=8646848](http://ubuntuforums.org/showthread.php?p=8646848)

---

### Post by mc4man on 2010-10-24
Do you have any ppa's enabled - particularly  one that has any webkit related lib's

---

### Post by 16spendl on 2010-10-24
> **sikander3786 said:**
> In most cases, changing the update servers from Software Center > Edit > Software Sources and disabling any third party PPAs from Other Software tab solves the problem.

[http://ubuntuforums.org/showthread.php?p=8646848](http://ubuntuforums.org/showthread.php?p=8646848)

So basically install reinstall libsoup?

---

### Post by 16spendl on 2010-10-24
> **sikander3786 said:**
> In most cases, changing the update servers from Software Center > Edit > Software Sources and disabling any third party PPAs from Other Software tab solves the problem.

[http://ubuntuforums.org/showthread.php?p=8646848](http://ubuntuforums.org/showthread.php?p=8646848)

> **mc4man said:**
> Do you have any ppa's enabled - particularly  one that has any webkit related lib's

Hmm, no, at least not that I know of. I don't really do any web development. Is there anyways that I could check?

---

### Post by vysakh on 2011-03-13
This was very useful for me (usung ubuntu 10.10)...
software center problem was solved..

---

### Post by tinnudile on 2011-03-13
I was facing same problem in ubuntu 10.10 . But I found that it was due to new icon theme that I installed . When I reverted back to old theme , problem was solved .

---

