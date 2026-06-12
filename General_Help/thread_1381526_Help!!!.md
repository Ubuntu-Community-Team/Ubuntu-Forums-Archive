---
title: "Help!!!"
date: 2010-01-14
forum: General Help
---

### Post by woodmaster on 2010-01-14
So, I've got my wife convinced on the whole free software thing.  That's good Yay!  Running Ubu 9.10 on a Dell Dimension 2400.  I got seemingly random freezes.  It seems as though it is freezing up coming out of sleep mode.  But it shouldn't be entering sleep because we are doing stuff.  Now that I know about it, I can Ctrl Alt F2 to terminal and reset or run commands from there.  When I check the memory use from there, it says 0% to very minimal usage(P4 2.66- 2Gb DDR SDRA.) I just don't get why it would enter sleep like that while doing stuff?  My messages log reads:
[CODE]Jan 14 14:06:16 Sam-Jenn kernel: [51128.520063] i915: Waking up sleeping processes
Jan 14 14:06:16 Sam-Jenn kernel: [51128.521315] Process 964(Xorg) has RLIMIT_CORE set to 0
Jan 14 14:06:16 Sam-Jenn kernel: [51128.521320] Aborting core
Jan 14 14:06:16 Sam-Jenn kernel: [51128.521874] reboot required
Jan 14 14:06:16 Sam-Jenn kernel: [51128.683545] [drm] DAC-5: set mode 1024x768 13
Jan 14 14:06:16 Sam-Jenn pppd[16963]: Terminating on signal 15
Jan 14 14:06:16 Sam-Jenn pppd[16963]: Connect time 62.4 minutes.
Jan 14 14:06:16 Sam-Jenn pppd[16963]: Sent 6753937 bytes, received 18056437 bytes.
Jan 14 14:06:16 Sam-Jenn pppd[16963]: Connection terminated.
Jan 14 14:06:17 Sam-Jenn pppd[16963]: Exit.
Jan 14 14:07:03 Sam-Jenn kernel: [51175.878928] SysRq : HELP : loglevel(0-9) reBoot Crash terminate-all-tasks(E) memory-full-oom-kill(F) kill-all-tasks(I) thaw-filesystems(J) saK show-backtrace-all-active-cpus(L) show-memory-usage(M) nice-all-RT-tasks(N) powerOff show-registers(P) show-all-timers(Q) unRaw Sync show-task-states(T) Unmount force-fb(V) show-blocked-tasks(W) dump-ftrace-buffer(Z) 
Jan 14 14:07:39 Sam-Jenn kernel: [51211.653197] SysRq : Keyboard mode set to system default
Jan 14 14:07:39 Sam-Jenn kernel: Kernel logging (proc) stopped.
Jan 14 14:07:40 Sam-Jenn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="19968" x-info="http://www.rsyslog.com"] (re)start
Jan 14 14:07:40 Sam-Jenn rsyslogd: rsyslogd's groupid changed to 102
Jan 14 14:07:40 Sam-Jenn rsyslogd: rsyslogd's userid changed to 101
Jan 14 14:07:40 Sam-Jenn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="20006" x-info="http://www.rsyslog.com"] (re)start
Jan 14 14:07:40 Sam-Jenn rsyslogd: rsyslogd's groupid changed to 102
Jan 14 14:07:40 Sam-Jenn rsyslogd: rsyslogd's userid changed to 101
Jan 14 14:08:03 Sam-Jenn kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Jan 14 14:08:03 Sam-Jenn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="677" x-info="http://www.rsyslog.com"] (re)start
Jan 14 14:08:03 Sam-Jenn rsyslogd: rsyslogd's groupid changed to 102
Jan 14 14:08:03 Sam-Jenn rsyslogd: rsyslogd's userid changed to 101
Jan 14 14:08:03 Sam-Jenn kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 14 14:08:03 Sam-Jenn kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 14 14:08:03 Sam-Jenn kernel: [    0.000000] Linux version 2.6.32-020632-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #020632 SMP Thu Dec 3 10:58:45 UTC 2009
/CODE]


any help???

---

### Post by woodmaster on 2010-01-14
also I get an error when I reboot.  I gues this is related to my huge amounts of logfile input.  I'd post all of it here but it is just too much to post.  the error on reboot, just before the login screen is:
Unable to find suitable fs in proc/mounts


What is this?

---

