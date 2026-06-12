---
title: "IP Address Changer"
date: 2010-06-12
forum: General Help
---

### Post by Hozza on 2010-06-12
Hi,

I have a program to update a dynamic domain name for me. I can start this program by calling on 

```
sudo /usr/local/bin/noip2
```

How can i get my computer to auto start this program on boot?

Im using Linux Mint 9 (based on ubuntu)

---

### Post by dcstar on 2010-06-13
> **Hozza said:**
> Hi,

I have a program to update a dynamic domain name for me. I can start this program by calling on 

```
sudo /usr/local/bin/noip2
```

How can i get my computer to auto start this program on boot?

Im using Linux Mint 9 (based on ubuntu)

```
sudo gedit /etc/rc.local
```

---

### Post by amite on 2010-06-13
system>>preferences >>startup application >>ADD

---

### Post by dcstar on 2010-06-13
> **amite said:**
> system>>preferences >>startup application >>ADD

That is **not** Startup on Boot, that is Startup on Login - two totally different things.

---

### Post by amite on 2010-06-13
Thanks.....
> **dcstar said:**
> That is **not** Startup on Boot, that is Startup on Login - two totally different things.
if i write a script and put it in init.d then would it run on boot or it require some other operation to run at boot time?


=======================================
i am new and try to learn...........

---

### Post by Hozza on 2010-06-13
> **dcstar said:**
> ```
sudo gedit /etc/rc.local
```

so what to i put into this file to make the program startup on boot?

---

### Post by spiky001 on 2010-06-13
I found this see if it helps
[http://www.ivankristianto.com/os/ubuntu/howto-run-script-on-boot-process-in-ubuntu/1171/](http://www.ivankristianto.com/os/ubuntu/howto-run-script-on-boot-process-in-ubuntu/1171/)

---

### Post by Hozza on 2010-06-13
Well my local.rc looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sh /usr/local/bin/noip2

exit 0
```

and it does not seem to work???

---

### Post by Hozza on 2010-06-16
anyone?

---

### Post by Hozza on 2010-06-30
Really anyone???? :bump:

---

