---
title: "Hangs on password entry panel during boot"
date: 2009-10-12
forum: General Help
---

### Post by hg21 on 2009-10-12
Hi,

For the last week or so when I boot and get to the login panel the system hangs for a long time.  The mouse cursor will not move and keyboard input of my password does not work for a couple of minutes or so.

Kernel details and extract of syslog below.
From the syslog the following seem to be the likely problems:-

kdm_greet[3168]: Cannot open default user face

console-kit-daemon[2693]: WARNING: Couldn't read /proc/2692/environ: Failed to open file '/proc/2692/environ': No such file or directory.

Any help will be gratefully appreciated.  I'll put this on the KDE forum also.


========================================================================
uname -a
Linux ahg 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

Oct 12 09:43:27 ahg NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 12 09:43:27 ahg kdm_greet[3168]: Cannot open default user face
Oct 12 09:43:25 ahg ntpdate[3239]: step time server 91.189.94.4 offset -3.499459 sec
Oct 12 09:43:25 ahg kernel: [   35.455691] NVRM: Xid (0001:00): 13, 0000 01019700 00001796 00000224 330019d1 00000002
Oct 12 09:43:29 ahg kernel: [   38.980014] eth0: no IPv6 routers present
Oct 12 09:43:43 ahg kernel: [   48.996046] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:43:55 ahg kernel: [   60.996046] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:43:55 ahg kernel: [   65.010992] NVRM: Xid (0001:00): 13, 0000 01019700 00001796 00000108 00000000 00000800
Oct 12 09:44:11 ahg kernel: [   72.996039] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:44:11 ahg kernel: [   81.145633] Clocksource tsc unstable (delta = 4687619986 ns)
Oct 12 09:44:27 ahg kernel: [   89.144041] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:44:43 ahg kernel: [  105.292040] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:44:59 ahg kernel: [  121.440041] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:45:15 ahg kernel: [  137.588041] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:45:31 ahg kernel: [  153.736041] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:45:43 ahg console-kit-daemon[2693]: WARNING: Couldn't read /proc/2692/environ: Failed to open file '/proc/2692/environ': No such file or directory
Oct 12 09:46:12 ahg kernel: [  198.761643] NVRM: Xid (0001:00): 6, PE0000 17fc ff386f96 00001404 00000000 ff386f96
Oct 12 09:46:30 ahg kernel: [  216.764041] NVRM: Xid (0001:00): 8, Channel 00000000
Oct 12 09:46:30 ahg kernel: [  220.857759] NVRM: Xid (0001:00): 13, 0000 01016100 0000008a 00000404 ff518094 00004000
Oct 12 09:46:30 ahg kernel: [  220.885923] NVRM: Xid (0001:00): 13, 0000 01016100 0000008a 00000404 ff3e728a 00004000
Oct 12 09:46:30 ahg kernel: [  220.900459] NVRM: Xid (0001:00): 13, 0000 01016100 0000008a 00000404 ff2c667e 00004000
Oct 12 09:46:30 ahg kernel: [  220.915440] NVRM: Xid (0001:00): 13, 0000 01016100 0000008a 00000404 ff1e5b77 00004000
Oct 12 09:48:17 ahg anacron[3012]: Job `cron.daily' started
Oct 12 09:48:17 ahg anacron[3578]: Updated timestamp for job `cron.daily' to 2009-10-12
Oct 12 09:50:01 ahg /USR/SBIN/CRON[3607]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

---

### Post by hg21 on 2009-10-20
I found this was a more serious problem than I first thought.  I think the Nvidia nvidia driver was updated and messed up the graphics. Switching to the X-org nvidia driver has made the problem go away.

However syslog is still showing the errors:-

kdm_greet[3168]: Cannot open default user face

console-kit-daemon[2693]: WARNING: Couldn't read /proc/2692/environ: Failed to open file '/proc/2692/environ': No such file or directory.

but they don't seem to cause an obvious problem

---

