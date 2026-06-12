---
title: "buffer verflow detected"
date: 2010-06-07
forum: General Help
---

### Post by maryjane on 2010-06-07
Hi everyone!

I'm newbie at Linux and I'm trying to make a simulation in a open source model. I have a test case which has already run well, but not with me:/ I have this message in the terminal:
*** buffer overflow detected ***: /home/mary/tmp_Saturne/ONDAS.CAS.06072145/cs13.exe terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x4756008]
/lib/tls/i686/cmov/libc.so.6[0x4755040]
/lib/tls/i686/cmov/libc.so.6[0x4754778]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x46de67e]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0xe24)[0x46b2964]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x475482d]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x475476d]
/home/mary/Code_Saturne/opt/fvm-0.12.0/arch/Linux/lib/libfvm.so.0[0x40908d6]
/home/mary/Code_Saturne/opt/fvm-0.12.0/arch/Linux/lib/libfvm.so.0(fvm_to_ensight_case_create+0x82a)[0x409158a]
/home/mary/Code_Saturne/opt/fvm-0.12.0/arch/Linux/lib/libfvm.so.0(fvm_to_ensight_init_writer+0x139)[0x408b989]
/home/mary/Code_Saturne/opt/fvm-0.12.0/arch/Linux/lib/libfvm.so.0(fvm_writer_init+0x9d2)[0x409af02]
/home/mary/tmp_Saturne/ONDAS.CAS.06072145/cs13.exe(cs_post_ajoute_writer+0x1b1)[0x80d7c19]
/home/mary/tmp_Saturne/ONDAS.CAS.06072145/cs13.exe(cs_post_init_pcp_writer+0x222)[0x80d94e5]
/home/mary/tmp_Saturne/ONDAS.CAS.06072145/cs13.exe(main+0x2c1)[0x80bfcc5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x468bb56]
/home/mary/tmp_Saturne/ONDAS.CAS.06072145/cs13.exe[0x805fa21]
======= Memory map: ========

I used valgrind meanwhile and it returns this:

==19168==    at 0x4024C1C: malloc (vg_replace_malloc.c:195)
==19168==    by 0x4752453: nss_parse_service_list (nsswitch.c:622)
==19168==    by 0x4752B98: __nss_database_lookup (nsswitch.c:164)
==19168==    by 0x4E04EAB: ???
==19168==    by 0x4E05B5C: ???
==19168==    by 0x470AE34: getpwuid_r@@GLIBC_2.1.2 (getXXbyYY_r.c:253)
==19168==    by 0x470A79E: getpwuid (getXXbyYY.c:117)
==19168==    by 0x80A1565: cs_base_info_systeme (cs_base.c:851)
==19168==    by 0x80BFB56: main (cs_main.c:294)


Thank you a lot in advance,
Maria

---

