---
title: "Street Fighter IV"
date: 2010-04-13
forum: General Help
---

### Post by champ1 on 2010-04-13
[COLOR=Blue]     This game is good. I tried it at my friend house on Playstation 3, and just had to get my own. This is the problem that happens whenever i try to launch it. If anyone could help, i'll be thankful. [/COLOR]


wine: Unhandled page fault on read access to 0x00000100 at address 0x425fa7 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000100 in 32-bit code (0x00425fa7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00425fa7 ESP:015bf7dc EBP:015bf8b0 EFLAGS:00010297(   - 00     RISAP1C)
 EAX:00000154 EBX:00400000 ECX:00000000 EDX:00471ec0
 ESI:00000100 EDI:00471ec0
Stack dump:
0x015bf7dc:  0000e000 00400000 015bf834 0107092e
0x015bf7ec:  00400000 00471ec0 0000e000 00000104
0x015bf7fc:  00000100 0040f224 00400000 0000e000
0x015bf80c:  0046f718 0012c3c8 0041a391 0000e000
0x015bf81c:  015bf834 00000100 0046f718 00400000
0x015bf82c:  ffffffff 015bfca2 00000000 00000000
Backtrace:
=>1 0x00425fa7 in sf4launcher (+0x25fa7) (0x015bf8b0)
  2 0x015bf8f4 (0x7d5027d8)
  3 0x602ae3f0 in libc.so.6 (+0x1423f0) (0x602ae3f0)
  4 0x602ae3e8 in libc.so.6 (+0x1423e8) (0x602ae3e8)
  5 0x602ae3e0 in libc.so.6 (+0x1423e0) (0x602ae3e0)
  6 0x7d53b1a8 (0x7d53b148)
  7 0x00000011 (0x00000000)
0x00425fa7: movw    0x0(%esi),%ax
Modules:
Module    Address            Debug info    Name (85 modules)
PE      400000- 10b1000    Export          sf4launcher
ELF    60000000-6001d000    Deferred        ld-linux.so.2
ELF    6001d000-60153000    Deferred        libwine.so.1
ELF    60153000-6016c000    Deferred        libpthread.so.0
ELF    6016c000-602b1000    Export          libc.so.6
ELF    602b1000-602b5000    Deferred        libdl.so.2
ELF    602b5000-602db000    Deferred        libm.so.6
ELF    602db000-602e3000    Deferred        libnss_compat.so.2
ELF    602e3000-602ef000    Deferred        libnss_files.so.2
ELF    602ef000-60308000    Deferred        dinput8<elf>
  \-PE    602f0000-60308000    \               dinput8
ELF    60308000-60340000    Deferred        dinput<elf>
  \-PE    60310000-60340000    \               dinput
ELF    60340000-603e6000    Deferred        ole32<elf>
  \-PE    60350000-603e6000    \               ole32
ELF    603e6000-60438000    Deferred        advapi32<elf>
  \-PE    603f0000-60438000    \               advapi32
ELF    60438000-60583000    Deferred        user32<elf>
  \-PE    60450000-60583000    \               user32
ELF    60583000-60622000    Deferred        gdi32<elf>
  \-PE    60590000-60622000    \               gdi32
ELF    60622000-60685000    Deferred        rpcrt4<elf>
  \-PE    60630000-60685000    \               rpcrt4
ELF    60685000-606a4000    Deferred        iphlpapi<elf>
  \-PE    60690000-606a4000    \               iphlpapi
ELF    606a4000-606b8000    Deferred        msimg32<elf>
  \-PE    606b0000-606b8000    \               msimg32
ELF    606b8000-607cc000    Deferred        shell32<elf>
  \-PE    606d0000-607cc000    \               shell32
ELF    607cc000-60827000    Deferred        shlwapi<elf>
  \-PE    607e0000-60827000    \               shlwapi
ELF    60827000-608ea000    Deferred        comctl32<elf>
  \-PE    60830000-608ea000    \               comctl32
ELF    608ea000-60990000    Deferred        oleaut32<elf>
  \-PE    60900000-60990000    \               oleaut32
ELF    60990000-60a0f000    Deferred        libfreetype.so.6
ELF    60a0f000-60a25000    Deferred        libz.so.1
ELF    60a25000-60a52000    Deferred        libfontconfig.so.1
ELF    60a52000-60aec000    Deferred        winex11<elf>
  \-PE    60a60000-60aec000    \               winex11
ELF    60aec000-60af5000    Deferred        libsm.so.6
ELF    60af5000-60b10000    Deferred        libice.so.6
ELF    60b10000-60b16000    Deferred        libxxf86vm.so.1
ELF    60b16000-60b26000    Deferred        libxext.so.6
ELF    60b26000-60b2b000    Deferred        libuuid.so.1
ELF    60b2b000-60b49000    Deferred        libxcb.so.1
ELF    60b49000-60b4e000    Deferred        libxdmcp.so.6
ELF    60b4e000-60b6f000    Deferred        imm32<elf>
  \-PE    60b50000-60b6f000    \               imm32
ELF    60b6f000-60b72000    Deferred        libxinerama.so.1
ELF    60b72000-60b7c000    Deferred        libxrender.so.1
ELF    60b7c000-60b85000    Deferred        libxrandr.so.2
ELF    60b85000-60b89000    Deferred        libxcomposite.so.1
ELF    60b89000-60b8f000    Deferred        libxfixes.so.3
ELF    60b8f000-60b9a000    Deferred        libxcursor.so.1
ELF    60b9a000-60be0000    Deferred        libcups.so.2
ELF    60be0000-60c0a000    Deferred        libgssapi_krb5.so.2
ELF    60c0a000-60cb0000    Deferred        libkrb5.so.3
ELF    60cb0000-60cd9000    Deferred        libk5crypto.so.3
ELF    60cd9000-60cdd000    Deferred        libcom_err.so.2
ELF    60cdd000-60ce5000    Deferred        libkrb5support.so.0
ELF    60ce5000-60ce9000    Deferred        libkeyutils.so.1
ELF    60ce9000-60cfb000    Deferred        libtasn1.so.3
ELF    60cfb000-60d77000    Deferred        libgcrypt.so.11
ELF    60d77000-60db0000    Deferred        libdbus-1.so.3
ELF    60db0000-60db9000    Deferred        librt.so.1
ELF    60db9000-60dbe000    Deferred        libgpg-error.so.0
ELF    64f4e000-64f85000    Deferred        winspool<elf>
  \-PE    64f60000-64f85000    \               winspool
ELF    67e3d000-67e64000    Deferred        libexpat.so.1
ELF    6ba2a000-6ba3b000    Deferred        libavahi-client.so.3
ELF    6c569000-6c580000    Deferred        libnsl.so.1
ELF    6e2c6000-6e2ca000    Deferred        libxau.so.6
ELF    6f8b5000-6f8c0000    Deferred        libnss_nis.so.2
ELF    74e47000-74eef000    Deferred        libgnutls.so.26
ELF    7593e000-75971000    Deferred        uxtheme<elf>
  \-PE    75940000-75971000    \               uxtheme
ELF    78237000-78366000    Deferred        libx11.so.6
ELF    792f1000-792fd000    Deferred        libavahi-common.so.3
ELF    7a674000-7a688000    Deferred        libresolv.so.2
ELF    7b800000-7b93c000    Deferred        kernel32<elf>
  \-PE    7b820000-7b93c000    \               kernel32
ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\CAPCOM\STREETFIGHTERIV\SF4Launcher.exe
    00000009    0 <==
0000000c 
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000016 
    00000017    0
Backtrace:
=>1 0x00425fa7 in sf4launcher (+0x25fa7) (0x015bf8b0)
  2 0x015bf8f4 (0x7d5027d8)
  3 0x602ae3f0 in libc.so.6 (+0x1423f0) (0x602ae3f0)
  4 0x602ae3e8 in libc.so.6 (+0x1423e8) (0x602ae3e8)
  5 0x602ae3e0 in libc.so.6 (+0x1423e0) (0x602ae3e0)
  6 0x7d53b1a8 (0x7d53b148)
  7 0x00000011 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x425fa7

---

### Post by cdenley on 2010-04-13
Not everything works well in wine. I'm always suprised when something does.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17140](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17140)

---

