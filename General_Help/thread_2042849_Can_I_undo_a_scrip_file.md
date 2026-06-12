---
title: "Can I undo a scrip file?"
date: 2012-08-15
forum: General Help
---

### Post by ziggutas on 2012-08-15
Some time ago I found and used the following thread in my hunt for solutions to a problem.
 
I followed the instructions at Post #6 of this thread:
[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)  

I am still fairly new as an active user of ubuntu and was mistaken in thinking the help in the thread was relevant to my suspend issue. It was similar, but not the same.

So can I undo the changes I have made? Or do I in fact need to undo them, since ubuntu has updated with two new complete kernels since then?

Any help or advice would be much appreciated.

---

### Post by Vaphell on 2012-08-15
to undo, simply delete the file you've created
```
sudo rm /etc/pm/sleep.d/20_custom-ehci_hcd
```
i think that file is simply a custom procedure executed when the conditions are met, if it does nothing in your case you don't need it. It doesn't make any permanent changes in system internals so there is nothing else to undo.

---

### Post by ziggutas on 2012-08-15
Thanks Vaphell. Job done.

Phew, that was quick!

---

