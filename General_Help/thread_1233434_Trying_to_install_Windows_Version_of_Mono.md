---
title: "Trying to install Windows Version of Mono"
date: 2009-08-06
forum: General Help
---

### Post by CrusaderAD on 2009-08-06
I need to install the windows version of mono to run .net apps. When I try to install it in wine I get these errors:

```
wine: Call from 0x6f144645 to unimplemented function msvcrt.dll.swprintf_s, aborting
wine: Call from 0x6f1ad310 to unimplemented function msvcrt.dll._except_handler4_common, aborting
err:seh:setup_exception_record stack overflow 816 bytes in thread 0009 eip b7e28e20 esp 00231000 stack 0x230000-0x231000-0x330000
```

I download this file from monos website:

mono-2.4.2.3-gtksharp-2.12.9-win32-3.exe

Any ideas on how to get this thing working?

---

### Post by martinbaselier on 2009-08-06
Try a virtual machine or check the wine application database.

---

### Post by CrusaderAD on 2009-08-07
I checked the Wine HQ database. Nothing there for Mono, but thanks for the great resource.

---

### Post by CrusaderAD on 2009-08-12
Bump

---

### Post by CrusaderAD on 2009-09-15
I get the same error when trying to install .net framework 2.0 in wine:

> wine: Call from 0x6f1ad310 to unimplemented function msvcrt.dll._except_handler4_common, aborting


---

### Post by directhex on 2009-09-15
Hm. It's talking about msvcrt.dll (Visual C++ runtime) - have you installed any Windows libraries that that sounds a bit like?

---

### Post by CrusaderAD on 2009-09-15
I haven't installed anything extra. I get errors when trying to install dotnetfx.exe too. I'm not sure if they're related.

