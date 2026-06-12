---
title: "Can't Write Netbook Remix To USB"
date: 2009-08-11
forum: General Help
---

### Post by DocHolliday2006 on 2009-08-11
I'm following the directions [here]("https://help.ubuntu.com/community/Installation/FromImgFiles"). 

I've installed image writer. 

When I select the image file and my USB drive and hit write, it says something went wrong, please see the details window. There it says:

"The dd process ended with an error"


In the terminal, it says:

0
Traceback (most recent call last):
  File "/usr/lib/imagewriter/imagewriter.py", line 112, in do_write
    self.raw_write(source, target)
  File "/usr/lib/imagewriter/imagewriter.py", line 150, in raw_write
    src_size = float(data.stdout.readline().split()[4])*1.0
IndexError: list index out of range


Anyone know what's going on?

---

### Post by dcstar on 2009-08-11
> **DocHolliday2006 said:**
> I'm following the directions [here]("https://help.ubuntu.com/community/Installation/FromImgFiles"). 

I've installed image writer. 

When I select the image file and my USB drive and hit write, it says something went wrong, please see the details window. There it says:
......?

Try the command line options.

---

### Post by RedSingularity on 2009-08-11
Try using **portable linux**.  Works great for me and it has a nice GUI.


Here: [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

---

### Post by DocHolliday2006 on 2009-08-12
Hey. So I installed portable linux, but it requires an ISO file, not an img file, which is what netbook remix comes in. How do I get it in ISO format?


> **Shadow121 said:**
> Try using **portable linux**.  Works great for me and it has a nice GUI.


Here: [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

---

### Post by DocHolliday2006 on 2009-08-12
I don't know what those are. How do I get to them?


> **dcstar said:**
> Try the command line options.

---

### Post by RedSingularity on 2009-08-12
> **DocHolliday2006 said:**
> Hey. So I installed portable linux, but it requires an ISO file, not an img file, which is what netbook remix comes in. How do I get it in ISO format?


Oh thats right it does require a ISO image.  Portable linux may not work then.  Did you try re-downloading the img file.  It may be corrupt.

---

