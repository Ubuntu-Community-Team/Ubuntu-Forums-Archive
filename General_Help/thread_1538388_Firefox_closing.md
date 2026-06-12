---
title: "Firefox closing"
date: 2010-07-25
forum: General Help
---

### Post by patman0623 on 2010-07-25
Ever since automatic upgrade to Firefox 3.5 (or is it 3.6, I can't remember, it's been a few months), Firefox hasn't prompted me on closing. This is a problem because Ctrl-W (close tab) is right next to Ctrl-Q (close Firefox).

In edit...preferences, I have "warn me when closing multiple tabs" checked, and about:config... browser.warnOnQuit is set to true. What's going on and how can I fix it?

---

### Post by lovinglinux on 2010-07-25
You also need to set **browser.tabs.warnOnClose** to **true** to make it work.

---

### Post by patman0623 on 2010-07-25
> **lovinglinux said:**
> You also need to set **browser.tabs.warnOnClose** to **true** to make it work.It is set to true already.

---

### Post by lovinglinux on 2010-07-25
> **patman0623 said:**
> It is set to true already.

That and **browser.warnOnQuit**?

I tested here. It should be working.

Try to create a new profile only to see if the problem persists. You can do that through the Profile Manager.

```
firefox -P
```

---

### Post by patman0623 on 2010-07-25
> **lovinglinux said:**
> That and **browser.warnOnQuit**?

I tested here. It should be working.

Try to create a new profile only to see if the problem persists. You can do that through the Profile Manager.

```
firefox -P
```Your above command did not start the profile manager.

---

### Post by lovinglinux on 2010-07-25
> **patman0623 said:**
> Your above command did not start the profile manager.

You need to close Firefox and make sure the process firefox-bin is not running. Otherwise you can use this:

```
firefox -no-remote -P
```

That will force it to start, even if Firefox is already running.

---

### Post by patman0623 on 2010-07-25
> **lovinglinux said:**
> You need to close Firefox and make sure the process firefox-bin is not running. Otherwise you can use this:

```
firefox -no-remote -P
```

That will force it to start, even if Firefox is already running.Yes, that worked. Now I'd sure like to know how to get it ported over to my current profile; I don't know if it's a plugin issue (I have several) or a bug.

---

### Post by patman0623 on 2010-07-25
FYI, I have tried disabling each of the add-ons, and none of them seem to be the problem.

---

### Post by lovinglinux on 2010-07-25
> **patman0623 said:**
> FYI, I have tried disabling each of the add-ons, and none of them seem to be the problem.

If you don't want to create  a new profile, close Firefox, move the file **prefs.js** from it to a safe place and restart Firefox. It will use the default settings. If that doesn't work, then put the **prefs.js** file back.

---

### Post by patman0623 on 2010-07-25
It's worked; I'm not happy with the way it's reset many of my settings (e.g., all my noscript info), but it'll do, thanks.

---

### Post by lovinglinux on 2010-07-25
> **patman0623 said:**
> It's worked; I'm not happy with the way it's reset many of my settings (e.g., all my noscript info), but it'll do, thanks.

Some extensions, like NoScript, have their own settings backup feature. Put the prefs.js file back into your profile, export NoScript settings, put the new prefs.js and import NoScript settings.

---

### Post by patman0623 on 2010-07-25
> **lovinglinux said:**
> Some extensions, like NoScript, have their own settings backup feature. Put the prefs.js file back into your profile, export NoScript settings, put the new prefs.js and import NoScript settings.I thought of that too. However, for your future reference, it appears that NoScript uses a combination of both: when I moved prefs.js back, my NoScript and Auto Pager preferences were still reset. It looks like it's necessary to backup the add-ons before removing the prefs file.

---

### Post by lovinglinux on 2010-07-25
> **patman0623 said:**
> I thought of that too. However, for your future reference, it appears that NoScript uses a combination of both: when I moved prefs.js back, my NoScript and Auto Pager preferences were still reset. It looks like it's necessary to backup the add-ons before removing the prefs file.

You need to restart to see changes when replacing the prefs.js. In fact, you should do it with Firefox closed.

---

### Post by patman0623 on 2010-07-25
> **lovinglinux said:**
> You need to restart to see changes when replacing the prefs.js. In fact, you should do it with Firefox closed.I know :). I think it has some sort of checksum in prefs.js, or stores it across both, and if they don't match, it will erase the information.

---

