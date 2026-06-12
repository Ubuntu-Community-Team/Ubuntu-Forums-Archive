---
title: "how to stop Lucid looking for external HD on bootup"
date: 2011-05-05
forum: General Help
---

### Post by ray field on 2011-05-05
I just installed Lucid over Karmic on my netbook, unfortunately I had a little removeable USB hard drive attached during the installation.  now when I boot, it keeps looking for the little HD, and I have to press "S" to make it "skip." what can I do to tell Lucid that I seldom use this drive so please shut up about it every time I turn it on?

---

### Post by Cheesehead on 2011-05-05
Remove the line describing it from /etc/fstab

---

