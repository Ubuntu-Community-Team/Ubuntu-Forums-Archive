---
title: "mail from terminal problem"
date: 2011-04-23
forum: General Help
---

### Post by meredith_fer on 2011-04-23
Hi guys

I am having this issue, when I try to send an email from the console. I have installed hirloommailx.

I write mailx "EMAIL ADDRESS HERE", then the subject, message and the final point, as usual, but this is what I get:

~$ /usr/lib/sendmail: Permiso denegado
"/home/MY USERNAME/dead.letter" 9/218
. . . message not sent.

thank you in advance!!!

---

### Post by dcstar on 2011-04-24
> **meredith_fer said:**
> Hi guys

I am having this issue, when I try to send an email from the console. I have installed hirloommailx.

I write mailx "EMAIL ADDRESS HERE", then the subject, message and the final point, as usual, but this is what I get:

~$ /usr/lib/sendmail: Permiso denegado
"/home/MY USERNAME/dead.letter" 9/218
. . . message not sent.

thank you in advance!!!

You need a MTA installed to use command line mail, install the **postfix** package.

---

### Post by meredith_fer on 2011-05-24
> **dcstar said:**
> You need a MTA installed to use command line mail, install the **postfix** package.

thanxs but still not getting any...

"EOT
/usr/lib/sendmail: Permiso denegado
user@user-laptop:~$ "/home/user/dead.letter" 9/220
. . . message not sent.
"

---

