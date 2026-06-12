---
title: "Having a problem with MT4 under ~/.wine"
date: 2010-02-09
forum: General Help
---

### Post by Tristan Tonks on 2010-02-09
Hi guys,
I have been coming back to this problem for a while now. I have finally weaned myself of windows with great programs like incscape, gFTP, Open Office etc and a few months ago I deleted Vista from my Partition and reinstalled a clean Ubuntu Distro (Karmic). However the one thing I have not been able to get running is MT4 trader.
There is an excellent post here [forex factory]("http://www.forexfactory.com/showthread.php?t=194856"). However having reinstalled 'wine' and double checked it against other emulation operations and reinstalled MT4 it still just crashes. I am now at the point where I get a crash report which is a step in the right direction but not a solution as yet.
Any help would be very much appreciated. I will post further

---

### Post by Tristan Tonks on 2010-02-09
There has been a critical error
Time        : 2010.02.09 22:48
Program     : Client Terminal
Version     : 4.00 (build: 225, 10 Jul 2009)
OS          : Windows XP Professional 5.1 Service Pack 2 (Build 2600)
Processors  : 2 x X86 (level 6)
Memory      : 1018180/666572 kb
Exception   : 80000100
Address     : 7BC478F0
Access Type : NA
Access Addr : 00000000

Registers   : EAX=000019E1 CS=0073 EIP=7BC478F0 EFLGS=00000202
            : EBX=7BC94FF4 SS=007b ESP=00326750 EBP=003267B4
            : ECX=00A9587C DS=007b ESI=0032675C FS=0033
            : EDX=00000000 ES=007b EDI=00A9587C GS=003b

Stack Trace : 0033011D 00000000 00000000 00000000
            : 00000000 00000000 00000000 00000000
            : 00000000 00000000 00000000 00000000
            : 00000000 00000000 00000000 00000000

Modules     :
          1 : 00400000 002B1000 c:\program files\metatrader - alpari uk\terminal.exe
          2 : 5F400000 000ED000 c:\windows\system32\mfc42.dll
          3 : 68320000 00020000 c:\windows\system32\ws2_32.dll
          4 : 68350000 0008C000 c:\windows\system32\winmm.dll
          5 : 68400000 00127000 c:\windows\system32\user32.dll
          6 : 68540000 00087000 c:\windows\system32\gdi32.dll
          7 : 685D0000 0004E000 c:\windows\system32\advapi32.dll
          8 : 68630000 0017E000 c:\windows\system32\shell32.dll
          9 : 687C0000 0004B000 c:\windows\system32\shlwapi.dll
         10 : 68810000 000C3000 c:\windows\system32\comctl32.dll
         11 : 688F0000 000DE000 c:\windows\system32\ole32.dll
         12 : 689E0000 0005B000 c:\windows\system32\rpcrt4.dll
         13 : 68A50000 000CE000 c:\windows\system32\oleaut32.dll
         14 : 68B20000 00013000 c:\windows\system32\system.drv16
         15 : 68C00000 00093000 c:\windows\system32\winex11.drv
         16 : 68E60000 00024000 c:\windows\system32\winealsa.drv
         17 : 69190000 00010000 c:\windows\system32\msacm32.drv
         18 : 691B0000 00016000 c:\windows\system32\msacm32.dll
         19 : 691D0000 0000C000 c:\windows\system32\midimap.dll
         20 : 691E0000 0002F000 c:\windows\system32\uxtheme.dll
         21 : 6D2C0000 00054000 c:\windows\system32\msvcrt.dll
         22 : 6D650000 00019000 c:\windows\system32\imm32.dll
         23 : 78C80000 00007000 c:\windows\system32\msimg32.dll
         24 : 7B820000 00151000 c:\windows\system32\kernel32.dll
         25 : 7BC10000 000A1000 c:\windows\system32\ntdll.dll

Call stack  :

---

### Post by Tristan Tonks on 2010-02-09
In the list above I have located all but;

1) system.drv16 (unknown)
2) winexll.drv (unknown)
3) winealsa.drv (wine core module??)


It's obviously missing something fundamental but I can't identify what that is.

I got some of the dll's I needed here (hope its ok to post this) seems like a good site but not used it before so use with caution.
[http://www.dlldump.com/]("http://www.dlldump.com/")

---

### Post by Mark Phelps on 2010-02-10
If you're going to use Wine, you really need to familiarize yourself with the CodWeavers App Compatibility database site.

The link below is to the MT page.  If you click on the test results, you'll see lots of support info:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1599]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1599")

---

### Post by Tristan Tonks on 2010-02-13
> **Mark Phelps said:**
> If you're going to use Wine, you really need to familiarize yourself with the CodWeavers App Compatibility database site.

The link below is to the MT page.  If you click on the test results, you'll see lots of support info:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1599]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1599")

Thanks for that I had not found that before and it is good resource.

---

