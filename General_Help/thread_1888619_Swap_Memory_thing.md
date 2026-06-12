---
title: "Swap Memory thing"
date: 2011-11-29
forum: General Help
---

### Post by SipSomeSalt on 2011-11-29
Yo, guys. When I check out my system monitor it says my "Swap Memory" is always 0%. How do I change it up?!?!?!

[IMG]http://img830.imageshack.us/img830/9748/screenshotsystemmonitorf.png[/IMG]

---

### Post by digithal on 2011-11-29
Swap space will be filled and used as virtual memory when you are out of RAM (or for hibernation).
Since only 43% of your RAM is used, there is no need Swap to be filled.

To read more about Swap, check [Ubuntu Documentation]("https://help.ubuntu.com/community/SwapFaq").

---

### Post by 11jmb on 2011-11-29
Is this a virtual machine?

edit: Or Wubi?

---

### Post by SipSomeSalt on 2011-11-29
> Swap space will be filled and used as virtual memory when you are out of RAM (or for hibernation).
Since only 43% of your RAM is used, there is no need Swap to be filled.

To read more about Swap, check [Ubuntu Documentation]("https://help.ubuntu.com/community/SwapFaq").

Oh! That makes a lot of sense. Thank you, man. That's all I needed to know.

---

### Post by 11jmb on 2011-11-29
Swap usage should generally be low, but I asked if you are running a VM because of the "of 0 bytes" capacity

If this is on a native install then that is a very weird error, but if it is on a virtual machine or Wubi, then it is to be expected.

---

### Post by digithal on 2011-11-29
> **11jmb said:**
> Swap usage should generally be low, but I asked if you are running a VM because of the "of 0 bytes" capacity

If this is on a native install then that is a very weird error, but if it is on a virtual machine or Wubi, then it is to be expected.
Actually there is nothing wrong, it's absolutely normal.

---

### Post by 11jmb on 2011-11-29
using zero swap space is normal for a native install, but system monitor listing swap capacity at 0 bytes is not.

should look more like the image in the link.

[http://www.thegeekstuff.com/wp-content/uploads/2009/10/system-monitor-resources.png](http://www.thegeekstuff.com/wp-content/uploads/2009/10/system-monitor-resources.png)

---

