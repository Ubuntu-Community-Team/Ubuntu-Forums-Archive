---
title: "No Longer can Slice Image in Gimp with Natty"
date: 2011-06-06
forum: General Help
---

### Post by Wmrit on 2011-06-06
After upgrading to Natty I can no longer slice images in Gimp.
When I use the Web->Slice filter and select options I get error message

Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 692, in response
    dialog.res = run_script(params)
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 353, in run_script
    return apply(function, params)
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 117, in pyslice
    left, right, top, bottom, i, j, ""))
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 172, in slice
    temp_image.crop(right - left, bottom - top, left, top)
TypeError: integer argument expected, got float

Any advise?
Thanks

---

### Post by Aure-lijus on 2011-06-12
Did a simple hack:
replaced temp_image.crop(int(right - left), int(bottom - top), int(left), int(top)) with
```
temp_image.crop(int(right - left), int(bottom - top), int(left), int(top))
```it is temporal solution but it works.

To change the text, you must be in root mode:
```
gksudo gedit /usr/lib/gimp/2.0/plug-ins/py-slice.py
```Reported bug to [https://bugzilla.gnome.org/show_bug.cgi?id=652406](https://bugzilla.gnome.org/show_bug.cgi?id=652406)

---

### Post by heepie on 2011-07-28
thank you, this work like a charm

---

### Post by barlaventoexpert on 2011-07-31
> **Aure-lijus said:**
> Did a simple hack:
replaced temp_image.crop(int(right - left), int(bottom - top), int(left), int(top)) with
```
temp_image.crop(int(right - left), int(bottom - top), int(left), int(top))
```it is temporal solution but it works.

To change the text, you must be in root mode:
```
gksudo gedit /usr/lib/gimp/2.0/plug-ins/py-slice.py
```Reported bug to [https://bugzilla.gnome.org/show_bug.cgi?id=652406](https://bugzilla.gnome.org/show_bug.cgi?id=652406)

When I did this, and relaunched GIMP, the py-slice entry on the Filters > Web menu was mssing!

Any ideas?

Thanks

---

### Post by barlaventoexpert on 2011-07-31
> **barlaventoexpert said:**
> When I did this, and relaunched GIMP, the py-slice entry on the Filters > Web menu was mssing!

Any ideas?

Thanks

Ok! Got py-slice.py to work! Problem was with the code indentations.

However, py-slice.py is now not recognising the guides on the image!!!! It is just producing the whole image as a slice.....Hundreds of them!  

Any ideas---Aaaaargh!

---

### Post by wn_bluebird on 2011-08-10
deleted.

---

### Post by waldherrvonbirnbaum on 2012-04-02
> **Aure-lijus said:**
> Did a simple hack:
replaced temp_image.crop(int(right - left), int(bottom - top), int(left), int(top)) with
```
temp_image.crop(int(right - left), int(bottom - top), int(left), int(top))
```it is temporal solution but it works.

To change the text, you must be in root mode:
```
gksudo gedit /usr/lib/gimp/2.0/plug-ins/py-slice.py
```Reported bug to [https://bugzilla.gnome.org/show_bug.cgi?id=652406](https://bugzilla.gnome.org/show_bug.cgi?id=652406)

hi,
i cant find a difference between the original line and replacing line. or am i just blind?

---

### Post by raja.genupula on 2012-04-02
i am also getting same about both of them , is this issue you're facing . then please start a new thread on your issue for better support .

---

### Post by NamiJason on 2012-04-30
Thanks for this hack.  It worked like a charm for me.  The original temp_image.crop looked slightly different but I just replaced it and it worked fine. 

I'm running Gimp 2.6.11 and Ubuntu 11.10.

Thanks Aure-lijus

---

