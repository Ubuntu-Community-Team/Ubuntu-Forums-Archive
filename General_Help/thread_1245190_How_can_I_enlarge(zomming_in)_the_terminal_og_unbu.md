---
title: "How can I enlarge(zomming in) the terminal og unbuntu server"
date: 2009-08-20
forum: General Help
---

### Post by brusk kurd on 2009-08-20
Hello!

I have a problem **with reading the small letters in the terminal of ubuntu server 8.04** , actually it is just terminal . How can I zoom in (enlarge) the script in the terminal?. :confused:

I will be thankfull if somebody help me:KS

---

### Post by HermanAB on 2009-08-20
Probably with stty.  Try 'man stty' or Google for 'stty man page' to figure out how to change the number of columns and rows.

---

### Post by brusk kurd on 2009-08-20
Thanks for replying!

I have looked at "man stty" , I saw that these (cs5,cs6,cs7 and cs8) are the size of the charechter..I have tried the following

stty -a -g cs7
 but It did not work:(

---

### Post by brusk kurd on 2009-08-21
I want to say to those people who have the same problem that they can download "putty" and work on it in stead of the terminal of Linux. Than it is easier to controll the large of the charachter and also the colour:popcorn:

I

---

