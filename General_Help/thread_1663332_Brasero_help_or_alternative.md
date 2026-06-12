---
title: "Brasero help or alternative"
date: 2011-01-09
forum: General Help
---

### Post by jmacgowan on 2011-01-09
I'm trying to make a 1:1 copy of an encoded DVD using Brasero under Ubuntu 10.10.  I've read about various errors and workarounds for *buring* an image, but not creating one.  Firing Brasero up in the terminal generates the following error:

> 
** (brasero:2909): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


Probably not that big of a deal, as it just fails to load an image.  Brasero opens fine and I navigate my way to creating a disk image.  I pick all my settings (1:1 copy of DVD, write disc to image file, etc.).  When I click create image, Brasero seems to close and the following errors can be found in the terminal:

> 
(brasero:2909): GLib-CRITICAL **: g_variant_builder_end: assertion `is_valid_builder (builder)' failed

(brasero:2909): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(brasero:2909): GLib-CRITICAL **: g_variant_type_is_array: assertion `g_variant_type_check (type)' failed

(brasero:2909): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

GLib-ERROR **: g_variant_new: expected array GVariantBuilder but the built value has type `(null)'
aborting...
Aborted


I would imagine the answer is "It's a known bug, it's being addressed", but I hope not.

My question is: has a fix been found?  Is there a similar program that will do the same task?

Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-01-09
K3b has always been better than Brasero, if you can afford the hideous kde dependencies. 

You can always try from command line
```
dd if=/dev/dvd of=/path/of/image/image.iso
```

---

### Post by marl30 on 2011-01-09
I second K3B. Simply the best free burning software for Linux. Gnomebaker is also another great one to try.

---

### Post by TeoBigusGeekus on 2011-01-09
Both K3b and Brasero seem to go through cycles of instability throughout the years.
After a frustrating issue I had with them about a year ago, I now use only the command line (growisofs, wodim, dd). At least you know that if these don't work, then nothing else will...

---

### Post by jmacgowan on 2011-01-09
dd worked perfectly.  Thank you TeoBigusGeekus, I didn't even know it existed.  I need to spend some time looking around at documentation more I guess. :D

---

