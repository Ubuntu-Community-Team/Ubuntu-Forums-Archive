---
title: "Odd Behavior when Logging in via ssh."
date: 2010-10-19
forum: General Help
---

### Post by telseth on 2010-10-19
I think this might have to do with me *trying* to use screen when upgrading from 10.04 to 10.10 over ssh.  Anyway, when I log in now it shows me this (edited for location anonymizin'):

Linux server 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

MythTV status for localhost
===========================
Status..........: Wed Oct 13 2010, 3:30 PM
Total Disk Space: Total space is 916.9 GB, with 450.2 GB used (49.1%)

Encoders:
server (1) - Idle
server (2) - Idle
server (3) - Recording

Recording Now:
The Ellen DeGeneres Show (xxxxx-TV) Ends: 16:00:00

Scheduled Recordings:
2010-10-13 17:00:00 - Valley News Live at 5pm (xxxx-TV)
2010-10-13 17:30:00 - NBC Nightly News (xxxx-TV)
2010-10-13 19:00:00 - The Middle (xxxx)
2010-10-13 19:30:00 - Better With You (xxxxx)
2010-10-13 20:00:00 - Modern Family (xxxx)
2010-10-13 20:31:00 - Cougar Town (xxxxx)
2010-10-13 23:37:00 - The Late Late Show With Craig Ferguson (xxxx)
2010-10-14 14:00:00 - How I Met Your Mother (xxxxx-DT)
2010-10-14 15:00:00 - The Ellen DeGeneres Show (xxxxx-TV)
2010-10-14 17:00:00 - Valley News Live at 5pm (xxxxx-TV)

Last login: Mon Oct 18 10:36:39 2010 from blahblahblah.net

-- Now no ellen jokes, it's for my wife.

Anyway, that output is from a program called mythtv-status... which isn't even installed anymore.  And notice the dates, it's no longer the 13th.

I have checked my .bashrc, it is standard issue now.

Any ideas why/how it is showing me the same information as when I first logged in after my upgrade?  It's not a big deal, but it is annoying.

---

