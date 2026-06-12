---
title: "Firefox bookmarks gone after automatic update"
date: 2009-07-22
forum: General Help
---

### Post by Dark Angel on 2009-07-22
This morning I allowed the system to update Firefox.  The manager wanted to update to FF v 3.0.0.12 which I thought nothing of.    After the update, however, I have lost ALL of my bookmarks, including many necessary for my university studies.  I them seemed to recall that the standard version was 3.5 ... something.  

Seriously ... what the ... ?????

What happened??  And more to the point, whose "clever" idea was is to regress to a version that is incompatible with the previous one?

---

### Post by jerrrys on 2009-07-22
theres a hidden file in your home directory named  **.mozilla  **your bookmarks should be there

---

### Post by Dark Angel on 2009-07-23
They are, but the version of Firefox that was installed by the updates won't restore them from backup or import them.  At all.  Period.  It also doesn't show a home page.  I have bypassed the issue by installing the now unsupported version 3.5.1 (which picked up all my bookmarks instantly) and have changed it to my default browser.

---

### Post by Dark Angel on 2009-07-23
Ok, firstly a correction:  I was using 3.0.0.11 before, not 3.5.  Sorry about that.

Next additional information:  This is specific to the 64bit version (I allowed the same updates on a 32bit machine and it worked fine)  I have also tried to add new bookmarks to the 3.0.0.12 (64bit) that I have now on THIS machine and it will not accept new bookmarks either.  I conclude that this indicates the entire bookmark subsystem in the 64bit version is broken somehow.

---

### Post by lovinglinux on 2009-07-23
> **Dark Angel said:**
> Ok, firstly a correction:  I was using 3.0.0.11 before, not 3.5.  Sorry about that.

Next additional information:  This is specific to the 64bit version (I allowed the same updates on a 32bit machine and it worked fine)  I have also tried to add new bookmarks to the 3.0.0.12 (64bit) that I have now on THIS machine and it will not accept new bookmarks either.  I conclude that this indicates the entire bookmark subsystem in the 64bit version is broken somehow.

See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

### Post by nikhilk on 2009-07-23
> **Dark Angel said:**
> Next additional information:  This is specific to the 64bit version (I allowed the same updates on a 32bit machine and it worked fine)  I have also tried to add new bookmarks to the 3.0.0.12 (64bit) that I have now on THIS machine and it will not accept new bookmarks either.  I conclude that this indicates the entire bookmark subsystem in the 64bit version is broken somehow.

See if there is a bug filed on Launchpad for that already, if not file a new one. But first check if the original Mozilla version has the same problem. This [link]("http://www.psychocats.net/ubuntu/firefox") should be helpful if you give that a try.

---

### Post by Dark Angel on 2009-07-23
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

Thankyou Thankyou Thankyou Thankyou! :D

---

### Post by lovinglinux on 2009-07-23
> **Dark Angel said:**
> Thankyou Thankyou Thankyou Thankyou! :D

You are welcome :)

---

