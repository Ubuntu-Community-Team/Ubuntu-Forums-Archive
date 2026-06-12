---
title: "World of Warcraft Crashes after character select."
date: 2010-03-07
forum: General Help
---

### Post by Goodspeed on 2010-03-07
Hello,

I am fairly new to the Linux community however I have done my research on this issue and tried every fix I could think of (registry edits, wine config changes, config.wtf alterations).  

All of these things got me where I am today.  WoW will run in OpenGL mode for a couple seconds after loading my character and then wine crashes with this error from the Terminal:

wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0039fc10 EBP:0039fc70 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00002000 ECX:00000de1 EDX:16cc0ad0
 ESI:00000000 EDI:0e071be8
Stack dump:
0x0039fc10:  00632b93 00000de1 00000000 000083f1
0x0039fc20:  00000080 00000080 00000000 00002000
0x0039fc30:  16cc0ad0 00000080 0e071be8 00000080
0x0039fc40:  00000000 00000000 00000080 00000080
0x0039fc50:  0061a9d3 00000008 00000000 00000100
0x0039fc60:  16cc2ad0 00002000 16cc0ad0 000083f1
Backtrace:
=>0 0x00000000 (0x0039fc70)
  1 0x00632da8 in wow (+0x232da8) (0x0039fcc8)
  2 0x00632e62 in wow (+0x232e62) (0x0039fcd8)
  3 0x0061995c in wow (+0x21995c) (0x0039fce4)
  4 0x00616f95 in wow (+0x216f95) (0x0039fd08)
  5 0x0048f7af in wow (+0x8f7af) (0x0039fd48)
  6 0x00427a39 in wow (+0x27a39) (0x0039fd78)
  7 0x00424aac in wow (+0x24aac) (0x0039fda0)
  8 0x0042614a in wow (+0x2614a) (0x0039fdf4)
  9 0x00426191 in wow (+0x26191) (0x0039fe0c)
  10 0x00406d8d in wow (+0x6d8d) (0x0039fea8)
  11 0x7b858944 in kernel32 (+0x48944) (0x0039fee8)
  12 0x7bc6ef14 call_thread_func+0xc() in ntdll (0x0039fef8)
  13 0x7bc6f0e0 call_thread_entry_point+0x70() in ntdll (0x0039ffc8)
  14 0x7bc4afea in ntdll (+0x3afea) (0x0039ffe8)
  15 0x74b4be9d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x00000000: addb    %al,0x0(%eax)
Modules:
Module    Address            Debug info    Name (120 modules)
PE      400000-  e24000    Export          wow
PE    10000000-10069000    Deferred        divxdecoder
ELF    20000000-20048000    Deferred        dsound<elf>
  \-PE    20010000-20048000    \               dsound
ELF    32007000-3200b000    Deferred        libnss_mdns4_minimal.so.2
PE    3c910000-3c984000    Deferred        battle.net
ELF    44921000-4498f000    Deferred        msvcrt<elf>
  \-PE    44930000-4498f000    \               msvcrt
ELF    500bc000-500c3000    Deferred        libnss_dns.so.2
ELF    50cb2000-50cd0000    Deferred        libgcc_s.so.1
ELF    68000000-68019000    Deferred        libpthread.so.0
ELF    68019000-6815e000    Deferred        libc.so.6
ELF    6815e000-68162000    Deferred        libdl.so.2
ELF    68162000-68188000    Deferred        libm.so.6
ELF    68188000-68190000    Deferred        libnss_compat.so.2
ELF    68190000-681a7000    Deferred        libnsl.so.1
ELF    681a7000-681b2000    Deferred        libnss_nis.so.2
ELF    681b2000-681be000    Deferred        libnss_files.so.2
ELF    681be000-6825b000    Deferred        opengl32<elf>
  \-PE    681d0000-6825b000    \               opengl32
