---
title: "Got myself into a jam"
date: 2012-03-01
forum: General Help
---

### Post by jazzD3 on 2012-03-01
Ok so...

I had been dualbooting xp and 10.04 with wubi.

I had decided to upgrade ubuntu so I ran the utility for that.

After asking around, a friend had told me to wait till the next version to do this (12.04?) as it would be lts

I rebooted X

Apparently the utility had deleted all my crucial ubuntu files.

Where should I go from here?

Thanks so much!

---

### Post by QIII on 2012-03-01
By "utility" do you mean 

```
sudo apt-get upgrade
```in the terminal,  an update option presented to you by Ubuntu (ie.: a message that updates were available) or some other method (ie.: running the Wubi installer again)?

---

### Post by jazzD3 on 2012-03-01
It was in the administrator menu I believe, under the update manager, had to do some fenagaling with the software sources so that it gave me the upgrade option. I must've let the utility delete the previous version and reset.

Now it goes to grub, and if I select ubuntu it goes to a menu that's missing pretty much everything and says to contact the system admin. 

Is there anyway to get into the terminal? Maybe I could do an apt-upgrade from there?

---

### Post by QIII on 2012-03-01
Windows update manager?

---

### Post by jazzD3 on 2012-03-02
No. Inside ubuntu there is an upgrade tool. I wish I could remember exactly what it's called. I either need to get into the terminal, back up my stuff, and reinstall ubuntu. Or I need to figure out how to grab my files from within windows and reinstall ubuntu.

---

### Post by winh8r on 2012-03-02
I would think that you were indeed using Update Manager and it would also put up a notification that a newer release of Ubuntu was available (which from 10.04 the upgrade would have been to 10.10). 
From what I gather in your first post you selected to "upgrade" rather than update and the upgrade procedure commenced, but if I understand correctly from what you have written, you were then advised to wait a while for the release of 12.04 the next LTS release, and rebooted your computer before the upgrade to 10.10 had completed.

Is this correct?

---

### Post by Retor on 2012-03-02
Perhaps this will make you able to get your files:

Download and create a bootable live CD:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)


Boot it and mount the wubi virtual disk by following the steps  under the subtitle "How can I access my Wubi install and repair my install if it won't boot?" on this page: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by QIII on 2012-03-02
> **jazzD3 said:**
> No. Inside ubuntu there is an upgrade tool.

Thank the fates -- maybe...

> **winh8r said:**
> From what I gather in your first post you  selected to "upgrade" rather than update and the upgrade procedure  commenced, but if I understand correctly from what you have written, you  were then advised to wait a while for the release of 12.04 the next LTS  release, and rebooted your computer before the upgrade to 10.10 had  completed.

Is this correct?

That's what I'm getting now.  Curse the fates?

---

