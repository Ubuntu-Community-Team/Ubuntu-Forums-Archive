---
title: "cannot enter the X-fce, login again,  again! (Xubuntn9.10)"
date: 2009-11-13
forum: General Help
---

### Post by dengx on 2009-11-13
Hi, everyone,

I upgrade the Xubuntu9.04 to Xubuntu9.10 , then it often cannot enter the X window,

and i has setting the "login sreen" to auto login, as saying, i am not login that it would be login himself when start the system, 

now , he does't that and i try to login in again,again, but he isn't say your password is wrong, just dont let you 
enter the X-windows.

 who can help me about the question of that .
 my englist is very poor,

---

### Post by mgigirey on 2009-11-13
Before you boot your system press ESC in the GRUB loader and choose for boot in recovery mode, when you get to the shell just execute pwconv to generate again your /etc/shadow.
[http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/](http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/)

---

