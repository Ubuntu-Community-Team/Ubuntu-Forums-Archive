---
title: "AOE2 on Wine"
date: 2012-01-01
forum: General Help
---

### Post by layers on 2012-01-01
AOE2 is supposed to be working under wine1.3 (all of them for that matter), but I get this message. What's more interesting, is that I have all the .dll's in the system32 folder...
```
ibo@ibo-vaio:~$ wine '/home/ibo/.wine/drive_c/Program Files/Age of Empires II Gold Expansion/age2_x1.exe' 
err:module:import_dll Library riched20.dll (which is needed by L"C:\\windows\\system32\\riched32.dll") not found
ibo@ibo-vaio:~$ err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x1126f4), expect failure


```

```
ibo@ibo-vaio:~$ ls '/home/ibo/.wine/drive_c/windows/system32' 
acledit.dll         dpnet.dll          msvcirt.dll    spoolss.dll
aclui.dll           dpnhpast.dll       msvcp100.dll   spoolsv.exe
activeds.dll        dpnlobby.dll       msvcp60.dll    stdole2.tlb
actxprxy.dll        dpwsockx.dll       msvcp70.dll    stdole32.tlb
advapi32.dll        drivers            msvcp71.dll    sti.dll
advpack.dll         drmclien.dll       msvcp90.dll    storage.dll
amstream.dll        dsound.dll         msvcr100.dll   stress.dll
apphelp.dll         dsound.vxd         msvcr70.dll    svchost.exe
appwiz.cpl          dssenh.dll         msvcr71.dll    svrapi.dll
atl.dll             dswave.dll         msvcr90.dll    sxs.dll
attrib.exe          dwmapi.dll         msvcrt20.dll   system.drv
authz.dll           dxdiag.exe         msvcrt40.dll   t2embed.dll
avicap32.dll        dxdiagn.dll        msvcrtd.dll    tapi32.dll
avifil32.dll        dxgi.dll           msvcrt.dll     taskkill.exe
avifile.dll         eject.exe          msvfw32.dll    taskmgr.exe
avrt.dll            expand.exe         msvidc32.dll   termsv.exe
bcrypt.dll          explorer.exe       msvideo.dll    toolhelp.dll
browseui.dll        explorerframe.dll  mswsock.dll    traffic.dll
cabarc.exe          extrac32.exe       msxml2.dll     typelib.dll
cabinet.dll         faultrep.dll       msxml3.dll     unicows.dll
cacls.exe           fltlib.dll         msxml4.dll     uninstaller.exe
capi2032.dll        FM20.DLL           msxml6.dll     unlodctr.exe
cards.dll           FM20ENU.DLL        msxml6r.dll    updspapi.dll
cfgmgr32.dll        fwpuclnt.dll       msxml.dll      url.dll
clock.exe           gameux.dll         mui            urlmon.dll
clusapi.dll         gdi32.dll          nddeapi.dll    usbd.sys
cmd.exe             gdi.exe            netapi32.dll   user32.dll
comcat.dll          gdiplus.dll        net.exe        userenv.dll
comctl32.dll        gecko              netfxperf.dll  user.exe
comdlg32.dll        glu32.dll          netsh.exe      usp10.dll
commdlg.dll         gphoto2.ds         newdev.dll     uxtheme.dll
comm.drv            gpkcsp.dll         normaliz.dll   VBAEN32.OLB
compobj.dll         hal.dll            notepad.exe    VBAEND32.OLB
compstui.dll        hhctrl.ocx         ntdll.dll      VBAME.DLL
control.exe         hid.dll            ntdsapi.dll    vbscript.dll
credui.dll          hlink.dll          ntoskrnl.exe   vcomp.dll
crtdll.dll          hnetcfg.dll        ntprint.dll    vdhcp.vxd
crypt32.dll         hostname.exe       objsel.dll     vdmdbg.dll
cryptdlg.dll        httpapi.dll        odbc32.dll     VEN2232.OLB
cryptdll.dll        iccvid.dll         odbccp32.dll   ver.dll
cryptnet.dll        icinfo.exe         ole2conv.dll   version.dll
cryptui.dll         icmp.dll           ole2disp.dll   view.exe
ctapi32.dll         ieframe.dll        ole2.dll       vmm.vxd
ctl3d32.dll         iexplore.exe       ole2nls.dll    vnbt.vxd
ctl3d.dll           ifsmgr.vxd         ole2prox.dll   vnetbios.vxd
ctl3dv2.dll         imaadp32.acm       ole2thk.dll    vtdapi.vxd
d3d10core.dll       imagehlp.dll       ole32.dll      vwin32.vxd
d3d10.dll           imm32.dll          oleacc.dll     w32skrnl.dll
d3d8.dll            imm.dll            oleaut32.dll   w32sys.dll
d3d9.dll            inetcomm.dll       olecli32.dll   wbem
d3dcompiler_33.dll  inetcpl.cpl        olecli.dll     wbemprox.dll
d3dcompiler_34.dll  inetmib1.dll       oledb32.dll    wer.dll
d3dcompiler_35.dll  infosoft.dll       oledlg.dll     wiaservc.dll
d3dcompiler_36.dll  initpki.dll        olepro32.dll   win32s16.dll
d3dcompiler_37.dll  INKED.DLL          olesvr32.dll   win87em.dll
d3dcompiler_38.dll  inkobj.dll         olesvr.dll     winaspi.dll
d3dcompiler_39.dll  inseng.dll         olethk32.dll   windebug.dll
d3dcompiler_40.dll  ipconfig.exe       oleview.exe    windowscodecs.dll
d3dcompiler_41.dll  iphlpapi.dll       openal32.dll   winealsa.drv
d3dcompiler_42.dll  itircl.dll         opengl32.dll   wineboot.exe
d3dcompiler_43.dll  itss.dll           pdh.dll        winebrowser.exe
d3dim.dll           jscript.dll        pidgen.dll     winecfg.exe
d3drm.dll           kernel32.dll       ping.exe       wineconsole.exe
d3dx10_33.dll       keyboard.drv       plugplay.exe   wined3d.dll
d3dx10_34.dll       krnl386.exe        powrprof.dll   winedbg.exe
d3dx10_35.dll       ktmw32.dll         printui.dll    winedevice.exe
d3dx10_36.dll       l_intl.nls         progman.exe    winefile.exe
d3dx10_37.dll       loadperf.dll       propsys.dll    winejoystick.drv
d3dx10_38.dll       localspl.dll       psapi.dll      winemapi.dll
d3dx10_39.dll       localui.dll        pstorec.dll    winemenubuilder.exe
d3dx10_40.dll       lodctr.exe         qcap.dll       winemine.exe
d3dx10_41.dll       lz32.dll           qedit.dll      winemp3.acm
d3dx10_42.dll       lzexpand.dll       qmgr.dll       winemsibuilder.exe
d3dx10_43.dll       mapi32.dll         qmgrprxy.dll   wineoss.drv
d3dx9_24.dll        mapistub.dll       quartz.dll     winepath.exe
d3dx9_25.dll        mciavi32.dll       query.dll      wineps16.drv
d3dx9_26.dll        mcicda.dll         rasapi16.dll   wineps.drv
d3dx9_27.dll        mciqtz32.dll       rasapi32.dll   winevdm.exe
d3dx9_28.dll        mciseq.dll         rasdlg.dll     winex11.drv
d3dx9_29.dll        mciwave.dll        regapi.dll     wing32.dll
d3dx9_30.dll        midimap.dll        reg.exe        wing.dll
d3dx9_31.dll        mlang.dll          regsvr32.exe   winhlp32.exe
d3dx9_32.dll        mmcndmgr.dll       resutils.dll   winhttp.dll
d3dx9_33.dll        mmdevapi.dll       riched20.dll   wininet.dll
d3dx9_34.dll        mmdevldr.vxd       riched32.dll   winmm.dll
d3dx9_35.dll        monodebg.vxd       rpcrt4.dll     winnls32.dll
d3dx9_36.dll        mouse.drv          rpcss.exe      winnls.dll
d3dx9_37.dll        mprapi.dll         rsabase.dll    winoldap.mod
d3dx9_38.dll        mpr.dll            rsaenh.dll     winscard.dll
d3dx9_39.dll        msacm32.dll        rstrtmgr.dll   winsock.dll
d3dx9_40.dll        msacm32.drv        rtutils.dll    winspool.drv
d3dx9_41.dll        msacm.dll          rundll32.exe   winsta.dll
d3dx9_42.dll        msadp32.acm        samlib.dll     wintab32.dll
d3dx9_43.dll        mscat32.dll        sane.ds        wintab.dll
d3dxof.dll          mscms.dll          scarddlg.dll   wintrust.dll
dbgeng.dll          MSCOMCTL.OCX       sccbase.dll    winver.exe
dbghelp.dll         mscoree.dll        sc.exe         WISPTIS.EXE
dciman32.dll        mscorier.dll       schannel.dll   wlanapi.dll
ddhelp.exe          mscories.dll       SCP32.DLL      wldap32.dll
ddraw.dll           msctf.dll          scrrun.dll     wmic.exe
ddrawex.dll         msdaps.dll         secedit.exe    wmi.dll
devenum.dll         msdmo.dll          secur32.dll    wmiutils.dll
dfshim.dll          msftedit.dll       security.dll   wnaspi32.dll
dinput8.dll         msg711.acm         sensapi.dll    wordpad.exe
dinput.dll          msgsm32.acm        serialui.dll   wow32.dll
dispdib.dll         mshta.exe          services.exe   write.exe
dispex.dll          mshtml.dll         setupapi.dll   ws2_32.dll
display.drv         mshtml.tlb         setupx.dll     wscript.exe
dmband.dll          msi.dll            sfc.dll        wshom.ocx
dmcompos.dll        msiexec.exe        sfc_os.dll     wsock32.dll
dmime.dll           msimg32.dll        shdoclc.dll    wtsapi32.dll
dmloader.dll        msimsg.dll         shdocvw.dll    wuapi.dll
dmscript.dll        msimtf.dll         shell32.dll    wuaueng.dll
dmstyle.dll         msisip.dll         shell.dll      xapofx1_1.dll
dmsynth.dll         msisys.ocx         shfolder.dll   xcopy.exe
dmusic32.dll        msnet32.dll        shlwapi.dll    xinput1_1.dll
dmusic.dll          mspatcha.dll       slbcsp.dll     xinput1_2.dll
dnsapi.dll          msrle32.dll        slc.dll        xinput1_3.dll
dosx.exe            mssign32.dll       snmpapi.dll    xinput9_1_0.dll
dplay.dll           mssip32.dll        softpub.dll    xmllite.dll
dplayx.dll          MSSTDFMT.DLL       sound.drv      xolehlp.dll
dpnaddr.dll         mstask.dll         spool
ibo@ibo-vaio:~$ 

```

