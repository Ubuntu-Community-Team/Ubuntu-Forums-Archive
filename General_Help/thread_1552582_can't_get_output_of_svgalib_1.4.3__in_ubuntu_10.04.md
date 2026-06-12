---
title: "can't get output of svgalib 1.4.3  in ubuntu 10.04"
date: 2010-08-13
forum: General Help
---

### Post by muhammed irshad on 2010-08-13
I am using ubuntu 10.04 and I installed svgalib 1.4.3 and while i run a simple c graphics program I can't get the output of this instead its getting an output in a black screen saying
"USING VGA driver
svgalib 1.4.3"

---

### Post by kiran r on 2010-10-17
type **sudo nano /etc/vga/libvga.config**
remove** # **symbol from  "#_chipset VESA          # nicely behaved Vesa Bioses_" line
ctrl+x to save the file
then try to get the o/p

---

