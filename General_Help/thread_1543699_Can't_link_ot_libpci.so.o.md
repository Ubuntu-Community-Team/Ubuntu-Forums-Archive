---
title: "Can't link ot libpci.so.o"
date: 2010-08-01
forum: General Help
---

### Post by lz1dsb on 2010-08-01
I'm trying to use my digital certificate on an OmniKey AG CardMan 6121 through pcscd and libpcsclite. In Firefox I'm trying to configure /usr/local/lib/libsiecap11.so as software security module, but it doesn't work, because the library has unsatisfied dependencies:

$ ldd /usr/local/lib/libsiecap11.so | grep 'not found'
	libpcsclite.so.0 => not found
	libpcsclite.so.0 => not found

I have created a symbolic link like this:

$ sudo ln -s /lib/libpcsclite.so.1.0.0 /lib/libpcsclite.so.0

But nothing changes, which bugs me. Why the symbolic link does not work with ld?

---

