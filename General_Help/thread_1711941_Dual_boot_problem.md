---
title: "Dual boot problem"
date: 2011-03-22
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-22
Hi All,

I am using ubuntu 10.10 before that  i am using ubuntu 9.10, that 9.10 was crashed i forget to delete the partition while installing the ubuntu 10.10. This is because of my too slow. it show swap partition. how to delete the crashed ubuntu only with out afficeting my new ubuntu 10.10

Thank you,

Regards,
Suresh

---

### Post by wilee-nilee on 2011-03-22
Install gparted in 10.10
sudo apt-get install gparted
take a screen shot of it and post it using the paperclip in the reply window.

---

### Post by suresh_vandiyur on 2011-03-22
> **wilee-nilee said:**
> Install gparted in 10.10
sudo apt-get install gparted
take a screen shot of it and post it using the paperclip in the reply window.

I have attached the screenshot. please find that

Thank you,

Regards,
Suresh

---

### Post by wilee-nilee on 2011-03-22
So the 10.10 was the last install you can remove the 9.10. Right click the 9.10 partition in gparted and choose delete.

It does help you you identify which is which though as you have 9.10 in a ext4 partition, you also have an extra swap not needed. Looks like sda1 is the earlier broken though.

---

### Post by suresh_vandiyur on 2011-03-22
> **wilee-nilee said:**
> So the 10.10 was the last install you can remove the 9.10. 

It does help you you identify which is which though as you have 9.10 in a ext4 partition, you also have an extra swap not needed. Looks like sda1 is the earlier broken though.

How i can remove the 9.10 and 9.10 swap.that why my system was dead slow. please help me

Thank you,

Regards,
Sureh

---

### Post by wilee-nilee on 2011-03-22
> **suresh_vandiyur said:**
> How i can remove the 9.10 and 9.10 swap.that why my system was dead slow. please help me

Thank you,

Regards,
Sureh

With gparted right click on the 9.10 partition then delete, then the check mark in gparted to run the delete.

It doesn't matter which swap you remove they are doing the same work.

To be safest with the delete you might boot a live ubuntu cd open gparted right click the swaps to make sure they are off then delete the 9.10 partition.

---