---

### Post by syerges on 2012-01-01
replace the file with a new one in case it was somehow currupted?

---

### Post by layers on 2012-01-01
> **syerges said:**
> replace the file with a new one in case it was somehow currupted?

tried it, different error now:```
ibo@ibo-vaio:~$ wine '/media/354.8 GB/Age of Empires II Gold Expansion/age2_x1.exe' 
wine: Call from 0x7bc4a950 to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
wine: Unimplemented function riched20.dll.RichEdit10ANSIWndProc called at address 0x7bc4a950 (thread 0009), starting debugger...
Unhandled exception: unimplemented function riched20.dll.RichEdit10ANSIWndProc called in 32-bit code (0x7bc4a950).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4a950 ESP:0032d274 EBP:0032d2d8 EFLAGS:00000202(   - --  I   - - - )
 EAX:7d7e320a EBX:7bca6ff4 ECX:7d7e1530 EDX:00000081
 ESI:0032d280 EDI:00010070
Stack dump:
0x0032d274:  00000010 7e2d8ff4 00000000 80000100
0x0032d284:  00000001 00000000 7bc4a950 00000002
0x0032d294:  7d7e3270 7d7e320a 00000000 0032d654
0x0032d2a4:  0032d2c4 7eacb000 00000004 00000001
0x0032d2b4:  0032d314 7eab5baa 0032d654 0032d654
0x0032d2c4:  0032d3d4 7e29fb5c 00010070 7eafeff4
Backtrace:
=>0 0x7bc4a950 call_dll_entry_point+0x5f0() in ntdll (0x0032d2d8)
  1 0x0034000f (0x0032d314)
  2 0x7ead8bfc in user32 (+0x98bfb) (0x0032d364)
  3 0x7eadb20d in user32 (+0x9b20c) (0x0032d3b4)
  4 0x7ea9acc1 in user32 (+0x5acc0) (0x0032d424)
  5 0x7eaa1876 in user32 (+0x61875) (0x0032d4a4)
  6 0x7eaa1c93 SendMessageA+0x52() in user32 (0x0032d4f4)
  7 0x7eacf822 in user32 (+0x8f821) (0x0032d7e4)
  8 0x7eac8c19 CreateWindowExA+0xf8() in user32 (0x0032da54)
  9 0x7ea6a501 in user32 (+0x2a500) (0x0032dd84)
  10 0x7ea6bbfb DialogBoxParamA+0x8a() in user32 (0x0032ddc4)
  11 0x10001fc3 in ebueulax (+0x1fc2) (0x006703ec)
0x7bc4a950 call_dll_entry_point+0x5f0 in ntdll: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  400000-  7a4000	Deferred        age2_x1
PE	  ce0000-  d33000	Deferred        language_x1
PE	10000000-1000e000	Export          ebueulax
PE	48000000-4804b000	Deferred        riched20
ELF	7b800000-7b9b7000	Deferred        kernel32<elf>
  \-PE	7b810000-7b9b7000	\               kernel32
ELF	7bc00000-7bcc3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d728000-7d7b5000	Deferred        msvcrt<elf>
  \-PE	7d740000-7d7b5000	\               msvcrt
ELF	7d7b5000-7d7d0000	Deferred        crtdll<elf>
  \-PE	7d7c0000-7d7d0000	\               crtdll
ELF	7d7d0000-7d7e4000	Deferred        riched32<elf>
  \-PE	7d7e0000-7d7e4000	\               riched32
ELF	7d7e4000-7d805000	Deferred        localspl<elf>
  \-PE	7d7f0000-7d805000	\               localspl
ELF	7d805000-7d80e000	Deferred        librt.so.1
ELF	7d80e000-7d813000	Deferred        libgpg-error.so.0
ELF	7d813000-7d82a000	Deferred        libresolv.so.2
ELF	7d82a000-7d82e000	Deferred        libkeyutils.so.1
ELF	7d82e000-7d877000	Deferred        libdbus-1.so.3
ELF	7d877000-7d8fc000	Deferred        libgcrypt.so.11
ELF	7d8fc000-7d90e000	Deferred        libtasn1.so.3
ELF	7d90e000-7d917000	Deferred        libkrb5support.so.0
ELF	7d917000-7d940000	Deferred        libk5crypto.so.3
ELF	7d940000-7da09000	Deferred        libkrb5.so.3
ELF	7da09000-7da1c000	Deferred        libavahi-client.so.3
ELF	7da1c000-7da2a000	Deferred        libavahi-common.so.3
ELF	7da2a000-7dada000	Deferred        libgnutls.so.26
ELF	7dada000-7db18000	Deferred        libgssapi_krb5.so.2
ELF	7db18000-7db6a000	Deferred        libcups.so.2
ELF	7db6b000-7db86000	Deferred        spoolss<elf>
  \-PE	7db70000-7db86000	\               spoolss
ELF	7dbb3000-7dbed000	Deferred        winspool<elf>
  \-PE	7dbc0000-7dbed000	\               winspool
ELF	7dbed000-7dc56000	Deferred        shlwapi<elf>
  \-PE	7dc00000-7dc56000	\               shlwapi
ELF	7dc56000-7de6c000	Deferred        shell32<elf>
  \-PE	7dc60000-7de6c000	\               shell32
ELF	7de6c000-7df4e000	Deferred        comdlg32<elf>
  \-PE	7de70000-7df4e000	\               comdlg32
ELF	7df64000-7df98000	Deferred        uxtheme<elf>
  \-PE	7df70000-7df98000	\               uxtheme
ELF	7df98000-7df9e000	Deferred        libxfixes.so.3
ELF	7df9e000-7dfa9000	Deferred        libxcursor.so.1
ELF	7e018000-7e042000	Deferred        libexpat.so.1
ELF	7e042000-7e077000	Deferred        libfontconfig.so.1
ELF	7e077000-7e087000	Deferred        libxi.so.6
ELF	7e087000-7e08b000	Deferred        libxcomposite.so.1
ELF	7e08b000-7e094000	Deferred        libxrandr.so.2
ELF	7e094000-7e09f000	Deferred        libxrender.so.1
ELF	7e09f000-7e0a5000	Deferred        libxxf86vm.so.1
ELF	7e0a5000-7e0a9000	Deferred        libxinerama.so.1
ELF	7e0a9000-7e0b0000	Deferred        libxdmcp.so.6
ELF	7e0b0000-7e0b4000	Deferred        libxau.so.6
ELF	7e0b4000-7e0d3000	Deferred        libxcb.so.1
ELF	7e0d3000-7e0d9000	Deferred        libuuid.so.1
ELF	7e0d9000-7e0f3000	Deferred        libice.so.6
ELF	7e0f3000-7e229000	Deferred        libx11.so.6
ELF	7e229000-7e23c000	Deferred        libxext.so.6
ELF	7e23c000-7e2e1000	Deferred        winex11<elf>
  \-PE	7e250000-7e2e1000	\               winex11
ELF	7e2e1000-7e2f6000	Deferred        libz.so.1
ELF	7e2f6000-7e38d000	Deferred        libfreetype.so.6
ELF	7e38d000-7e3ac000	Deferred        libtinfo.so.5
ELF	7e3ac000-7e3ce000	Deferred        libncurses.so.5
ELF	7e3ce000-7e3d2000	Deferred        libcom_err.so.2
ELF	7e3ea000-7e40c000	Deferred        iphlpapi<elf>
  \-PE	7e3f0000-7e40c000	\               iphlpapi
ELF	7e40c000-7e43e000	Deferred        ws2_32<elf>
  \-PE	7e410000-7e43e000	\               ws2_32
ELF	7e43e000-7e460000	Deferred        imm32<elf>
  \-PE	7e440000-7e460000	\               imm32
ELF	7e460000-7e593000	Deferred        wined3d<elf>
  \-PE	7e470000-7e593000	\               wined3d
ELF	7e593000-7e5f9000	Deferred        ddraw<elf>
  \-PE	7e5a0000-7e5f9000	\               ddraw
ELF	7e5f9000-7e63e000	Deferred        dsound<elf>
  \-PE	7e600000-7e63e000	\               dsound
ELF	7e63e000-7e673000	Deferred        dplayx<elf>
  \-PE	7e640000-7e673000	\               dplayx
ELF	7e673000-7e76a000	Deferred        comctl32<elf>
  \-PE	7e680000-7e76a000	\               comctl32
ELF	7e76a000-7e792000	Deferred        msacm32<elf>
  \-PE	7e770000-7e792000	\               msacm32
ELF	7e792000-7e808000	Deferred        rpcrt4<elf>
  \-PE	7e7a0000-7e808000	\               rpcrt4
ELF	7e808000-7e90e000	Deferred        ole32<elf>
  \-PE	7e820000-7e90e000	\               ole32
ELF	7e90e000-7e96e000	Deferred        advapi32<elf>
  \-PE	7e920000-7e96e000	\               advapi32
ELF	7e96e000-7ea26000	Deferred        gdi32<elf>
  \-PE	7e980000-7ea26000	\               gdi32
ELF	7ea26000-7eb66000	Dwarf           user32<elf>
  \-PE	7ea40000-7eb66000	\               user32
ELF	7eb66000-7ec0b000	Deferred        winmm<elf>
  \-PE	7eb70000-7ec0b000	\               winmm
ELF	7ec0b000-7ec36000	Deferred        msvfw32<elf>
  \-PE	7ec10000-7ec36000	\               msvfw32
ELF	7ec36000-7ec4f000	Deferred        version<elf>
  \-PE	7ec40000-7ec4f000	\               version
ELF	7ef88000-7ef95000	Deferred        libnss_files.so.2
ELF	7ef95000-7efa1000	Deferred        libnss_nis.so.2
ELF	7efa1000-7efba000	Deferred        libnsl.so.1
ELF	7efba000-7efe4000	Deferred        libm.so.6
ELF	7efe5000-7f000000	Deferred        wsock32<elf>
  \-PE	7eff0000-7f000000	\               wsock32
ELF	f74d1000-f74da000	Deferred        libsm.so.6
ELF	f74db000-f74e0000	Deferred        libdl.so.2
ELF	f74e0000-f765a000	Deferred        libc.so.6
ELF	f765b000-f7676000	Deferred        libpthread.so.0
ELF	f7676000-f7680000	Deferred        libnss_compat.so.2
ELF	f7692000-f77d4000	Dwarf           libwine.so.1
ELF	f77d6000-f77f6000	Deferred        ld-linux.so.2
ELF	f77f6000-f77f7000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\354.8 GB\Age of Empires II Gold Expansion\age2_x1.exe
	00000009    0 <==
0000000e services.exe
	0000001e    0
	0000001d    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	0000001f    0
	0000001c    0
	0000001b    0
00000020 explorer.exe
	00000021    0
Backtrace:
=>0 0x7bc4a950 call_dll_entry_point+0x5f0() in ntdll (0x0032d2d8)
  1 0x0034000f (0x0032d314)
  2 0x7ead8bfc in user32 (+0x98bfb) (0x0032d364)
  3 0x7eadb20d in user32 (+0x9b20c) (0x0032d3b4)
  4 0x7ea9acc1 in user32 (+0x5acc0) (0x0032d424)
  5 0x7eaa1876 in user32 (+0x61875) (0x0032d4a4)
  6 0x7eaa1c93 SendMessageA+0x52() in user32 (0x0032d4f4)
  7 0x7eacf822 in user32 (+0x8f821) (0x0032d7e4)
  8 0x7eac8c19 CreateWindowExA+0xf8() in user32 (0x0032da54)
  9 0x7ea6a501 in user32 (+0x2a500) (0x0032dd84)
  10 0x7ea6bbfb DialogBoxParamA+0x8a() in user32 (0x0032ddc4)
  11 0x10001fc3 in ebueulax (+0x1fc2) (0x006703ec)
wine: Call from 0x7bc4a950 to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
ibo@ibo-vaio:~$ 
```

---

### Post by syerges on 2012-01-01
it appears that you have files from both 32 bit software and 64 bit software conflicting with each other... If your system is 32 bit, then I think I would try a whole reinstall, if your system is 64 bit, you copied the wrong file. This is just a guess however.

---

### Post by layers on 2012-01-01
I was looking at that line, too. However, my system is 64-bit. Does that mean that the problem is with WINE, because it is invoking the 32-bit version of the file? Or is the game the 32-bit one? Or the .dll?

---

### Post by syerges on 2012-01-01
32 bit and 64 bit have completely different files so you probably either have the 32 bit version of wine and need to reinstall that to the 64 bit or you have the 32 bit version of the game and need the 64 bit....Maybe...lol

---

### Post by layers on 2012-01-01
> **syerges said:**
> 32 bit and 64 bit have completely different files so you probably either have the 32 bit version of wine and need to reinstall that to the 64 bit or you have the 32 bit version of the game and need the 64 bit....Maybe...lol

lol... since when do games come in 32/64 bit versions?

---

### Post by layers on 2012-01-01
it works under a 32bit host.

---

