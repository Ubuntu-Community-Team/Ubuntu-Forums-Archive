---
title: "wine: Unhandled page fault on read access"
date: 2010-06-21
forum: General Help
---

### Post by darkapec on 2010-06-21
I have recently installed ubuntu on a different computer. I have had multiply instances of wine running fine on multiple desktops. I have had some issues before and I ended up reinstalling ubuntu and it worked fine. I do not want to reinstall ubuntu again if it is avoidable. I have not been able to get any windows programs to run successfully with this installation of wine. 

[B]Wine version:
wine-1.1.42

Errors in terminal 
Application: "Heroes of might and magic III"[/B]

[EMAIL="jake@jake-ubuntu:%7E/.wine"]jake@jake-ubuntu:~/.wine[/EMAIL]/dosdevices/c:/Program Files/Heroes of Might and Magic III Complete$ wine Heroes3.exe
wine: Unhandled page fault on read access to 0x00000004 at address 0x7dfd4ef6 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7dfd4ef6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7dfd4ef6 ESP:0032d130 EBP:7dc98668 EFLAGS:00210216(  R- --  I   -A-P- )
 EAX:00000041 EBX:7dcc5f40 ECX:7dc9e810 EDX:7e021d60
 ESI:00000000 EDI:00000001
Stack dump:
0x0032d130:  b749f9ae b74a1ecd 00000000 00000000
0x0032d140:  0000000d 00000078 0032d168 0000000d
0x0032d150:  00000064 00000001 7dc98668 00002000
0x0032d160:  7dcc5ef4 7dfd25d0 7dc98668 0032d1ac
0x0032d170:  0032d1b0 b75893c0 b7564ccd b75893f0
0x0032d180:  b7587ff4 b75893c0 0032f1d8 7dcc5ed8
Backtrace:
=>0 0x7dfd4ef6 XF86DRIQueryExtension+0x8e() in libgl.so.1 (0x7dc98668)
0x7dfd4ef6 XF86DRIQueryExtension+0x8e in libgl.so.1: movzbl    0x4(%esi),%edx
Modules:
Module    Address            Debug info    Name (83 modules)
PE      330000-  35b000    Deferred        binkw32
PE      360000-  383000    Deferred        ifc20
PE      400000-  6b6000    Deferred        heroes3
PE    10000000-1001b000    Deferred        smackw32
PE    21000000-21058000    Deferred        mss32
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7df6f000-7e025000    Export          libgl.so.1
ELF    7e025000-7e15b000    Deferred        wined3d<elf>
  \-PE    7e030000-7e15b000    \               wined3d
ELF    7e1f3000-7e212000    Deferred        libgcc_s.so.1
ELF    7e212000-7e25a000    Deferred        dsound<elf>
  \-PE    7e220000-7e25a000    \               dsound
ELF    7e25b000-7e263000    Deferred        libatiuki.so.1
ELF    7e2c3000-7e2f6000    Deferred        uxtheme<elf>
  \-PE    7e2d0000-7e2f6000    \               uxtheme
ELF    7e2f6000-7e300000    Deferred        libxcursor.so.1
ELF    7e300000-7e306000    Deferred        libxfixes.so.3
ELF    7e306000-7e30a000    Deferred        libxcomposite.so.1
ELF    7e30a000-7e312000    Deferred        libxrandr.so.2
ELF    7e312000-7e31c000    Deferred        libxrender.so.1
ELF    7e31c000-7e322000    Deferred        libxxf86vm.so.1
ELF    7e322000-7e326000    Deferred        libxinerama.so.1
ELF    7e326000-7e347000    Deferred        imm32<elf>
  \-PE    7e330000-7e347000    \               imm32
ELF    7e347000-7e34d000    Deferred        libxdmcp.so.6
ELF    7e34d000-7e367000    Deferred        libxcb.so.1
ELF    7e367000-7e484000    Deferred        libx11.so.6
ELF    7e484000-7e494000    Deferred        libxext.so.6
ELF    7e494000-7e4ad000    Deferred        libice.so.6
ELF    7e4ad000-7e4b6000    Deferred        libsm.so.6
ELF    7e4c6000-7e565000    Deferred        winex11<elf>
  \-PE    7e4d0000-7e565000    \               winex11
