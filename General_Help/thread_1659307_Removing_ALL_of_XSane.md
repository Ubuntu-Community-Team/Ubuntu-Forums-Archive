---
title: "Removing ALL of XSane"
date: 2011-01-03
forum: General Help
---

### Post by measekite on 2011-01-03
I removed what I thought was all of XSane using Synaptic.  However there still must have been some file left over.  Upon installation and doing everything I was supposed to do my Epson 4180 is still not recognized by XSane after reinstall.

It was working fine under Mav 10.10 for quite some time until I installed TurboPrint.  Apparently the install did something.  Still I initially was able to run it by:

```
sudo xsane
```

but even after changing the 50 rules file from 0664 to 0666 it did not work.  So I did a complete removal via Synaptic and a complete install but now it will not even work under root.

Any ideas.

---

### Post by GerryB on 2011-01-26
I don't know if this will help but it might. Go to your home folder. Click on "show hidden files". You'll see a folder named .xsane. Open whatever layers you need to get to a file ending in .drc. Eliminate it. Plug in your scanner again and let Ubuntu set it up again. You'll get another file ending in .drc. Hopefully you'll be back to the point where it worked before. Let me know how it went.

---

