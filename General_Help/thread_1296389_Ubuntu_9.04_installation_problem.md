---
title: "Ubuntu 9.04 installation problem"
date: 2009-10-20
forum: General Help
---

### Post by koaung on 2009-10-20
My laptop have 3 partition C: D: and F:
C: in window Vista
D: in my important prive data
F: is free space .

All partition are NTFS .
I install ubuntu 9.04 in F: partition 
but not finish and appera installation error.
Pls help me.

thank you   :confused:

---

### Post by QIII on 2009-10-20
Can you post the text of the error?  When does it occur?

---

### Post by mike555 on 2009-10-20
What size id F , and Ubuntu probably is trying to make a swap partition but can't because of the 4 partition limit .......... you might need to delete the F partition and then make it a logical .


 err ...... I guess that should be "extended" partition , with other partition in it ...

---

### Post by koaung on 2009-10-20
This partition F: had deleted and re-creative new partition (NTFS)
But one of my friend 's ubuntu install partition is ext3
His ubuntu is successful ..
Why ?

---

### Post by koaung on 2009-10-20
> **QIII said:**
> Can you post the text of the error?

ok bro, I will show tomorrow that text error 
Thank you for your reply

---

### Post by hurdevan on 2009-10-20
At what point does the installation error out... before or after it formats drive F.

Make sure it tries to format the drive because I think that Ubuntu will install on NTFS... but it should tell you that.

Cheers

---

### Post by P4man on 2009-10-20
are you trying to install from within windows (wubi install) or are you booting from the cd? Id strongly recommend booting from the cd, so you can test it first, then install to its own partition, not inside the windows partition (=wubi)

---

