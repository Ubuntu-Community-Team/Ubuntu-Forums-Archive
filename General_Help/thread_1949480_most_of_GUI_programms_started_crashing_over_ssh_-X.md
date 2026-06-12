---
title: "most of GUI programms started crashing over ssh -X on Ubuntu 11.10"
date: 2012-03-30
forum: General Help
---

### Post by agurkas on 2012-03-30
Hello, 

I have 4 Ubuntu workstations that I work with remotely.
Sometimes I log over ssh using -X so I can access some gui applications on remote desktop.

3 boxes are Ubuntu 11.10 Unity. kernel 3.0.0-17 with all the latest package updates.
1 box is Ubuntu 11.04. Unity.

so running gui applications used to work.
But recently on those 3 Ubuntu boxes running most of gui applications that used to work started crashing with similar errors. (Ubuntu 11.04 still works)

I understand all went broken after some library update but is there a way to fix it?

So for instance starting even the simplest gcalctool (calculator) it chashes like this:

gcalctool
*** glibc detected *** gcalctool: malloc(): memory corruption: 0x00000000026a6e60 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7a6e6)[0x7f24ec9c26e6]
/lib/x86_64-linux-gnu/libc.so.6(+0x7c248)[0x7f24ec9c4248]
/lib/x86_64-linux-gnu/libc.so.6(__libc_calloc+0xc2)[0x7f24ec9c76e2]
/usr/lib/x86_64-linux-gnu/libXi.so.6(XIQueryDevice+0x1bc)[0x7f24eaa7a62c]
/usr/lib/libgdk-3.so.0(+0x3dcdb)[0x7f24edebccdb]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x883)[0x7f24ed495483]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_new_valist+0x1d6)[0x7f24ed495d66]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_new+0xd4)[0x7f24ed496074]
/usr/lib/libgdk-3.so.0(+0x3c462)[0x7f24edebb462]
/usr/lib/libgdk-3.so.0(+0x40943)[0x7f24edebf943]
/usr/lib/libgdk-3.so.0(+0x3edf0)[0x7f24edebddf0]
/usr/lib/libgtk-3.so.0(gtk_init_check+0x14)[0x7f24ee24cda4]
/usr/lib/libgtk-3.so.0(gtk_init+0x9)[0x7f24ee24cdc9]
gcalctool(main+0x46a)[0x40d4ea]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f24ec96930d]
gcalctool[0x40d675]
======= Memory map: ========
00400000-0043e000 r-xp 00000000 08:01 14417941                           /usr/bin/gcalctool
0063d000-0063e000 r--p 0003d000 08:01 14417941                           /usr/bin/gcalctool
0063e000-0063f000 rw-p 0003e000 08:01 14417941                           /usr/bin/gcalctool
0063f000-00643000 rw-p 00000000 00:00 0 
0262d000-026b1000 rw-p 00000000 00:00 0                                  [heap]
7f24e0000000-7f24e0021000 rw-p 00000000 00:00 0 
7f24e0021000-7f24e4000000 ---p 00000000 00:00 0 
7f24e55d5000-7f24e55ea000 r-xp 00000000 08:01 12058670                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f24e55ea000-7f24e57e9000 ---p 00015000 08:01 12058670                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f24e57e9000-7f24e57ea000 r--p 00014000 08:01 12058670                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f24e57ea000-7f24e57eb000 rw-p 00015000 08:01 12058670                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f24e57eb000-7f24e57ec000 ---p 00000000 00:00 0 
7f24e57ec000-7f24e5fec000 rw-p 00000000 00:00 0 
7f24e5fec000-7f24e5ffa000 r-xp 00000000 08:01 14424878                   /usr/lib/liboverlay-scrollbar3-0.2.so.0.0.11
7f24e5ffa000-7f24e61f9000 ---p 0000e000 08:01 14424878                   /usr/lib/liboverlay-scrollbar3-0.2.so.0.0.11
7f24e61f9000-7f24e61fa000 r--p 0000d000 08:01 14424878                   /usr/lib/liboverlay-scrollbar3-0.2.so.0.0.11
7f24e61fa000-7f24e61fb000 rw-p 0000e000 08:01 14424878                   /usr/lib/liboverlay-scrollbar3-0.2.so.0.0.11
7f24e61fb000-7f24e61fc000 ---p 00000000 00:00 0 
7f24e61fc000-7f24e69fc000 rw-p 00000000 00:00 0 
7f24e69fc000-7f24e6a08000 r-xp 00000000 08:01 12059184                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f24e6a08000-7f24e6c07000 ---p 0000c000 08:01 12059184                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f24e6c07000-7f24e6c08000 r--p 0000b000 08:01 12059184                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f24e6c08000-7f24e6c09000 rw-p 0000c000 08:01 12059184                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f24e6c09000-7f24e6c13000 r-xp 00000000 08:01 12059189                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f24e6c13000-7f24e6e13000 ---p 0000a000 08:01 12059189                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f24e6e13000-7f24e6e14000 r--p 0000a000 08:01 12059189                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f24e6e14000-7f24e6e15000 rw-p 0000b000 08:01 12059189                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f24e6e15000-7f24e6e2c000 r-xp 00000000 08:01 12059176                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f24e6e2c000-7f24e702b000 ---p 00017000 08:01 12059176                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f24e702b000-7f24e702c000 r--p 00016000 08:01 12059176                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f24e702c000-7f24e702d000 rw-p 00017000 08:01 12059176                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f24e702d000-7f24e702f000 rw-p 00000000 00:00 0 
7f24e702f000-7f24e7037000 r-xp 00000000 08:01 12059179                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f24e7037000-7f24e7236000 ---p 00008000 08:01 12059179                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f24e7236000-7f24e7237000 r--p 00007000 08:01 12059179                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f24e7237000-7f24e7238000 rw-p 00008000 08:01 12059179                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f24e7238000-7f24e723f000 r-xp 00000000 08:01 14420921                   /usr/lib/gio/modules/libdconfsettings.so
7f24e723f000-7f24e743f000 ---p 00007000 08:01 14420921                   /usr/lib/gio/modules/libdconfsettings.so
7f24e743f000-7f24e7440000 r--p 00007000 08:01 14420921                   /usr/lib/gio/modules/libdconfsettings.so
7f24e7440000-7f24e7441000 rw-p 00008000 08:01 14420921                   /usr/lib/gio/modules/libdconfsettings.so
7f24e7441000-7f24e7457000 r-xp 00000000 08:01 14419562                   /usr/lib/gvfs/libgvfscommon.so
7f24e7457000-7f24e7656000 ---p 00016000 08:01 14419562                   /usr/lib/gvfs/libgvfscommon.so
7f24e7656000-7f24e7657000 r--p 00015000 08:01 14419562                   /usr/lib/gvfs/libgvfscommon.so
7f24e7657000-7f24e7658000 rw-p 00016000 08:01 14419562                   /usr/lib/gvfs/libgvfscommon.so
7f24e7658000-7f24e769a000 r-xp 00000000 08:01 12059120                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f24e769a000-7f24e7899000 ---p 00042000 08:01 12059120                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f24e7899000-7f24e789a000 r--p 00041000 08:01 12059120                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f24e789a000-7f24e789b000 rw-p 00042000 08:01 12059120                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f24e789b000-7f24e78ae000 r-xp 00000000 08:01 14419564                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f24e78ae000-7f24e7aad000 ---p 00013000 08:01 14419564                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f24e7aad000-7f24e7aae000 r--p 00012000 08:01 14419564                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f24e7aae000-7f24e7aaf000 rw-p 00013000 08:01 14419564                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f24e7aaf000-7f24e8033000 r--p 00000000 08:01 14418312                   /usr/lib/locale/locale-archive
7f24e8033000-7f24e8038000 r-xp 00000000 08:01 14419664                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f24e8038000-7f24e8237000 ---p 00005000 08:01 14419664                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f24e8237000-7f24e8238000 r--p 00004000 08:01 14419664                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f24e8238000-7f24e8239000 rw-p 00005000 08:01 14419664                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f24e8239000-7f24e823b000 r-xp 00000000 08:01 14419660                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f24e823b000-7f24e843a000 ---p 00002000 08:01 14419660                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f24e843a000-7f24e843b000 r--p 00001000 08:01 14419660                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f24e843b000-7f24e843c000 rw-p 00002000 08:01 14419660                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f24e843c000-7f24e8463000 r-xp 00000000 08:01 12058662                   /lib/x86_64-linux-gnu/libexpat.so.1.5.2
7f24e8463000-7f24e8663000 ---p 00027000 08:01 12058662                   /lib/x86_64-linux-gnu/libexpat.so.1.5.2
7f24e8663000-7f24e8665000 r--p 00027000 08:01 12058662                   /lib/x86_64-linux-gnu/libexpat.so.1.5.2
7f24e8665000-7f24e8666000 rw-p 00029000 08:01 12058662                   /lib/x86_64-linux-gnu/libexpat.so.1.5.2
7f24e8666000-7f24e866f000 r-xp 00000000 08:01 14420286                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f24e866f000-7f24e886f000 ---p 00009000 08:01 14420286                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f24e886f000-7f24e8870000 r--p 00009000 08:01 14420286                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f24e8870000-7f24e8871000 rw-p 0000a000 08:01 14420286                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f24e8871000-7f24e8878000 r-xp 00000000 08:01 14420269                   /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f24e8878000-7f24e8a78000 ---p 00007000 08:01 14420269                   /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f24e8a78000-7f24e8a79000 r--p 00007000 08:01 14420269                   /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f24e8a79000-7f24e8a7a000 rw-p 00008000 08:01 14420269                   /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f24e8a7a000-7f24e8a7c000 r-xp 00000000 08:01 14420283                   /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f24e8a7c000-7f24e8c7b000 ---p 00002000 08:01 14420283                   /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f24e8c7b000-7f24e8c7c000 r--p 00001000 08:01 14420283                   /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f24e8c7c000-7f24e8c7d000 rw-p 00002000 08:01 14420283                   /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f24e8c7d000-7f24e8ca3000 r-xp 00000000 08:01 12058645                   /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f24e8ca3000-7f24e8ea3000 ---p 00026000 08:01 12058645                   /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f24e8ea3000-7f24e8ea4000 r--p 00026000 08:01 12058645                   /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f24e8ea4000-7f24e8ea5000 rw-p 00027000 08:01 12058645                   /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f24e8ea5000-7f24e8f13000 r-xp 00000000 08:01 14419650                   /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.22.2
7f24e8f13000-7f24e9113000 ---p 0006e000 08:01 14419650                   /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.22.2
7f24e9113000-7f24e9118000 r--p 0006e000 08:01 14419650                   /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.22.2
7f24e9118000-7f24e9119000 rw-p 00073000 08:01 14419650                   /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.22.2
7f24e9119000-7f24e9134000 r-xp 00000000 08:01 14419668                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f24e9134000-7f24e9333000 ---p 0001b000 08:01 14419668                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f24e9333000-7f24e9334000 r--p 0001a000 08:01 14419668                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f24e9334000-7f24e9335000 rw-p 0001b000 08:01 14419668                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f24e9335000-7f24e93c7000 r-xp 00000000 08:01 14422491                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7f24e93c7000-7f24e95c6000 ---p 00092000 08:01 14422491                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7f24e95c6000-7f24e95cc000 r--p 00091000 08:01 14422491                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7f24e95cc000-7f24e95cd000 rw-p 00097000 08:01 14422491                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7f24e95cd000-7f24e95d4000 r-xp 00000000 08:01 12059205                   /lib/x86_64-linux-gnu/librt-2.13.so
7f24e95d4000-7f24e97d3000 ---p 00007000 08:01 12059205                   /lib/x86_64-linux-gnu/librt-2.13.so
7f24e97d3000-7f24e97d4000 r--p 00006000 08:01 12059205                   /lib/x86_64-linux-gnu/librt-2.13.so
7f24e97d4000-7f24e97d5000 rw-p 00007000 08:01 12059205                   /lib/x86_64-linux-gnu/librt-2.13.so
7f24e97d5000-7f24e9810000 r-xp 00000000 08:01 12059263                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f24e9810000-7f24e9a0f000 ---p 0003b000 08:01 12059263                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f24e9a0f000-7f24e9a10000 r--p 0003a000 08:01 12059263                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f24e9a10000-7f24e9a11000 rw-p 0003b000 08:01 12059263                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f24e9a11000-7f24e9a18000 r-xp 00000000 08:01 14418956                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f24e9a18000-7f24e9c17000 ---p 00007000 08:01 14418956                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f24e9c17000-7f24e9c18000 r--p 00006000 08:01 14418956                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f24e9c18000-7f24e9c19000 rw-p 00007000 08:01 14418956                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f24e9c19000-7f24e9c1d000 r-xp 00000000 08:01 14420568                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f24e9c1d000-7f24e9e1c000 ---p 00004000 08:01 14420568                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f24e9e1c000-7f24e9e1d000 r--p 00003000 08:01 14420568                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f24e9e1d000-7f24e9e1e000 rw-p 00004000 08:01 14420568                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f24e9e1e000-7f24e9e35000 r-xp 00000000 08:01 12059202                   /lib/x86_64-linux-gnu/libresolv-2.13.so
7f24e9e35000-7f24ea035000 ---p 00017000 08:01 12059202                   /lib/x86_64-linux-gnu/libresolv-2.13.so
7f24ea035000-7f24ea036000 r--p 00017000 08:01 12059202                   /lib/x86_64-linux-gnu/libresolv-2.13.so
7f24ea036000-7f24ea037000 rw-p 00018000 08:01 12059202                   /lib/x86_64-linux-gnu/libresolv-2.13.so
7f24ea037000-7f24ea039000 rw-p 00000000 00:00 0 
7f24ea039000-7f24ea055000 r-xp 00000000 08:01 12058710                   /lib/x86_64-linux-gnu/libselinux.so.1
7f24ea055000-7f24ea254000 ---p 0001c000 08:01 12058710                   /lib/x86_64-linux-gnu/libselinux.so.1
7f24ea254000-7f24ea255000 r--p 0001b000 08:01 12058710                   /lib/x86_64-linux-gnu/libselinux.so.1
7f24ea255000-7f24ea256000 rw-p 0001c000 08:01 12058710                   /lib/x86_64-linux-gnu/libselinux.so.1
7f24ea256000-7f24ea257000 rw-p 00000000 00:00 0 
7f24ea257000-7f24ea259000 r-xp 00000000 08:01 14420134                   /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f24ea259000-7f24ea458000 ---p 00002000 08:01 14420134                   /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f24ea458000-7f24ea459000 r--p 00001000 08:01 14420134                   /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f24ea459000-7f24ea45a000 rw-p 00002000 08:01 14420134                   /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f24ea45a000-7f24ea45c000 r-xp 00000000 08:01 14418267                   /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0
7f24ea45c000-7f24ea65b000 ---p 00002000 08:01 14418267                   /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0
7f24ea65b000-7f24ea65c000 r--p 00001000 08:01 14418267                   /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0
7f24ea65c000-7f24ea65d000 rw-p 00002000 08:01 14418267                   /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0
7f24ea65d000-7f24ea666000 r-xp 00000000 08:01 14420128                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f24ea666000-7f24ea865000 ---p 00009000 08:01 14420128                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f24ea865000-7f24ea866000 r--p 00008000 08:01 14420128                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f24ea866000-7f24ea867000 rw-p 00009000 08:01 14420128                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f24ea867000-7f24ea86f000 r-xp 00000000 08:01 14428393                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f24ea86f000-7f24eaa6e000 ---p 00008000 08:01 14428393                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f24eaa6e000-7f24eaa6f000 r--p 00007000 08:01 14428393                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f24eaa6f000-7f24eaa70000 rw-p 00008000 08:01 14428393                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f24eaa70000-7f24eaa7f000 r-xp 00000000 08:01 14421644                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f24eaa7f000-7f24eac7e000 ---p 0000f000 08:01 14421644                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f24eac7e000-7f24eac7f000 r--p 0000e000 08:01 14421644                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f24eac7f000-7f24eac80000 rw-p 0000f000 08:01 14421644                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f24eac80000-7f24eac82000 r-xp 00000000 08:01 14428387                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f24eac82000-7f24eae81000 ---p 00002000 08:01 14428387                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f24eae81000-7f24eae82000 r--p 00001000 08:01 14428387                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f24eae82000-7f24eae83000 rw-p 00002000 08:01 14428387                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f24eae83000-7f24eae95000 r-xp 00000000 08:01 14417962                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f24eae95000-7f24eb094000 ---p 00012000 08:01 14417962                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f24eb094000-7f24eb095000 r--p 00011000 08:01 14417962                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f24eb095000-7f24eb096000 rw-p 00012000 08:01 14417962                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f24eb096000-7f24eb099000 r-xp 00000000 08:01 14420712                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f24eb099000-7f24eb298000 ---p 00003000 08:01 14420712                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f24eb298000-7f24eb299000 r--p 00002000 08:01 14420712                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f24eb299000-7f24eb29a000 rw-p 00003000 08:01 14420712                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f24eb29a000-7f24eb2ce000 r-xp 00000000 08:01 14417939                   /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
7f24eb2ce000-7f24eb4ce000 ---p 00034000 08:01 14417939                   /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
7f24eb4ce000-7f24eb4cf000 r--p 00034000 08:01 14417939                   /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
7f24eb4cf000-7f24eb4d0000 rw-p 00035000 08:01 14417939                   /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
7f24eb4d0000-7f24eb4fa000 r-xp 00000000 08:01 14421005                   /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.2903.0
7f24eb4fa000-7f24eb6f9000 ---p 0002a000 08:01 14421005                   /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.2903.0
7f24eb6f9000-7f24eb6fa000 r--p 00029000 08:01 14421005                   /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.2903.0
7f24eb6fa000-7f24eb6fb000 rw-p 0002a000 08:01 14421005                   /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.2903.0
7f24eb6fb000-7f24eb719000 r-xp 00000000 08:01 14417961                   /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
7f24eb719000-7f24eb918000 ---p 0001e000 08:01 14417961                   /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
7f24eb918000-7f24eb919000 r--p 0001d000 08:01 14417961                   /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
7f24eb919000-7f24eb91a000 rw-p 0001e000 08:01 14417961                   /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
7f24eb91a000-7f24eb9d3000 r-xp 00000000 08:01 14420310                   /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f24eb9d3000-7f24ebbd2000 ---p 000b9000 08:01 14420310                   /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f24ebbd2000-7f24ebbd4000 r--p 000b8000 08:01 14420310                   /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f24ebbd4000-7f24ebbd5000 rw-p 000ba000 08:01 14420310                   /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f24ebbd5000-7f24ebbd8000 rw-p 00000000 00:00 0 
7f24ebbd8000-7f24ebbde000 r-xp 00000000 08:01 14421318                   /usr/lib/x86_64-linux-gnu/libcairo-gobject.so.2.11000.2
7f24ebbde000-7f24ebdde000 ---p 00006000 08:01 14421318                   /usr/lib/x86_64-linux-gnu/libcairo-gobject.so.2.11000.2
7f24ebdde000-7f24ebde0000 r--p 00006000 08:01 14421318                   /usr/lib/x86_64-linux-gnu/libcairo-gobject.so.2.11000.2
7f24ebde0000-7f24ebde1000 rw-p 00008000 08:01 14421318                   /usr/lib/x86_64-linux-gnu/libcairo-gobject.so.2.11000.2
7f24ebde1000-7f24ebde6000 r-xp 00000000 08:01 14420120                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f24ebde6000-7f24ebfe5000 ---p 00005000 08:01 14420120                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f24ebfe5000-7f24ebfe6000 r--p 00004000 08:01 14420120                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f24ebfe6000-7f24ebfe7000 rw-p 00005000 08:01 14420120                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f24ebfe7000-7f24ec11a000 r-xp 00000000 08:01 14419656                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f24ec11a000-7f24ec31a000 ---p 00133000 08:01 14419656                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f24ec31a000-7f24ec31b000 r--p 00133000 08:01 14419656                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f24ec31b000-7f24ec31f000 rw-p 00134000 08:01 14419656                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f24ec31f000-7f24ec32a000 r-xp 00000000 08:01 14421008                   /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.2903.0
7f24ec32a000-7f24ec52a000 ---p 0000b000 08:01 14421008                   /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.2903.0
7f24ec52a000-7f24ec52b000 r--p 0000b000 08:01 14421008                   /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.2903.0
7f24ec52b000-7f24ec52c000 rw-p 0000c000 08:01 14421008                   /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.2903.0
7f24ec52c000-7f24ec543000 r-xp 00000000 08:01 12058652                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f24ec543000-7f24ec742000 ---p 00017000 08:01 12058652                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f24ec742000-7f24ec743000 r--p 00016000 08:01 12058652                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f24ec743000-7f24ec744000 rw-p 00017000 08:01 12058652                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f24ec744000-7f24ec746000 r-xp 00000000 08:01 12059167                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f24ec746000-7f24ec946000 ---p 00002000 08:01 12059167                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f24ec946000-7f24ec947000 r--p 00002000 08:01 12059167                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f24ec947000-7f24ec948000 rw-p 00003000 08:01 12059167                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f24ec948000-7f24ecadf000 r-xp 00000000 08:01 12059158                   /lib/x86_64-linux-gnu/libc-2.13.so
7f24ecadf000-7f24eccde000 ---p 00197000 08:01 12059158                   /lib/x86_64-linux-gnu/libc-2.13.so
7f24eccde000-7f24ecce2000 r--p 00196000 08:01 12059158                   /lib/x86_64-linux-gnu/libc-2.13.so
7f24ecce2000-7f24ecce3000 rw-p 0019a000 08:01 12059158                   /lib/x86_64-linux-gnu/libc-2.13.so
7f24ecce3000-7f24ecce9000 rw-p 00000000 00:00 0 
7f24ecce9000-7f24ecd01000 r-xp 00000000 08:01 12059199                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f24ecd01000-7f24ecf00000 ---p 00018000 08:01 12059199                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f24ecf00000-7f24ecf01000 r--p 00017000 08:01 12059199                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f24ecf01000-7f24ecf02000 rw-p 00018000 08:01 12059199                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f24ecf02000-7f24ecf06000 rw-p 00000000 00:00 0 
7f24ecf06000-7f24ecf89000 r-xp 00000000 08:01 12059170                   /lib/x86_64-linux-gnu/libm-2.13.so
7f24ecf89000-7f24ed188000 ---p 00083000 08:01 12059170                   /lib/x86_64-linux-gnu/libm-2.13.so
7f24ed188000-7f24ed189000 r--p 00082000 08:01 12059170                   /lib/x86_64-linux-gnu/libm-2.13.so
7f24ed189000-7f24ed18a000 rw-p 00083000 08:01 12059170                   /lib/x86_64-linux-gnu/libm-2.13.so
7f24ed18a000-7f24ed27e000 r-xp 00000000 08:01 12059087                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f24ed27e000-7f24ed47d000 ---p 000f4000 08:01 12059087                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f24ed47d000-7f24ed47e000 r--p 000f3000 08:01 12059087                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f24ed47e000-7f24ed47f000 rw-p 000f4000 08:01 12059087                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f24ed47f000-7f24ed480000 rw-p 00000000 00:00 0 
7f24ed480000-7f24ed4ce000 r-xp 00000000 08:01 14420544                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f24ed4ce000-7f24ed6ce000 ---p 0004e000 08:01 14420544                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f24ed6ce000-7f24ed6cf000 r--p 0004e000 08:01 14420544                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f24ed6cf000-7f24ed6d0000 rw-p 0004f000 08:01 14420544                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f24ed6d0000-7f24ed6d1000 rw-p 00000000 00:00 0 
7f24ed6d1000-7f24ed718000 r-xp 00000000 08:01 14421004                   /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.2903.0
7f24ed718000-7f24ed918000 ---p 00047000 08:01 14421004                   /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.2903.0
7f24ed918000-7f24ed91a000 r--p 00047000 08:01 14421004                   /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.2903.0
7f24ed91a000-7f24ed91b000 rw-p 00049000 08:01 14421004                   /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.2903.0
7f24ed91b000-7f24eda56000 r-xp 00000000 08:01 14419682                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.3000.0
7f24eda56000-7f24edc55000 ---p 0013b000 08:01 14419682                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.3000.0
7f24edc55000-7f24edc59000 r--p 0013a000 08:01 14419682                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.3000.0
7f24edc59000-7f24edc5b000 rw-p 0013e000 08:01 14419682                   /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.3000.0
7f24edc5b000-7f24edc5d000 rw-p 00000000 00:00 0 
7f24edc5d000-7f24edc7c000 r-xp 00000000 08:01 14421210                   /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.20209.1
7f24edc7c000-7f24ede7c000 ---p 0001f000 08:01 14421210                   /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.20209.1
7f24ede7c000-7f24ede7e000 r--p 0001f000 08:01 14421210                   /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.20209.1
7f24ede7e000-7f24ede7f000 rw-p 00021000 08:01 14421210                   /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.20209.1
7f24ede7f000-7f24edef6000 r-xp 00000000 08:01 14419066                   /usr/lib/libgdk-3.so.0.200.0
7f24edef6000-7f24ee0f6000 ---p 00077000 08:01 14419066                   /usr/lib/libgdk-3.so.0.200.0
7f24ee0f6000-7f24ee0f9000 r--p 00077000 08:01 14419066                   /usr/lib/libgdk-3.so.0.200.0
7f24ee0f9000-7f24ee0fb000 rw-p 0007a000 08:01 14419066                   /usr/lib/libgdk-3.so.0.200.0
7f24ee0fb000-7f24ee53d000 r-xp 00000000 08:01 14427326                   /usr/lib/libgtk-3.so.0.200.0
7f24ee53d000-7f24ee73d000 ---p 00442000 08:01 14427326                   /usr/lib/libgtk-3.so.0.200.0
7f24ee73d000-7f24ee743000 r--p 00442000 08:01 14427326                   /usr/lib/libgtk-3.so.0.200.0
7f24ee743000-7f24ee747000 rw-p 00448000 08:01 14427326                   /usr/lib/libgtk-3.so.0.200.0
7f24ee747000-7f24ee74a000 rw-p 00000000 00:00 0 
7f24ee74a000-7f24ee74d000 r-xp 00000000 08:01 14418361                   /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f24ee74d000-7f24ee94c000 ---p 00003000 08:01 14418361                   /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f24ee94c000-7f24ee94d000 r--p 00002000 08:01 14418361                   /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f24ee94d000-7f24ee94e000 rw-p 00003000 08:01 14418361                   /usr/lib/liblaunchpad-integration-3.0.so.1.0.0
7f24ee94e000-7f24eea9f000 r-xp 00000000 08:01 14421028                   /usr/lib/libxml2.so.2.7.8
7f24eea9f000-7f24eec9e000 ---p 00151000 08:01 14421028                   /usr/lib/libxml2.so.2.7.8
7f24eec9e000-7f24eeca6000 r--p 00150000 08:01 14421028                   /usr/lib/libxml2.so.2.7.8
7f24eeca6000-7f24eeca8000 rw-p 00158000 08:01 14421028                   /usr/lib/libxml2.so.2.7.8
7f24eeca8000-7f24eeca9000 rw-p 00000000 00:00 0 
7f24eeca9000-7f24eecca000 r-xp 00000000 08:01 12059150                   /lib/x86_64-linux-gnu/ld-2.13.so
7f24eee6f000-7f24eee91000 r--p 00000000 08:01 15467417                   /usr/share/glib-2.0/schemas/gschemas.compiled
7f24eee91000-7f24eeea7000 rw-p 00000000 00:00 0 
7f24eeeb1000-7f24eeeb2000 r--p 00000000 08:01 16525433                   /usr/share/locale-langpack/en_GB/LC_MESSAGES/atk10.mo
7f24eeeb2000-7f24eeeb3000 r--p 00000000 08:01 16523017                   /usr/share/locale-langpack/en/LC_MESSAGES/gtk30.mo
7f24eeeb3000-7f24eeeb5000 r--p 00000000 08:01 16523008                   /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk30.mo
7f24eeeb5000-7f24eeeb9000 r--p 00000000 08:01 16523014                   /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk30-properties.mo
7f24eeeb9000-7f24eeeba000 r--p 00000000 08:01 20325578                   /home/user/.config/dconf/user
7f24eeeba000-7f24eeebb000 r--s 00000000 08:01 19136614                   /home/user/.cache/dconf/user
7f24eeebb000-7f24eeebc000 r--p 00000000 08:01 16527560                   /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
7f24eeebc000-7f24eeebf000 r--p 00000000 08:01 16522516                   /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
7f24eeebf000-7f24eeec6000 r--s 00000000 08:01 18743372                   /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7f24eeec6000-7f24eeec7000 r--p 00000000 08:01 16522563                   /usr/share/locale-langpack/en_GB/LC_MESSAGES/gcalctool.mo
7f24eeec7000-7f24eeec9000 rw-p 00000000 00:00 0 
7f24eeec9000-7f24eeeca000 r--p 00020000 08:01 12059150                   /lib/x86_64-linux-gnu/ld-2.13.so
7f24eeeca000-7f24eeecc000 rw-p 00021000 08:01 12059150                   /lib/x86_64-linux-gnu/ld-2.13.so
7fff96613000-7fff96634000 rw-p 00000000 00:00 0                          [stack]
7fff9665c000-7fff9665d000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

Thank you.

---

