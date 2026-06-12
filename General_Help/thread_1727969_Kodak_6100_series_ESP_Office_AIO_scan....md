---
title: "Kodak 6100 series ESP Office AIO scan..."
date: 2011-04-13
forum: General Help
---

### Post by timgood on 2011-04-13
I have been able to get this AIO to print in Ubuntu, but have not been able to get the scanner working. Has anyone had any success scanning with these units? Would like to do this for a client as I could then move them over to be 100% Ubuntu!

Help would be gratefully appreciated.

---

### Post by fragos on 2011-04-13
Linux only supports scanners that use the SANE API. HP scanners use SANE and older Canon scanners did. Perhaps Kodak use a proprietary scanner API which could be why it doesn't work for use. The real question is dose Kodak use SANE for scanning? For that I don't have an answer.

---

### Post by timgood on 2011-04-14
> **fragos said:**
> Linux only supports scanners that use the SANE API. HP scanners use SANE and older Canon scanners did. Perhaps Kodak use a proprietary scanner API which could be why it doesn't work for use. The real question is dose Kodak use SANE for scanning? For that I don't have an answer.

Thanks for the response. Does anyone out there know if Kodak uses SANE or a proprietary format, or how I could find out?

---

### Post by timgood on 2011-04-14
There is a Mac OSX scanner driver for this model. What are the chances of getting that to work in Ubuntu?

---

