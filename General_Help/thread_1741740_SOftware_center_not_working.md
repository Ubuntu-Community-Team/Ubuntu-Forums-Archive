---
title: "SOftware center not working"
date: 2011-04-28
forum: General Help
---

### Post by ravitejamulpuri on 2011-04-28
I just have  installed Ubuntu 11.04 and changed all my proxy settings to that of 10.10..(software center used to work with these settings in 10.10)...but when i tried to install  softwares via software center it is just showing "In Progress" for a fraction of second and it disappears....synaptic is not running and i even restarted the system for several times...any idea how to overcome this???

---

### Post by Rubi1200 on 2011-04-28
Try this in the terminal:

```
sudo apt-get update 
```

Then start the software center again and see if the problem persists.

Hope this helps.

---

### Post by ithejdi on 2011-04-30
Had this happen to me today on xubuntu. Tried the command listed above and no results. I was moving some files over from an external hard drive. Came back and it looks like everything crashed. After a reboot my Software Center just hangs and never loads.

---

### Post by therrmann on 2011-05-01
Software center is not working for me either.  I tried apt-get update but after it loads the files it says
Fetched 181 kB in 7s (25.3 kB/s)                                               
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Now I cannot open Synaptic at all.

I have just intalled xubuntu on my Asus netbook out of curiousity.  However it does not have any of my frequently used productivity software, so if I can't get this working I'm going back to vanilla Ubuntu with Gnome.

---

### Post by Pazystamas on 2011-05-03
Same for me, instaled 11.04 and now software center cant start. in console i got error:
```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 52, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 35, in <module>
    from softwarepane import SoftwarePane
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 49, in <module>
    from purchaseview import PurchaseView
  File "/usr/share/software-center/softwarecenter/view/purchaseview.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.7/webkit/__init__.py", line 21, in <module>
    import webkit
ImportError: libicui18n.so.42: file not found

```

In libicui there is no libicui18n.so.42 file, where can i find it?

---

### Post by Fungle10 on 2011-05-03
This happened to me an hour ago, What I did was reinstall Ubuntu but this time I checked the "Install updates while downloading" box and it seemed to have fixed everything, Personally I reckon it was Ubuntu One that messed up mine..

Hope this helps

---

### Post by udayarr on 2011-05-11
same here but unable to recover..any ideas would be appreciated

---

### Post by Pazystamas on 2011-05-29
I fixed software centre.. It looks like on natty it uses lib from lucid. Natty uses libicu44 and lucid uses libicu42 which has lib libicui18n.so.42. So i downloaded lib from here [http://packages.ubuntu.com/ca/lucid/libicu42](http://packages.ubuntu.com/ca/lucid/libicu42) (i use 64bit version) and software centre now works!.

---

