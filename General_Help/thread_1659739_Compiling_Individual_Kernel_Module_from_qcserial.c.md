---
title: "Compiling Individual Kernel Module from qcserial.c"
date: 2011-01-04
forum: General Help
---

### Post by atroph on 2011-01-04
I am trying to figure out how to compile qcserial.c kernel module from the latest kernel source file located in the 2.6.37-rc8 kernel tree. I have installed the sources for my current kernel 2.6.35-24-generic on maverick and it seems that my includes are not in the right place to make the qcserial.c file happy. 

I overcame this issue by passing the -I option to gcc that points to the directories that it is looking for. I am currently getting errors while compiling and I was wondering if it is impossible to compile qcserial.c on my current kernel? 

I am looking to get the diagnostic port and GPS port enabled for my built-in 3G card. 

I havent built modules for quite some time and that was on opensuse with the fglrx module.

Any ideas would be greatly appreciated.

I have attached qcserial.c for reference.

---

### Post by atroph on 2011-01-04
I am trying to figure out how to compile qcserial.c kernel module from the latest kernel source file located in the 2.6.37-rc8 kernel tree. I have installed the sources for my current kernel 2.6.35-24-generic on maverick and it seems that my includes are not in the right place to make the qcserial.c file happy. 

I overcame this issue by passing the -I option to gcc that points to the directories that it is looking for. I am currently getting errors while compiling and I was wondering if it is impossible to compile qcserial.c on my current kernel? 

I am looking to get the diagnostic port and GPS port enabled for my built-in 3G card. 

I havent built modules for quite some time and that was on opensuse with the fglrx module.

Any ideas would be greatly appreciated.

I have attached qcserial.c for reference.

---

### Post by atroph on 2011-01-04
I am trying to figure out how to compile qcserial.c kernel module from the latest kernel source file located in the 2.6.37-rc8 kernel tree. I have installed the sources for my current kernel 2.6.35-24-generic on maverick and it seems that my includes are not in the right place to make the qcserial.c file happy. 

I overcame this issue by passing the -I option to gcc that points to the directories that it is looking for. I am currently getting errors while compiling and I was wondering if it is impossible to compile qcserial.c on my current kernel? 

I am looking to get the diagnostic port and GPS port enabled for my built-in 3G card. 

I havent built modules for quite some time and that was on opensuse with the fglrx module.

Any ideas would be greatly appreciated.

I have attached qcserial.c for reference.

---

### Post by atroph on 2011-01-04
I am trying to figure out how to compile qcserial.c kernel module from the latest kernel source file located in the 2.6.37-rc8 kernel tree. I have installed the sources for my current kernel 2.6.35-24-generic on maverick and it seems that my includes are not in the right place to make the qcserial.c file happy. 

I overcame this issue by passing the -I option to gcc that points to the directories that it is looking for. I am currently getting errors while compiling and I was wondering if it is impossible to compile qcserial.c on my current kernel? 

I am looking to get the diagnostic port and GPS port enabled for my built-in 3G card. 

I havent built modules for quite some time and that was on opensuse with the fglrx module.

Any ideas would be greatly appreciated.

I have attached qcserial.c for reference.

---

### Post by atroph on 2011-01-04
I am trying to figure out how to compile qcserial.c kernel module from the latest kernel source file located in the 2.6.37-rc8 kernel tree. I have installed the sources for my current kernel 2.6.35-24-generic on maverick and it seems that my includes are not in the right place to make the qcserial.c file happy. 

I overcame this issue by passing the -I option to gcc that points to the directories that it is looking for. I am currently getting errors while compiling and I was wondering if it is impossible to compile qcserial.c on my current kernel? 

I am looking to get the diagnostic port and GPS port enabled for my built-in 3G card. 

I havent built modules for quite some time and that was on opensuse with the fglrx module.

Any ideas would be greatly appreciated.

I have attached qcserial.c for reference.

I tried to do something like mentioned here "http://vaioz31.blogspot.com/2009/04/3g-support-qualcomm-gobi-chipset-step1.html"

---

### Post by atroph on 2011-01-04
The attachment didn't stick. Reposting.

---

### Post by cariboo on 2011-01-04
I merged the duplicate threads, atroph report the posts you want removed.

---

### Post by atroph on 2011-01-04
Please remove posts 1-4. Thanks.

---

### Post by linwiz on 2011-06-16
I am having the same issue. How was this resolved?

---

### Post by atroph on 2011-06-16
The problem with the code on the website is the formatting when copying and pasting. I believe that the make program requires tabs and not spaces to separate the fields. I don't have the file that I edited to make work. Hope this helps.

---

