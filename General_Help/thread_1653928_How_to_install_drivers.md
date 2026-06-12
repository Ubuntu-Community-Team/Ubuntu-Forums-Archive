---
title: "How to install drivers"
date: 2010-12-27
forum: General Help
---

### Post by Ott3rpop on 2010-12-27
Hey everyone, I am SUPER new to ubuntu and need to install a new printer driver and have no idea how to do it. Can someone in the most simple dumbed-down terms walk me through installing a new driver into ubuntu? The printer is a Samsung ML-1665.
I would really appreciate some help! Thanks!

---

### Post by ezsit on 2010-12-27
Most printers are auto detected and installed without any user interaction necessary. Plug in your printer and hope for the best. If Ubuntu does not auto-install your printer, go the the System / Administration / Printing tool and add a printer, it will walk you through selecting the connection type, model and driver. It should be fairly self-explanatory.

---

### Post by Verbeck on 2010-12-27
from what i found on google

1. download the linux drivers from [[LINK]]("http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/mono-laser-printer/ML-1665/XSA/index.idx?pagetype=prd_detail&tab=support")
2. extract the archive (right click>extract here)
3. connect the printer
4. open a terminal and enter the following (case sensitive)
```

sudo sh ~/Downloads/cdroot/autorun

```(that's amusing that you extracted it in to the downloads folder)
5. follow the on-screen instructions

---

### Post by WlaadDyaab on 2010-12-27
> **Verbeck said:**
> 4. open a terminal and enter

To open Terminal:

Click on Applications (you'll see that in top-left corner of your screen) - Accessories - Terminal

---

