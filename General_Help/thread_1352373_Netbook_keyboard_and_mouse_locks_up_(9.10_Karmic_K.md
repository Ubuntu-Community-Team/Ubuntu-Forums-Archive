---
title: "Netbook keyboard and mouse locks up (9.10 Karmic Koala Desktop version)"
date: 2009-12-11
forum: General Help
---

### Post by Saigo on 2009-12-11
I am running the desktop version of 9.10 on my Acer Aspire One D250 (1gb of Ram) and am encountering a weird problem.  My keyboard and mouse (touchpad and usb mouse) will lock up whenever the computer goes idle, the screen is blacked out as well but that might just be because the keyboard and mouse do not "wake" the screen.  The only way I am able to start working again is to hard reboot it which is not optimal.  The netbook wakes from sleep and hibernation without any problems and it has me a little confused.  I am still pretty new but I tried to look through the forums and find a problem that was similar to mine but I was not able to.  I did copy the last entry from my syslog file before I had to hard reboot it. If you guys need anymore info just let me know.  Thank you

                                 Dec 11 13:18:24 username*-netbook kernel: [43143.978916] Out of memory: kill process 1472 (gnome-session) score 16181 or a child 
 Dec 11 13:18:24 username*-netbook kernel: [43143.978992] Killed process 1665 (evolution-alarm) 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436408] Xorg invoked oom-killer: gfp_mask=0xd0, order=0, oomkilladj=0 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436420] Xorg cpuset=/ mems_allowed=0 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436429] Pid: 949, comm: Xorg Not tainted 2.6.31-15-generic #50-Ubuntu 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436435] Call Trace: 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436451]  [<c01b5a0f>] oom_kill_process+0x9f/0x250 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436460]  [<c01b601e>] ? select_bad_process+0xbe/0xf0 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436468]  [<c01b60a1>] __out_of_memory+0x51/0xa0 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436476]  [<c01b6143>] out_of_memory+0x53/0xb0 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436484]  [<c01b83fe>] __alloc_pages_slowpath+0x42e/0x480 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436493]  [<c01b855f>] __alloc_pages_nodemask+0x10f/0x120 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436502]  [<c01b85b7>] __get_free_pages+0x17/0x30 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436510]  [<c01f69d9>] __pollwait+0x99/0xd0 
 Dec 11 13:18:24 username*-netbook kernel: [43144.436519]  [<c050ca27>] unix_poll+0x17/0xa0

---

