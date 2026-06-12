---
title: "errors reported by WINE"
date: 2009-12-31
forum: General Help
---

### Post by Willye on 2009-12-31
hey Guys, i have ubuntu 9.10 i installed it with wubi, i'm trying to run a windows program with wine and appears this messages:
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x7
err:win:WINPOS_GetWinOffset bad hwndFrom = 0xfffffffd
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
wine: Unhandled page fault on read access to 0x00000058 at address 0x7c3428ed (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000058 in 32-bit code (0x7c3428ed).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7c3428ed ESP:0032b668 EBP:00000000 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000058 EBX:00010028 ECX:00343a70 EDX:00002a2a
 ESI:00000058 EDI:00000058
Stack dump:

thanks for your help, what should i do ?????      :guitar:

---

### Post by Willye on 2009-12-31
it's appearing at the end this messages too:

Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\CallCenter\callcntr.exe
    0000001a    0
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
00000018 
    00000019    0
Backtrace:
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7c3428ed

thanks for your help

---

### Post by Mark Phelps on 2009-12-31
> **Willye said:**
> hey Guys, i have ubuntu 9.10 i installed it with wubi, i'm trying to run a windows program with wine and appears this messages: ... thanks for your help, what should i do ?????      :guitar:

Why on earth would you install Wine when you're already running Ubuntu in wubi? Doesn't make sense.

As to the error, what program are you trying to run? Not every MS WIndows program runs in Wine, only a few do, and some of them, not very well.

You would do better to check the WinHQ application compatibility site to see how well your app rates.

---

### Post by MichealH on 2009-12-31
> **Willye said:**
> hey Guys, i have ubuntu 9.10 i installed it with wubi, i'm trying to run a windows program with wine
thanks for your help, what should i do ?????      :guitar:

Ermmm... I suppose you are NOT trying to run itunes because that doesn't work with wine!

---

### Post by Willye on 2009-12-31
> **Mark Phelps said:**
> Why on earth would you install Wine when you're already running Ubuntu in wubi? Doesn't make sense.

As to the error, what program are you trying to run? Not every MS WIndows program runs in Wine, only a few do, and some of them, not very well.

You would do better to check the WinHQ application compatibility site to see how well your app rates.



I've installed ubuntu 'cause some other windows programs are running well on it, but i have one of them  that was not done for linux, then i would like to run it with the others, if i cannot run it program, then i would have to come agin to windows, 'cause it's a main program,see my friend ?????
:guitar:

---

