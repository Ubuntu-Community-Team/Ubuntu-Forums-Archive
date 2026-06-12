---
title: "server won't hibernate/sleep"
date: 2011-04-03
forum: General Help
---

### Post by jim.hitch on 2011-04-03
Hi

The backend I've set up for mythtv won't hibernate/sleep. This has nothing to do with mythtv itself as I set this up as a server 1st and the problem existed then.

I've knocked about the forums looking for a solution. As built, the system would freeze with the screen on, the only marginal success I've had is given below, but that blanks the monitor, and the server still hums along, so I have to mechanical reboot.

My system is running ubuntu 10.04 server 64bit, RAID1.

As suggested elsewhere I installed the 'hibernate' package, and tried it, but only got the blank screen above. I then tried it using the --dry-run option with the verbose debug mode -v4, here are the results:

```
jim@master-backend:~$ sudo hibernate -v4 --dry-run
hibernate:Warning: Tuxonice binary signature file not found.
hibernate: Trying method in suspend2.conf...
hibernate: Trying method in disk.conf...
hibernate: Trying method in ususpend-disk.conf...
hibernate: Including configuration from common.conf
+ + teedate -a
 -i /var/log/hibernate.log
+ echo Starting suspend at Sun Apr 3 14:15:09 BST 2011
+ EXIT_CODE=0
+ [ tee -a -i /var/log/hibernate.log = cat ]
+ [ -n  ]
+ trap  INT
+ exec
+ exec
+ DoWork
+ trap ctrlc_handler INT HUP
+ local ret
+ local CHAIN_UP_TO+ 
tee -a -i+  /var/log/hibernate.loglocal
 bit
+ CHAIN_UP_TO=0
+ SortSuspendBits
+ /bin/echo -ne 95XHacksSuspendHook2\n11XHacksSuspendHook1\n91ModulesUnloadBlacklist\n99DoUSuspend\n10EnsureUSuspendCapable\n59RemountXFSBootRO\n01NewKernelFileCheck\n89SaveKernelModprobe\n98CheckRunlevel\n01CheckRunlevel\n01CheckLastResume\n01LockFileGet\n
+ sort -n
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("01CheckLastResume", 1, 2)}
+ new_CHAIN_UP_TO=01
+ [ -n 01 ]
+ CHAIN_UP_TO=01
+ bit=CheckLastResume
+ vecho 1 hibernate: [01] Executing CheckLastResume ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [01] Executing CheckLastResume ...
+ [ -nhibernate: [01] Executing CheckLastResume ...
 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("01CheckRunlevel", 1, 2)}
+ new_CHAIN_UP_TO=01
+ [ -n 01 ]
+ CHAIN_UP_TO=01
+ bit=CheckRunlevel
+ vecho 1 hibernate: [01] Executing CheckRunlevel ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [01] Executing CheckRunlevel ...
+ [hibernate: [01] Executing CheckRunlevel ...
 -n 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("01LockFileGet", 1, 2)}
+ new_CHAIN_UP_TO=01
+ [ -n 01 ]
+ CHAIN_UP_TO=01
+ bit=LockFileGet
+ vecho 1 hibernate: [01] Executing LockFileGet ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [01] Executing LockFileGet ...
+ [hibernate: [01] Executing LockFileGet ...
 -n 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("01NewKernelFileCheck", 1, 2)}
+ new_CHAIN_UP_TO=01
+ [ -n 01 ]
+ CHAIN_UP_TO=01
+ bit=NewKernelFileCheck
+ vecho 1 hibernate: [01] Executing NewKernelFileCheck ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [01] Executing NewKernelFileCheck ...
+ [hibernate: [01] Executing NewKernelFileCheck ...
 -n 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("10EnsureUSuspendCapable", 1, 2)}
+ new_CHAIN_UP_TO=10
+ [ -n 10 ]
+ CHAIN_UP_TO=10
+ bit=EnsureUSuspendCapable
+ vecho 1 hibernate: [10] Executing EnsureUSuspendCapable ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [10] Executing EnsureUSuspendCapable ...
+ [ -n 1 ]
+ continue
hibernate: [10] Executing EnsureUSuspendCapable ...
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("11XHacksSuspendHook1", 1, 2)}
+ new_CHAIN_UP_TO=11
+ [ -n 11 ]
+ CHAIN_UP_TO=11
+ bit=XHacksSuspendHook1
+ vecho 1 hibernate: [11] Executing XHacksSuspendHook1 ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [11] Executing XHacksSuspendHook1 ...
+ [ -nhibernate: [11] Executing XHacksSuspendHook1 ...
 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("59RemountXFSBootRO", 1, 2)}
+ new_CHAIN_UP_TO=59
+ [ -n 59 ]
+ CHAIN_UP_TO=59
+ bit=RemountXFSBootRO
+ vecho 1 hibernate: [59] Executing RemountXFSBootRO ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [59] Executing RemountXFSBootRO ...
+ [ -nhibernate: [59] Executing RemountXFSBootRO ...
 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("89SaveKernelModprobe", 1, 2)}
+ new_CHAIN_UP_TO=89
+ [ -n 89 ]
+ CHAIN_UP_TO=89
+ bit=SaveKernelModprobe
+ vecho 1 hibernate: [89] Executing SaveKernelModprobe ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [89] Executing SaveKernelModprobe ...
+ [ -nhibernate: [89] Executing SaveKernelModprobe ...
 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("91ModulesUnloadBlacklist", 1, 2)}
+ new_CHAIN_UP_TO=91
+ [ -n 91 ]
+ CHAIN_UP_TO=91
+ bit=ModulesUnloadBlacklist
+ vecho 1 hibernate: [91] Executing ModulesUnloadBlacklist ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [91] Executing ModulesUnloadBlacklist ...
+ [ -nhibernate: [91] Executing ModulesUnloadBlacklist ...
 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("95XHacksSuspendHook2", 1, 2)}
+ new_CHAIN_UP_TO=95
+ [ -n 95 ]
+ CHAIN_UP_TO=95
+ bit=XHacksSuspendHook2
+ vecho 1 hibernate: [95] Executing XHacksSuspendHook2 ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [95] Executing XHacksSuspendHook2 ...
+ [hibernate: [95] Executing XHacksSuspendHook2 ...
 -n 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("98CheckRunlevel", 1, 2)}
+ new_CHAIN_UP_TO=98
+ [ -n 98 ]
+ CHAIN_UP_TO=98
+ bit=CheckRunlevel
+ vecho 1 hibernate: [98] Executing CheckRunlevel ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [98] Executing CheckRunlevel ...
+ [hibernate: [98] Executing CheckRunlevel ...
 -n 1 ]
+ continue
+ local new_CHAIN_UP_TO
+ awk BEGIN{print substr("99DoUSuspend", 1, 2)}
+ new_CHAIN_UP_TO=99
+ [ -n 99 ]
+ CHAIN_UP_TO=99
+ bit=DoUSuspend
+ vecho 1 hibernate: [99] Executing DoUSuspend ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [99] Executing DoUSuspend ...
+ [hibernate: [99] Executing DoUSuspend ...
 -n 1 ]
+ continue
+ SortResumeBits
+ /bin/echo -ne 85XHacksResumeHook2\n11XHacksResumeHook1\n90ModulesLoad\n70ClockRestore\n59RemountXFSBootRW\n89RestoreKernelModprobe\n01NoteLastResume\n01LockFilePut\n
+ sort -rn
+ awk BEGIN{print substr("90ModulesLoad", 1, 2)}
+ THIS_POS=90
+ [ -z 90 ]
+ bit=ModulesLoad
+ [ 90 -gt 99 ]
+ vecho 1 hibernate: [90] Executing ModulesLoad ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [90] Executing ModulesLoad ...
+ [ -nhibernate: [90] Executing ModulesLoad ...
 1 ]
+ continue
+ awk BEGIN{print substr("89RestoreKernelModprobe", 1, 2)}
+ THIS_POS=89
+ [ -z 89 ]
+ bit=RestoreKernelModprobe
+ [ 89 -gt 99 ]
+ vecho 1 hibernate: [89] Executing RestoreKernelModprobe ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [89] Executing RestoreKernelModprobe ...
+ [ -nhibernate: [89] Executing RestoreKernelModprobe ...
 1 ]
+ continue
+ awk BEGIN{print substr("85XHacksResumeHook2", 1, 2)}
+ THIS_POS=85
+ [ -z 85 ]
+ bit=XHacksResumeHook2
+ [ 85 -gt 99 ]
+ vecho 1 hibernate: [85] Executing XHacksResumeHook2 ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [85] Executing XHacksResumeHook2 ...
+ [hibernate: [85] Executing XHacksResumeHook2 ...
 -n 1 ]
+ continue
+ awk BEGIN{print substr("70ClockRestore", 1, 2)}
+ THIS_POS=70
+ [ -z 70 ]
+ bit=ClockRestore
+ [ 70 -gt 99 ]
+ vecho 1 hibernate: [70] Executing ClockRestore ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [70] Executing ClockRestore ...
+ [ -nhibernate: [70] Executing ClockRestore ...
 1 ]
+ continue
+ awk BEGIN{print substr("59RemountXFSBootRW", 1, 2)}
+ THIS_POS=59
+ [ -z 59 ]
+ bit=RemountXFSBootRW
+ [ 59 -gt 99 ]
+ vecho 1 hibernate: [59] Executing RemountXFSBootRW ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [59] Executing RemountXFSBootRW ...
hibernate: [59] Executing RemountXFSBootRW ...
+ [ -n 1 ]
+ continue
+ awk BEGIN{print substr("11XHacksResumeHook1", 1, 2)}
+ THIS_POS=11
+ [ -z 11 ]
+ bit=XHacksResumeHook1
+ [ 11 -gt 99 ]
+ vecho 1 hibernate: [11] Executing XHacksResumeHook1 ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [11] Executing XHacksResumeHook1 ...
+ [ -n 1 ]
+ continue
hibernate: [11] Executing XHacksResumeHook1 ...
+ awk BEGIN{print substr("01NoteLastResume", 1, 2)}
+ THIS_POS=01
+ [ -z 01 ]
+ bit=NoteLastResume
+ [ 01 -gt 99 ]
+ vecho 1 hibernate: [01] Executing NoteLastResume ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [01] Executing NoteLastResume ...
+ [ -n 1 ]
+ continue
hibernate: [01] Executing NoteLastResume ...
+ awk BEGIN{print substr("01LockFilePut", 1, 2)}
+ THIS_POS=01
+ [ -z 01 ]
+ bit=LockFilePut
+ [ 01 -gt 99 ]
+ vecho 1 hibernate: [01] Executing LockFilePut ... 
+ local v
+ v=1
+ shift
+ [ x = x1 ]
+ [ 1 -le 4 ]
+ echo hibernate: [01] Executing LockFilePut ...
+ [ -n 1 ]
+ continue
+ return 0
hibernate: [01] Executing LockFilePut ...
+ echo EXIT_CODE=0
+ eval EXIT_CODE=0
+ EXIT_CODE=0
+ PluginTermination
+ local i
+ TuxOnIceTermination
+ return 0
+ return 0
+ + tee -adate -i
 /var/log/hibernate.log
+ echo Resumed at Sun Apr 3 14:15:09 BST 2011
+ exit 0
jim@master-backend:~$
```

I have a pretty clean install on 10.04 server. Is it just not set up to sleep, is that the problem?

Does anyone have any suggestions / fixes?

Would be MUCH appreciated.

Jim

---

### Post by jim.hitch on 2011-04-08
I wouldn't say this was solved exactly, but the server now does what I want it to. 

You can check the solution here:

[http://tinyurl.com/5tahhlv]("http://tinyurl.com/5tahhlv")

---

