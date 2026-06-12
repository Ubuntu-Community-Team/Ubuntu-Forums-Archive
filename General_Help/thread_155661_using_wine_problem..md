---
title: "using wine problem."
date: 2006-04-05
forum: General Help
---

### Post by newpants2003 on 2006-04-05
when i running a exe file by wine in terminal it tells me:

root@ubuntu:/home/tian# wine /home/tian/Desktop/KOF/Perfect148XP.exe
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
err:seh:setup_exception stack overflow 0 bytes in thread 0009 eip 7beb8a79 esp 7f9f1000 stack 0x7f9f0000-0x7faf0000

what shuold i do? is there a guide for setting wine for Beginer?
thanx

---

### Post by h3llfyr3 on 2006-04-05
HTH but I'm a bit new to wine myself.

go to winehq.com and read the beginners intro, for a better intro.

Quick try,

#1 run winecfg then add your application, set it to be winXP ...it should help

if this does'nt work

#2 copy the .vxd files from a windows box to  the directory where your .exe is on ubuntu.

#3 a 'good thing' is to copy the fonts package from a windows box c:\windows\fonts to /home/usr/.wine/drive_c/WINDOWS/fonts

otherwise it is likely to like poor.

Best h3llfyr3

---

### Post by newpants2003 on 2006-04-05
when install the ie(sp1) it tells me mfc40.dell not installed yet. and i chose to keep going, then it tells me install fail. thats where the falls start.

and also my windows are in E:/ , but looks like the wt defaul to looking in C:/ , then tells me could not find the file it need, then falls.

Wine is finalizing your software installation. This may take a few minutes,
though it never actually does.
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\Program Files\\Common Files\\Microsoft Shared\\MSInfo\\ieinfo5.ocx") not found
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
Registration of c:\windows\system32\StdOle2.Tlb successful.


how to solve the problem?

---

### Post by taipan899 on 2006-04-25
Hi All,

I am having excatly the same problem as "newpants2003". ](*,)  Any help to solve this problem will be appreciated.

Thanks, Taipan899]

---

### Post by taipan899 on 2006-04-25
Newpants,

I went to www.driverskit.com" and downloaded "mfc40.dll" and then copied it into the wine directories (I was not sure which directory to copy it to). that worked. Now I get the following eror.

err:module:load_builtin_dll loaded .so for L"compobj.dll" but got L"ole32.dll" instead - probably 16-bit dll
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP004.TMP\\stdole2.tlb" -> "c:\\windows\\system32\\stdole2.tlb"
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP004.TMP\\olepro32.dll" -> "c:\\windows\\system32\\olepro32.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP004.TMP\\asycfilt.dll" -> "c:\\windows\\system32\\asycfilt.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP004.TMP\\install.exe" -> "c:\\windows\\system32\\dcom98\\oldole\\uninstall.exe"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP004.TMP\\dcom98.inf" -> "c:\\windows\\system32\\dcom98\\oldole\\dcom98.inf"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP004.TMP\\eula98.txt" -> "c:\\windows\\system32\\dcom98\\license.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP004.TMP\\relnt98.txt" -> "c:\\windows\\system32\\dcom98\\relnotes.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP004.TMP\\dcom98.inf" -> "c:\\windows\\inf\\dcom98.inf"
all wineservers endet after 7 seconds...
Failed: 0
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 0
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...

I seem to moving forward but ever so slow.](*,) 

I am now trying to find out to fix this problem!!!!

Regards Taipan899

N.B. "compobj.dll", not at drivers kit.com.

---

