---
title: "POSX EVO-rp1 Printer Install"
date: 2010-11-12
forum: General Help
---

### Post by vandalla on 2010-11-12
I'm having some trouble with this I'm using the CBM1000 PPD file and  its telling me I need to install the  rastertocbm1k program however when  I go to compile it it gives me this...  
 [INDENT] pos@pos-desktop:~/Downloads$ gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocbm1k rastertocbm1k.c -lcupsimage -lcups
rastertocbm1k.c: In function ‘initializeSettings’:
rastertocbm1k.c:259: warning: implicit declaration of function ‘memset’
rastertocbm1k.c:259: warning: incompatible implicit declaration of built-in function ‘memset’
rastertocbm1k.c: In function ‘main’:
rastertocbm1k.c:403: warning: implicit declaration of function ‘sleep’
rastertocbm1k.c:421: warning: implicit declaration of function ‘close’
pos@pos-desktop:~/Downloads$ 
 
 [/INDENT] It does create the file but when I go to run it it does nothing.  Any ideas??  
 Thanks!  
 Adam

---

