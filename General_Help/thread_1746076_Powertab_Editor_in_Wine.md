---
title: "Powertab Editor in Wine"
date: 2011-05-01
forum: General Help
---

### Post by Lebuin on 2011-05-01
Hi,

I'm trying to install powertab editor under wine in 11.04. The installation went fine in 10.10, so I wasn't expecting any problems. Although, when installing, some error occurs:

```

seppe@FREDDIE:~/Downloads$ wine PowerTabInstaller.exe 
fixme:hnetcfg:fw_manager_GetIDsOfNames 0x134cb0 {00000000-0000-0000-0000-000000000000} 0x83e7e4 1 1033 0x83e828
fixme:urlmon:CoInternetSetFeatureEnabled 8, 0x00000002, 0, stub
fixme:urlmon:CoInternetSetFeatureEnabled 6, 0x00000002, ffffffff, stub
fixme:shdocvw:PersistStreamInit_InitNew (0x137960)
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -701
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -703
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -704
fixme:urlmon:CoInternetCreateSecurityManager pSP not supported
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32fe14:3; TargetFrameName 0x4b5a74:10)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x104e914, overlapped 0x104e918): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x137a10)->((null) 1 0x32d950 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x137a10)->(0x32d920)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x137a10)
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x137a10)->(0x32f22c)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b839552 (thread 0043), starting debugger...              #Right here, a window pops up, saying there was a serious problem, and the installation needs to closed
err:seh:setup_exception_record stack overflow 944 bytes in thread 0043 eip 7bc70ab0 esp 00230f80 stack 0x230000-0x231000-0x330000
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 42 on event 0
Ctrl-C: stopping debuggee
0x68000830 GLIBC_2+0x830 in ld-linux.so.2: int    $0x80
Modules:
Module    Address            Debug info    Name (130 modules)
PE      3c0000-  3cc000    Deferred        xpcom
PE      400000-  4ff000    Export          powertabinstaller
ELF    20000000-20099000    Deferred        winmm<elf>
  \-PE    20010000-20099000    \               winmm
ELF    20099000-200ad000    Deferred        msimg32<elf>
  \-PE    200a0000-200ad000    \               msimg32
ELF    200ad000-200d2000    Deferred        usp10<elf>
  \-PE    200b0000-200d2000    \               usp10
ELF    23ba2000-23bbf000    Deferred        hnetcfg<elf>
  \-PE    23bb0000-23bbf000    \               hnetcfg
ELF    363d0000-36442000    Deferred        jscript<elf>
  \-PE    363e0000-36442000    \               jscript
ELF    3664f000-3666a000    Deferred        wsock32<elf>
  \-PE    36650000-3666a000    \               wsock32
ELF    3cfdb000-3cfef000    Deferred        olepro32<elf>
  \-PE    3cfe0000-3cfef000    \               olepro32
ELF    40006000-40063000    Deferred        shdocvw<elf>
  \-PE    40010000-40063000    \               shdocvw
ELF    40ceb000-40d01000    Deferred        psapi<elf>
  \-PE    40cf0000-40d01000    \               psapi
ELF    44d64000-44d85000    Deferred        iphlpapi<elf>
  \-PE    44d70000-44d85000    \               iphlpapi
ELF    4ccb5000-4ccbb000    Deferred        libnss_dns.so.2
ELF    5b7b4000-5b7d0000    Deferred        libgcc_s.so.1
ELF    5fa18000-5faff000    Deferred        mshtml<elf>
  \-PE    5fa30000-5faff000    \               mshtml
PE    61700000-6178d000    Deferred        mozsqlite3
PE    61e40000-61e4c000    Deferred        mozalloc
PE    622c0000-622cd000    Deferred        plds4
PE    62a80000-62ab1000    Deferred        ssl3
PE    64e00000-64e1a000    Deferred        nssutil3
PE    64f40000-64f7d000    Deferred        nspr4
ELF    65ec3000-65ec7000    Deferred        libnss_mdns4_minimal.so.2
ELF    68000000-6801e000    Dwarf           ld-linux.so.2
ELF    6801e000-6815f000    Dwarf           libwine.so.1
ELF    6815f000-68178000    Dwarf           libpthread.so.0
ELF    68178000-682d9000    Dwarf           libc.so.6
ELF    682d9000-682dd000    Deferred        libdl.so.2
ELF    682dd000-68303000    Deferred        libm.so.6
ELF    68303000-6830b000    Deferred        libnss_compat.so.2
ELF    6830b000-68322000    Deferred        libnsl.so.1
ELF    68322000-6832e000    Deferred        libnss_files.so.2
ELF    6832e000-6838a000    Deferred        advapi32<elf>
  \-PE    68340000-6838a000    \               advapi32
ELF    6838a000-6847e000    Deferred        comctl32<elf>
  \-PE    68390000-6847e000    \               comctl32
ELF    6847e000-685b2000    Deferred        user32<elf>
  \-PE    68490000-685b2000    \               user32
ELF    685b2000-685cb000    Deferred        version<elf>
  \-PE    685c0000-685cb000    \               version
ELF    685cb000-687c8000    Deferred        shell32<elf>
  \-PE    685e0000-687c8000    \               shell32
ELF    687c8000-6882c000    Deferred        shlwapi<elf>
  \-PE    687e0000-6882c000    \               shlwapi
ELF    6882c000-68864000    Deferred        winspool<elf>
  \-PE    68830000-68864000    \               winspool
ELF    68864000-68968000    Deferred        ole32<elf>
  \-PE    68880000-68968000    \               ole32
ELF    68968000-689db000    Deferred        rpcrt4<elf>
  \-PE    68970000-689db000    \               rpcrt4
ELF    689db000-68ac8000    Deferred        oleaut32<elf>
  \-PE    689f0000-68ac8000    \               oleaut32
ELF    68ac8000-68b38000    Deferred        urlmon<elf>
  \-PE    68ad0000-68b38000    \               urlmon
ELF    68b38000-68b4d000    Deferred        libz.so.1
ELF    68b4d000-68b71000    Deferred        mpr<elf>
  \-PE    68b50000-68b71000    \               mpr
ELF    68b71000-68ba9000    Deferred        libncurses.so.5
ELF    68ba9000-68c2f000    Deferred        libfreetype.so.6
ELF    68c2f000-68c59000    Deferred        libexpat.so.1
ELF    68c59000-68d02000    Deferred        winex11<elf>
  \-PE    68c70000-68d02000    \               winex11
ELF    68d02000-68d0a000    Deferred        libsm.so.6
ELF    68d0a000-68d22000    Deferred        libice.so.6
ELF    68d22000-68d31000    Deferred        libxext.so.6
ELF    68d31000-68e4c000    Deferred        libx11.so.6
ELF    68e4c000-68e51000    Deferred        libuuid.so.1
ELF    68e51000-68e6a000    Deferred        libxcb.so.1
ELF    68e6a000-68e6e000    Deferred        libxau.so.6
ELF    68e6e000-68e74000    Deferred        libxdmcp.so.6
ELF    68e74000-68e95000    Deferred        imm32<elf>
  \-PE    68e80000-68e95000    \               imm32
ELF    68e95000-68e99000    Deferred        libxinerama.so.1
ELF    68e99000-68e9f000    Deferred        libxxf86vm.so.1
ELF    68e9f000-68ea9000    Deferred        libxrender.so.1
ELF    68ea9000-68eb1000    Deferred        libxrandr.so.2
ELF    68eb1000-68eb5000    Deferred        libxcomposite.so.1
ELF    68eb5000-68ebf000    Deferred        libxcursor.so.1
ELF    68ebf000-68ec5000    Deferred        libxfixes.so.3
ELF    68ec5000-68ef9000    Deferred        uxtheme<elf>
  \-PE    68ed0000-68ef9000    \               uxtheme
ELF    68ef9000-68f43000    Deferred        libcups.so.2
ELF    68f43000-68f73000    Deferred        libgssapi_krb5.so.2
ELF    68f73000-69021000    Deferred        libkrb5.so.3
ELF    69021000-69045000    Deferred        libk5crypto.so.3
ELF    69045000-69049000    Deferred        libcom_err.so.2
ELF    69049000-690df000    Deferred        libgnutls.so.26
ELF    690df000-69153000    Deferred        libgcrypt.so.11
ELF    69153000-6915f000    Deferred        libavahi-common.so.3
ELF    6915f000-6916f000    Deferred        libavahi-client.so.3
ELF    6916f000-69177000    Deferred        libkrb5support.so.0
ELF    69177000-6917b000    Deferred        libkeyutils.so.1
ELF    6917b000-69190000    Deferred        libresolv.so.2
ELF    69190000-691a1000    Deferred        libtasn1.so.3
ELF    691a1000-691a6000    Deferred        libgpg-error.so.0
ELF    691a6000-691af000    Deferred        librt.so.1
PE    69c40000-6b45d000    Deferred        xul
ELF    6bbe5000-6bc15000    Deferred        ws2_32<elf>
  \-PE    6bbf0000-6bc15000    \               ws2_32
ELF    6caa2000-6cab7000    Deferred        t2embed<elf>
  \-PE    6cab0000-6cab7000    \               t2embed
PE    6ce40000-6ce4d000    Deferred        plc4
ELF    6d7d2000-6d80f000    Deferred        libdbus-1.so.3
PE    6e840000-6e865000    Deferred        smime3
ELF    6f2ae000-6f315000    Deferred        wininet<elf>
  \-PE    6f2c0000-6f315000    \               wininet
ELF    6f424000-6f4b2000    Deferred        gdi32<elf>
  \-PE    6f430000-6f4b2000    \               gdi32
PE    70200000-702e9000    Deferred        nss3
ELF    72a2c000-72b0f000    Deferred        comdlg32<elf>
  \-PE    72a30000-72b0f000    \               comdlg32
ELF    751df000-751ea000    Deferred        libnss_nis.so.2
ELF    76311000-7639e000    Deferred        msvcrt<elf>
  \-PE    76320000-7639e000    \               msvcrt
ELF    7b435000-7b464000    Deferred        libfontconfig.so.1
ELF    7b800000-7b990000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b990000    \               kernel32
ELF    7bc00000-7bcbb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcbb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000c services.exe
    00000024    0
    00000025    0
    00000029    0
    0000000e    0
    0000000d    0
00000026 winedevice.exe
    0000002a    0
    00000028    0
    00000027    0
00000042 (D) Z:\home\seppe\Downloads\PowerTabInstaller.exe
    00000031    0
    0000000b    0
    00000010    0
    00000020    0
    0000001f    0
    0000001e    0
    00000018    0
    00000017   -1
    00000021    0
    00000023    0
    00000011    0
    00000046    0 <==
00000044 explorer.exe
    00000045    0
Backtrace:
=>0 0x68000830 GLIBC_2+0x830() in ld-linux.so.2 (0x0073e568)
  1 0x7bc78a13 NTDLL_wait_for_multiple_objects+0x232() in ntdll (0x0073e788)
  2 0x7bc78b39 NtWaitForMultipleObjects+0x68() in ntdll (0x0073e7c8)
  3 0x7bc78b8c NtWaitForSingleObject+0x3b() in ntdll (0x0073e7f8)
  4 0x7bc3ec37 in ntdll (+0x2ec36) (0x0073e8f8)
  5 0x7bc417d7 NtFsControlFile+0xa6() in ntdll (0x0073e988)
  6 0x7b86c8c1 ConnectNamedPipe+0x90() in kernel32 (0x0073e9e8)
  7 0x004661b5 in powertabinstaller (+0x661b4) (0x0073ea44)
  8 0x00463a8d in powertabinstaller (+0x63a8c) (0x0073ea68)
  9 0x7bc71bf8 call_thread_func+0xb() in ntdll (0x0073ea78)
  10 0x7bc746d0 call_thread_entry_point+0x6f() in ntdll (0x0073eb48)
  11 0x7bc7a578 in ntdll (+0x6a577) (0x0073f398)
  12 0x68164e99 start_thread+0xd8() in libpthread.so.0 (0x0073f498)

```This happens with the most recent ppa-version, and with the version in the Ubuntu repositories too. Any ideas on how to fix this? I would really like to be able to use this application again.

