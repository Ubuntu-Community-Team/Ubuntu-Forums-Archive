---
title: "Ubuntu Software Center Ubuntu crashing in 10.10"
date: 2010-12-16
forum: General Help
---

### Post by hman1169 on 2010-12-16
I am a little better than a beginner but not much... Just did a fresh install of 10.10 in a brand new Computer. (AMD on ASUS) Everything seems to be working fine, but the Ubuntu Software Center says it's starting then... nothing. So I read through some of the posts here and tried all the remedies but they are all something different than the problem I am having, I even tried to remove it with Synaptic Package Manager, reboot then install it again... Still nothing improved.

So the last thing I have done so far is this...

gksudo software-center

and the results are:

Traceback (most recent call last):  File "/usr/bin/software-center", line 88, in <module>
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
  File "/usr/share/software-center/softwarecenter/view/purchasedialog.py", line 23, in <module>
    import simplejson
ImportError: No module named simplejson

And this is a language I don't understand.

Can anyone teach or help me with this?

thanks, 

Chris

---

### Post by hman1169 on 2010-12-16
OK, I don't know what caused it yet, but I just booted from the Live CD, and installed it again, without deleting the home partition and everything is working. I would bet there is a better way to fix it but that worked for me.

---

### Post by fizmhd on 2011-03-15
Solution is here

[http://ubuntuforums.org/showthread.php?p=10562520#post10562520](http://ubuntuforums.org/showthread.php?p=10562520#post10562520)

---

