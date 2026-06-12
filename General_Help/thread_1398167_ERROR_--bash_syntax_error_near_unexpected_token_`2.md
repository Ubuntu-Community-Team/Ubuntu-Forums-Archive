---
title: "ERROR --bash: syntax error near unexpected token `2 --"
date: 2010-02-04
forum: General Help
---

### Post by Sakrow on 2010-02-04
First of all welcome 

The following problem occurs to me, I'm creating a distribution (as a class project) for my school (I'm studying telecommunications and computer systems). 

I am following, in order to create the distribution, the manual that you can find on this page: 

[http://lpmagazine.org/es/magazine/796-ecomercio-y-oscommerce ]("http://lpmagazine.org/es/magazine/796-ecomercio-y-oscommerce")

But when I get to write: 

*for i in "/etc/hosts /etc/hostname /etc/resolv.conf /etc/timezone /etc/fstab /etc/mtab /etc/shadow /etc/shadow- /etc/gshadow /etc/gshadow- /etc/gdm/gdm- cdd.conf /etc/gdm/gdm.conf- custom /etc/X11/xorg.conf /boot/grub/menu.lst /boot/grub/device.map" do rm $i done 2>/dev/null*

I get the following error: 

**bash: syntax error near unexpected token `2 ' **

And I tried to find a solution, but can not. 

If anyone could help I would appreciate it greatly. 

Att 

Sakrow

---

### Post by bluefrog on 2010-02-04
missing ; 

for i in foo; do command; done

---

### Post by Sakrow on 2010-02-05
> **bluefrog said:**
> missing ; 

for i in foo; do command; done

Thanks!!!! It works perfectly!!!!

But now I think of a problem inthis sintasix command: 

**do uid = `cat / etc / passwd | grep" ^ $ (i): "| awk-F": " '(print $ 3)'` [ "$ uid"-gt "999"-a "$ uid" -- ****ne "65,534"] & & userdel - force $ (i) 2> / dev / null done **

I get the following error: 

*bash: syntax error near unexpected token `do ' *

I tried to fix it by putting ";" where thought necessary, but can not. 

Did I might provide some type of solution? 

Thank you very much

---

### Post by bluefrog on 2010-02-05
you need a for to use do.
uid is not a command
if you want to assign the result of a command to a variable
var=$(command)  or var=`command`

---

