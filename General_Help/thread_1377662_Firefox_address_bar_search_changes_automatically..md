---
title: "Firefox address bar search changes automatically."
date: 2010-01-10
forum: General Help
---

### Post by bhishan on 2010-01-10
I use google search in the firefox address bar by pasting "http://www.google.com/search?btnG=Google+Search&q=" in about:config > keyword.URL

But it automatically changes to "chrome://browser-region/locale/region.properties" in some hours or the next day and I cannot search using the address bar. I have to change it back again to make it work. This is really annoying.

Anyone got a solution?

---

### Post by y-lee on 2010-01-12
> **bhishan said:**
> Anyone got a solution?

Strange problem, and I am not sure I have a solution but i do have a few ideas on things you can check or do:


A few more **about:config** options you could check

[LIST]
[*]**browser.search.defaultenginename**  should say Google

[*]**browser.search.order.1**   should say Google

[*]**browser.search.selectedEngine**  you may not have this but if you do should say Google
[/LIST]

and of course be sure **keyword.URL** is properly set.

If that fails you could try a search in **about:config** for **chrome://browser-region/locale/region.properties** to see if this value shows up in any *unusual* place. You should be able to tell because the status would be User set instead of default. Any place chrome://browser-region/locale/region.properties shows up and is not a default value change back to the default for that entry.

Honestly this sounds like an add-on problem most likely (in windows I would also suspect malware but hopefully this is not the case here). The ask tool bar, for example, has been reported as causing this problem. How many add ons do you have installed? If you have the ask tool bar uninstall it. Also uninstall or disable any plugin you do not need. If you are not sure google the plugins name to see if it is necessary.

A few other things ...

Have you tried creating a new [firefox profile]("http://support.mozilla.com/en-US/kb/Managing+profiles")? Your new profile will have no addons installed.

To create a new profile, be sure Firefox is closed and then open a terminal and paste the code below in the terminal window and hit enter:

```
firefox -P
```

See if the new profile has the same problem.

Or Firefox's [firefox's safe mode]("http://support.mozilla.com/en-US/kb/Safe+Mode")? You can disable all your addons in safe-mode or reset all about:config preferences.

To open firefox in safe mode, be sure Firefox is closed and then open a terminal and paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
firefox -safe-mode
```


Hopefully, this helps, let us know. And if not, I can probably think of a few more things we could try.

---

### Post by warfacegod on 2010-01-12
Click the icon next to it and select manage search engines. Move google to the top of the list. That worked for me when I started using ixquick.

---

### Post by bhishan on 2010-01-12
@y-lee: thanks for the reply. I think I recently installed a toolbar, I will remove and see if it works. Thanks!

---

