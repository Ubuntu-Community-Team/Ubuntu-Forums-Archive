---
title: "can't change boot order"
date: 2010-03-23
forum: General Help
---

### Post by jeepdriver on 2010-03-23
Started out with a 10 year old Maxtor 10Gb HDD and installed Ubuntu 9.04. Several months later added a Samsung 40Gb HDD and installed 9.10. Both drives are IDE. Everything works fine until I try to set the Samsung to boot before the Maxtor then I get Error 15. I would like to remove the Maxtor with 9.04 on it because it's pretty old, I plan on installing a newer drive. So, I guess my question is, what exactly do I need to do to the Samsung to get it to boot without the Maxtor installed. I assume it involves repairing the MBR. What would be the correct procedure ?

---

### Post by john newbuntu on 2010-03-23
Search for error 15 in the following post:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by jeepdriver on 2010-03-23
Thanks for the link. Will give it a try.
Thanks again.

---

### Post by jeepdriver on 2010-03-24
Checked out the info on the link you posted, reconfigured grub, and all is well.
Thanks

---

### Post by fragos on 2010-03-25
When you have multiple hard drives, the one selected for booting is controlled in your BIOS. At least that was the case for my system.

---

### Post by jeepdriver on 2010-03-26
When I selected the drive with 9.10 to be the first boot device, I would get the error 15. When I would have the drive with 9.04 selected as first boot device, I would be presented with the option of booting to 9.04 or 9.10. So, I guess that when you have 2 drives with one installed sometime later than the first one, the MBR is on the original drive. I could have installed 9.10 on the second drive with the original drive NOT connected and would have been alright ??
Been playing with Ubuntu since 6.06 and I'm still learning.

---

### Post by fragos on 2010-03-26
If you upgraded to 9.10 you'd still be using the old grub. A clean install gives you grub2 which for me I could't get to work. Error 15 was my problem as well. I fixed it the hard way -- reinstalled 9.04 and then upgraded to 9.10. I'm sure there's an easier way but I grew impatient and went with what I knew would work.

---

