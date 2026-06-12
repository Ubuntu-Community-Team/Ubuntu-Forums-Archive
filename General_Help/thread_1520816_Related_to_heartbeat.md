---
title: "Related to heartbeat"
date: 2010-06-30
forum: General Help
---

### Post by hellomythili on 2010-06-30
hi,
I installed clusterglue,heartbeat and resource agent in mu ubuntu machine.
I configured ha.cf,authkeys and tried to start heartbeat ,At that time i am getting following errors.....
Starting High-Availability services: *** glibc detected *** heartbeat: free(): invalid pointer: 0x0810e428 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7da7b25]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7dab590]
heartbeat[0x805af61]
heartbeat[0x805a828]
heartbeat[0x805c692]
heartbeat(init_config+0x44f)[0x805ce1f]
heartbeat(main+0xb73)[0x80566a3]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d52450]
heartbeat[0x804f151]
======= Memory map: ========
08048000-08072000 r-xp 00000000 08:03 1533166    /usr/lib/heartbeat/heartbeat
08072000-08073000 rw-p 0002a000 08:03 1533166    /usr/lib/heartbeat/heartbeat
08073000-08128000 rw-p 08073000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0 
b7a21000-b7b00000 ---p b7a21000 00:00 0 
b7b13000-b7b1b000 r-xp 00000000 08:03 689163     /lib/tls/i686/cmov/libnss_nis-2.7.so
b7b1b000-b7b1d000 rw-p 00007000 08:03 689163     /lib/tls/i686/cmov/libnss_nis-2.7.so
b7b1d000-b7b31000 r-xp 00000000 08:03 689158     /lib/tls/i686/cmov/libnsl-2.7.so
b7b31000-b7b33000 rw-p 00013000 08:03 689158     /lib/tls/i686/cmov/libnsl-2.7.so
b7b33000-b7b35000 rw-p b7b33000 00:00 0 
b7b35000-b7b3e000 r-xp 00000000 08:03 689161     /lib/tls/i686/cmov/libnss_files-2.7.so
b7b3e000-b7b40000 rw-p 00008000 08:03 689161     /lib/tls/i686/cmov/libnss_files-2.7.so
b7b40000-b7b4a000 r-xp 00000000 08:03 671756     /lib/libgcc_s.so.1
b7b4a000-b7b4b000 rw-p 0000a000 08:03 671756     /lib/libgcc_s.so.1
b7b4b000-b7b4d000 r-xp 00000000 08:03 1533130    /usr/lib/heartbeat/plugins/HBcomm/ping.so
b7b4d000-b7b4e000 rw-p 00002000 08:03 1533130    /usr/lib/heartbeat/plugins/HBcomm/ping.so
b7b4e000-b7b4f000 rw-p b7b4e000 00:00 0 
b7b4f000-b7b52000 r-xp 00000000 08:03 1533123    /usr/lib/heartbeat/plugins/HBcomm/bcast.so
b7b52000-b7b53000 rw-p 00002000 08:03 1533123    /usr/lib/heartbeat/plugins/HBcomm/bcast.so
b7b53000-b7b95000 rw-p b7b53000 00:00 0 
b7b95000-b7bb8000 r-xp 00000000 08:03 689156     /lib/tls/i686/cmov/libm-2.7.so
b7bb8000-b7bba000 rw-p 00023000 08:03 689156     /lib/tls/i686/cmov/libm-2.7.so
b7bba000-b7bce000 r-xp 00000000 08:03 689166     /lib/tls/i686/cmov/libpthread-2.7.so
b7bce000-b7bd0000 rw-p 00013000 08:03 689166     /lib/tls/i686/cmov/libpthread-2.7.so
b7bd0000-b7bd2000 rw-p b7bd0000 00:00 0 
b7bd2000-b7bf8000 r-xp 00000000 08:03 1222596    /usr/lib/libpcre.so.3.12.1
b7bf8000-b7bf9000 rw-p 00026000 08:03 1222596    /usr/lib/libpcre.so.3.12.1
b7bf9000-b7c02000 r-xp 00000000 08:03 671850     /lib/libpam.so.0.81.6
b7c02000-b7c03000 rw-p 00008000 08:03 671850     /lib/libpam.so.0.81.6
b7c03000-b7c04000 rw-p b7c03000 00:00 0 
b7c04000-b7d1e000 r-xp 00000000 08:03 1223469    /usr/lib/libxml2.so.2.6.31
b7d1e000-b7d23000 rw-p 00119000 08:03 1223469    /usr/lib/libxml2.so.2.6.31
b7d23000-b7d24000 rw-p b7d23000 00:00 0 
b7d24000-b7d2a000 r-xp 00000000 08:03 1222495    /usr/lib/libltdl.so.3.1.6
b7d2a000-b7d2b000 rw-p 00005000 08:03 1222495    /usr/lib/libltdl.so.3.1.6
b7d2b000-b7d2d000 r-xp 00000000 08:03 689155     /lib/tls/i686/cmov/libdl-2.7.so
b7d2d000-b7d2f000 rw-p 00001000 08:03 689155     /lib/tls/i686/cmov/libdl-2.7.so
b7d2f000-b7d36000 r-xp 00000000 08:03 689168     /lib/tls/i686/cmov/librt-2.7.so
b7d36000-b7d38000 rw-p 00006000 08:03 689168     /lib/tls/i686/cmov/librt-2.7.so
b7d38000-b7d3b000 r-xp 00000000 08:03 671891     /lib/libuuid.so.1.2
b7d3b000-b7d3c000 rw-p 00002000 08:03 671891     /lib/libuuid.so.1.2
b7d3c000-b7e85000 r-xp 00000000 08:03 689152     /lib/tls/i686/cmov/libc-2.7.so
b7e85000-b7e86000 r--p 00149000 08:03 689152     /lib/tls/i686/cmov/libc-2.7.so
b7e86000-b7e88000 rw-p 0014a000 08:03 689152     /lib/tls/i686/cmov/libc-2.7.so
b7e88000-b7e8c000 rw-p b7e88000 00:00 0 
b7e8c000-b7ea0000 r-xp 00000000 08:03 1222790    /usr/lib/libz.so.1.2.3.3
b7ea0000-b7ea1000 rw-p 00013000 08:03 1222790    /usr/lib/libz.so.1.2.3.3
b7ea1000-b7eb0000 r-xp 00000000 08:03 671782     /lib/libbz2.so.1.0.4
b7eb0000-b7eb1000 rw-p 0000f000 08:03 671782     /lib/libbz2.so.1.0.4
b7eb1000-b7f61000 r-xp 00000000 08:03 1223437    /usr/lib/libglib-2.0.so.0.1600.6
b7f61000-b7f62000 rw-p 000b0000 08:03 1223437    /usr/lib/libglib-2.0.so.0.1600.6
b7f62000-b7f64000 r-xp 00000000 08:03 1223708    /usr/lib/libapphb.so.2.0.0
b7f64000-b7f65000 rw-p 00001000 08:03 1223708    /usr/lib/libapphb.so.2.0.0
b7f65000-b7f66000 r-xp 00000000 08:03 1223839    /usr/lib/libplumbgpl.so.1.0.0
b7f66000-b7f67000 rw-p 00000000 08:03 1223839    /usr/lib/libplumbgpl.so.1.0.0
b7f67000-b7f69000 rw-p b7f67000 00:00 0 
b7f69000-b7f90000 r-xp 00000000 08:03 1223838    /usr/lib/libplumb.so.1.0.0
b7f90000-b7f92000 rw-p 00026000 08:03 1223838    /usr/lib/libplumb.so.1.0.0
b7f92000-b7f93000 rw-p b7f92000 00:00 0 
b7f93000-b7f9a000 r-xp 00000000 08:03 1223837    /usr/lib/libpils.so.1.0.0
b7f9a000-b7f9b000 rw-p 00006000 08:03 1223837    /usr/lib/libpils.so.1.0.0
b7f9b000-b7f9f000 r-xp 00000000 08:03 1223841    /usr/lib/libstonith.so.1.0.0
b7f9f000-b7fa0000 rw-p 00003000 08:03 1223841    /usr/lib/libstonith.so.1.0.0
b7fa0000-b7fa7000 r-xp 00000000 08:03 689159     /lib/tls/i686/cmov/libnss_compat-2.7.so
b7fa7000-b7fa9000 rw-p 00006000 08:03 689159     /lib/tls/i686/cmov/libnss_compat-2.7.so
b7fa9000-b7faa000 rw-p b7fa9000 00:00 0 
b7faa000-b7fac000 rw-s 00000000 00:09 1179662    /SYSV00000000 (deleted)
b7fac000-b7fae000 r-xp 00000000 08:03 1532957    /usr/lib/heartbeat/plugins/InterfaceMgr/generic.so
b7fae000-b7faf000 rw-p 00001000 08:03 1532957    /usr/lib/heartbeat/plugins/InterfaceMgr/generic.so
b7faf000-b7fb1000 rw-p b7faf000 00:00 0 
b7fb1000-b7fb2000 r-xp b7fb1000 00:00 0          [vdso]
b7fb2000-b7fcc000 r-xp 00000000 08:03 671813     /lib/ld-2.7.so
b7fcc000-b7fce000 rw-p 00019000 08:03 671813     /lib/ld-2.7.so
bfc06000-bfc1b000 rw-p bffeb000 00:00 0          [stack]
Aborted
 Heartbeat failure [rc=134]. Failed.

