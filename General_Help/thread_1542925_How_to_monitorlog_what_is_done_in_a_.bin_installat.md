---
title: "How to monitor/log what is done in a *.bin installation?"
date: 2010-07-31
forum: General Help
---

### Post by pstein on 2010-07-31
Assume I install a software package not through Synaptics/apt but manually from terminal by calling a *.bin package.
 
Is there something like a detailed monitor/log which shows later what was done during this installation?
 
I mean I want to know which files are copied into which target directory and which existing files were changed.
 
Can I force apt to monitor/perform a *.bin installation even if the (already downloaded) *.bin package is not previosuly fetched through an apt repository?
 
Thank you
Peter

---

### Post by jsyl on 2010-07-31
You could try:
```
./<filename>.bin > output.txt
```
so that whatever happens during the installation gets outputted to that text file.

---

