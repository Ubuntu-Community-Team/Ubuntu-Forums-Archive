---
title: "Evolution receives but won't send."
date: 2010-07-05
forum: General Help
---

### Post by dluzius on 2010-07-05
Evolution receives messages, but won't send email.
I think I set it up properly, ie.. outgoing   smtp.comcast.net
I'm using Ubuntu 10.04 LTS and Evolution 2.28.3
Ive googled for the solution with no success, and couldn't find an answer doing a search in Ubuntuforums. What could possibly be wrong?
  Dave

---

### Post by plucky on 2010-07-06
> **dluzius said:**
> Evolution receives messages, but won't send email.
I think I set it up properly, ie.. outgoing   smtp.comcast.net
I'm using Ubuntu 10.04 LTS and Evolution 2.28.3
Ive googled for the solution with no success, and couldn't find an answer doing a search in Ubuntuforums. What could possibly be wrong?
  Dave


Use ```
smtp.comcast.net:587
``` as the server address as you need to use port 587 without SSL encryption according to the comcast help site.


Good Luck

---

### Post by Tallorder64 on 2010-07-18
I have the same problem but with Verizon.  I have spent about 100 hours trying everything I could and still cannot get my mail to send.

---

### Post by joaotoscano on 2011-12-15
Hi everybody

Evolution receives messages, but won't send email.
I'm using Ubuntu 10.04 LTS and Evolution 2.28.3
I think I set it up properly, ie.. outgoing smtp.live.com

Ive googled for the solution with no success, and couldn't find an answer doing a search in Ubuntuforums. What could possibly be wrong?

Joao Toscano

---

### Post by lisati on 2011-12-15
Old thread.

The settings for hotmail accounts can be found at [http://explore.live.com/windows-live-mobile-hotmail-pop-settings-phone-faq](http://explore.live.com/windows-live-mobile-hotmail-pop-settings-phone-faq)

Set server to **smtp.live.com:25** with **TLS** for the security, your Windows live (Hotmail) email address for the username and plain login.

---

