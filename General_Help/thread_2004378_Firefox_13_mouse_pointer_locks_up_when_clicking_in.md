---
title: "Firefox 13 mouse pointer locks up when clicking in bookmarks toolbar (Ubuntu 12.04)"
date: 2012-06-15
forum: General Help
---

### Post by cwmccabe on 2012-06-15
Occasionally, when I click on a link in my FF13 bookmarks toolbar, the mouse pointer changes to the grabbing hand icon but will not release.  When this happens, I can move the mouse around but cannot click on anything in Firefox or anywhere else in the Ubuntu GUI.  I can still use some (not all) keyboard navigation, but the mouse pointer seems to be permanently locked.  I end up having to Ctrl+Alt+t to open a terminal, where I can find the Firefox process ID and kill it.  Has anyone else experienced this, or is there a known solution?

I cannot recreate this bug on demand.  It doesn't happen each time I click on links in the bookmarks toolbar.  Maybe 1 in 20+ times.

**_EDIT (add'l info): _**  I use the Ghostery add-on and Firefox Sync.  Also, this lock-up has occured on two separate installations of 12.04, one a laptop and the other a desktop.

---

### Post by EgillSkallagrimsson on 2012-06-16
I'm having the same thing happen. You can also hit alt+f and go to exit with the keyboard. Quicker than your current method. I hope somebody finds an actual solution because it is quite annoying.

---

### Post by AVH on 2012-06-16
Same problem here in Lucid. Has anyone filed a bug report on this.

---

### Post by colin.p on 2012-06-17
I have a similar, if not entirely related issue. However, I "THINK" I have narrowed it down to Newsfox as it (so far) "seems" to only happen when I am using it. It doesn't happen all the time though. But the same symptoms as the posts above.

---

### Post by rlapa on 2012-06-19
Have a farm with +400 centrallized users with Lucid and Firefox 13 acessing it via NX.

This behaviour is happening at least 5 times a day, on random users.

It happens even with only one tab, no addons.

---

### Post by PypeBros on 2012-06-26
Happens here as well. Ubuntu LTS "Lucid", ia32, since upgrade to firefox 13.0

I can reproduce it fairly consistently in the old blogger post-edition interface: all I have to do is to select a block of text, click the "insert link" button, and then try to scroll with the mouse wheel.

---

### Post by Seb71 on 2012-06-26
Happens in Firefox in Xubuntu 12.04 too. Never happened to me in previous Ubuntu releases (but that may be because of older versions of Firefox).

---

### Post by PypeBros on 2012-06-26
> **AVH said:**
> Same problem here in Lucid. Has anyone filed a bug report on this.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1017913](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1017913) has just been filed.

---

### Post by skinnersbane on 2012-06-29
So, I see the bug report, which is actually a duplicate of [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1012257](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1012257)

The bug says fix released, but I don't think I've received a fix through the normal repos.  It happened to me today and my software is up to date.  Does anyone know what that means?  I thought Fix released meant that a software update would fix it for good (assuming the bug is actually fixed completely).

---

### Post by colin.p on 2012-07-01
Not too sure yet, but I updated Newsfox to 1.0.8.4 beta 1, and for the past two days, no freeze ups. I don't know if that was it, or another update from update mgr "fixed" it. I'll report back if FF freezes up again and the circumstances when it does.
BTW, FF is at version 13.0.1

update:
It is now July 3 and so far no freeze ups whatsoever.
It is now July 8 and no freeze ups, so whatever was causing it FOR ME, is now solved. Hopefully, this is my last edit for this subject.

---

### Post by skinnersbane on 2012-07-01
Yeah, I have FF 13.0.1 with Ubuntu 12.04 x64, so pretty much standard.

---

### Post by ieee488 on 2012-07-02
Happened again to me this morning.

I don't have Newsfox.

It is quite annoying.

It happens when clicking any link not just bookmarks toolbar.

Ubuntu 11.04  32-bit

---

### Post by cwmccabe on 2012-08-15
Followup-- I no longer have the problem described in my first post.  It must have been fixed.

I still do have a related issue:  I have folders of bookmarks on my bookmarks toolbar and subfolders within those.  Sometimes when I click on a subfolder, the pointer "grabs" the folder rather than clicking it.  The folder then gets carried along with mouse movements and accidentally deposited elsewhere.  This is not nearly as concerning as the original freezing problem, but might be helpful info for anyone looking into it.

---

