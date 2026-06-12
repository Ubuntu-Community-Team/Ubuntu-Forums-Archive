---
title: "Memory usage detective work"
date: 2006-02-14
forum: General Help
---

### Post by Prospero2006 on 2006-02-14
Hello,

The last two mornings I've gotten up to the superkaramba system monitor 
reporting 900 mb of memory in use out of my 1024. When I go to bed, it's like 300 mb. The O/S runs very slow for the first few minutes. 

Any ideas how I can track down what processes are using memory?

Thanks, 
Pros

---

### Post by der_joachim on 2006-02-14
[QUOTE=Prospero2006]The last two mornings I've gotten up to the superkaramba system monitor 
reporting 900 mb of memory in use out of my 1024. When I go to bed, it's like 300 mb. The O/S runs very slow for the first few minutes. 

Any ideas how I can track down what processes are using memory?[/QUOTE]

Open a console like Konsole (no pun  intended) and run the command 'top'. You get a list of all the running programs and services as well as their memory consumption and processor stats. 

There are apparently some graphical tools as well, although I never tried them. 

BTW: Keep in mind that unlike Windows, as much is stored in memory as possible, in order to eliminate swapping. This may well be the case for your PC. 900 megs of memory is a lot though... :confused:

---

### Post by Prospero2006 on 2006-02-14
You know, when I did the install, Ubuntu defaulted to
1 mb swap. It seemed strange, but I figured, "Trust Ubuntu."

I wonder if a reinstall with 1 gig of swap would make a difference.

  -Somehow I doubt it.

Thanks
Pros

---

