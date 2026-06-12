---
title: "After update to 11.10 my thunderbird crash on start"
date: 2011-10-19
forum: General Help
---

### Post by amfibrahii on 2011-10-19
Hello everyone.

I'a update my ubuntu upto 11.10 version.

After that my email client - thunderbird crash after 3-4 seconds work.

Run on console..and in out...after crash...write whis text:

enigmail.js: Registered components

(thunderbird-bin:15290): libebook-WARNING **: e_book_client_new: Cannot get book from factory: Invalid source
Inconsistency detected by ld.so: dl-open.c: 597: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

Please help:)

---

### Post by davidoca on 2011-11-14
This seems to be due to Thunderbird integration with Gnome / Evolution, and in my case, I resolved it (I think) by installing "evolution-couchdb-backend".

You could also try removing "thunderbird-gnome-support".

David

---

