---
title: "Printing high-res A3-size image"
date: 2009-10-14
forum: General Help
---

### Post by Pigeon. on 2009-10-14
Anyone suggest a package which is capable of producing valid, error-free postscript when outputting a high-res colour image to an A3 printer...

Every single package I've tried produces postscript which is unacceptable, and gives "Error: /rangecheck in --colorimage--" in the CUPS error log.

Printer is an Epson 1270.

Sample image which causes this error: [http://www.lucy-pinder.tv/forum/images/lucy-pinder/lucy-pinder-energy-saving-trust-3-22.jpg](http://www.lucy-pinder.tv/forum/images/lucy-pinder/lucy-pinder-energy-saving-trust-3-22.jpg)

The resolution of this image is 3494x5153.

If there is anyone on here who has successfully printed images of such a resolution onto A3 size paper, please let me know what application worked for you.

Thanks.

---

### Post by tgalati4 on 2009-10-15
Try posterazor.  Could be a memory limit  in the epson.

---

### Post by Pigeon. on 2009-10-16
Hmm, could have been a memory limit *somewhere*... top was not reporting much memory usage by the process, but nevertheless I tried printing from a different machine with more memory installed and it is working, so thanks for that suggestion.

The other potentially significant difference is that the new machine is using a foomatic driver rather than a gutenprint one.

---

