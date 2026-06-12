---
title: "Sharing not retained"
date: 2010-06-06
forum: General Help
---

### Post by KMJones1 on 2010-06-06
Ref; Ubuntu 10.04 new clean installation, fully updated.
I have set sharing for some folders so they can be seen on my windows network ethernet.
However the sharing option is lost when I next turn on the computer. Can I make the sharing permanent?

---

### Post by HermanAB on 2010-06-06
Configure Samba to start at boot.

---

### Post by KMJones1 on 2010-06-06
Thanks! How do I do that?

---

### Post by KMJones1 on 2010-06-06
OK I think I found the way. I added a Startup item with command
sudo etc/init.d/samba start
Seems to work.

---

### Post by Morbius1 on 2010-06-06
I'm glad you got it working but I don't think it's because of this:
```
 sudo /etc/init.d/samba start
```At least not if your using 10.04.

There is no /etc/init.d/samba. The old "samba" service has been split apart into it's component daemons just to confuse people or maybe to be nostalgic since this is the way it used to be way back when.

"samba" is now smbd and nmbd.

---

### Post by KMJones1 on 2010-06-06
Thanks; I think you're right. I just removed the startup item and the sharing is OK on re-booting. I don't know what changed, but I'm not going to change it now!

---

