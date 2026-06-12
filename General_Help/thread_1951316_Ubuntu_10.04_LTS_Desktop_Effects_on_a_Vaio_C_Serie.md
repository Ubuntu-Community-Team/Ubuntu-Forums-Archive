---
title: "Ubuntu 10.04 LTS Desktop Effects on a Vaio C Series"
date: 2012-04-02
forum: General Help
---

### Post by nj96 on 2012-04-02
I recently bought a Vaio C Series laptop with the specs listed as follows:

Intel Core i5- 2410M
Windows 7 (The second I got the laptop I installed ubuntu alongside)
Hard Disk Drive 500GB
4GB Ram
ATI Radeon 6630/Some Intel Graphic chipset

The problem is, I can't install any CompizConfig settings and desktop effects on my laptops. So far, I've done the following:


Right Clicked on Desktop, went to the Visual Effects tab and clicked Extra. Checks for graphic cards for a bit then complains that Desktop Effects could not be enabled. I downloaded AMD Radeon drivers and installed them, they didn't work either. What should I do? 
I figure it may be a problem with the fact that there's two graphical options and there's no physical way of switching between them. 
For more info: 

[http://www.sony-asia.com/product/vpcca15fg](http://www.sony-asia.com/product/vpcca15fg)
Niranjan :-?

---

### Post by Paddy Landau on 2012-04-02
It is possible that the graphics card on your new computer is not fully supported with the drivers available for 10.04.

As an experiment, load 12.04 (Beta) onto a Live USB or Live CD and run it. Open a terminal (press Ctrl-Alt-T) and enter the following two commands:
```
echo ${DESKTOP_SESSION}
/usr/lib/nux/unity_support_test --print
```The first command will display "ubuntu" if the graphics card is full supported, and "ubuntu-2d" if not. The second command will display "Yes" and not "No" on all lines if fully supported.

---

