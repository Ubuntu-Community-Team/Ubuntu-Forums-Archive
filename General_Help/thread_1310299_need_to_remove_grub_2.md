---
title: "need to remove grub 2"
date: 2009-11-01
forum: General Help
---

### Post by michaelaye on 2009-11-01
hi, i had ubuntu installed through wubi and i was like yay its working really well, so i removed it and installed in on a partition. when i restarted my comp i found that grub 2 was booting into ubuntu, that would be fine if i didnt have windows xp. now i have my windows xp encrypted with truecrypt. so my question is how do i remove grub 2 (or at least change it) so i boot to the truecrypt bootloader 1st instead of grub 2?

btw i'm still kinda new with linux so i dont know much. i tried using the synaptic package manager to remove grub 2 but it didnt work.
 plz help me.

---

### Post by ranch hand on 2009-11-01
Read link in my sig.  The first 3 links are great and the 1st one does deal somewhat with encrypted partitions.  There is also a link to a thread on removing grub2 and installing grub-legacy.

---

### Post by michaelaye on 2009-11-01
i'v tried removing grub 2 and replacing it with legacy grub but it does the same thing. i need the truecrypt bootloader the boot 1st not grub. 
is there any other way to do this then decrypting windows xp and using the win xp installation disk to fix the mbr?

---

### Post by ranch hand on 2009-11-01
Did you check hermans notes on encrypted partitions and grub2?

I think he got it to work, maybe not, I don't use encryption on my partitions so I don't keep up on it.

---

### Post by michaelaye on 2009-11-01
i cant find anything on encrypted partitions and grub 2 in herman's notes, i did find how to chainload another bootloader. i tried it but i cant get it to work. to tell the truth i have no idea what i am doing

---

### Post by ranch hand on 2009-11-01
Have you used grub-legacy to boot to encrypted partitions before?

---

### Post by michaelaye on 2009-11-01
no, i'v never had this problem b4, when i had ubuntu 8.10 installed the comp booted to the truecrypt bootloader and then all i had to do was press esc to boot into grub to go to ubuntu.
i'v also just relized that grub 2 could have over written the truecrypt boot loader, if so all i need to do is restore it uing the truecrypt rescue iso, which i wll try tomorrow.

---

### Post by ranch hand on 2009-11-02
Good thinking.

---

