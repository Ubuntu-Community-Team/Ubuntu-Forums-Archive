---
title: "Games don't work, maybe Wine?"
date: 2010-08-08
forum: General Help
---

### Post by xBiocorex on 2010-08-08
Okey dokey, so when I first got Ubuntu a few weeks ago, and got the older version of Wine from the Software Center, and it could run pretty much any game I wanted. albeit REEEAAAALLY slowly. 

Well, I upgraded to 1.2 using the instructions on the wine website, and now a couple of my low-power games (like Bootfighter Windom XP) run totally perfectly, but a lot of mainstream games like Mirror's Edge and Mass Effect 2 just crash when I attempt to open them, and all they all have the same message where the main .exe file has "encountered a serious error."

Here's what the terminal gives me:
```

Backtrace:
=>0 0x68286bbe in libc.so.6 (+0x110bbe) (0x033bd9c0)
  1 0x693815a1 in winhttp (+0x115a0) (0x033bea20)
  2 0x69381aa1 WinHttpQueryDataAvailable+0x60() in winhttp (0x033bea70)
0x68286bbe: fmull    0x488bdc4a(%ecx)
Modules:
Module    Address            Debug info    Name (155 modules)
PE      230000-  372000    Deferred        wxmsw28u_vc_custom
PE      380000-  3fc000    Deferred        wxmsw28u_html_vc_custom
PE      400000- 2ce4000    Deferred        mirrorsedge
PE     33f0000- 3476000    Deferred        wxmsw28u_xrc_vc_custom
PE     3480000- 3533000    Deferred        wxmsw28u_adv_vc_custom
PE     3540000- 3562000    Deferred        wxmsw28u_xml_vc_custom
PE     3570000- 361c000    Deferred        ilpointcloudlib
PE     3620000- 3632000    Deferred        libresample
PE     3640000- 366a000    Deferred        physxextensions
PE     3670000- 36d3000    Deferred        nxcooking
PE     36e0000- 3731000    Deferred        vorbis
PE     3740000- 3749000    Deferred        ogg
PE     3750000- 3842000    Deferred        vorbisenc
PE     3850000- 3858000    Deferred        vorbisfile
PE     3860000- 38a7000    Deferred        wxmsw28u_aui_vc_custom
PE     38b0000- 391d000    Deferred        d3dx10_35
PE     3920000- 3936000    Deferred        xinput1_3
PE     3940000- 3ce8000    Deferred        d3dx9_35
PE     4520000- 456c000    Export          paul
PE     4680000- 46bc000    Deferred        winui
PE    10000000-1030a000    Deferred        wxmsw28u_core_vc_custom
PE    18000000-18038000    Deferred        binkw32
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-6815d000    Deferred        libwine.so.1
ELF    6815d000-68176000    Deferred        libpthread.so.0
ELF    68176000-682d0000    Export          libc.so.6
ELF    682d0000-682d4000    Deferred        libdl.so.2
ELF    682d4000-682fa000    Deferred        libm.so.6
ELF    682fa000-68302000    Deferred        libnss_compat.so.2
ELF    68302000-68319000    Deferred        libnsl.so.1
ELF    68319000-68323000    Deferred        libnss_nis.so.2
ELF    68323000-6832f000    Deferred        libnss_files.so.2
ELF    6832f000-6841a000    Deferred        comctl32<elf>
  \-PE    68340000-6841a000    \               comctl32
ELF    6841a000-6854c000    Deferred        user32<elf>
  \-PE    68430000-6854c000    \               user32
ELF    6854c000-685d7000    Deferred        gdi32<elf>
  \-PE    68560000-685d7000    \               gdi32
ELF    685d7000-68632000    Deferred        advapi32<elf>
  \-PE    685e0000-68632000    \               advapi32
ELF    68632000-686a7000    Deferred        rpcrt4<elf>
  \-PE    68640000-686a7000    \               rpcrt4
ELF    686a7000-6887f000    Deferred        shell32<elf>
  \-PE    686c0000-6887f000    \               shell32
ELF    6887f000-688e1000    Deferred        shlwapi<elf>
  \-PE    68890000-688e1000    \               shlwapi
ELF    688e1000-68963000    Deferred        msvcrt<elf>
  \-PE    688f0000-68963000    \               msvcrt
ELF    68963000-68a1a000    Deferred        comdlg32<elf>
  \-PE    68970000-68a1a000    \               comdlg32
ELF    68a1a000-68a52000    Deferred        winspool<elf>
  \-PE    68a20000-68a52000    \               winspool
ELF    68a52000-68b3b000    Deferred        oleaut32<elf>
  \-PE    68a70000-68b3b000    \               oleaut32
ELF    68b3b000-68b93000    Deferred        dbghelp<elf>
  \-PE    68b40000-68b93000    \               dbghelp
ELF    68b93000-68ba9000    Deferred        psapi<elf>
  \-PE    68ba0000-68ba9000    \               psapi
ELF    68ba9000-68bd6000    Deferred        ws2_32<elf>
  \-PE    68bb0000-68bd6000    \               ws2_32
ELF    68bd6000-68bf7000    Deferred        iphlpapi<elf>
  \-PE    68be0000-68bf7000    \               iphlpapi
ELF    68bf7000-68c0c000    Deferred        faultrep<elf>
  \-PE    68c00000-68c0c000    \               faultrep
ELF    68c0c000-68c2e000    Deferred        imm32<elf>
  \-PE    68c10000-68c2e000    \               imm32
ELF    68c2e000-68c44000    Deferred        powrprof<elf>
  \-PE    68c30000-68c44000    \               powrprof
ELF    68c44000-68c78000    Deferred        d3d9<elf>
  \-PE    68c50000-68c78000    \               d3d9
ELF    68c78000-68db0000    Deferred        wined3d<elf>
  \-PE    68c80000-68db0000    \               wined3d
ELF    68db0000-68dcb000    Deferred        dinput8<elf>
  \-PE    68dc0000-68dcb000    \               dinput8
ELF    68dcb000-68e04000    Deferred        dinput<elf>
  \-PE    68dd0000-68e04000    \               dinput
ELF    68e04000-68e62000    Deferred        setupapi<elf>
  \-PE    68e10000-68e62000    \               setupapi
ELF    68e62000-68e7b000    Deferred        version<elf>
  \-PE    68e70000-68e7b000    \               version
ELF    68e7b000-68e8f000    Deferred        lz32<elf>
  \-PE    68e80000-68e8f000    \               lz32
ELF    68e8f000-68eb9000    Deferred        netapi32<elf>
  \-PE    68ea0000-68eb9000    \               netapi32
ELF    68eb9000-68f2f000    Deferred        libfreetype.so.6
ELF    68f2f000-68f44000    Deferred        libz.so.1
ELF    68f44000-68f6b000    Deferred        libexpat.so.1
ELF    68f6b000-6900e000    Deferred        winex11<elf>
  \-PE    68f80000-6900e000    \               winex11
ELF    6900e000-69017000    Deferred        libsm.so.6
ELF    69017000-69030000    Deferred        libice.so.6
ELF    69030000-69040000    Deferred        libxext.so.6
ELF    69040000-69045000    Deferred        libuuid.so.1
ELF    69045000-6905f000    Deferred        libxcb.so.1
ELF    6905f000-69063000    Deferred        libxau.so.6
ELF    69063000-69069000    Deferred        libxdmcp.so.6
ELF    69069000-6906d000    Deferred        libxinerama.so.1
ELF    6906d000-69073000    Deferred        libxxf86vm.so.1
ELF    69073000-6907d000    Deferred        libxrender.so.1
ELF    6907d000-69081000    Deferred        libxcomposite.so.1
ELF    69081000-690a2000    Deferred        localspl<elf>
  \-PE    69090000-690a2000    \               localspl
ELF    690a2000-690bd000    Deferred        spoolss<elf>
  \-PE    690b0000-690bd000    \               spoolss
ELF    690bd000-69104000    Deferred        libcups.so.2
ELF    69104000-6919f000    Deferred        libgnutls.so.26
ELF    6919f000-691ab000    Deferred        libavahi-common.so.3
ELF    691ab000-691bc000    Deferred        libavahi-client.so.3
ELF    691bc000-6926d000    Deferred        libkrb5.so.3
ELF    6926d000-69291000    Deferred        libk5crypto.so.3
ELF    69291000-69299000    Deferred        libkrb5support.so.0
ELF    69299000-6929d000    Deferred        libkeyutils.so.1
ELF    6929d000-692ae000    Deferred        libtasn1.so.3
ELF    692ae000-69321000    Deferred        libgcrypt.so.11
ELF    69321000-6935a000    Deferred        libdbus-1.so.3
ELF    6935a000-69363000    Deferred        librt.so.1
ELF    69363000-69368000    Deferred        libgpg-error.so.0
ELF    69368000-6936a000    Deferred        libnvidia-tls.so.1
ELF    6936a000-69391000    Export          winhttp<elf>
  \-PE    69370000-69391000    \               winhttp
ELF    69391000-693ac000    Deferred        oleacc<elf>
  \-PE    693a0000-693ac000    \               oleacc
ELF    693ac000-693b0000    Deferred        libnss_mdns4_minimal.so.2
ELF    693b0000-69502000    Deferred        libcrypto.so.0.9.8
ELF    69502000-6953f000    Deferred        rsaenh<elf>
  \-PE    69510000-6953f000    \               rsaenh
ELF    6a333000-6a337000    Deferred        libcom_err.so.2
ELF    6baa2000-6bae8000    Deferred        libssl.so.0.9.8
ELF    6d181000-6d1b0000    Deferred        libgssapi_krb5.so.2
ELF    6f113000-6f119000    Deferred        libxfixes.so.3
ELF    6fdb1000-6feb1000    Deferred        ole32<elf>
  \-PE    6fdd0000-6feb1000    \               ole32
ELF    705ab000-70670000    Deferred        libgl.so.1
ELF    71fa9000-72045000    Deferred        crypt32<elf>
  \-PE    71fb0000-72045000    \               crypt32
ELF    73852000-73882000    Deferred        libfontconfig.so.1
ELF    73982000-7398a000    Deferred        libxrandr.so.2
ELF    7412a000-74130000    Deferred        libnss_dns.so.2
ELF    75164000-751f5000    Deferred        winmm<elf>
  \-PE    75170000-751f5000    \               winmm
ELF    75f1e000-75f39000    Deferred        wsock32<elf>
  \-PE    75f20000-75f39000    \               wsock32
ELF    76663000-76677000    Deferred        libresolv.so.2
ELF    76b0b000-76b3f000    Deferred        uxtheme<elf>
  \-PE    76b10000-76b3f000    \               uxtheme
ELF    76d67000-76d71000    Deferred        libxcursor.so.1
PE    78130000-781cb000    Deferred        msvcr80
ELF    78a17000-7a027000    Deferred        libglcore.so.1
ELF    7b800000-7b972000    Deferred        kernel32<elf>
  \-PE    7b810000-7b972000    \               kernel32
ELF    7bc00000-7bcb8000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb8000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c18e000-7c2ab000    Deferred        libx11.so.6
PE    7c420000-7c4a7000    Deferred        msvcp80
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\EA Games\Mirror's Edge\Binaries\MirrorsEdge.exe
    00000009    0 <==
0000000e services.exe
    0000001a    0
    00000014    0
    00000010    0
    0000000f    0
00000011 svchost.exe
    00000023    0
    00000022    1
    00000021    0
    00000020    0
    0000001f    0
    0000001e    0
    00000016    0
    00000013    0
    00000012    0
00000017 winedevice.exe
    0000001d    0
    0000001c    0
    00000019    0
    00000018    0
0000002e explorer.exe
    0000002f    0
Backtrace:
=>0 0x68286bbe in libc.so.6 (+0x110bbe) (0x033bd9c0)
  1 0x693815a1 in winhttp (+0x115a0) (0x033bea20)
  2 0x69381aa1 WinHttpQueryDataAvailable+0x60() in winhttp (0x033bea70)
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
brennan@BIO:~$ fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
```

