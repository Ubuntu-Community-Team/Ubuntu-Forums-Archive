---
title: "[fbpanel] no menu"
date: 2006-04-22
forum: General Help
---

### Post by twirp on 2006-04-22
I tried to install fbpanel, but no menu was created.
Is there a way to uninstall, then reinstall?
I tried creating my own default profile in both ~/.fbpanel and then in /usr/share/fbpanel

OpenBox also didn't install a menu...

---

### Post by Sutekh on 2006-04-23
To reinstall try these commands to removce fbpanel and configs
```
sudo apt-get remove --purge fbpanel
rm -rf ~/.fbpanel/
sudo apt-get install fbpanel
```

I'll attach the default fbpanel config and my current panels (top and bottom in a XFCE kind of look) if you want to have a look.  I changed them to *.txt to attach them, you should remove the .txt extension if you want to use them.

I'm not sure why you didn't get the right-click menu in OpenBox though...

---

