---
title: "issue opening hplip device manager"
date: 2009-12-04
forum: General Help
---

### Post by Lostin60's on 2009-12-04
My HP2110 printer works fine, the features I can get to work that is.  Running under ubuntu some of the buttons on the printer don't work. Up till now that has not been an issue as I scanned from the printer's device manager. However, now I can't bring up the manager.  Instead I get the following:
```
daniel@mypos:~$ hp-toolbox
Traceback (most recent call last):
  File "/usr/bin/hp-toolbox", line 39, in <module>
    from base import status, tui, module
  File "/usr/share/hplip/base/status.py", line 40, in <module>
ImportError: /usr/lib/python2.6/dist-packages/hpmudext.so: undefined symbol: hpmud_make_par_uri

```  I have googled for this issue, and it seems to be mine and mine alone...wheeee.  One thing I know, the "/usr/share/hplip/base/status.py" file does not exist.  And since I can't open the 2 related files in the error message, I am stumped.  If anyone has an idea how to correct this, I would be most appreciative.
[COLOR="White"]aa[/COLOR]

---

### Post by jbrown96 on 2009-12-04
Try reinstalling ```
sudo apt-get --reinstall hplip*
```

---