[http://ubuntuforums.org/showthread.php?t=1267113]("http://ubuntuforums.org/showthread.php?t=1267113")

---

### Post by CrusaderAD on 2009-09-17
I got .net install within wine. I try to fire up my application and I am getting further. However now I'm getting this in the terminal:

```
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:ole:CoGetContextToken stub
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic.Compatibility"
fixme:win:EnumDisplayDevicesW ((null),0,0x32d758,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d758,0x00000000), stub!
fixme:advapi:CheckTokenMembership (0x1dc 0x1682a8 0x32e1d8) stub!
fixme:imm:ImmDisableIME (-1): stub
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime 2.0 Error Reporting"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00001388,(nil),0x000b,0x00000106,0x3009a1b4,0x7e1885d4): stub
err:eventlog:ReportEventW L"clr20r3"
err:eventlog:ReportEventW L"project1.exe"
err:eventlog:ReportEventW L"1.0.3540.21487"
err:eventlog:ReportEventW L"4aa930f9"
err:eventlog:ReportEventW L"project1"
err:eventlog:ReportEventW L"1.0.3540.21487"
err:eventlog:ReportEventW L"4aa930f9"
err:eventlog:ReportEventW L"14"
err:eventlog:ReportEventW L"ca"
err:eventlog:ReportEventW L"system.invalidoperationexception"
err:eventlog:ReportEventW L"NIL"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet

Unhandled Exception: System.InvalidOperationException: An error occurred creating the form. See Exception.InnerException for details.  The error is: Attempted to read or write protected memory. This is often an indication that other memory is corrupt. ---> System.AccessViolationException: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
   at System.Drawing.SafeNativeMethods.Gdip.GdipCreateFontFromLogfontW(HandleRef hdc, Object lf, IntPtr& font)
   at System.Drawing.Font.FromLogFont(Object lf, IntPtr hdc)
   at System.Drawing.Font.FromHfont(IntPtr hfont)
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.Control.get_FontHeight()
   at System.Windows.Forms.TextBoxBase.get_PreferredHeight()
   at System.Windows.Forms.TextBoxBase.get_DefaultSize()
   at System.Windows.Forms.Control..ctor(Boolean autoInstallSyncContext)
   at System.Windows.Forms.TextBoxBase..ctor()
   at System.Windows.Forms.TextBox..ctor()
   at Project1.frmlogin.InitializeComponent()
   at Project1.frmlogin..ctor()
   --- End of inner exception stack trace ---
   at Project1.My.MyProject.MyForms.Create__Instance__[T](T Instance)
   at Project1.frmlogin.Main()
wine: Unhandled exception 0xe0434f4d at address 0x7b845450 (thread 0009), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:0032f184 EBP:0032f1e8 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:0032f220
 ESI:0032f220 EDI:e0434f4d
Stack dump:
0x0032f184:  0032f220 00000004 0000003c e0434f4d
0x0032f194:  00000001 00000000 7b845450 00000001
0x0032f1a4:  80131509 e0434f4d 0032f220 00392010
0x0032f1b4:  02000036 0032f1cc 79e814da 0032f1d8
0x0032f1c4:  02000036 00000001 0032f248 79e87ff4
0x0032f1d4:  0000012c 003f161c 7b84545a 00135248
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032f1e8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f248)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f30c)
  4 0x02d57890 (0x0032f3c4)
  5 0x02d571e8 (0x0032f3e0)
  6 0x79e88ee4 in mscorwks (+0x18ee4) (0x0032f460)
  7 0x79e88e31 in mscorwks (+0x18e31) (0x0032f598)
  8 0x79e88d19 in mscorwks (+0x18d19) (0x0032f66c)
  9 0x03735fa0 (0x03730500)
  10 0x00200186 (0x09000063)
  11 0x00000000 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (79 modules)
PE	  400000-  42e000	Deferred        project1
PE	59b10000-59b70000	Deferred        microsoft.visualbasic.compatibilC:\windows\assembly\GAC_MSIL\Microsoft.VisualBasic.Compatibility\8.0.0.0__b03f5f7f11d50a3a\Microsoft.VisualBasic.Compatibility.dll
PE	5e380000-5e409000	Deferred        diasymreader
PE	5e410000-5e4b8000	Deferred        microsoft.visualbasic
PE	60000000-60008000	Deferred        accessibility
PE	70d00000-70e91000	Deferred        gdiplus
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Export          mscorwks
PE	7a440000-7a724000	Deferred        system
PE	7ade0000-7ae8e000	Deferred        system.drawing
PE	7afd0000-7b4e6000	Deferred        system.windows.forms
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e08d000-7e0a2000	Deferred        lz32<elf>
  \-PE	7e090000-7e0a2000	\               lz32
ELF	7e1b3000-7e278000	Deferred        comctl32<elf>
  \-PE	7e1c0000-7e278000	\               comctl32
ELF	7e278000-7e38c000	Deferred        shell32<elf>
  \-PE	7e290000-7e38c000	\               shell32
ELF	7e40c000-7e427000	Deferred        version<elf>
  \-PE	7e410000-7e427000	\               version
ELF	7e454000-7e487000	Deferred        uxtheme<elf>
  \-PE	7e460000-7e487000	\               uxtheme
ELF	7e487000-7e49d000	Deferred        libresolv.so.2
ELF	7e4b4000-7e4d3000	Deferred        iphlpapi<elf>
  \-PE	7e4c0000-7e4d3000	\               iphlpapi
ELF	7e4d3000-7e536000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e536000	\               rpcrt4
ELF	7e536000-7e5dc000	Deferred        ole32<elf>
  \-PE	7e540000-7e5dc000	\               ole32
ELF	7e7fe000-7e86a000	Deferred        msvcrt<elf>
  \-PE	7e810000-7e86a000	\               msvcrt
ELF	7e86a000-7e873000	Deferred        libxcursor.so.1
ELF	7e873000-7e878000	Deferred        libxfixes.so.3
ELF	7e878000-7e87c000	Deferred        libxcomposite.so.1
ELF	7e87c000-7e884000	Deferred        libxrandr.so.2
ELF	7e884000-7e88e000	Deferred        libxrender.so.1
ELF	7e88e000-7e891000	Deferred        libxinerama.so.1
ELF	7e891000-7e8b2000	Deferred        imm32<elf>
  \-PE	7e8a0000-7e8b2000	\               imm32
ELF	7e8b2000-7e8b7000	Deferred        libxdmcp.so.6
ELF	7e8b7000-7e8d1000	Deferred        libxcb.so.1
ELF	7e8d1000-7e8d5000	Deferred        libxau.so.6
ELF	7e8d5000-7e8da000	Deferred        libuuid.so.1
ELF	7e8da000-7e9c9000	Deferred        libx11.so.6
ELF	7e9c9000-7e9d9000	Deferred        libxext.so.6
ELF	7e9d9000-7e9df000	Deferred        libxxf86vm.so.1
ELF	7e9df000-7e9f7000	Deferred        libice.so.6
ELF	7e9f7000-7ea00000	Deferred        libsm.so.6
ELF	7ea17000-7eab2000	Deferred        winex11<elf>
  \-PE	7ea30000-7eab2000	\               winex11
ELF	7ead7000-7eafe000	Deferred        libexpat.so.1
ELF	7eafe000-7eb2b000	Deferred        libfontconfig.so.1
ELF	7eb2b000-7eb41000	Deferred        libz.so.1
ELF	7eb41000-7ebb8000	Deferred        libfreetype.so.6
ELF	7ebcf000-7ec6f000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec6f000	\               gdi32
ELF	7ec6f000-7edbb000	Deferred        user32<elf>
  \-PE	7ec90000-7edbb000	\               user32
ELF	7edbb000-7ee16000	Deferred        shlwapi<elf>
  \-PE	7edd0000-7ee16000	\               shlwapi
ELF	7ee16000-7ee69000	Deferred        advapi32<elf>
  \-PE	7ee20000-7ee69000	\               advapi32
ELF	7ef93000-7ef9f000	Deferred        libnss_files.so.2
ELF	7ef9f000-7efaa000	Deferred        libnss_nis.so.2
ELF	7efaa000-7efc3000	Deferred        libnsl.so.1
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	b7d33000-b7d3c000	Deferred        libnss_compat.so.2
ELF	b7d3d000-b7d41000	Deferred        libdl.so.2
ELF	b7d41000-b7ea4000	Deferred        libc.so.6
ELF	b7ea5000-b7ebe000	Deferred        libpthread.so.0
ELF	b7ed5000-b800c000	Deferred        libwine.so.1
ELF	b800e000-b802c000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\dave\Desktop\user\bin\Project1.exe
	0000001b    0
	00000018    2
	00000017    0
	00000009    0 <==
0000000c 
	00000016    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
0000001c 
	0000001e    0
	0000001d    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032f1e8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f248)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f30c)
  4 0x02d57890 (0x0032f3c4)
  5 0x02d571e8 (0x0032f3e0)
  6 0x79e88ee4 in mscorwks (+0x18ee4) (0x0032f460)
  7 0x79e88e31 in mscorwks (+0x18e31) (0x0032f598)
  8 0x79e88d19 in mscorwks (+0x18d19) (0x0032f66c)
  9 0x03735fa0 (0x03730500)
  10 0x00200186 (0x09000063)
  11 0x00000000 (0x00000000)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32eccc,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (79F97075) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
dave@ubuntu:~/Desktop/user/bin$ fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\PCHealth\\ErrorRep\\QSignoff" 1 -2147483644 (nil) (nil) 0x1343c4 (nil)
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x5

```

---

### Post by directhex on 2009-09-17
mmm, doesn't mean anything to me, i don't speak WINE

---

### Post by gtr32 on 2009-09-17
> **raptormanad said:**
> I need to install the windows version of mono to run .net apps.


Are these .NET applications dependent on native Windows calls and do not work with Linux Mono? If so, have you tried installing .NET on Wine instead?

---

### Post by gtr32 on 2009-09-17
Ok, read the last posts as well. It seems this is your own project, true? Is there a reason why you don't make it platform independent?

---

### Post by CrusaderAD on 2009-09-17
> **directhex said:**
> mmm, doesn't mean anything to me, i don't speak WINE

They should call it Whine :lolflag:

I didn't build all of it. I picked up a half way done project and finished it by compiling it in VB 2008 Express Edition.

---

### Post by CrusaderAD on 2009-09-17
> **gtr32 said:**
> Is there a reason why you don't make it platform independent?

It involves reading from and updating a MS SQL database. I have no idea how you would do this with anything other than Visual Basic or similar MS software.

---

### Post by gtr32 on 2009-09-17
You might want to run MoMA and try to fix the incompatibility problems. That way you can run it with Mono with the native Linux package instead of Wine.

[http://www.mono-project.com/MoMA](http://www.mono-project.com/MoMA)

---

### Post by gtr32 on 2009-09-17
> **raptormanad said:**
> It involves reading from and updating a MS SQL database. I have no idea how you would do this with anything other than Visual Basic or similar MS software.

It depends on the implementation. The interface should be standard so switching to MySQL or PostgreSQL should be simple but I think you can still use SQL Server (if that's what the MS server is) from Linux Mono. If you have all the source code, it is worth the effort to do this instead of hacking it to work with Wine.

---

### Post by CrusaderAD on 2009-09-17
> **gtr32 said:**
> You might want to run MoMA and try to fix the incompatibility problems. That way you can run it with Mono with the native Linux package instead of Wine.

[http://www.mono-project.com/MoMA](http://www.mono-project.com/MoMA)

That's pretty cool. Thanks for the info!

---

