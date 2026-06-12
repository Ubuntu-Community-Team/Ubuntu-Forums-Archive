---
title: "init: ureadahead-other main process (814) terminated with status 4"
date: 2011-05-20
forum: General Help
---

### Post by ergo-proxy on 2011-05-20
I found below message in my boot.log, is it anything serious??


init: ureadahead-other main process (814) terminated with status 4

---

### Post by Rubi1200 on 2011-05-20
Hi,
does the computer boot normally? How often do you see this message?

Take a look here for more information:
> [B]ureadahead exits with status 4!

[/B]Status 4 (usually ureadahead-other exits with this) means that you had a  mountpoint in your fstab that didn't have any files on it needed during  boot.  Probably that drive with all those MP3s and movie files on it.
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

If you have any more questions, feel free to ask.

---

### Post by ergo-proxy on 2011-05-21
Hi, thx for the answer, yesterday I found the link you provided. As I understand there is nothing to worry about, my computer boots normally though the message appears each I restar it

---

### Post by Rubi1200 on 2011-05-21
Great, glad you found the answer.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by ergo-proxy on 2011-05-21
Done ;)

---

