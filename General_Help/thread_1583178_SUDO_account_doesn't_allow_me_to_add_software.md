---
title: "SUDO account doesn't allow me to add software"
date: 2010-09-27
forum: General Help
---

### Post by Like2Learn on 2010-09-27
Hi there,
 
I recently got my sudo account from our system administrator on a Linux Box (Red Hat Enterprise 5.0). I logged on with my SUDO account and password, no problem. However, when I tried to add software into the Linux Box, I got the following warning:
"Sorry, user ****** is not allowed to execute '/bin/su' as root on computer *******".
 
I tried the following tricks and none of them works. They all asked for root password besides of the sudo pasword.
$sudo bash
$sudo -s
$sudo password root
$sudo su -
$su - root
 
Is there any way to bypass the root password and install the software? I guess the administrator didn't assign authorization to my sudo account to add software, right? Any suggestion?
 
Thank you!

---

### Post by andrewthomas on 2010-09-27
> **Like2Learn said:**
>  Any suggestion?
 

Talk to your sys admin.

---

### Post by 3Miro on 2010-09-27
> **andrewthomas said:**
> Talk to your sys admin.

+1. If the sys admin has made a mistake on your sudo account, then he can fix that (talk to him/her). If he meant to restrict you, then what you are trying to do is hacking and we don't help with that here. (also this is an Ubuntu forum, not a RHEL one)

---

