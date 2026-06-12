---
title: "Ubuntu Bootloader is missing!"
date: 2012-06-20
forum: General Help
---

### Post by Richiegs on 2012-06-20
I have 2 partitions in my HD, one for Ubuntu and the other for Vista. After I reinstalled Vista in my PC, I couldn't go back to Ubuntu. Whenever I turn on the PC, it will go directly to Vista because the bootloader for Ubuntu is missing. Please help.

---

### Post by Redblade20XX on 2012-06-20
See here: [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

-Red

---

### Post by Mr.Dee on 2012-06-20
"Linux plays well with Windose, but Windose does not play well with Linux."  There are probably a few thousand posts about the exact same issue.  I have not had this issue, but I'm sure you will be able to find the answer in these forums.

---

### Post by drs305 on 2012-06-20
Assuming your Grub files are intact (they should be), you merely need to reset the MBR to look to your Ubuntu grub folder.

An easy way to do this is to install Boot Repair and click on "Recommended Repair". See the Boot Repair link in my signature line.

There is a  simple 2 command fix you can run from a terminal while on the LiveCD but we'd need a bit of information first. BR will probably be easier.

---