---

### Post by burpootus on 2011-05-01
> **Lebuin said:**
> Hi,

I'm trying to install powertab editor under wine in 11.04. The installation went fine in 10.10, so I wasn't expecting any problems. Although, when installing, some error occurs:

```

seppe@FREDDIE:~/Downloads$ wine PowerTabInstaller.exe 
fixme:hnetcfg:fw_manager_GetIDsOfNames 0x134cb0 {00000000-0000-0000-0000-000000000000} 0x83e7e4 1 1033 0x83e828
fixme:urlmon:CoInternetSetFeatureEnabled 8, 0x00000002, 0, stub
fixme:urlmon:CoInternetSetFeatureEnabled 6, 0x00000002, ffffffff, stub
fixme:shdocvw:PersistStreamInit_InitNew (0x137960)
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -701
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -703
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -704
fixme:urlmon:CoInternetCreateSecurityManager pSP not supported
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32fe14:3; TargetFrameName 0x4b5a74:10)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x104e914, overlapped 0x104e918): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x137a10)->((null) 1 0x32d950 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x137a10)->(0x32d920)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x137a10)
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x137a10)->(0x32f22c)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b839552 (thread 0043), starting debugger...              #Right here, a window pops up, saying there was a serious problem, and the installation needs to closed
err:seh:setup_exception_record stack overflow 944 bytes in thread 0043 eip 7bc70ab0 esp 00230f80 stack 0x230000-0x231000-0x330000
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 42 on event 0
Ctrl-C: stopping debuggee
0x68000830 GLIBC_2+0x830 in ld-linux.so.2: int    $0x80
Modules:
Module    Address            Debug info    Name (130 modules)
PE      3c0000-  3cc000    Deferred        xpcom
PE      400000-  4ff000    Export          powertabinstaller
ELF    20000000-20099000    Deferred        winmm<elf>
  \-PE    20010000-20099000    \               winmm
ELF    20099000-200ad000    Deferred        msimg32<elf>
  \-PE    200a0000-200ad000    \               msimg32
ELF    200ad000-200d2000    Deferred        usp10<elf>
  \-PE    200b0000-200d2000    \               usp10
ELF    23ba2000-23bbf000    Deferred        hnetcfg<elf>
  \-PE    23bb0000-23bbf000    \               hnetcfg
ELF    363d0000-36442000    Deferred        jscript<elf>
  \-PE    363e0000-36442000    \               jscript
ELF    3664f000-3666a000    Deferred        wsock32<elf>
  \-PE    36650000-3666a000    \               wsock32
ELF    3cfdb000-3cfef000    Deferred        olepro32<elf>
  \-PE    3cfe0000-3cfef000    \               olepro32
ELF    40006000-40063000    Deferred        shdocvw<elf>
  \-PE    40010000-40063000    \               shdocvw
ELF    40ceb000-40d01000    Deferred        psapi<elf>
  \-PE    40cf0000-40d01000    \               psapi
ELF    44d64000-44d85000    Deferred        iphlpapi<elf>
  \-PE    44d70000-44d85000    \               iphlpapi
ELF    4ccb5000-4ccbb000    Deferred        libnss_dns.so.2
ELF    5b7b4000-5b7d0000    Deferred        libgcc_s.so.1
ELF    5fa18000-5faff000    Deferred        mshtml<elf>
  \-PE    5fa30000-5faff000    \               mshtml
PE    61700000-6178d000    Deferred        mozsqlite3
PE    61e40000-61e4c000    Deferred        mozalloc
PE    622c0000-622cd000    Deferred        plds4
PE    62a80000-62ab1000    Deferred        ssl3
PE    64e00000-64e1a000    Deferred        nssutil3
PE    64f40000-64f7d000    Deferred        nspr4
ELF    65ec3000-65ec7000    Deferred        libnss_mdns4_minimal.so.2
ELF    68000000-6801e000    Dwarf           ld-linux.so.2
ELF    6801e000-6815f000    Dwarf           libwine.so.1
ELF    6815f000-68178000    Dwarf           libpthread.so.0
ELF    68178000-682d9000    Dwarf           libc.so.6
ELF    682d9000-682dd000    Deferred        libdl.so.2
ELF    682dd000-68303000    Deferred        libm.so.6
ELF    68303000-6830b000    Deferred        libnss_compat.so.2
ELF    6830b000-68322000    Deferred        libnsl.so.1
ELF    68322000-6832e000    Deferred        libnss_files.so.2
ELF    6832e000-6838a000    Deferred        advapi32<elf>
  \-PE    68340000-6838a000    \               advapi32
ELF    6838a000-6847e000    Deferred        comctl32<elf>
  \-PE    68390000-6847e000    \               comctl32
ELF    6847e000-685b2000    Deferred        user32<elf>
  \-PE    68490000-685b2000    \               user32
ELF    685b2000-685cb000    Deferred        version<elf>
  \-PE    685c0000-685cb000    \               version
ELF    685cb000-687c8000    Deferred        shell32<elf>
  \-PE    685e0000-687c8000    \               shell32
ELF    687c8000-6882c000    Deferred        shlwapi<elf>
  \-PE    687e0000-6882c000    \               shlwapi
ELF    6882c000-68864000    Deferred        winspool<elf>
  \-PE    68830000-68864000    \               winspool
ELF    68864000-68968000    Deferred        ole32<elf>
  \-PE    68880000-68968000    \               ole32
ELF    68968000-689db000    Deferred        rpcrt4<elf>
  \-PE    68970000-689db000    \               rpcrt4
ELF    689db000-68ac8000    Deferred        oleaut32<elf>
  \-PE    689f0000-68ac8000    \               oleaut32
ELF    68ac8000-68b38000    Deferred        urlmon<elf>
  \-PE    68ad0000-68b38000    \               urlmon
ELF    68b38000-68b4d000    Deferred        libz.so.1
ELF    68b4d000-68b71000    Deferred        mpr<elf>
  \-PE    68b50000-68b71000    \               mpr
ELF    68b71000-68ba9000    Deferred        libncurses.so.5
ELF    68ba9000-68c2f000    Deferred        libfreetype.so.6
ELF    68c2f000-68c59000    Deferred        libexpat.so.1
ELF    68c59000-68d02000    Deferred        winex11<elf>
  \-PE    68c70000-68d02000    \               winex11
ELF    68d02000-68d0a000    Deferred        libsm.so.6
ELF    68d0a000-68d22000    Deferred        libice.so.6
ELF    68d22000-68d31000    Deferred        libxext.so.6
ELF    68d31000-68e4c000    Deferred        libx11.so.6
ELF    68e4c000-68e51000    Deferred        libuuid.so.1
ELF    68e51000-68e6a000    Deferred        libxcb.so.1
ELF    68e6a000-68e6e000    Deferred        libxau.so.6
ELF    68e6e000-68e74000    Deferred        libxdmcp.so.6
ELF    68e74000-68e95000    Deferred        imm32<elf>
  \-PE    68e80000-68e95000    \               imm32
ELF    68e95000-68e99000    Deferred        libxinerama.so.1
ELF    68e99000-68e9f000    Deferred        libxxf86vm.so.1
ELF    68e9f000-68ea9000    Deferred        libxrender.so.1
ELF    68ea9000-68eb1000    Deferred        libxrandr.so.2
ELF    68eb1000-68eb5000    Deferred        libxcomposite.so.1
ELF    68eb5000-68ebf000    Deferred        libxcursor.so.1
ELF    68ebf000-68ec5000    Deferred        libxfixes.so.3
ELF    68ec5000-68ef9000    Deferred        uxtheme<elf>
  \-PE    68ed0000-68ef9000    \               uxtheme
ELF    68ef9000-68f43000    Deferred        libcups.so.2
ELF    68f43000-68f73000    Deferred        libgssapi_krb5.so.2
ELF    68f73000-69021000    Deferred        libkrb5.so.3
ELF    69021000-69045000    Deferred        libk5crypto.so.3
ELF    69045000-69049000    Deferred        libcom_err.so.2
ELF    69049000-690df000    Deferred        libgnutls.so.26
ELF    690df000-69153000    Deferred        libgcrypt.so.11
ELF    69153000-6915f000    Deferred        libavahi-common.so.3
ELF    6915f000-6916f000    Deferred        libavahi-client.so.3
ELF    6916f000-69177000    Deferred        libkrb5support.so.0
ELF    69177000-6917b000    Deferred        libkeyutils.so.1
ELF    6917b000-69190000    Deferred        libresolv.so.2
ELF    69190000-691a1000    Deferred        libtasn1.so.3
ELF    691a1000-691a6000    Deferred        libgpg-error.so.0
ELF    691a6000-691af000    Deferred        librt.so.1
PE    69c40000-6b45d000    Deferred        xul
ELF    6bbe5000-6bc15000    Deferred        ws2_32<elf>
  \-PE    6bbf0000-6bc15000    \               ws2_32
ELF    6caa2000-6cab7000    Deferred        t2embed<elf>
  \-PE    6cab0000-6cab7000    \               t2embed
PE    6ce40000-6ce4d000    Deferred        plc4
ELF    6d7d2000-6d80f000    Deferred        libdbus-1.so.3
PE    6e840000-6e865000    Deferred        smime3
ELF    6f2ae000-6f315000    Deferred        wininet<elf>
  \-PE    6f2c0000-6f315000    \               wininet
ELF    6f424000-6f4b2000    Deferred        gdi32<elf>
  \-PE    6f430000-6f4b2000    \               gdi32
PE    70200000-702e9000    Deferred        nss3
ELF    72a2c000-72b0f000    Deferred        comdlg32<elf>
  \-PE    72a30000-72b0f000    \               comdlg32
ELF    751df000-751ea000    Deferred        libnss_nis.so.2
ELF    76311000-7639e000    Deferred        msvcrt<elf>
  \-PE    76320000-7639e000    \               msvcrt
ELF    7b435000-7b464000    Deferred        libfontconfig.so.1
ELF    7b800000-7b990000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b990000    \               kernel32
ELF    7bc00000-7bcbb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcbb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000c services.exe
    00000024    0
    00000025    0
    00000029    0
    0000000e    0
    0000000d    0
00000026 winedevice.exe
    0000002a    0
    00000028    0
    00000027    0
00000042 (D) Z:\home\seppe\Downloads\PowerTabInstaller.exe
    00000031    0
    0000000b    0
    00000010    0
    00000020    0
    0000001f    0
    0000001e    0
    00000018    0
    00000017   -1
    00000021    0
    00000023    0
    00000011    0
    00000046    0 <==
00000044 explorer.exe
    00000045    0
Backtrace:
=>0 0x68000830 GLIBC_2+0x830() in ld-linux.so.2 (0x0073e568)
  1 0x7bc78a13 NTDLL_wait_for_multiple_objects+0x232() in ntdll (0x0073e788)
  2 0x7bc78b39 NtWaitForMultipleObjects+0x68() in ntdll (0x0073e7c8)
  3 0x7bc78b8c NtWaitForSingleObject+0x3b() in ntdll (0x0073e7f8)
  4 0x7bc3ec37 in ntdll (+0x2ec36) (0x0073e8f8)
  5 0x7bc417d7 NtFsControlFile+0xa6() in ntdll (0x0073e988)
  6 0x7b86c8c1 ConnectNamedPipe+0x90() in kernel32 (0x0073e9e8)
  7 0x004661b5 in powertabinstaller (+0x661b4) (0x0073ea44)
  8 0x00463a8d in powertabinstaller (+0x63a8c) (0x0073ea68)
  9 0x7bc71bf8 call_thread_func+0xb() in ntdll (0x0073ea78)
  10 0x7bc746d0 call_thread_entry_point+0x6f() in ntdll (0x0073eb48)
  11 0x7bc7a578 in ntdll (+0x6a577) (0x0073f398)
  12 0x68164e99 start_thread+0xd8() in libpthread.so.0 (0x0073f498)

```This happens with the most recent ppa-version, and with the version in the Ubuntu repositories too. Any ideas on how to fix this? I would really like to be able to use this application again.

I also have many powertabs. I found a much better (for me at least) solution, I installed tuxguitar. An added bonus is that it reads guitar pro tabs as well.

---

### Post by Lebuin on 2011-05-01
I've been using it today, porting some tabs. What bothers me, is that it lacks some (in my eyes) basic functionality, i.e. coda and dal segno, double bars. Also, it doesn't import changes in time signatures from .ptb files. And I think it's a pity that it doesn't seem to be developped anymore. Or am I wrong here? The last release is a year and a half old.

Anyway, I was just hoping that this problem wouldn't be too difficult to solve. But using tuxguitar is my second choice.

---

