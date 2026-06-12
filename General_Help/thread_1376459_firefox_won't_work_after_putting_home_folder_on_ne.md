---
title: "firefox won't work after putting home folder on new partition"
date: 2010-01-09
forum: General Help
---

### Post by Mickser_52 on 2010-01-09
I have just finished transferring my home folder to a new partition. I did so by carefully following instructions on this link [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")
I had firefox open and was copying instructions one by one into an open terminal window.

When I tried to reboot ubuntu I first had a problem with ICEauthority which I think is now fixed and ubuntu then started as normal but when I tried to run Firefox I got a message saying that it was already open.

As I had Firefox open when I was copying files to the new partition  I assume that some setting was copied saying that Firefox was open?

Is it possible to simply adjust this setting or do I have to undo the transfer and repeat the process with firefox closed. 

I have not deleted my copy of the old home folder yet.

---

### Post by irishbreakfast on 2010-01-09
Try this:

[http://support.mozilla.com/en-US/kb/Firefox+is+already+running+but+is+not+responding](http://support.mozilla.com/en-US/kb/Firefox+is+already+running+but+is+not+responding)

---

### Post by HiImTye on 2010-01-09
try
```
sudo chown -R <name> /home/<name>
```where <name> is your username

---

### Post by Mickser_52 on 2010-01-09
Thanks HiImTye, I tried your suggestion. Stangely although I got a permission denied message, Firefox is now working and so is Thunderbird which was not responding either.

---

### Post by dcstar on 2010-01-10
> **Mickser_52 said:**
> I have just finished transferring my home folder to a new partition. I did so by carefully following instructions on this link [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")
I had firefox open and was copying instructions one by one into an open terminal window.
.........

I hope you put /home on a Linux filesystem.

---

### Post by Mickser_52 on 2010-01-10
Hi David,
Yes the partition is formatted linux ext3. One other point in case someone else has a similar problem... When I did get firefox to work it behaved as if it was just installed with no sites in history. Because I had not deleted my old home folder copy I was able to copy profiles.ini from the old folder to the new home partition firefox folder and again had history favourites etc.

---

