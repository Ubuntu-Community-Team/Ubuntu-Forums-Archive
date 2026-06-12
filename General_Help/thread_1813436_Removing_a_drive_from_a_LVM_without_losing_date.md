---
title: "Removing a drive from a LVM without losing date"
date: 2011-07-27
forum: General Help
---

### Post by Vyizis on 2011-07-27
My little server box running 11.04 currently has two drives configured in a LVM, a 160gb internal drive and a 1tb usb drive.

I have three logical volumes root and swap on the 160gb and backup on the 1tb. I am going to be changing the internal drive for a 8gb SSD and would like to keep the data currently on the external, is it possible to do this?

---

### Post by bodhi.zazen on 2011-07-27
This will get you started ;

[http://tldp.org/HOWTO/LVM-HOWTO/removepvsfromvg.html](http://tldp.org/HOWTO/LVM-HOWTO/removepvsfromvg.html)

You may need to use pvmove first ;)

---

### Post by Vyizis on 2011-07-27
I have seen that but I cannot do that without losing the data on the drive i want to remove from the LVM.

---

### Post by bodhi.zazen on 2011-07-27
> **Vyizis said:**
> I have seen that but I cannot do that without losing the data on the drive i want to remove from the LVM.

Did you run pvmove ?

[http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

---

### Post by Vyizis on 2011-07-27
I do not have enough drive space to move the 600gb of data stored on the 1tb drive elsewhere on the LVM, the other drive is only a 160gb. 

It is the 1tb external drive I would like to remove from the LVM so I can mount it as a normal drive without removing the data from it.

---

### Post by bodhi.zazen on 2011-07-27
> **Vyizis said:**
> I do not have enough drive space to move the 600gb of data stored on the 1tb drive elsewhere on the LVM, the other drive is only a 160gb. 

It is the 1tb external drive I would like to remove from the LVM so I can mount it as a normal drive without removing the data from it.

Well, than you can not expect to remove the hard drive without data loss.

> If you do not have enough free physical extents to distribute the old physical extents to, you will have to add a disk to the volume group and move the extents to it.

[http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

---

### Post by Vyizis on 2011-07-28
> **bodhi.zazen said:**
> Well, than you can not expect to remove the hard drive without data loss.



[http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

I wasn't expecting anything, I was asking if it was possible...

---

