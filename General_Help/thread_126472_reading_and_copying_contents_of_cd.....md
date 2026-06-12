---
title: "reading and copying contents of cd...."
date: 2006-02-06
forum: General Help
---

### Post by Specialsauce on 2006-02-06
from the command line. pretty simple, i need to know how to do it.

---

### Post by ]Nbx*cmD[ on 2006-02-06
well first you have to mount the device:
```
sudo mount /media/cdromX
```
X is a number starting by 0 and incrementing 1 for each cd-rom drive you have.
then you can access it by moving to that dir:
```
cd /media/cdromX
```
For copying contents from cd to hd just do:
```
cp /media/cdromX/myfile /mylocaldir/mylocalsubdir/
```
And for duplicating the cdrom you may use cdrecord, do a man cdrecord for more info. Remeber, you may need to```
 cdrecord --scanbus 
``` to find which bus is your drive connected to.

---