ELF    7e5b1000-7e5d8000    Deferred        libexpat.so.1
ELF    7e5d8000-7e608000    Deferred        libfontconfig.so.1
ELF    7e608000-7e61d000    Deferred        libz.so.1
ELF    7e61d000-7e693000    Deferred        libfreetype.so.6
ELF    7e693000-7e761000    Deferred        comctl32<elf>
  \-PE    7e6a0000-7e761000    \               comctl32
ELF    7e761000-7e7c0000    Deferred        shlwapi<elf>
  \-PE    7e770000-7e7c0000    \               shlwapi
ELF    7e7c0000-7e954000    Deferred        shell32<elf>
  \-PE    7e7d0000-7e954000    \               shell32
ELF    7e954000-7e968000    Deferred        libresolv.so.2
ELF    7e96b000-7e970000    Deferred        libuuid.so.1
ELF    7e978000-7e998000    Deferred        iphlpapi<elf>
  \-PE    7e980000-7e998000    \               iphlpapi
ELF    7e998000-7e9c4000    Deferred        ws2_32<elf>
  \-PE    7e9a0000-7e9c4000    \               ws2_32
ELF    7e9c4000-7e9df000    Deferred        wsock32<elf>
  \-PE    7e9d0000-7e9df000    \               wsock32
ELF    7e9df000-7eadb000    Deferred        ole32<elf>
  \-PE    7ea00000-7eadb000    \               ole32
ELF    7eadb000-7eb33000    Deferred        ddraw<elf>
  \-PE    7eae0000-7eb33000    \               ddraw
ELF    7eb33000-7eba4000    Deferred        rpcrt4<elf>
  \-PE    7eb40000-7eba4000    \               rpcrt4
ELF    7eba4000-7ebfd000    Deferred        advapi32<elf>
  \-PE    7ebb0000-7ebfd000    \               advapi32
ELF    7ebfd000-7ec87000    Deferred        gdi32<elf>
  \-PE    7ec10000-7ec87000    \               gdi32
ELF    7ec87000-7ed96000    Deferred        user32<elf>
  \-PE    7eca0000-7ed96000    \               user32
ELF    7ed96000-7ee1d000    Deferred        winmm<elf>
  \-PE    7eda0000-7ee1d000    \               winmm
ELF    7ee1d000-7ee31000    Deferred        lz32<elf>
  \-PE    7ee20000-7ee31000    \               lz32
ELF    7ee31000-7ee4a000    Deferred        version<elf>
  \-PE    7ee40000-7ee4a000    \               version
ELF    7efa7000-7efb3000    Deferred        libnss_files.so.2
ELF    7efb3000-7efca000    Deferred        libnsl.so.1
ELF    7efca000-7eff0000    Deferred        libm.so.6
ELF    7eff0000-7eff4000    Deferred        libxau.so.6
ELF    7eff6000-7f000000    Deferred        libnss_nis.so.2
ELF    b7425000-b742d000    Deferred        libnss_compat.so.2
ELF    b742e000-b7432000    Deferred        libdl.so.2
ELF    b7432000-b758c000    Deferred        libc.so.6
ELF    b758d000-b75a6000    Deferred        libpthread.so.0
ELF    b75b6000-b76f1000    Deferred        libwine.so.1
ELF    b76f3000-b7710000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Heroes of Might and Magic III Complete\Heroes3.exe
    00000009    0 <==
0000000e services.exe
    00000016    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 explorer.exe
    0000001a    0
Backtrace:
=>0 0x7dfd4ef6 XF86DRIQueryExtension+0x8e() in libgl.so.1 (0x7dc98668)

[B][SIZE=3]I then tried it again with a different game and received the following

Application: "Quake"[/SIZE] 

[/B]jake@jake-ubuntu:~/.wine/dosdevices/c:/Program Files/Quake$ wine winquake.exe -nolan
wine: Unhandled page fault on read access to 0x00000004 at address 0x7e3dcef6 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7e3dcef6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e3dcef6 ESP:0032d038 EBP:7d7a15c0 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000041 EBX:7d7f7d30 ECX:7d7a7768 EDX:7e429d60
 ESI:00000000 EDI:00000001
