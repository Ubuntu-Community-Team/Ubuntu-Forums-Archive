---
title: "Xmarks won't stop asking for psswrd in Firefox"
date: 2010-04-27
forum: General Help
---

### Post by ubunterooster on 2010-04-27
...and won't sync. password is correct as I can log in to the xmarks site. Other pc's using same acct are fine. I removed and reinstalled xmarks but no difference. Chromium works fine on same computer. .xsessions has no recent errors except for that of the samba share going down when one pc died(unrelated problem).
Any ideas?

---

### Post by wilee-nilee on 2010-04-27
> **ubunterooster said:**
> ...and won't sync. password is correct as I can log in to the xmarks site. Other pc's using same acct are fine. I removed and reinstalled xmarks but no difference. Chromium works fine on same computer. .xsessions has no recent errors except for that of the samba share going down when one pc died(unrelated problem).
Any ideas?

I had this happen a couple of days ago, basically it was a password corrupt that, xmarks could not recognize so just wouldn't work.
Here are three links, the site is down for work at the moment though.
[http://getsatisfaction.com/foxmarks/top](http://getsatisfaction.com/foxmarks/top) ... on_error_4
[http://getsatisfaction.com/foxmarks/top](http://getsatisfaction.com/foxmarks/top) ... t_foxmarks
[http://www.xmarks.com/help](http://www.xmarks.com/help)

Basically in the end I removed the key3.db file in FF this removes all the passwords it seems it was a password corruption that xmarks just wasn't tough enough to deal with, wimpy thoughtless programs. Oh wait I'm the wimpy thoughtless one. I had saved the bookmarks onto the computer with an export 1st, and some where in this process I got all the passwords back. I then did a run the wizard on the all OS that I have installed 4 in all to wipe the overwrite all with the same download. the 1st link was where I got the file removal from. The key3.db is rebuilt.

This is a bug they are working on, it was posted as fixed 
but was not so they are still at fixing it

---

### Post by ubunterooster on 2010-04-27
THX. will remove key3.db

BTW: your first two links only describe how I feel currently... LOL

---

### Post by ubunterooster on 2010-04-27
Thanks Wilee. See you around :D

---

### Post by wilee-nilee on 2010-04-27
> **ubunterooster said:**
> Thanks Wilee. See you around :D

Since the site was down I had to just copy & paste from another forum. Glad you got it fixed. I purged all thing FF to start with and spent about 3 hours figuring this out so that it worked for me.

---