ELF    6825b000-68264000    Deferred        libsm.so.6
ELF    68264000-6827f000    Deferred        libice.so.6
ELF    6827f000-6828f000    Deferred        libxext.so.6
ELF    6828f000-683be000    Deferred        libx11.so.6
ELF    683be000-68422000    Deferred        libgl.so.1
ELF    68422000-68427000    Deferred        libuuid.so.1
ELF    68427000-68445000    Deferred        libxcb.so.1
ELF    68445000-6844b000    Deferred        libxxf86vm.so.1
ELF    6844b000-6844e000    Deferred        libxdamage.so.1
ELF    6844e000-68454000    Deferred        libxfixes.so.3
ELF    68454000-6845e000    Deferred        libdrm.so.2
ELF    6845e000-68463000    Deferred        libxdmcp.so.6
ELF    68463000-6846c000    Deferred        librt.so.1
ELF    6846c000-68579000    Deferred        user32<elf>
  \-PE    68480000-68579000    \               user32
ELF    68579000-68603000    Deferred        gdi32<elf>
  \-PE    68590000-68603000    \               gdi32
ELF    68603000-6865c000    Deferred        advapi32<elf>
  \-PE    68610000-6865c000    \               advapi32
ELF    6865c000-686cc000    Deferred        rpcrt4<elf>
  \-PE    68670000-686cc000    \               rpcrt4
ELF    686cc000-686e5000    Deferred        version<elf>
  \-PE    686d0000-686e5000    \               version
ELF    686e5000-686f9000    Deferred        lz32<elf>
  \-PE    686f0000-686f9000    \               lz32
ELF    686f9000-6871a000    Deferred        imm32<elf>
  \-PE    68700000-6871a000    \               imm32
ELF    6871a000-68772000    Deferred        wininet<elf>
  \-PE    68720000-68772000    \               wininet
ELF    68772000-68788000    Deferred        libz.so.1
ELF    68788000-687e6000    Deferred        shlwapi<elf>
  \-PE    687a0000-687e6000    \               shlwapi
ELF    687e6000-68977000    Deferred        shell32<elf>
  \-PE    68800000-68977000    \               shell32
ELF    68977000-68a45000    Deferred        comctl32<elf>
  \-PE    68980000-68a45000    \               comctl32
ELF    68a45000-68a70000    Deferred        ws2_32<elf>
  \-PE    68a50000-68a70000    \               ws2_32
ELF    68a70000-68a8b000    Deferred        dinput8<elf>
  \-PE    68a80000-68a8b000    \               dinput8
ELF    68a8b000-68ac4000    Deferred        dinput<elf>
  \-PE    68a90000-68ac4000    \               dinput
ELF    68ac4000-68b4b000    Deferred        winmm<elf>
  \-PE    68ad0000-68b4b000    \               winmm
ELF    68b4b000-68b71000    Deferred        msacm32<elf>
  \-PE    68b50000-68b71000    \               msacm32
ELF    68b71000-68bca000    Deferred        setupapi<elf>
  \-PE    68b80000-68bca000    \               setupapi
ELF    68bca000-68c00000    Deferred        winspool<elf>
  \-PE    68bd0000-68c00000    \               winspool
ELF    68c00000-68c15000    Deferred        hid<elf>
  \-PE    68c10000-68c15000    \               hid
ELF    68c15000-68c94000    Deferred        libfreetype.so.6
ELF    68c94000-68cc1000    Deferred        libfontconfig.so.1
ELF    68cc1000-68ce8000    Deferred        libexpat.so.1
ELF    68ce8000-68d87000    Deferred        winex11<elf>
  \-PE    68d00000-68d87000    \               winex11
ELF    68d87000-68d8a000    Deferred        libxinerama.so.1
ELF    68d8a000-68d93000    Deferred        libxrandr.so.2
ELF    68d93000-68d97000    Deferred        libxcomposite.so.1
ELF    68d97000-68da2000    Deferred        libxcursor.so.1
ELF    68da2000-69038000    Deferred        i965_dri.so
ELF    69038000-69042000    Deferred        libdrm_intel.so.1
ELF    69042000-69075000    Deferred        uxtheme<elf>
  \-PE    69050000-69075000    \               uxtheme
ELF    69075000-690b3000    Deferred        wineoss<elf>
  \-PE    69080000-690b3000    \               wineoss
