---
title: "Thunderbird + hotmail"
date: 2010-06-25
forum: General Help
---

### Post by J V on 2010-06-25
Thunderbird 3 just won't work: I've tried every setting I could think of, but SMTP just won't work (POP works fine though)

Does anyone know how to setup SMTP?

```
LoadPlugin: failed to initialize shared library /home/j/.mozilla/plugins/libflashplayer.so [/home/j/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [libxul.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /home/j/.mozilla/plugins/libflashplayer.so [/home/j/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [libxul.so: cannot open shared object file: No such file or directory]
deliver mode: 0
```

---

### Post by J V on 2010-06-26
Bump... Please help...

---

### Post by philinux on 2010-06-26
This is smtp from evolution I think TB uses port 25 anyway so maybe no need to specify.
Weird flash player errors! Try 
```
thunderbird -safe-mode

```
I once put smpt by mistake in the server bit. That wont work. :lolflag:

---

### Post by matt-fender on 2010-06-26
Have you tried doing a google search for an "Hotmail addon for thunderbird" i had to use this even when in winbloze

---

### Post by philinux on 2010-06-26
> **matt-fender said:**
> Have you tried doing a google search for an "Hotmail addon for thunderbird" i had to use this even when in winbloze

No need now they allow pop.

---

### Post by matt-fender on 2010-06-26
> **philinux said:**
> No need now they allow pop.

SWEET, folder support too? :D

---

### Post by philinux on 2010-06-26
> **matt-fender said:**
> SWEET, folder support too? :D

Ah, I'm not sure as I use evolution. Maybe it works in thunderbird.
[http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html)

I've got Yahoo working in evo too.

---

### Post by J V on 2010-06-26
Yes they allow POP and SMTP: It worked in Evolution but every timeout (Which happened often) it erased my password and had a bugged interface: If this hasn't passed 100 paperclips yet it never will so I decided to switch to thunderbird... Only now SMTP won't work. Could it be that tbird wants TSL specifically? (Tbird 3 only has the option for "SSL/TLS")

-safe-mode didn't help, still got the plugin errors... wtf is thunderbird doing trying to run firefox plugins anyway?

---

### Post by J V on 2010-06-27
Bump... can't send email... losing connection to the internet... dying... melting...

---

### Post by J V on 2010-06-28
Bump, need email

Edti: Fixed... but now I have to use STARTTLS without "Secure authentication" - Does this mean everyone with wireshark can read my info? 

Also, when I get a large batch of email, the notifications last forever, isn't there a setting to make them all go at once?

---

### Post by MoRoBoShi on 2010-07-23
I've just sniffed a test email, everything seems to be encrypted with TLSv1.
Maybe this is not a "strong" encryption.;)

Ciao.

---