---

### Post by ed-koala on 2010-08-08
Check the Wine HQ app database.  It has plenty of info on campatibility and tricks to get programs working.

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by sandyd on 2010-08-08
> **xBiocorex said:**
> Okey dokey, so when I first got Ubuntu a few weeks ago, and got the older version of Wine from the Software Center, and it could run pretty much any game I wanted. albeit REEEAAAALLY slowly. 

Well, I upgraded to 1.2 using the instructions on the wine website, and now a couple of my low-power games (like Bootfighter Windom XP) run totally perfectly, but a lot of mainstream games like Mirror's Edge and Mass Effect 2 just crash when I attempt to open them, and all they all have the same message where the main .exe file has "encountered a serious error."

Here's what the terminal gives me:
```

Backtrace:
=>0 0x68286bbe in libc.so.6 (+0x110bbe) (0x033bd9c0)
  1 0x693815a1 in winhttp (+0x115a0) (0x033bea20)
  2 0x69381aa1 WinHttpQueryDataAvailable+0x60() in winhttp (0x033bea70)
0x68286bbe: fmull    0x488bdc4a(%ecx)
Modules:
Module    Address            Debug info    Name (155 modules)
PE      230000-  372000    Deferred        wxmsw28u_vc_custom
PE      380000-  3fc000    Deferred        wxmsw28u_html_vc_custom
PE      400000- 2ce4000    Deferred        mirrorsedge
PE     33f0000- 3476000    Deferred        wxmsw28u_xrc_vc_custom
PE     3480000- 3533000    Deferred        wxmsw28u_adv_vc_custom
PE     3540000- 3562000    Deferred        wxmsw28u_xml_vc_custom
PE     3570000- 361c000    Deferred        ilpointcloudlib
PE     3620000- 3632000    Deferred        libresample
PE     3640000- 366a000    Deferred        physxextensions
PE     3670000- 36d3000    Deferred        nxcooking
PE     36e0000- 3731000    Deferred        vorbis
PE     3740000- 3749000    Deferred        ogg
PE     3750000- 3842000    Deferred        vorbisenc
PE     3850000- 3858000    Deferred        vorbisfile
PE     3860000- 38a7000    Deferred        wxmsw28u_aui_vc_custom
PE     38b0000- 391d000    Deferred        d3dx10_35
PE     3920000- 3936000    Deferred        xinput1_3
PE     3940000- 3ce8000    Deferred        d3dx9_35
PE     4520000- 456c000    Export          paul
PE     4680000- 46bc000    Deferred        winui
PE    10000000-1030a000    Deferred        wxmsw28u_core_vc_custom
PE    18000000-18038000    Deferred        binkw32
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-6815d000    Deferred        libwine.so.1
ELF    6815d000-68176000    Deferred        libpthread.so.0
ELF    68176000-682d0000    Export          libc.so.6
ELF    682d0000-682d4000    Deferred        libdl.so.2
ELF    682d4000-682fa000    Deferred        libm.so.6
ELF    682fa000-68302000    Deferred        libnss_compat.so.2
ELF    68302000-68319000    Deferred        libnsl.so.1
ELF    68319000-68323000    Deferred        libnss_nis.so.2
ELF    68323000-6832f000    Deferred        libnss_files.so.2
ELF    6832f000-6841a000    Deferred        comctl32<elf>
  \-PE    68340000-6841a000    \               comctl32
ELF    6841a000-6854c000    Deferred        user32<elf>
  \-PE    68430000-6854c000    \               user32
ELF    6854c000-685d7000    Deferred        gdi32<elf>
  \-PE    68560000-685d7000    \               gdi32
ELF    685d7000-68632000    Deferred        advapi32<elf>
  \-PE    685e0000-68632000    \               advapi32
ELF    68632000-686a7000    Deferred        rpcrt4<elf>
  \-PE    68640000-686a7000    \               rpcrt4
ELF    686a7000-6887f000    Deferred        shell32<elf>
  \-PE    686c0000-6887f000    \               shell32
ELF    6887f000-688e1000    Deferred        shlwapi<elf>
  \-PE    68890000-688e1000    \               shlwapi
ELF    688e1000-68963000    Deferred        msvcrt<elf>
  \-PE    688f0000-68963000    \               msvcrt
ELF    68963000-68a1a000    Deferred        comdlg32<elf>
  \-PE    68970000-68a1a000    \               comdlg32
ELF    68a1a000-68a52000    Deferred        winspool<elf>
  \-PE    68a20000-68a52000    \               winspool
ELF    68a52000-68b3b000    Deferred        oleaut32<elf>
  \-PE    68a70000-68b3b000    \               oleaut32
ELF    68b3b000-68b93000    Deferred        dbghelp<elf>
  \-PE    68b40000-68b93000    \               dbghelp
ELF    68b93000-68ba9000    Deferred        psapi<elf>
  \-PE    68ba0000-68ba9000    \               psapi
ELF    68ba9000-68bd6000    Deferred        ws2_32<elf>
  \-PE    68bb0000-68bd6000    \               ws2_32
ELF    68bd6000-68bf7000    Deferred        iphlpapi<elf>
  \-PE    68be0000-68bf7000    \               iphlpapi
ELF    68bf7000-68c0c000    Deferred        faultrep<elf>
  \-PE    68c00000-68c0c000    \               faultrep
ELF    68c0c000-68c2e000    Deferred        imm32<elf>
  \-PE    68c10000-68c2e000    \               imm32
ELF    68c2e000-68c44000    Deferred        powrprof<elf>
  \-PE    68c30000-68c44000    \               powrprof
ELF    68c44000-68c78000    Deferred        d3d9<elf>
  \-PE    68c50000-68c78000    \               d3d9
ELF    68c78000-68db0000    Deferred        wined3d<elf>
  \-PE    68c80000-68db0000    \               wined3d
ELF    68db0000-68dcb000    Deferred        dinput8<elf>
  \-PE    68dc0000-68dcb000    \               dinput8
ELF    68dcb000-68e04000    Deferred        dinput<elf>
  \-PE    68dd0000-68e04000    \               dinput
ELF    68e04000-68e62000    Deferred        setupapi<elf>
  \-PE    68e10000-68e62000    \               setupapi
ELF    68e62000-68e7b000    Deferred        version<elf>
  \-PE    68e70000-68e7b000    \               version
ELF    68e7b000-68e8f000    Deferred        lz32<elf>
  \-PE    68e80000-68e8f000    \               lz32
ELF    68e8f000-68eb9000    Deferred        netapi32<elf>
  \-PE    68ea0000-68eb9000    \               netapi32
ELF    68eb9000-68f2f000    Deferred        libfreetype.so.6
ELF    68f2f000-68f44000    Deferred        libz.so.1
ELF    68f44000-68f6b000    Deferred        libexpat.so.1
ELF    68f6b000-6900e000    Deferred        winex11<elf>
  \-PE    68f80000-6900e000    \               winex11
ELF    6900e000-69017000    Deferred        libsm.so.6
ELF    69017000-69030000    Deferred        libice.so.6
ELF    69030000-69040000    Deferred        libxext.so.6
ELF    69040000-69045000    Deferred        libuuid.so.1
ELF    69045000-6905f000    Deferred        libxcb.so.1
ELF    6905f000-69063000    Deferred        libxau.so.6
ELF    69063000-69069000    Deferred        libxdmcp.so.6
ELF    69069000-6906d000    Deferred        libxinerama.so.1
ELF    6906d000-69073000    Deferred        libxxf86vm.so.1
ELF    69073000-6907d000    Deferred        libxrender.so.1
ELF    6907d000-69081000    Deferred        libxcomposite.so.1
ELF    69081000-690a2000    Deferred        localspl<elf>
  \-PE    69090000-690a2000    \               localspl
ELF    690a2000-690bd000    Deferred        spoolss<elf>
  \-PE    690b0000-690bd000    \               spoolss
ELF    690bd000-69104000    Deferred        libcups.so.2
ELF    69104000-6919f000    Deferred        libgnutls.so.26
ELF    6919f000-691ab000    Deferred        libavahi-common.so.3
ELF    691ab000-691bc000    Deferred        libavahi-client.so.3
ELF    691bc000-6926d000    Deferred        libkrb5.so.3
ELF    6926d000-69291000    Deferred        libk5crypto.so.3
ELF    69291000-69299000    Deferred        libkrb5support.so.0
ELF    69299000-6929d000    Deferred        libkeyutils.so.1
ELF    6929d000-692ae000    Deferred        libtasn1.so.3
ELF    692ae000-69321000    Deferred        libgcrypt.so.11
ELF    69321000-6935a000    Deferred        libdbus-1.so.3
ELF    6935a000-69363000    Deferred        librt.so.1
ELF    69363000-69368000    Deferred        libgpg-error.so.0
ELF    69368000-6936a000    Deferred        libnvidia-tls.so.1
ELF    6936a000-69391000    Export          winhttp<elf>
  \-PE    69370000-69391000    \               winhttp
ELF    69391000-693ac000    Deferred        oleacc<elf>
  \-PE    693a0000-693ac000    \               oleacc
ELF    693ac000-693b0000    Deferred        libnss_mdns4_minimal.so.2
ELF    693b0000-69502000    Deferred        libcrypto.so.0.9.8
ELF    69502000-6953f000    Deferred        rsaenh<elf>
  \-PE    69510000-6953f000    \               rsaenh
ELF    6a333000-6a337000    Deferred        libcom_err.so.2
ELF    6baa2000-6bae8000    Deferred        libssl.so.0.9.8
ELF    6d181000-6d1b0000    Deferred        libgssapi_krb5.so.2
ELF    6f113000-6f119000    Deferred        libxfixes.so.3
ELF    6fdb1000-6feb1000    Deferred        ole32<elf>
  \-PE    6fdd0000-6feb1000    \               ole32
ELF    705ab000-70670000    Deferred        libgl.so.1
ELF    71fa9000-72045000    Deferred        crypt32<elf>
  \-PE    71fb0000-72045000    \               crypt32
ELF    73852000-73882000    Deferred        libfontconfig.so.1
ELF    73982000-7398a000    Deferred        libxrandr.so.2
ELF    7412a000-74130000    Deferred        libnss_dns.so.2
ELF    75164000-751f5000    Deferred        winmm<elf>
  \-PE    75170000-751f5000    \               winmm
ELF    75f1e000-75f39000    Deferred        wsock32<elf>
  \-PE    75f20000-75f39000    \               wsock32
ELF    76663000-76677000    Deferred        libresolv.so.2
ELF    76b0b000-76b3f000    Deferred        uxtheme<elf>
  \-PE    76b10000-76b3f000    \               uxtheme
ELF    76d67000-76d71000    Deferred        libxcursor.so.1
PE    78130000-781cb000    Deferred        msvcr80
ELF    78a17000-7a027000    Deferred        libglcore.so.1
ELF    7b800000-7b972000    Deferred        kernel32<elf>
  \-PE    7b810000-7b972000    \               kernel32
ELF    7bc00000-7bcb8000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb8000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c18e000-7c2ab000    Deferred        libx11.so.6
PE    7c420000-7c4a7000    Deferred        msvcp80
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\EA Games\Mirror's Edge\Binaries\MirrorsEdge.exe
    00000009    0 <==
0000000e services.exe
    0000001a    0
    00000014    0
    00000010    0
    0000000f    0
00000011 svchost.exe
    00000023    0
    00000022    1
    00000021    0
    00000020    0
    0000001f    0
    0000001e    0
    00000016    0
    00000013    0
    00000012    0
00000017 winedevice.exe
    0000001d    0
    0000001c    0
    00000019    0
    00000018    0
0000002e explorer.exe
    0000002f    0
Backtrace:
=>0 0x68286bbe in libc.so.6 (+0x110bbe) (0x033bd9c0)
  1 0x693815a1 in winhttp (+0x115a0) (0x033bea20)
  2 0x69381aa1 WinHttpQueryDataAvailable+0x60() in winhttp (0x033bea70)
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
brennan@BIO:~$ fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133508, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
```you need the [FONT=monospace][/FONT]d3dx9 and d3dx10 winetricks overrides

