---
title: "Anacron job 'cron.daily' error - what does this mean?"
date: 2011-06-03
forum: General Help
---

### Post by creativelies on 2011-06-03
I received this email thismorning - what do I need to look into? Mdadm appears to be running fine as far as I can tell, no arrays are degraded...

/etc/cron.daily/mdadm:
mdadm: Unknown keyword  ============================================================================
mdadm: Unknown keyword  Netrw Directory Listing                                        (netrw v140)
mdadm: Unknown keyword    /etc/update-motd.d
mdadm: Unknown keyword    Sorted by      name
mdadm: Unknown keyword    Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~$
mdadm: Unknown keyword    Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:exec
mdadm: Unknown keyword  ============================================================================
mdadm: Unknown keyword ../
mdadm: Unknown keyword 00-header*
mdadm: Unknown keyword 10-help-text*
mdadm: Unknown keyword 50-landscape-sysinfo@
mdadm: Unknown keyword 90-updates-available*
mdadm: Unknown keyword 91-release-upgrade*
mdadm: Unknown keyword 98-fsck-at-reboot*
mdadm: Unknown keyword 98-reboot-required*
mdadm: Unknown keyword 99-footer*

---

### Post by creativelies on 2011-06-03
Actually, when I do mdadm --detail /dev/xxx I get the same error message:


$ sudo mdadm --detail /dev/md0

mdadm: Unknown keyword  ============================================================================
mdadm: Unknown keyword  Netrw Directory Listing                                        (netrw v140)
mdadm: Unknown keyword    /etc/update-motd.d
mdadm: Unknown keyword    Sorted by      name
mdadm: Unknown keyword    Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~$
mdadm: Unknown keyword    Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:exec
mdadm: Unknown keyword  ============================================================================
mdadm: Unknown keyword ../
mdadm: Unknown keyword 00-header*
mdadm: Unknown keyword 10-help-text*
mdadm: Unknown keyword 50-landscape-sysinfo@
mdadm: Unknown keyword 90-updates-available*
mdadm: Unknown keyword 91-release-upgrade*
mdadm: Unknown keyword 98-fsck-at-reboot*
mdadm: Unknown keyword 98-reboot-required*
mdadm: Unknown keyword 99-footer*
/dev/md0:
        Version : 0.90
  Creation Time : Thu Apr 21 22:44:39 2011
     Raid Level : raid1
     Array Size : 58613696 (55.90 GiB 60.02 GB)
  Used Dev Size : 58613696 (55.90 GiB 60.02 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jun  4 09:02:06 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : d1541011:7279984b:0265081a:79477f0c
         Events : 0.15868

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       81        2      active sync   /dev/sdf1

Any ideas?

---

