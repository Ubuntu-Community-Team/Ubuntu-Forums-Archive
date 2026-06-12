---
title: "Gimp Print Problem - Only getting blank documents"
date: 2010-09-24
forum: General Help
---

### Post by jdorenbush on 2010-09-24
Gimp is failing to print documents correctly. It will spit out a page, whether it be PDF or an actual piece of paper, but the result is just a blank white document. I've tried printing through my HP printer, Cups PDF printer, and the default Print to File.

I'm able to print documents through other applications on my system just fine.

I've done a fresh install of Ubuntu, but I'm still having the problem. I'm not sure if there are certain packages I need for Gimp to print. There are so many different PDF, PostScript, GhostScript, Cups, Foomatic, HP, etc. files in Synaptic that it's hard to tell what is important and what isn't.

I'm using GIMP 2.7.2 on Ubuntu 10.10.

Any help is very appreciated. Cheers!

---

### Post by peddy on 2010-09-27
I have the same problem. A blank page even appears under the 'image settings' preview dialog.

---

### Post by jdorenbush on 2010-09-27
> **peddy said:**
> I have the same problem. A blank page even appears under the 'image settings' preview dialog.

Yeah, I get a blank page in in the preview too.

I haven't seen much about this on the forums or launchpad. Anyone??

---

### Post by peddy on 2010-09-27
> **jdorenbush said:**
> Yeah, I get a blank page in in the preview too.

I haven't seen much about this on the forums or launchpad. Anyone??

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/636329](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/636329)

---

### Post by jdorenbush on 2010-09-27
> **peddy said:**
> [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/636329](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/636329)

Great, thank you! Have you tried the solution they suggested on there of downgrading the Cairo package?

---

### Post by jdorenbush on 2010-11-08
This is fixed in GIMP 2.6.11, but unfortunately I still experience the problem in GIMP 2.7.

Hopefully the patch will be applied to 2.7 soon.

---

### Post by JuliaHenson on 2010-12-06
Dear Sirs,
     I had this problem with a scanned document which I then pulled into GIMP to try to print, without any success.
     My immediate solution was to "select all", and paste the document into OpenOffice word processor, where I could print with no problem.
     That will suffice until the fix is okayed.  The fix has been found, but not approved, at 
[https://launchpad.net/~ubuntu-treblig/+archive/gimpfixes](https://launchpad.net/~ubuntu-treblig/+archive/gimpfixes)

Thank you,
Julia

---

