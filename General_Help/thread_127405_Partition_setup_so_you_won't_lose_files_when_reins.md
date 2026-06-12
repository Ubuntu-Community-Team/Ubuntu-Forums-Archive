---
title: "Partition setup so you won't lose files when reinstall/upgrade?"
date: 2006-02-08
forum: General Help
---

### Post by Protex on 2006-02-08
Hi guys.

What's the partition setup so that you won't lose files or configs when you update? I just recovered from a boo-boo and have /home on a seperate partition. It saved all the stuff there, but some installed programs like Firefox, Thunderbird, Azureus, Mercury messeger, etc, don't work anymore.

Is there a way to perserve these through an update?

---

### Post by dcstar on 2006-02-09
[QUOTE=Protex]Hi guys.

What's the partition setup so that you won't lose files or configs when you update? I just recovered from a boo-boo and have /home on a seperate partition. It saved all the stuff there, but some installed programs like Firefox, Thunderbird, Azureus, Mercury messeger, etc, don't work anymore.

Is there a way to perserve these through an update?[/QUOTE]
If you don't change the partition layout they should be preserved, otherwise you can change what is mounted as /home after you use a different location during the update.

---

### Post by aysiu on 2006-02-09
[QUOTE=Protex]
What's the partition setup so that you won't lose files or configs when you update? I just recovered from a boo-boo and have /home on a seperate partition. It saved all the stuff there, but some installed programs like Firefox, Thunderbird, Azureus, Mercury messeger, etc, don't work anymore.

Is there a way to perserve these through an update?[/QUOTE] What you want is not only a separate /home partition (for config files) but also a separate /usr partition (for all your programs).

---

### Post by Protex on 2006-02-09
And how big should that partition be?

---

### Post by lamego on 2006-02-09
Your problem is not just about the partitions but also about they way you have installed those apps.
Having a dedicated partition for /home is enough as long you install your apps inside it.
You can just create a /home/apps with the correct owner/permissions and install those (non-package installed) apps into it.

---

### Post by taurus on 2006-02-09
If you really want to do it, you could have partitions for

/
/boot
/var
/usr
/bin
/etc
/home
/opt

     Your kernel will go into /boot; most if not all your programs will go into /usr & /bin; system config files will be in /etc; log files will be in /var; user accounts will be in /home; and third party software will probably be installed in /opt...

---

