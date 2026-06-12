---
title: "No Sound, No TouchPad"
date: 2009-10-05
forum: General Help
---

### Post by pedrambehroozi on 2009-10-05
Hello community,
I just upgraded to 9.10 Beta from 9.04 (Ubuntu) but I don't have sound and my touchpad doesn't work.
I have a dell vostro 1520.
Is this a bug I should file it or what?
Many thanks :)

---

### Post by JTCA on 2009-10-15
I too have this same problem with a Dell Latitude D820.  I have been watching this post to see if there was any activity towards a solution.  Here's hoping...

---

### Post by JTCA on 2009-10-31
I fixed it but not exactly sure how...here's what I think I did.
 I upgraded to 9.10 from 9.04 and just noticed that the "latest" kernel, 2.6.31-14-generic was not being used. I went into system> administration>synaptic package manager and checked grub-pc which installed Grub2 and uninstalled Grub. After I rebooted I found that the boot list now allowed me to select kernel 2.6.31 (this wasn't even a choice before). Everything seems to be cool now.
 I hope this helps someone, sorry that I don't have a better technical explanation of what happened.

---

