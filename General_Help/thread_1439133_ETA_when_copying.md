---
title: "ETA when copying?"
date: 2010-03-25
forum: General Help
---

### Post by Loves SSH on 2010-03-25
I'm copying some large files from on drive to another. Is there a command similar to cp that shows a progress bar, or some signs of life that it's copying and how long 'till it's done? I've tried cp -v, but the output isn't as '-v' as I hoped. 

TIA.

---

### Post by 666f6f on 2010-03-25
The rsync file-copying tool has a *--progress* param.

---

### Post by gordintoronto on 2010-03-25
Nautilus shows a progress bar.

---

### Post by 666f6f on 2010-03-26
You may also want to try [this shell script]("http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/").

---

