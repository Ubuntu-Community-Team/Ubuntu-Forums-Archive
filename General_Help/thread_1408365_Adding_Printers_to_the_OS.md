---
title: "Adding Printers to the OS"
date: 2010-02-16
forum: General Help
---

### Post by Bender2k14 on 2010-02-16
How would I go about adding printers to Ubuntu that are not there by default?  I have access to a collection of PPD's where at least one of them is not in Ubuntu by default.  Is this something that is done at the kernel level?

---

### Post by Bender2k14 on 2010-02-16
bump

---

### Post by InspiredIndividual on 2010-02-16
Did you try System -> Administration -> Printing and than Server -> New Printer?

---

### Post by efflandt on 2010-02-16
Then when you select a local or network print, you just point to the proper ppd file (or maybe just the directory you have them in) and pick from that list if it does not recognize the specific one from that.

---

### Post by Bender2k14 on 2010-03-02
Sure, I figured out how to add this printers for myself, but that is not what I was asking.

I want to know how I can add the PPD files into Ubuntu by default so that other Ubuntu users do not have to search for the files like I did.

(My searching was easy though because my school provided all the PPD files for their printers.)

---

### Post by InspiredIndividual on 2010-04-01
I'm not an expert by any means, but in my system the new ppd-files are added to the /etc/cups folder. This seems to be user independent, so it may not be completely clear what your problem is exactly. Isn't it working like this for you?

---

