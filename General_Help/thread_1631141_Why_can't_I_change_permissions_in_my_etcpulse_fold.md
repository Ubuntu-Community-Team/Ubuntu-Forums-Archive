---
title: "Why can't I change permissions in my /etc/pulse folder?"
date: 2010-11-26
forum: General Help
---

### Post by giddyup306 on 2010-11-26
Hi all.

I'm trying to (hopefully) fix my audio glitch.  I'm trying to edit my /etc/pulse/default.pa.


I tried:

```
sudo chmod 775 /etc/pulse
```and

```
sudo chmod 775 /etc/pulse/default.pa
```and

```
sudo chmod g+rwx,o+rwx /etc/pulse
```Since I have SElinux I thought this may be the problem, so I tried.

```
sudo echo 0 > /etc/selinux/enforce

```But it said permission denied.

Thanks in advance.

---

### Post by coldsystem on 2010-11-26
try  to  be  a  real root on  the  machine  and  try again 

Su -  root 
then  echo  Selinux enforcing

---

### Post by ubey on 2010-11-26
Sounds weird.
You could try to run nautilus as root user
```
sudo nautilus
```
And try access the file(s) from there.

---

### Post by giddyup306 on 2010-11-26
> **coldsystem said:**
> try  to  be  a  real root on  the  machine  and  try again 

Su -  root 
then  echo  Selinux enforcing

I forgot to mention I tried that as well.

---

### Post by giddyup306 on 2010-11-26
> **ubey said:**
> Sounds weird.
You could try to run nautilus as root user
```
sudo nautilus
```And try access the file(s) from there.


That's what I was looking for!  I know I've done it before, but I couldn't find how to do it for he life of me.  Every time I run into some neat code trick, I make a new text file.  Either I misplaced it, or I mislabeled it.

---

### Post by qamelian on 2010-11-26
> **ubey said:**
> Sounds weird.
You could try to run nautilus as root user
```
sudo nautilus
```And try access the file(s) from there.
This is wrong. Only use sudo for commandline tasks. For graphical applications, always use gksu or gksudo. Using sudo with some graphical apps can cause things on your system to break.

---

