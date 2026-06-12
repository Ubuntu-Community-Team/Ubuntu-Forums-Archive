---
title: "2 problems : Flash player in chromium and unable to delete software"
date: 2012-02-26
forum: General Help
---

### Post by holytree on 2012-02-26
How to get flash player in chromium ? i tried downloading it from the website but it says package operation failed andf frankly that message is coming for everything i try to download

and im unable to delete anything from the software center
please help

thanking you holytree

---

### Post by efflandt on 2012-02-26
Are you the original user or a user you set up as admin?  Or did you change anything in /etc/ related to sudoers.

It is best to install things from the **Software Center**, install **Synaptic** from there and use that, or using **sudo apt-get**.

If you download and install things by other means (like scripts) none of those methods may even be aware of that, so would not be able to remove such things you added.  You would have to check whatever you downloaded to see if it has a way to uninstall (likely using **sudo**) or you may have to manually remove what it installed.

In **Software Center**, **Ubuntu Restricted Extras** includes Flash, an open source java, and assorted useful codecs, or the separate **Adobe Flash plugin** (for mozilla) should automatically work for Chromium, as long as you have not installed a conflicting flash like plugin.

---

### Post by holytree on 2012-02-27
thanks for your time but my computer crashed and am using my laptop to post this and dont have ubuntu on it but thanks

SIncerely,
Holytree

---

### Post by cortman on 2012-02-27
Computer crash == reinstall.

Let us know if you have similar problems with the new installation.

Good luck!

---