---

### Post by xBiocorex on 2010-08-09
Okay, installing d3dx10 and 9 get me very similar errors (maybe?) for either. Well, they don't seem to help anything in terms of running Mirror's Edge, I'm not even going to try Mass Effect or anything else.

According to the Wine website, I should be able to play, the last tester found it only crashes when loading a save file.

The first little bit is me starting winetricks, I had a bit of trouble distinguishing it from the rest of the terminal diarrhea.

```

<name withheld>~$ sh winetricks
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6ddb08 0x6ddb10
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6ddb90
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dda68 0x6dda70
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6ddaf0
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6ddb08 0x6ddb10
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6ddb90
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dd1e0 0x6dd1e8
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6dd268
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dd140 0x6dd148
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6dd1c8
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dd1e0 0x6dd1e8
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6dd268
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xaddc00 0xaddc08
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0xaddc88
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xaddb60 0xaddb68
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0xaddbe8
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xaddc00 0xaddc08
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0xaddc88
fixme:hnetcfg:fw_ports_get__NewEnum 0x133400, 0xbde1cc
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133400, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133400, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x135620, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133328, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133328, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133328, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133328, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133328, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6ddb08 0x6ddb10
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6ddb90
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dda68 0x6dda70
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6ddaf0
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6ddb08 0x6ddb10
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6ddb90
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dd1e0 0x6dd1e8
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6dd268
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dd140 0x6dd148
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6dd1c8
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x6dd1e0 0x6dd1e8
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0x6dd268
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xaddc00 0xaddc08
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0xaddc88
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xaddb60 0xaddb68
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0xaddbe8
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xaddc00 0xaddc08
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:wtsapi:WTSQueryUserToken 0 0xaddc88
fixme:hnetcfg:fw_ports_get__NewEnum 0x132ad0, 0xbde1cc
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132ad0, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/winetrickstmp -L -F *d3dx10*x86* /home/brennan/.winetrickscache/directx_feb2010_redist.exe
Extracting cabinet: /home/brennan/.winetrickscache/directx_feb2010_redist.exe
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/apr2007_d3dx10_33_x86.cab
fixme:hnetcfg:fw_ports_get__NewEnum 0x132e68, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2007_d3dx10_35_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2008_d3dx10_39_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2009_d3dx10_42_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/dec2006_d3dx10_00_x86.cab
fixme:hnetcfg:fw_ports_get__NewEnum 0x132f40, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2007_d3dx10_34_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2008_d3dx10_38_x86.cab
fixme:hnetcfg:fw_ports_get__NewEnum 0x132fd0, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2008_d3dx10_37_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2009_d3dx10_41_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2007_d3dx10_36_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2008_d3dx10_40_x86.cab

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/apr2007_d3dx10_33_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/apr2007_d3dx10_33_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/apr2007_d3dx10_33_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_33.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_33.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2007_d3dx10_35_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2007_d3dx10_35_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2007_d3dx10_35_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_35.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_35.dll
fixme:hnetcfg:fw_ports_get__NewEnum 0x132e98, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2008_d3dx10_39_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2008_d3dx10_39_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2008_d3dx10_39_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_39.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_39.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2009_d3dx10_42_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2009_d3dx10_42_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/aug2009_d3dx10_42_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_42.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/dec2006_d3dx10_00_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/dec2006_d3dx10_00_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/dec2006_d3dx10_00_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2007_d3dx10_34_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2007_d3dx10_34_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2007_d3dx10_34_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_34.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_34.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2008_d3dx10_38_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2008_d3dx10_38_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/jun2008_d3dx10_38_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_38.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_38.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2008_d3dx10_37_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2008_d3dx10_37_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2008_d3dx10_37_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_37.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_37.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2009_d3dx10_41_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2009_d3dx10_41_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/mar2009_d3dx10_41_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_41.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_41.dll

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2007_d3dx10_36_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2007_d3dx10_36_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2007_d3dx10_36_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_36.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_36.dll
fixme:hnetcfg:fw_ports_get__NewEnum 0x132e98, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1

All done, no errors.
Executing /usr/bin/cabextract -d /home/brennan/.wine/dosdevices/c:/windows/system32 -L -F *.dll /home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2008_d3dx10_40_x86.cab
/home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2008_d3dx10_40_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/brennan/.wine/dosdevices/c:/winetrickstmp/nov2008_d3dx10_40_x86.cab
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dx10_40.dll
  extracting /home/brennan/.wine/dosdevices/c:/windows/system32/d3dcompiler_40.dll

All done, no errors.
Using native override for following DLLs: d3dx10_33 d3dx10_34 d3dx10_35 d3dx10_36 d3dx10_37
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*d3dx10_33"="native"
"*d3dx10_34"="native"
"*d3dx10_35"="native"
"*d3dx10_36"="native"
"*d3dx10_37"="native"
Using native override for following DLLs: d3dx10_38 d3dx10_39 d3dx10_40 d3dx10_41 d3dx10_42
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*d3dx10_38"="native"
"*d3dx10_39"="native"
"*d3dx10_40"="native"
"*d3dx10_41"="native"
"*d3dx10_42"="native"
Install of d3dx10 done
winetricks done.
brennan@BIO:~$ fixme:hnetcfg:fw_ports_get__NewEnum 0x132e98, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132e98, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132e98, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132e98, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132fa0, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132fa0, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132b08, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x132b00, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133018, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133018, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133018, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
fixme:hnetcfg:fw_ports_get__NewEnum 0x133018, 0xbde284
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
err:ole:CoGetClassObject class {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} not registered
err:ole:CoGetClassObject no class object {0ca545c6-37ad-4a6c-bf92-9f7610067ef5} could be created for context 0x1
```

---

### Post by dino99 on 2010-08-09
you might use 1.3 now with this ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

you'd post on wine subforum, not here

---

### Post by xBiocorex on 2010-08-09
I don't think upgrading to a potentially unstable beta is what I need here.

---

### Post by sandyd on 2010-08-09
> **xBiocorex said:**
> I don't think upgrading to a potentially unstable beta is what I need here.
its not as unstable as people think...

im running WINE svn/git (wine-9999 from gentoo, which is EXTREME bleeding edge), and mass effect 2 runs okay with those two overrides.

---

### Post by xBiocorex on 2010-08-09
Well, that worked, thanks. It's a wee bit choppy, but not unplayable in the least. Thanks. ^^

---

