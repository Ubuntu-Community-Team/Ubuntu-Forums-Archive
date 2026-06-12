---
title: "Pidgim Crash"
date: 2010-02-16
forum: General Help
---

### Post by sinurge on 2010-02-16
I use jaunty, and everytime i start pidgim it crashes not error message shown, i removed it and installed it again, no sucess. I guess it must be dropping error messages somewhere.  Can someone help or provide me where should i be looking for the error messages, i went to system log but could not find it. I tried dmsg | tail , post the crash, did not see anything.

---

### Post by Vaphell on 2010-02-17
launch pidgin from terminal, most apps spit warnings and errors that way. if there is nothing, i think you may be out of luck.

also you can try newer version using this ppa:
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by akakingess on 2010-02-17
> **Vaphell said:**
> launch pidgin from terminal, most apps spit warnings and errors that way. if there is nothing, i think you may be out of luck.

also you can try newer version using this ppa:
[https://launchpad.net/~pidgin-developers/+archive/ppa]("https://launchpad.net/%7Epidgin-developers/+archive/ppa")

+1 on the running it from the terminal, as I have solved a few issues that route.

---

### Post by sinurge on 2010-02-17
this is the output of running it from command prompt 
*** stack smashing detected ***: pidgin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb765cda8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb765cd60]
/usr/lib/pidgin/musictracker.so[0xb6568ed4]
/usr/lib/pidgin/musictracker.so[0xb6557330]
/usr/lib/libpurple.so.0(purple_plugin_load+0x233)[0xb774a493]
/usr/lib/libpurple.so.0(purple_plugins_load_saved+0x79)[0xb774aff9]
pidgin(main+0x6b6)[0x80cae96]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7575775]
pidgin[0x8070aa1]

---

