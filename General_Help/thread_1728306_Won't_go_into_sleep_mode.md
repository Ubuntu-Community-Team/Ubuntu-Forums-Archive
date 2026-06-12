---
title: "Won't go into sleep mode"
date: 2011-04-13
forum: General Help
---

### Post by MacKai on 2011-04-13
Asus u43f wont go into sleep/suspend mode. Either manually from the shut down menu or by closing the lid. the screen will turn off but the various lights do not turn of and hard drive continue to spin.

 I found this suggested test with a google search but no fix

sudo /etc/acpi/sleep.sh

which returned:

cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory


any suggestions

---

### Post by earthpigg on 2011-04-13
that folder is empty on my system, too.

can you share the guide you found on google?

---

### Post by MacKai on 2011-04-13
this is were i found that string

[http://ubuntuforums.org/showthread.php?t=1551229]("http://ubuntuforums.org/showthread.php?t=1551229")

---

### Post by earthpigg on 2011-04-13
ya, im a bit skeptical about the approach being taken in that thread.

did hibernate/suspend work for you with ubuntu on that laptop in the past? what version of ubuntu? if that is the case, i can walk you through using an older kernel from when it did work.

failing that...

in your shoes, i'd scour the internet and find someone that has that exact laptop and has sleep/hibernate functioning correctly, and i would find out the exact kernel that person used (i wouldn't worry about what version of ubuntu or even if they are using ubuntu - i'd just want the exact kernel version). i'd then install that kernel from synaptic, and hope for the best.

you can find out what kernel you are using now with this command:

```
uname -a
```

i underline the kernel version, below:

```
[chris: ~]$ uname -a
Linux chris-desktop _**2.6.35-27-generic-pae**_ #48-Ubuntu SMP Tue Feb 22 21:46:58 UTC 2011 i686 GNU/Linux
```

---

### Post by MacKai on 2011-04-13
no its a new laptop and so it has never worked .... ill look around some more thanks for looking at it though...


Ubuntu 10.10

---

### Post by earthpigg on 2011-04-13
does the problem present from the 10.10 live cd?

if so, does it also present on a 10.04 live cd?

sometimes, folks have to skip an Ubuntu release because of a very specific issue like this. many people skipped ubuntu 9.04 and went from 8.10 to 9.10, for example.

---

