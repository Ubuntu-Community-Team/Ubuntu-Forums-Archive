---
title: "List physical disk blocks for a file"
date: 2010-08-28
forum: General Help
---

### Post by Asmodai on 2010-08-28
Is there a way to show which physical block ranges a file is occupying on the disk? The file system used is ext4.

---

### Post by rnerwein on 2010-08-28
> **Asmodai said:**
> Is there a way to show which physical block ranges a file is occupying on the disk? The file system used is ext4.
hi
oh folk that's a long way to go !!!
have a look at: --> [http://openbook.galileocomputing.de/ubuntu/ubuntu_19_architektur_008.htm](http://openbook.galileocomputing.de/ubuntu/ubuntu_19_architektur_008.htm)
i know the way but it' to complex to explain it here.
if you are very interesting in this complex theme you have to invest o lot of time for it.
oh forgot - it's not for only ubuntu - it's vlaild for nearly all currently unix/linix systems
ciao
      have fun

---

### Post by Asmodai on 2010-08-28
Thanks for the reply, although I was hoping to do this without full knowledge about the ext4 structure.
It seems that diskfrag -v file does exactly what I want. It uses an ioctl call, so I should be able to start from there.

---

