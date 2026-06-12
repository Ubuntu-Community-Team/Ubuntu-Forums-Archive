---
title: "kwrite non-advancing cursor"
date: 2011-07-14
forum: General Help
---

### Post by jktjs on 2011-07-14
I am running kubuntu 10.04 on an IBM Thinkpad laptop, and have an odd problem with kwrite. 

It sometimes gets into a state whereby the cursor does not advance after each keypress. The character is put in the correct place (to the right of where the cursor was), but the cursor does not move (so the character stays to the right of it). The results of any typing therefore appear **backwards**, for example:
H
eH
leH
lleH
olleH

This renders kwrite partially unusable for some time, as it is not straightforward to work around. It affects only part of a document, and fixes itself after 5-10 minutes. I have not spotted a clear pattern in when it appears or disappears, although it might be associated with a cut-paste from a terminal into the document with the middle mouse button.

Any ideas? 
Thanks.

---

### Post by enimeizoo on 2011-07-14
It would look like a qt problem if it wasn't restricted to kwrite. Could you try to use something else (like kate) and see if the problem remains?
I just found a bug report about it : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=598837](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=598837)
It is a quite old bug and someone is asking if it is still there. You could give them info about it.

The easiest solution would probably be to use another editor. By the way, is there a reason why you use kwrite? I'm just curious as I never really used it.

---

