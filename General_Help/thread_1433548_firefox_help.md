---
title: "firefox help"
date: 2010-03-19
forum: General Help
---

### Post by Doug11 on 2010-03-19
Just wondering,,when i minimize a page in firefox,,it disappears,,i have to start firefox again with my homepage,,is there a way to stop this,,i dont see it in my toolbar or anything?

---

### Post by wojox on 2010-03-19
Sounds like you Windows List is missing. Right click you bottom panel Select Add to Panel And add Windows list.

---

### Post by lovinglinux on 2010-03-19
I don' understand the description of your problem.

You don't minimize a page, you minimize Firefox windows. Pages in Firefox are opened in new windows or new tabs. 

If you open a page on a new window, then you can minimize the window containing that page. I this case, the minimized window should remain available in the Gnome panel. If not, then verify if you have the "Window List" applet or something like that in your panel.

If you open a page on a new tab, then you can't minimize it. Nevertheless, you can close it, by clicking the "x" button on the right side of the tab. If this is what you are doing, then the problem is that if you have only one tab open and then close it, then Firefox will close too by default. To change that behavior, type **about:config** in the address bar, then locate **browser.tabs.closeWindowWithLastTab** and set it to **false**, by right-clicking it and selecting the **Toggle** option.

---

### Post by Doug11 on 2010-03-20
> **wojox said:**
> Sounds like you Windows List is missing. Right click you bottom panel Select Add to Panel And add Windows list.
Thank you,,that was the problem.

---

### Post by wojox on 2010-03-20
You're welcome. ;)

---