Stack dump:
0x0032d038:  b74bb9ae b74bdecd 00000000 00000000
0x0032d048:  0000000d 00000078 0032d070 0000000d
0x0032d058:  00000064 00000001 7d7a15c0 00002000
0x0032d068:  7d7f7ce4 7e3da5d0 7d7a15c0 0032d0b4
0x0032d078:  0032d0b8 b75a53c0 b7580ccd b75a53f0
0x0032d088:  b75a3ff4 b75a53c0 0032f0e0 7d7f7cc8
Backtrace:
=>0 0x7e3dcef6 XF86DRIQueryExtension+0x8e() in libgl.so.1 (0x7d7a15c0)
0x7e3dcef6 XF86DRIQueryExtension+0x8e in libgl.so.1: movzbl    0x4(%esi),%edx
Modules:
Module    Address            Debug info    Name (65 modules)
PE      400000-  507000    Deferred        winquake
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e350000-7e36f000    Deferred        libgcc_s.so.1
ELF    7e36f000-7e377000    Deferred        libatiuki.so.1
ELF    7e377000-7e42d000    Export          libgl.so.1
ELF    7e42d000-7e563000    Deferred        wined3d<elf>
  \-PE    7e440000-7e563000    \               wined3d
ELF    7e563000-7e65f000    Deferred        ole32<elf>
  \-PE    7e580000-7e65f000    \               ole32
ELF    7e65f000-7e6b7000    Deferred        ddraw<elf>
  \-PE    7e670000-7e6b7000    \               ddraw
ELF    7e734000-7e73e000    Deferred        libxcursor.so.1
ELF    7e73e000-7e744000    Deferred        libxfixes.so.3
ELF    7e744000-7e748000    Deferred        libxcomposite.so.1
ELF    7e748000-7e750000    Deferred        libxrandr.so.2
ELF    7e750000-7e75a000    Deferred        libxrender.so.1
ELF    7e75a000-7e760000    Deferred        libxxf86vm.so.1
ELF    7e760000-7e764000    Deferred        libxinerama.so.1
ELF    7e764000-7e785000    Deferred        imm32<elf>
  \-PE    7e770000-7e785000    \               imm32
ELF    7e785000-7e78b000    Deferred        libxdmcp.so.6
ELF    7e78b000-7e78f000    Deferred        libxau.so.6
ELF    7e78f000-7e7a9000    Deferred        libxcb.so.1
ELF    7e7a9000-7e8c6000    Deferred        libx11.so.6
ELF    7e8c6000-7e8d6000    Deferred        libxext.so.6
ELF    7e8d6000-7e8ef000    Deferred        libice.so.6
ELF    7e8ef000-7e8f8000    Deferred        libsm.so.6
ELF    7e908000-7e9a7000    Deferred        winex11<elf>
  \-PE    7e920000-7e9a7000    \               winex11
ELF    7e9f3000-7ea1a000    Deferred        libexpat.so.1
ELF    7ea1a000-7ea4a000    Deferred        libfontconfig.so.1
ELF    7ea4a000-7ea5f000    Deferred        libz.so.1
ELF    7ea5f000-7ead5000    Deferred        libfreetype.so.6
ELF    7ead5000-7eae9000    Deferred        libresolv.so.2
ELF    7eaec000-7eaf1000    Deferred        libuuid.so.1
ELF    7eaf9000-7eb19000    Deferred        iphlpapi<elf>
  \-PE    7eb00000-7eb19000    \               iphlpapi
ELF    7eb19000-7eb45000    Deferred        ws2_32<elf>
  \-PE    7eb20000-7eb45000    \               ws2_32
ELF    7eb45000-7eb60000    Deferred        wsock32<elf>
  \-PE    7eb50000-7eb60000    \               wsock32
ELF    7eb60000-7ebd1000    Deferred        rpcrt4<elf>
  \-PE    7eb70000-7ebd1000    \               rpcrt4
ELF    7ebd1000-7ec2a000    Deferred        advapi32<elf>
  \-PE    7ebe0000-7ec2a000    \               advapi32
ELF    7ec2a000-7ecb4000    Deferred        gdi32<elf>
  \-PE    7ec40000-7ecb4000    \               gdi32
ELF    7ecb4000-7edc3000    Deferred        user32<elf>
  \-PE    7ecd0000-7edc3000    \               user32
ELF    7edc3000-7ee4a000    Deferred        winmm<elf>
  \-PE    7edd0000-7ee4a000    \               winmm
