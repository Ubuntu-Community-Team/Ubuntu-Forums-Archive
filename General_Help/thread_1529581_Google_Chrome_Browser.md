---
title: "Google Chrome Browser"
date: 2010-07-12
forum: General Help
---

### Post by kkimes on 2010-07-12
I'm not sure if I have a problem or if this is a 'feature' of 10.04.  After installing a new harddrive and installing 10.04 for the first time, I went to google and downloaded and installed the correct version of the Chrome browser.

I can use it and everythings works just fine.  The problem is that after I reboot the computer, the icon for the chrome browser is no longer there and I have to do a reinstall to be able to use it.  Is anyone else having this problem?  Is there a workaround?  I have never had this problem with any other program I'm installed in Ubuntu.

Note, I had installed and used Chrome for a year or more under 8.10 and never had a problem.

PS I did a search in the forums and nothing came up about this problem.

---

### Post by ricardino on 2010-07-12
when you say the icon is no longer there, do you mean in the applications menu? 

also if you open a terminal and type google-chrome do you get any response? 

can you confirm if your using the official google chrome, or the open source chromium variety?

---

### Post by Irony on 2010-07-12
You don't have to re-install - all thats happened is that the icon disappeared not the whole program.

Just go to;

```
System > Preferences > Main Menu > Internet > New Item
```

And add;

```
/opt/google/chrome/google-chrome %U
```

Click the icon button navigate to add an icon;

```
/usr/share/icons/hicolor/48x48/apps/google-chrome.png
```

And that's it.

---

### Post by kkimes on 2010-07-12
Thanks Irony.  That worked.  The test will be when I reboot to see if it is still there.  If so, I'll mark the thread resolved.

---

### Post by kkimes on 2010-07-13
Irony.  Just want to say that your solution worked.  It was all still there when I rebooted.  Not sure why it was acting so weird when I installed Chrome.  I've never seen that before.

---

