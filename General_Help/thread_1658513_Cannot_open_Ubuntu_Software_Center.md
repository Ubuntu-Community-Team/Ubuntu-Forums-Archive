---
title: "Cannot open Ubuntu Software Center"
date: 2011-01-02
forum: General Help
---

### Post by hackNperl on 2011-01-02
I seem to have broken the Ubuntu Software Center by adding the Linux Mint repositories and installing the mint-menu package.  When I click on Ubuntu Software Center it changes my cursor and shows it in the windows list for about 10 seconds like it is going to open but never does.  I tried removing the mint-menu package and all of the mint packages, I reinstalled software-center andall of the ubuntu keyring packages.  Still not able to open the software center.:confused:

---

### Post by hackNperl on 2011-01-02
I notice when i ```
sudo apt-get install --reinstall software-center
```

It seems to install and run several scripts and in the end it gives me something like this:

```
Processing triggers for python-support ...
Setting up software-center (3.0.7) ...
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 34, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 41, in <module>
    from softwarecenter.db.database import parse_axi_values_file
  File "/usr/share/software-center/softwarecenter/db/database.py", line 26, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 31, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 127, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 116, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint

```

I opened up the __init__.py file to try and see where it was coming up with the distro name of Linux Mint.  I couldn't figure it out.  Is there a way to change my distro name back to Ubuntu and reinstall software center?  I should have never installed that stupid Linux Mint menu!!!](*,)

---

### Post by hackNperl on 2011-01-02
Also, when i type software-center in a terminal I get this:

> tony@sqone-office:~$ software-center
2011-01-02 22:47:42,808 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2011-01-02 22:47:42,808 - root - WARNING - No styling hints for SmoothGNOME were found... using Human hints.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 220, in __init__
    self.navhistory_forward_action)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 101, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 112, in _build_ui
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 251, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 434, in build
    self.categories = self.parse_applications_menu(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 109, in parse_applications_menu
    category = self._parse_menu_tag(child)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 265, in _parse_menu_tag
    query = self._parse_include_tag(element)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 226, in _parse_include_tag
    return self._parse_and_or_not_tag(include, query, xapian.Query.OP_AND)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 173, in _parse_and_or_not_tag
    or_elem = self._parse_and_or_not_tag(and_elem, xapian.Query(), xapian.Query.OP_OR)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 213, in _parse_and_or_not_tag
    q = self.db.xapian_parser.parse_query(s, xapian.QueryParser.FLAG_WILDCARD)
AttributeError: 'StoreDatabase' object has no attribute 'xapian_parser'


---

### Post by hackNperl on 2011-01-03
Well I have tried numerous things and I am now giving up.  I am actually considering a distribution which is a little more customizable.  It seems I am starting to outgrow Ubuntu after 3 years anyway.  Always running into headaches trying to compile certain packages and trying to do some basic things that seem simple on other distros.  I was considering FreeBSD but I think that will cause many more problems in the long run...  I'm kind of thinking of going with Debian 5 seen as i need to reinstall to fix this problem either way... i don't know... just thinking out loud i guess....

---

