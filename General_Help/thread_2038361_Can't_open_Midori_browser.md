---
title: "Can't open Midori browser"
date: 2012-08-06
forum: General Help
---

### Post by geovino on 2012-08-06
I've just installed Midori browser to try it out and after install I get this error:

Error - file:///usr/share/ubuntu-artwork/home/index.html

The page 'file:///usr/share/ubuntu-artwork/home/index.html' couldn't be loaded.

Error opening file: No such file or directory

Why would I need this file for Midori? How do get it to open?

running Ubuntu 12.04 64bit

---

### Post by Toz on 2012-08-10
That's a bug ([https://bugs.launchpad.net/ubuntu/+source/midori/+bug/950285]("https://bugs.launchpad.net/ubuntu/+source/midori/+bug/950285")). The file doesn't exist. Just change your homepage to something else and you won't see it again.

---

### Post by geovino on 2012-08-10
> **Toz said:**
> That's a bug ([https://bugs.launchpad.net/ubuntu/+source/midori/+bug/950285]("https://bugs.launchpad.net/ubuntu/+source/midori/+bug/950285")). The file doesn't exist. Just change your homepage to something else and you won't see it again.

How would I change the home page if its never been opened before?

Do you mean change the home on Chrome or Firefox?

---

### Post by Toz on 2012-08-10
Sorry, I meant to say start page. The default start page in Midori points to a non-existant file. In Midori, go to the preferences page and change your start page to another url. This will get rid of the message.

---

### Post by geovino on 2012-08-10
> **Toz said:**
> Sorry, I meant to say start page. The default start page in Midori points to a non-existant file. In Midori, go to the preferences page and change your start page to another url. This will get rid of the message.

but Midori doesn't open. I just get that error. Is there a way to open it?

---

### Post by Toz on 2012-08-10
After you start Midori and see the error message, click on the icon in the top right-corner of the Midori screen (the Menu icon), select Preferences and make adjustments on the Startup tab.

---

### Post by geovino on 2012-08-10
> **Toz said:**
> After you start Midori and see the error message, click on the icon in the top right-corner of the Midori screen (the Menu icon), select Preferences and make adjustments on the Startup tab.

Thanks. I got it working now. Too bad about the bug, many people won't use it until they fix the bug.

[solved]

---

### Post by vasa1 on 2012-09-17
> **geovino said:**
> Thanks. I got it working now. Too bad about the bug, many people won't use it until they fix the bug.

[solved]
Don't mark it [solved] in your post alone. Go up to near the top right of the page and look for **Thread Tools**. It's one of the options in the dropdown. Do it from there.

---

