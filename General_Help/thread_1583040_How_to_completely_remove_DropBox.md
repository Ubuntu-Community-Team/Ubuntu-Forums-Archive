---
title: "How to completely remove DropBox"
date: 2010-09-27
forum: General Help
---

### Post by sosaudio1 on 2010-09-27
Love the idea....just need my own repository for storage away from the laptop....still have the deb on hand just in case I want to reinstall....

Here is my issue. I installed dropbox and removed it. I noticed in the first start of dropbox it installs a daemon called dropboxd. Is dropboxd removed when you uninstall? I uninstalled and purged. I just want to make sure the daemon is gone as well. Trying to be as tidy as possible. Less code rolling around the better.

Thanks
Rich

---

### Post by pricetech on 2010-09-27
[http://forums.dropbox.com/topic.php?id=2858#post-18076](http://forums.dropbox.com/topic.php?id=2858#post-18076)

It refers to Gutsy, but should work.

---

### Post by sosaudio1 on 2010-09-27
> **pricetech said:**
> [http://forums.dropbox.com/topic.php?id=2858#post-18076](http://forums.dropbox.com/topic.php?id=2858#post-18076)

It refers to Gutsy, but should work.

Cool did that....removed a few of the files in config and the home dir. Others look like icons here and there...But does that remove the dropboxd (daemon) file, app that is installed in the initial install and run of dropbox?

---

### Post by hrickh on 2010-09-27
> **sosaudio1 said:**
> Cool did that....removed a few of the files in config and the home dir. Others look like icons here and there...But does that remove the dropboxd (daemon) file, app that is installed in the initial install and run of dropbox?
Removing .dropbox and .dropbox-dist from your home directory will remove everything.

R.
==

---

### Post by sosaudio1 on 2010-09-27
> **hrickh said:**
> Removing .dropbox and .dropbox-dist from your home directory will remove everything.

R.
==

cool

---

