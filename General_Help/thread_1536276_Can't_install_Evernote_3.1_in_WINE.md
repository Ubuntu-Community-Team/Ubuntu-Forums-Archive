---
title: "Can't install Evernote 3.1 in WINE"
date: 2010-07-22
forum: General Help
---

### Post by xjgnsdof on 2010-07-22
I can't install Evernote 3.1 in Linux Mint 9.10 through Wine. Here's what I get when I try to run the installer through the command line:

```
wine Evernote_3.1.0.1225.exe
wine: Unhandled page fault on read access to 0x000000fc at address 0x41ec42 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000fc in 32-bit code (0x0041ec42).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0041ec42 ESP:0032e494 EBP:0032e4a0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:005920c0 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:0032e4c0
Stack dump:
0x0032e494:  0044d590 00001400 005920c0 0032e4b4
0x0032e4a4:  00408245 005920c0 00001400 0032e4c0
0x0032e4b4:  0032e4fc 004080cd 005920c0 00000000
0x0032e4c4:  0044d590 0032f608 00000000 004475c0
0x0032e4d4:  00000044 00447550 00592028 00000081
0x0032e4e4:  0044755c 0012d9d4 00447554 00000002
Backtrace:
=>1 0x0041ec42 in evernote_3.1.0.1225 (+0x1ec42) (0x0032e4a0)
  2 0x00408245 in evernote_3.1.0.1225 (+0x8245) (0x0032e4b4)
  3 0x004080cd in evernote_3.1.0.1225 (+0x80cd) (0x0032e4fc)
  4 0x0040650b in evernote_3.1.0.1225 (+0x650b) (0x0032e5c0)
  5 0x0040c50b in evernote_3.1.0.1225 (+0xc50b) (0x0032fe7c)
  6 0x0043b3e9 in evernote_3.1.0.1225 (+0x3b3e9) (0x0032ff08)
  7 0x7b877f48 in kernel32 (+0x57f48) (0x0032ffe8)
  8 0xb7792b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0041ec42: cmpl	%eax,0xfc(%esi)
Modules:
Module	Address			Debug info	Name (70 modules)
PE	  400000-  476000	Export          evernote_3.1.0.1225
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e2af000-7e2ea000	Deferred        rsaenh<elf>
  \-PE	7e2c0000-7e2ea000	\               rsaenh
ELF	7e35b000-7e3c5000	Deferred        crypt32<elf>
  \-PE	7e370000-7e3c5000	\               crypt32
ELF	7e411000-7e444000	Deferred        uxtheme<elf>
  \-PE	7e420000-7e444000	\               uxtheme
ELF	7e444000-7e44f000	Deferred        libxcursor.so.1
ELF	7e44f000-7e455000	Deferred        libxfixes.so.3
ELF	7e455000-7e459000	Deferred        libxcomposite.so.1
ELF	7e459000-7e462000	Deferred        libxrandr.so.2
ELF	7e462000-7e46c000	Deferred        libxrender.so.1
ELF	7e46c000-7e46f000	Deferred        libxinerama.so.1
ELF	7e46f000-7e490000	Deferred        imm32<elf>
  \-PE	7e480000-7e490000	\               imm32
ELF	7e490000-7e495000	Deferred        libxdmcp.so.6
ELF	7e495000-7e4b3000	Deferred        libxcb.so.1
ELF	7e4b3000-7e4b8000	Deferred        libuuid.so.1
ELF	7e4b8000-7e5e7000	Deferred        libx11.so.6
ELF	7e5e7000-7e5f7000	Deferred        libxext.so.6
ELF	7e5f7000-7e612000	Deferred        libice.so.6
ELF	7e612000-7e61b000	Deferred        libsm.so.6
ELF	7e62b000-7e6c5000	Deferred        winex11<elf>
  \-PE	7e640000-7e6c5000	\               winex11
ELF	7e701000-7e728000	Deferred        libexpat.so.1
ELF	7e728000-7e755000	Deferred        libfontconfig.so.1
ELF	7e755000-7e76b000	Deferred        libz.so.1
ELF	7e76b000-7e7e0000	Deferred        libfreetype.so.6
ELF	7e7e0000-7e886000	Deferred        oleaut32<elf>
  \-PE	7e7f0000-7e886000	\               oleaut32
ELF	7e886000-7e89a000	Deferred        libresolv.so.2
ELF	7e89c000-7e8a2000	Deferred        libxxf86vm.so.1
ELF	7e8aa000-7e8c9000	Deferred        iphlpapi<elf>
  \-PE	7e8b0000-7e8c9000	\               iphlpapi
ELF	7e8c9000-7e92c000	Deferred        rpcrt4<elf>
  \-PE	7e8e0000-7e92c000	\               rpcrt4
ELF	7e92c000-7e9d2000	Deferred        ole32<elf>
  \-PE	7e940000-7e9d2000	\               ole32
ELF	7e9d2000-7ea2d000	Deferred        shlwapi<elf>
  \-PE	7e9e0000-7ea2d000	\               shlwapi
ELF	7ea2d000-7eb41000	Deferred        shell32<elf>
  \-PE	7ea40000-7eb41000	\               shell32
ELF	7eb41000-7eb56000	Deferred        lz32<elf>
  \-PE	7eb50000-7eb56000	\               lz32
ELF	7eb56000-7eb71000	Deferred        version<elf>
  \-PE	7eb60000-7eb71000	\               version
ELF	7eb71000-7ebc3000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebc3000	\               advapi32
ELF	7ebc3000-7ec62000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec62000	\               gdi32
ELF	7ec62000-7edad000	Deferred        user32<elf>
  \-PE	7ec80000-7edad000	\               user32
ELF	7edad000-7ee70000	Deferred        comctl32<elf>
  \-PE	7edc0000-7ee70000	\               comctl32
ELF	7ef9c000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb3000	Deferred        libnss_nis.so.2
ELF	7efb3000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff8000-7f000000	Deferred        libnss_compat.so.2
ELF	b7610000-b7614000	Deferred        libxau.so.6
ELF	b7618000-b761c000	Deferred        libdl.so.2
ELF	b761c000-b7761000	Deferred        libc.so.6
ELF	b7762000-b777b000	Deferred        libpthread.so.0
ELF	b778b000-b78c1000	Export          libwine.so.1
ELF	b78c3000-b78e0000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\emones\Downloads\Evernote_3.1.0.1225.exe
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
=>1 0x0041ec42 in evernote_3.1.0.1225 (+0x1ec42) (0x0032e4a0)
  2 0x00408245 in evernote_3.1.0.1225 (+0x8245) (0x0032e4b4)
  3 0x004080cd in evernote_3.1.0.1225 (+0x80cd) (0x0032e4fc)
  4 0x0040650b in evernote_3.1.0.1225 (+0x650b) (0x0032e5c0)
  5 0x0040c50b in evernote_3.1.0.1225 (+0xc50b) (0x0032fe7c)
  6 0x0043b3e9 in evernote_3.1.0.1225 (+0x3b3e9) (0x0032ff08)
  7 0x7b877f48 in kernel32 (+0x57f48) (0x0032ffe8)
  8 0xb7792b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x41ec42
```

---