ELF    690b3000-690cb000    Deferred        msacm32<elf>
  \-PE    690c0000-690cb000    \               msacm32
ELF    690cb000-690e1000    Deferred        midimap<elf>
  \-PE    690d0000-690e1000    \               midimap
ELF    690e1000-6910b000    Deferred        libgssapi_krb5.so.2
ELF    6910b000-691b3000    Deferred        libgnutls.so.26
ELF    691b3000-691bf000    Deferred        libavahi-common.so.3
ELF    691bf000-691d0000    Deferred        libavahi-client.so.3
ELF    691d0000-69276000    Deferred        libkrb5.so.3
ELF    69276000-6929f000    Deferred        libk5crypto.so.3
ELF    6929f000-692a7000    Deferred        libkrb5support.so.0
ELF    692a7000-692ab000    Deferred        libkeyutils.so.1
ELF    692ab000-692bf000    Deferred        libresolv.so.2
ELF    692bf000-692d1000    Deferred        libtasn1.so.3
ELF    692d1000-6934d000    Deferred        libgcrypt.so.11
ELF    6934d000-69386000    Deferred        libdbus-1.so.3
ELF    69386000-6938b000    Deferred        libgpg-error.so.0
ELF    6f7e1000-6f7fe000    Deferred        ld-linux.so.2
ELF    715bf000-715c3000    Deferred        libcom_err.so.2
ELF    71fa6000-71fb0000    Deferred        libxrender.so.1
ELF    72422000-7251f000    Deferred        ole32<elf>
  \-PE    72440000-7251f000    \               ole32
ELF    7389b000-738e1000    Deferred        libcups.so.2
ELF    74872000-74876000    Deferred        libxau.so.6
ELF    74b44000-74c7f000    Export          libwine.so.1
PE    78130000-781cb000    Deferred        msvcr80
ELF    7b800000-7b93a000    Export          kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb5000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb5000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c062000-7c085000    Deferred        mpr<elf>
  \-PE    7c070000-7c085000    \               mpr
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\wow.exe
    00000037    0
    00000033    1
    00000030    0
    0000002f    1
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    2
    00000027   15
    00000026   15
    00000022    2
    00000021   15
    0000001f   15
    0000001d    0
    0000001c    0
    0000001b    0
    00000009    0 <==
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000016    0
    00000013    0
    00000012    0
00000019 explorer.exe
    0000001a    0
Backtrace:
=>0 0x00000000 (0x0039fc70)
  1 0x00632da8 in wow (+0x232da8) (0x0039fcc8)
  2 0x00632e62 in wow (+0x232e62) (0x0039fcd8)
  3 0x0061995c in wow (+0x21995c) (0x0039fce4)
  4 0x00616f95 in wow (+0x216f95) (0x0039fd08)
  5 0x0048f7af in wow (+0x8f7af) (0x0039fd48)
  6 0x00427a39 in wow (+0x27a39) (0x0039fd78)
  7 0x00424aac in wow (+0x24aac) (0x0039fda0)
  8 0x0042614a in wow (+0x2614a) (0x0039fdf4)
  9 0x00426191 in wow (+0x26191) (0x0039fe0c)
  10 0x00406d8d in wow (+0x6d8d) (0x0039fea8)
  11 0x7b858944 in kernel32 (+0x48944) (0x0039fee8)
  12 0x7bc6ef14 call_thread_func+0xc() in ntdll (0x0039fef8)
  13 0x7bc6f0e0 call_thread_entry_point+0x70() in ntdll (0x0039ffc8)
  14 0x7bc4afea in ntdll (+0x3afea) (0x0039ffe8)
  15 0x74b4be9d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
Killed

---

### Post by Goodspeed on 2010-03-07
Thought I should add that I can run WoW in D3D mode however, I get random black polygons all over the place, usually under characters and places where there should be shadows (even with shadows turned off).

I would run in D3D mode but OpenGL gives better FPS and isn't graphically annoying.

---

### Post by Goodspeed on 2010-03-08
Anyone?

---