heartbeat: udpport setting must precede media statementsheartbeat[7435]: 2010/06/29_12:16:11 info: Version 2 support: on
heartbeat[7435]: 2010/06/29_12:16:11 WARN: File /usr/etc/ha.d//haresources exists.
heartbeat[7435]: 2010/06/29_12:16:11 WARN: This file is not used because crm is enabled
heartbeat[7435]: 2010/06/29_12:16:11 info: Version 2 support: respawn
heartbeat[7435]: 2010/06/29_12:16:11 WARN: File /usr/etc/ha.d//haresources exists.
heartbeat[7435]: 2010/06/29_12:16:11 WARN: This file is not used because crm is enabled
heartbeat[7435]: 2010/06/29_12:16:11 ERROR: Duplicate apiauth directive for API client cib: [cib     uid=hacluster]
heartbeat[7435]: 2010/06/29_12:16:11 ERROR: Invalid apiauth directive [cib     uid=hacluster]
heartbeat[7435]: 2010/06/29_12:16:11 info: Syntax: apiauth client [uid=uidlist] [gid=gidlist]
heartbeat[7435]: 2010/06/29_12:16:11 info: Where uidlist is a comma-separated list of uids,
heartbeat[7435]: 2010/06/29_12:16:11 info: and gidlist is a comma-separated list of gids
heartbeat[7435]: 2010/06/29_12:16:11 info: One or the other must be specified.
can any help me in solving this
Thanks
mythili

---

