---
title: "Software center doesn't start"
date: 2010-01-09
forum: General Help
---

### Post by ok_dr on 2010-01-09
Hi all.
Suddenly I seem not to be able to start Ubuntu Software Center anymore. It worked ok for 2 months. When I try software-center in the Terminal here is what comes out.

 File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type

I tried reinstalling app-install-data as suggested in some other thread (same problem, different output though)to no avail. 
The only thing I can think to have triggered this problem is checking for updates, otherwise haven't done anything apart surfing the net and downloading torrents.
Hope someone can help me.

---

### Post by lyall on 2010-01-10
have you tried installing Software Center from Synaptic Package Manager?

if after trying to re-install it and it still does not work
try removing it and re-install it

good luck and have fun learning

---

### Post by Prominence on 2010-01-10
grayson@Providence:~$ software-center
/home/grayson/.themes/Wasp-Alt Alt/gtk-2.0/panels/panel.rc:7: Unable to locate image file in pixmap_path: "/panels/panel-bg-dark.png"
/home/grayson/.themes/Wasp-Alt Alt/gtk-2.0/panels/panel.rc:12: Unable to locate image file in pixmap_path: "/panels/panel-bg-dark.png"
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type

is what I got, this needs fixed

---

### Post by m4n_in_bl4ck on 2010-01-11
Check out the solution [here]("http://ubuntuforums.org/showpost.php?p=8626026&postcount=3"). ;)

---

### Post by ok_dr on 2010-01-15
Ok I solved it, but reinstalling software-center didn't work, and I didn't go through with the solution proposed in that other advised thread as it asked me if I wanted to uninstall some other things I didn't want to.
After I tried in vain reinstalling libwebkit 1.0.2 from synaptic, I tried instead downgrading it (Package/Force version) choosing karmic instead of the new version. It worked like a charm.

---

