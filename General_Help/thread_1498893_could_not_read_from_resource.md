---
title: "could not read from resource"
date: 2010-06-01
forum: General Help
---

### Post by anil567 on 2010-06-01
hi all i have recently upgraded to 10.04 Lucid Lynx 32 bit. my processor is pentium dual core Acer aspire SA90  when i incert DVD/ CD for playing movie an error code comes up with "Could not read form resource". what can i do :confused::confused: any help will be appreciated.

---

### Post by Shakz on 2010-06-01
Did you install the restricted extras?
I had this issue too till I installed 

sudo apt-get install ubuntu-restricted-extras

**AND**

sudo /usr/share/doc/libdvdread4/install-css.sh

Got the exact same error as you till I installed libdvdread4.

---

### Post by fordguydude on 2010-06-01
I did the exact thing as above but the last one I get this at the end--

```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

After a restart, I no longer get an error message, but the DVD's won't play. It gets stuck before it even starts.

---

### Post by Mark M Bravura on 2010-06-06
@Shakz - Thankyou, worked like a charm! Now to finally watch a film:popcorn:

---

