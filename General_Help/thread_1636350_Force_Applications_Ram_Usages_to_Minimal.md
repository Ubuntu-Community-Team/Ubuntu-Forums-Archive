---
title: "Force Applications Ram Usages to Minimal"
date: 2010-12-03
forum: General Help
---

### Post by dboy1612 on 2010-12-03
So I've come across something that I can't seem to solve with the help of my own knowledge or anything from Google. Let me explain; on Windows, I found an AutoIt script that had the ability to reset a program's ram usage without affecting the programs performance. Meaning, instead of for example Skype using 60MBs of Ram, it was reduced to 12MBs. This script would run every 2 seconds, without effecting windows or the programs performance, keeping the CPU at minimal usage, and in all keeping the ram usage of the program to as low as possible.

For anyone curious, this is the script.
```

#include <Misc.au3>
_Singleton("skype-memory-reducer")

Opt("TrayMenuMode", 1)
Opt("TrayOnEventMode", 1)

TrayCreateItem("Quit")
TrayItemSetOnEvent(-1, "Bye")
TraySetState()

Global Const $interval = 2000 ; interval at which the memory is freed, anything below this will almost certainly only slow down your system.

;here you can add any other process,
;but be carefull which process you choose,
;bacause in some cases this will slow down your application or even your PC
Global $list = "skype.exe|skypePM.exe"
Global $processlist = StringSplit($list, "|")

While 1
    For $i = 1 To UBound($processlist) - 1
        $pid = ProcessExists($processlist[$i])
        If $pid Then _ReduceMemory($pid)
    Next
    _ReduceMemory(); also reduce the memory used by the script itself...
    Sleep($interval)
WEnd

Func Bye()
    Exit
EndFunc   ;==>Bye

;I don't remember who was the author of this UDF... (it's not me)
Func _ReduceMemory($i_PID = -1)
    If $i_PID <> -1 Then
        Local $ai_Handle = DllCall("kernel32.dll", 'int', 'OpenProcess', 'int', 0x1f0fff, 'int', False, 'int', $i_PID)
        Local $ai_Return = DllCall("psapi.dll", 'int', 'EmptyWorkingSet', 'long', $ai_Handle[0])
        DllCall('kernel32.dll', 'int', 'CloseHandle', 'int', $ai_Handle[0])
    Else
        Local $ai_Return = DllCall("psapi.dll", 'int', 'EmptyWorkingSet', 'long', -1)
    EndIf

    Return $ai_Return[0]
EndFunc   ;==>_ReduceMemory
```

Now my issue is, I can't find ANYTHING that'll help me do the same effect on Ubuntu. Not even a command line to help get me started. So my question is, is there any program out there that can force ram of an application to a minimal? Not even to repeat it over again, I can easily make something up myself, I just need a little help on the first step. :P

Any help is appreciated. Thanks. :)

---

### Post by satish_j on 2010-12-03
I dont the solution,but i am also looking for something similar FOR XP AND NOT UBUNTU.
My system(Lucid) uses around 320MB of RAM with all the frequently used applications running,which i think is fair enough.
But,XP uses the same amount under Idle condition after boot-up(i.e with no App yet started)
Will definitely look into the XP solution you mentioned though..
thanks..:)

---

### Post by dcstar on 2010-12-03
> **dboy1612 said:**
> So I've come across something that I can't seem to solve with the help of my own knowledge or anything from Google. Let me explain; on Windows, I found an AutoIt script that had the ability to reset a program's ram usage without affecting the programs performance. ............
Now my issue is, I can't find ANYTHING that'll help me do the same effect on Ubuntu. Not even a command line to help get me started. So my question is, is there any program out there that can force ram of an application to a minimal? Not even to repeat it over again, I can easily make something up myself, I just need a little help on the first step. :P

Any help is appreciated. Thanks. :)

Totally pointless, the Ubuntu kernel manages the memory quite well and if you decide that you (somehow) know better than the kernel developers, then do a search for "swappiness" and read the posts.

---

### Post by mcduck on 2010-12-03
Such tools haven't really been any use since Windows 98 (which had some problems freeing RAM after closing programs). For everything else you'll just decrease the performance by removing programs data from RAM. Especially if the program is still running, as it will just have to read the same data again and again back to memory if it needs to use it.

If you need to decrease your RAM usage, decrease the amount of running applications.

@satish_j: Even when idle, you most likely have loads and loads of stuff running on the XP machine. Antivirus, firewall, all kinds of systray applets that don't really do anything suefull, bunc of programs that all run their own updaters in the background etc... Just remove all the unnecessary services and programs that start by default and your RAM usage will go down.

---

