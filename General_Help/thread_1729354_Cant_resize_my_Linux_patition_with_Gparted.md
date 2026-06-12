---
title: "Cant resize my Linux patition with Gparted"
date: 2011-04-14
forum: General Help
---

### Post by ssulaco on 2011-04-14
I wanted to shrink my windows partition and enlarge ubuntu's partition,I shrunk windows ok,but Gparted wont let me enlarge the Linux partition to the left side,toward the unallocated space....Gparted will allow me to expand my windows partition back,I even tried creating a new partition and formatted it to ext4,and then deleting the partition.no go,I read somewhere that Gparted may not allow you to move the front side of the Linux partition,...Thanks in advance.

---

### Post by yetiman64 on 2011-04-14
> **ssulaco said:**
> I wanted to shrink my windows partition and enlarge ubuntu's partition,I shrunk windows ok,but Gparted wont let me enlarge the Linux partition to the left side,toward the unallocated space....Gparted will allow me to expand my windows partition back,I even tried creating a new partition and formatted it to ext4,and then deleting the partition.no go,I read somewhere that Gparted may not allow you to move the front side of the Linux partition,...Thanks in advance.

You have an active swap partition (note the key indicating "it's locked") inside of the extended partition showing in the first screenshot. Try right clicking on the swap partition and selecting "swapoff". No partitions within the extended partition can be in use if the extended partition is to be altered.

---

### Post by lmarmisa on 2011-04-14
I agree with yetiman64 but I would like to add a recommendation: do not forget to enlarge the extended partition /dev/sda2 before to enlarge the ext4 partition /dev/sda5.

---

### Post by yetiman64 on 2011-04-14
> **lmarmisa said:**
> I agree with yetiman64 but I would like to add a recommendation: do not forget to enlarge the extended partition /dev/sda2 before to enlarge the ext4 partition /dev/**sda**5.

@lmarmisa, Good extra point thanks, just note I've bolded a typo you may want to fix in your post, cheers from yetiman64.

---

### Post by lmarmisa on 2011-04-14
> **yetiman64 said:**
> @lmarmisa, Good extra point thanks, just note I've bolded a typo you may want to fix in your post, cheers from yetiman64.

@yetiman64 Thanks for your comment. I have corrected my lapsus calami. 

Best regards,

Luis

---

### Post by ssulaco on 2011-04-14
> **yetiman64 said:**
> You have an active swap partition (note the key indicating "it's locked") 
I originally tried expanding the Linux partition with Gparted live,the swap was unlocked,Thanks for the heads up.

> **lmarmisa said:**
>  I would like to add a recommendation: do not forget to enlarge the extended partition /dev/sda2 before to enlarge the ext4 partition /dev/sda5.
What was I thinking ](*,)......That was it
Thank you yetiman64 and lmarmisa for the help.

---

### Post by lmarmisa on 2011-04-14
You are very welcome.

Please, mark the thread as solved.

Best regards,

Luis

---

### Post by yetiman64 on 2011-04-14
> **lmarmisa said:**
> You are very welcome.

Please, mark the thread as solved.

Best regards,

Luis

"Ditto"  :smile: and link #5 in my sig has instructions if needed, cheers from yetiman64. Edit, note it is now done.

---