ELF    7efa7000-7efb3000    Deferred        libnss_files.so.2
ELF    7efb3000-7efca000    Deferred        libnsl.so.1
ELF    7efca000-7eff0000    Deferred        libm.so.6
ELF    7eff6000-7f000000    Deferred        libnss_nis.so.2
ELF    b7441000-b7449000    Deferred        libnss_compat.so.2
ELF    b744a000-b744e000    Deferred        libdl.so.2
ELF    b744e000-b75a8000    Deferred        libc.so.6
ELF    b75a9000-b75c2000    Deferred        libpthread.so.0
ELF    b75d2000-b770d000    Deferred        libwine.so.1
ELF    b770f000-b772c000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Quake\winquake.exe
    00000009    0 <==
0000000e services.exe
    00000016    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 explorer.exe
    0000001a    0
Backtrace:
=>0 0x7e3dcef6 XF86DRIQueryExtension+0x8e() in libgl.so.1 (0x7d7a15c0)

[B]I usually just do some googling until I find the answer but I figured it was about time for me to join the ubuntu family. 

Thanks in advance for any help
Jake

[/B]

---

### Post by 3Miro on 2010-06-21
Wine is tricky. Almost every windows program requires a special setup or tweak. The best place to get started is winehq forums, that is where you will find most answers, Ubuntuforums is lacking when it comes to wine.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=394](http://appdb.winehq.org/objectManager.php?sClass=application&iId=394)

I have set up and played Civilization IV (+ 2 expansions), Oblivion GOYE, STALKER SoC, Heroes of MM V, Diablo I + II, Starcraft and Zeus, as well as other small games all under Ubuntu with wine. All of those required a tweak or two.

---

### Post by darkapec on 2010-06-21
Yah I have been continuing to look for answers after I posted and I figured I would get sent over there. As it looks like it is more of a wine problem and not a ubuntu problem. 

What version of wine are you using? 
Graphics card?
Motherboard?

I am assuming that hardware might have something to do with this also.
Thanks
Jake

---

### Post by 3Miro on 2010-06-21
I have trouble with ATI graphics and many people are complaining about incompatibilities between ATI and wine. I have used three different NVIDIA cards most notably GF8600GT and GTX260.

I have used mobos with NVIDIA and ATI chipsets and it doesn't seem to make any difference. CPU also doesn't matter (as long as it is fast enough).

I have been using wine heavily since 0.9.something. Compatibility has been improving greatly, every now and then there is a regression bug or two, but overall there has been great progress.

(BTW another option for playing old non 3D games is Virtual Box + an old copy of Windows XP)

---

### Post by Kilz on 2010-06-21
looks like a graphics driver problem since you are getting faults  indicating libgl.so.1. Do you have the proprietary graphics driver installed for your brand and make of video card?

---

### Post by darkapec on 2010-06-21
That may be my problem as I have been with ATI for quiet a while now. I felt that I was getting better performance with them since I was using them on windows for gaming. I think a change to nvidia might make the difference. I was testing 2d games in hopes that they would run no matter what, then I would move on to the 3d games. I am so tired of windows, just wish linux could handle my gaming needs. I ended up doing a install of wine 1.0, and wine is running really really slow right now. I checked the ati control center and it is giving me some errors about the graphics card... nvidia here I come. I was thinking about getting a GTX 285, I am assuming because the 260 works fine the 285 should to?

Thanks again for your response

---

### Post by darkapec on 2010-06-21
> **Kilz said:**
> looks like a graphics driver problem since you are getting faults  indicating libgl.so.1. Do you have the proprietary graphics driver installed for your brand and make of video card?

Thats what I also just noticed when I tried to go to the ATI control panel, yes the restricted driver is installed and says it is activated and currently in use. I pulled my 4870x2 out and I am currently using the onboard graphics but I am getting the same results with wine. The onboard is ATI HD4200.

---

### Post by darkapec on 2010-06-21
ok I seemed to have figured it out. It was a very simple problem. RESTART!, I am now on the newest beta version of wine (don't know if that makes a difference or not). But I restarted and the ATI control panel now works and so do the games. Thanks again for the responses.

---

### Post by 3Miro on 2010-06-21
Heroes III should work. If you have the driver properly installed then the issue is with wine. For a 2D game, you can try to disable the driver to see if it helps (this will revert to the default driver which is OK for 2D things).

I have Heroes III complete and it is giving me some trouble with "heroes 3 is missing files". I guess it did not install properly. Depending on the version of Heroes 3 that you have, you might have to do different things. WineHQ is the place to start.

---

### Post by darkapec on 2010-06-21
You will get that error because of the copy protection on the disk. Install the game on a windows machine then use a no cd hack then copy and paste the entire folder over to your wine program files on your ubuntu machine. Should work fine.

---

