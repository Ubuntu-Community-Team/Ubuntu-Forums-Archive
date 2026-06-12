---
title: "I screw ubuntu and wine somehow :|"
date: 2010-06-13
forum: General Help
---

### Post by vampiremind on 2010-06-13
Hi dudes :) 
Well I kind messed up something.
Some of my ubuntu games just doesn't start anymore.
And my wine start giving me errors like this one:

```
silver@Silver:~/starcraft$ wine StarCraft.exe 
fixme:advapi:SetSecurityInfo stub
wine: Unhandled page fault on read access to 0x00000004 at address 0x201f3ef6 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x201f3ef6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:201f3ef6 ESP:0032cc98 EBP:7c9a1a30 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00000041 EBX:7c9db0a8 ECX:7c9a7620 EDX:20240d60
 ESI:00000000 EDI:00000001
Stack dump:
0x0032cc98:  681de9ae 681e0ecd 00000000 00000000
0x0032cca8:  0000000d 00000078 0032ccd0 0000000d
0x0032ccb8:  00000064 00000001 7c9a1a30 00002000
0x0032ccc8:  7c9db05c 201f15d0 7c9a1a30 0032cd14
0x0032ccd8:  0032cd18 682c83c0 682a3ccd 682c83f0
0x0032cce8:  682c6ff4 682c83c0 0032ed40 bff729fc
Backtrace:
=>0 0x201f3ef6 XF86DRIQueryExtension+0x8e() in libgl.so.1 (0x7c9a1a30)
0x201f3ef6 XF86DRIQueryExtension+0x8e in libgl.so.1: movzbl	0x4(%esi),%edx
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  400000-  6ec000	Deferred        starcraft
PE	 2000000- 2011000	Deferred        local
PE	15000000-15069000	Deferred        storm
ELF	20000000-20058000	Deferred        ddraw<elf>
  \-PE	20010000-20058000	\               ddraw
ELF	20058000-2018e000	Deferred        wined3d<elf>
  \-PE	20060000-2018e000	\               wined3d
ELF	2018e000-20244000	Export          libgl.so.1
ELF	2d197000-2d19f000	Deferred        libatiuki.so.1
ELF	3f138000-3f157000	Deferred        libgcc_s.so.1
ELF	68000000-6801d000	Deferred        ld-linux.so.2
ELF	6801d000-68158000	Deferred        libwine.so.1
ELF	68158000-68171000	Deferred        libpthread.so.0
ELF	68171000-682cb000	Deferred        libc.so.6
ELF	682cb000-682f1000	Deferred        libm.so.6
ELF	682f1000-682f9000	Deferred        libnss_compat.so.2
ELF	682f9000-68310000	Deferred        libnsl.so.1
ELF	68310000-6831a000	Deferred        libnss_nis.so.2
ELF	6831a000-68326000	Deferred        libnss_files.so.2
ELF	68326000-683b0000	Deferred        gdi32<elf>
  \-PE	68330000-683b0000	\               gdi32
ELF	683b0000-683d1000	Deferred        imm32<elf>
  \-PE	683c0000-683d1000	\               imm32
ELF	683d1000-683ea000	Deferred        version<elf>
  \-PE	683e0000-683ea000	\               version
ELF	683ea000-683fe000	Deferred        lz32<elf>
  \-PE	683f0000-683fe000	\               lz32
ELF	683fe000-68592000	Deferred        shell32<elf>
  \-PE	68410000-68592000	\               shell32
ELF	68592000-68602000	Deferred        msvcrt<elf>
  \-PE	685a0000-68602000	\               msvcrt
ELF	68602000-686d0000	Deferred        comctl32<elf>
  \-PE	68610000-686d0000	\               comctl32
ELF	686d0000-68746000	Deferred        libfreetype.so.6
ELF	68746000-6875b000	Deferred        libz.so.1
ELF	6875b000-6878b000	Deferred        libfontconfig.so.1
ELF	6878b000-687b2000	Deferred        libexpat.so.1
ELF	687b2000-68851000	Deferred        winex11<elf>
  \-PE	687c0000-68851000	\               winex11
ELF	68851000-6885a000	Deferred        libsm.so.6
ELF	6885a000-68873000	Deferred        libice.so.6
ELF	68873000-68883000	Deferred        libxext.so.6
ELF	68883000-68888000	Deferred        libuuid.so.1
ELF	68888000-688a2000	Deferred        libxcb.so.1
ELF	688a2000-688a6000	Deferred        libxau.so.6
ELF	688a6000-688ac000	Deferred        libxdmcp.so.6
ELF	688ac000-688b0000	Deferred        libxinerama.so.1
ELF	688b0000-688ba000	Deferred        libxrender.so.1
ELF	688ba000-688c2000	Deferred        libxrandr.so.2
ELF	688c2000-688c6000	Deferred        libxcomposite.so.1
ELF	688c6000-688cc000	Deferred        libxfixes.so.3
ELF	688cc000-688d6000	Deferred        libxcursor.so.1
ELF	688d6000-68909000	Deferred        uxtheme<elf>
  \-PE	688e0000-68909000	\               uxtheme
ELF	68909000-68a05000	Deferred        ole32<elf>
  \-PE	68920000-68a05000	\               ole32
ELF	68a05000-68a4b000	Deferred        libcups.so.2
ELF	68a4b000-68a7a000	Deferred        libgssapi_krb5.so.2
ELF	68a7a000-68b15000	Deferred        libgnutls.so.26
ELF	68b15000-68b21000	Deferred        libavahi-common.so.3
ELF	68b21000-68b32000	Deferred        libavahi-client.so.3
ELF	68b32000-68be3000	Deferred        libkrb5.so.3
ELF	68be3000-68be7000	Deferred        libcom_err.so.2
ELF	68be7000-68bef000	Deferred        libkrb5support.so.0
ELF	68bef000-68bf3000	Deferred        libkeyutils.so.1
ELF	68bf3000-68c07000	Deferred        libresolv.so.2
ELF	68c07000-68c7a000	Deferred        libgcrypt.so.11
ELF	68c7a000-68c83000	Deferred        librt.so.1
ELF	68c83000-68c88000	Deferred        libgpg-error.so.0
ELF	694f3000-694f9000	Deferred        libxxf86vm.so.1
ELF	69b4c000-69bf7000	Deferred        comdlg32<elf>
  \-PE	69b50000-69bf7000	\               comdlg32
ELF	69ded000-69e26000	Deferred        libdbus-1.so.3
ELF	6a0d5000-6a0e6000	Deferred        libtasn1.so.3
ELF	6c456000-6c565000	Deferred        user32<elf>
  \-PE	6c470000-6c565000	\               user32
ELF	6e84b000-6e8a4000	Deferred        advapi32<elf>
  \-PE	6e860000-6e8a4000	\               advapi32
ELF	6f1c9000-6f23a000	Deferred        rpcrt4<elf>
  \-PE	6f1e0000-6f23a000	\               rpcrt4
ELF	6f7e8000-6f80c000	Deferred        libk5crypto.so.3
ELF	703a3000-703d9000	Deferred        winspool<elf>
  \-PE	703b0000-703d9000	\               winspool
PE	70bd0000-70c35000	Deferred        shlwapi
ELF	78614000-78618000	Deferred        libdl.so.2
ELF	7abe6000-7ad03000	Deferred        libx11.so.6
ELF	7b800000-7b93a000	Deferred        kernel32<elf>
  \-PE	7b810000-7b93a000	\               kernel32
ELF	7bc00000-7bcb6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb6000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\silver\starcraft\StarCraft.exe
	00000019    1
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
0000001a explorer.exe
	0000001b    0
Backtrace:
=>0 0x201f3ef6 XF86DRIQueryExtension+0x8e() in libgl.so.1 (0x7c9a1a30)
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  716
  Current serial number in output stream:  718
silver@Silver:~/starcraft$ 

```
I care most for the wine... any ideas :confused:

---

