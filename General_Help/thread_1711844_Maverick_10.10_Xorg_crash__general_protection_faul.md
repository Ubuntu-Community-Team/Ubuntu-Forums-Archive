---
title: "Maverick 10.10 Xorg crash / general protection fault"
date: 2011-03-21
forum: General Help
---

### Post by naudster on 2011-03-21
I have an occasional problem where Xorg will crash causing a blank screen and, after a few seconds, a return to the GDM login screen.

This was happening regularly, on average once a week, but after I switched out some bad RAM I had a good run of no crashes for a couple of months, until today. I only have the logs of today's crash. This is from kern.log, but dmesg, syslog & messages show the same thing:


```

Mar 22 10:16:48 metis kernel: [2838251.998139] NVRM: os_raise_smp_barrier(), invalid context!
Mar 22 10:16:48 metis kernel: [2838251.999265] NVRM: os_raise_smp_barrier(), invalid context!
Mar 22 10:16:49 metis kernel: [2838253.068935] ptrace of non-child pid 25468 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068937] ptrace of non-child pid 25469 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068939] ptrace of non-child pid 27159 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068941] ptrace of non-child pid 27160 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068943] ptrace of non-child pid 27161 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068945] ptrace of non-child pid 27162 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068947] ptrace of non-child pid 27163 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068949] ptrace of non-child pid 27164 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068950] ptrace of non-child pid 27165 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:49 metis kernel: [2838253.068952] ptrace of non-child pid 27166 was attempted by: firefox-bin (pid 5598)
Mar 22 10:16:51 metis kernel: [2838255.057292] do_general_protection: 138 callbacks suppressed
Mar 22 10:16:51 metis kernel: [2838255.057295] workrave[2983] general protection ip:7f4650e95445 sp:7fffbc4799a0 error:0 in libc-2.12.1.so[7f4650e5c000+17a000]
Mar 22 10:16:51 metis kernel: [2838255.660753] VirtualBox[28667]: segfault at 38ac11e0 ip 00007f3dc7cf2445 sp 00007f3da48ee8c0 error 4 in libc-2.12.1.so[7f3dc7cb9000+17a000]
Mar 22 10:16:56 metis kernel: [2838260.523714] NVRM: Xid (0001:00): 13, 0003 00000000 00008597 00000104 00000000 00000140
Mar 22 10:16:58 metis kernel: [2838262.606567] chromium-browse[5983]: segfault at 0 ip 00007f9e367acea8 sp 00007f9e26ac3740 error 6 in chromium-browser[7f9e35d7b000+30c9000]
Mar 22 10:17:05 metis kernel: [2838269.507754] NVRM: os_raise_smp_barrier(), invalid context!
Mar 22 10:17:05 metis kernel: [2838269.523230] NVRM: os_raise_smp_barrier(), invalid context!

```

Xorg.0.log.old shows no entries at the time of the crash.

Details of the environment:

[LIST]
[*]Maverick 10.10 64bit
[*]Linux 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
[*]Firefox 3.6.13
[*]Adobe flash 10,2,161,22 64bit preview, manually installed around Sept 2010. Not the latest "Square" preview.
[*]Nvidia graphics with Ubuntu provided drivers (260.19.06)
[/LIST]

Does anybody have any clues as to what caused the crash? A bit of googling seems to suggest that the "ptrace of non-child pid" attempt by firefox could be caused by the flash plugin, but could it then cause Xorg to crash? The segfaults in workrave, virtualbox and chromium seem to a result of Xorg dying, but I can't be certain.

Is bad RAM or other hardware fault a possible cause?

Thanks for any help.

---

