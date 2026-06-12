---
title: "Terminal problems"
date: 2006-02-18
forum: General Help
---

### Post by hung_gar on 2006-02-18
Hi.  I'm trying to install java.  I'm following the instructions on the web page; however, it tells me from the terminal program to enter su then password....

This is were my problem is:
     su
     password: _

When I'm prompted for the password nothing happens when I type.  The only key that it seems to see is the return key (hence not my password) and acess denied.

I suspect this is something simple.  I'm new to linux. Any help is greatly appreciated
Thank you.
A^2

---

### Post by JasonL on 2006-02-18
When entering a password into terminal it never shows any kind of input happening, it does even show **** so just type in your password and press enter and it should work.

---

### Post by hung_gar on 2006-02-18
I've tried that but it still isn't working.
I know the password is correct because it works in other places.

---

### Post by kaamos on 2006-02-18
type "sudo su" instead of "su"

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by JasonL on 2006-02-18
I think its because your trying to use su, su is for the superuser which I think is disabled. Try using sudo instead.

^^ beat me to it.

---

### Post by hung_gar on 2006-02-18
This is the error message I get,


su: Authentication failure
Sorry.


Any other ideas?

---

### Post by JasonL on 2006-02-18
Looks like your still using the su command, type sudo instead of su.

---

### Post by hung_gar on 2006-02-18
Thank you I think that's going to do it.  I'll let you know in a minute.

:)

---

### Post by hung_gar on 2006-02-18
\\:D/ 

sudo -i
password

Done!!!

Thanks to you all.

:)

---

