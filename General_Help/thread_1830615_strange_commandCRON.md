---
title: "strange command:CRON"
date: 2011-08-22
forum: General Help
---

### Post by luofeiyu on 2011-08-22
please see,
ps aux

USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
root 1355 0.0 0.0 2264 904 ? Ss 09:05 0:00 cron
daemon 1356 0.0 0.0 2128 352 ? Ss 09:05 0:00 atd
root 8832 0.0 0.2 9900 2476 ? S 10:30 0:00 CRON
root 8834 0.0 0.0 1908 504 ? Ss 10:30 0:00 /bin/sh -c m
pengtao 8962 0.0 0.1 4704 1192 pts/1 R+ 10:33 0:00 ps -aux

the  CRON  ,PID  8832
i use command
sudo find / -name CRON -print  
find nothing,maybe it is a verus in my computer,do you think so?

---

### Post by Thewhistlingwind on 2011-08-22
```
 man cron 
```

It's an event scheduler.

If you didn't schedule anything, there might be a problem.

---

### Post by luofeiyu on 2011-08-22
it is a problem,in my output ,the pid 1355 and 1356  is normal,but the pid 8832  is a big problem,

CRON all leters uppercase,not lower case.

so i think it is a verus,how to detect it?how to verify it?

USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
root 1355 0.0 0.0 2264 904 ? Ss 09:05 0:00 cron
daemon 1356 0.0 0.0 2128 352 ? Ss 09:05 0:00 atd
root 8832 0.0 0.2 9900 2476 ? S 10:30 0:00 CRON

---

### Post by Sazhen86 on 2011-08-22
If it's still process 8832, try 'cat /proc/8832/cmdline' to see the command that ran the process.  Also, try 'sudo lsof | grep 8832' to see what files it has open.  One of them should be marked 'txt' which is the program file and should have the complete path.

---

### Post by luofeiyu on 2011-08-22
this time ,the pid is 7995.

 sudo lsof | grep 7995
[sudo] password for pengtao: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/pengtao/.gvfs
      Output information may be incomplete.
gconfd-2  4082    pengtao   24u     unix 0xf364b8c0      0t0      17995 /tmp/orbit-pengtao/linc-ff2-0-72d26f7978d2b
cron      7995       root  cwd       DIR        8,8     4096      47811 /var/spool/cron
cron      7995       root  rtd       DIR        8,2     4096          2 /
cron      7995       root  txt       REG        8,7    38864     431677 /usr/sbin/cron
cron      7995       root  mem       REG        8,2    38500    1737586 /lib/i386-linux-gnu/libnss_nis-2.13.so
cron      7995       root  mem       REG        8,7    91852     310426 /usr/lib/libsasl2.so.2.0.23
cron      7995       root  mem       REG        8,2     5344    1746685 /lib/i386-linux-gnu/security/pam_permit.so
cron      7995       root  mem       REG        8,2    13672    1737600 /lib/security/pam_ecryptfs.so
cron      7995       root  mem       REG        8,7    13696     310347 /usr/lib/libplc4.so
cron      7995       root  mem       REG        8,2    50864    1746663 /lib/i386-linux-gnu/security/pam_unix.so
cron      7995       root  mem       REG        8,2   121644    1737601 /lib/i386-linux-gnu/libpthread-2.13.so
cron      7995       root  mem       REG        8,2    26400    1737578 /lib/i386-linux-gnu/libnss_compat-2.13.so
cron      7995       root  mem       REG        8,7   272384     310221 /usr/lib/libldap_r-2.4.so.2.5.6
cron      7995       root  mem       REG        8,7    62908     311404 /usr/lib/i386-linux-gnu/libtasn1.so.3.1.9
cron      7995       root  mem       REG        8,7    38296     310477 /usr/lib/libtalloc.so.2.0.5
cron      7995       root  mem       REG        8,7    91360     309850 /usr/lib/libwbclient.so.0
cron      7995       root  mem       REG        8,7     9568     310348 /usr/lib/libplds4.so
cron      7995       root  mem       REG        8,2    13632    1746669 /lib/i386-linux-gnu/security/pam_env.so
cron      7995       root  mem       REG        8,2     9524    1737636 /lib/security/pam_ck_connector.so
cron      7995       root  mem       REG        8,2    30684    1737605 /lib/i386-linux-gnu/librt-2.13.so
cron      7995       root  mem       REG        8,7   191240     311350 /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
cron      7995       root  mem       REG        8,7     9580     309826 /usr/lib/libck-connector.so.0.0.0
cron      7995       root  mem       REG        8,2     5284    1746668 /lib/i386-linux-gnu/security/pam_deny.so
cron      7995       root  mem       REG        8,7   109852     311480 /usr/lib/libecryptfs.so.0.0.0
cron      7995       root  mem       REG        8,2    42652    1737778 /lib/security/pam_ldap.so
cron      7995       root  mem       REG        8,7   608728     311344 /usr/lib/i386-linux-gnu/libgnutls.so.26.14.12
cron      7995       root  mem       REG        8,2    71432    1737603 /lib/i386-linux-gnu/libresolv-2.13.so
cron      7995       root  mem       REG        8,2   471064    1737566 /lib/i386-linux-gnu/libgcrypt.so.11.6.0
cron      7995       root  mem       REG        8,2     9460    1737572 /lib/i386-linux-gnu/libkeyutils.so.1.3
cron      7995       root  mem       REG        8,2    13816    1736741 /lib/libcap.so.2.20
cron      7995       root  mem       REG        8,7   199676     310463 /usr/lib/libssl3.so
cron      7995       root  mem       REG        8,7    95996     310296 /usr/lib/libnssutil3.so
cron      7995       root  mem       REG        8,2    79672    1737576 /lib/i386-linux-gnu/libnsl-2.13.so
cron      7995       root  mem       REG        8,2   243400    1736723 /lib/i386-linux-gnu/libdbus-1.so.3.5.4
cron      7995       root  mem       REG        8,2  1434180    1737536 /lib/i386-linux-gnu/libc-2.13.so
cron      7995       root  mem       REG        8,2     9736    1737546 /lib/i386-linux-gnu/libdl-2.13.so
cron      7995       root  mem       REG        8,7   711308     311363 /usr/lib/i386-linux-gnu/libkrb5.so.3.3
cron      7995       root  mem       REG        8,2     9608    1737541 /lib/i386-linux-gnu/libcom_err.so.2.1
cron      7995       root  mem       REG        8,7    26112     311365 /usr/lib/i386-linux-gnu/libkrb5support.so.0.1
cron      7995       root  mem       REG        8,7   195972     310293 /usr/lib/libnspr4.so
cron      7995       root  mem       REG        8,2   117960    1737523 /lib/i386-linux-gnu/ld-2.13.so
cron      7995       root  mem       REG        8,7   140788     311361 /usr/lib/i386-linux-gnu/libk5crypto.so.3.1
cron      7995       root  mem       REG        8,7    46424     310216 /usr/lib/liblber-2.4.so.2.5.6
cron      7995       root  mem       REG        8,2    42580    1737582 /lib/i386-linux-gnu/libnss_files-2.13.so
cron      7995       root  mem       REG        8,2    34264    1737542 /lib/i386-linux-gnu/libcrypt-2.13.so
cron      7995       root  mem       REG        8,2  1866412    1737652 /lib/security/pam_smbpass.so
cron      7995       root  mem       REG        8,2    13564    1737570 /lib/i386-linux-gnu/libgpg-error.so.0.8.0
cron      7995       root  mem       REG        8,2    17828    1746683 /lib/i386-linux-gnu/security/pam_limits.so
cron      7995       root  mem       REG        8,2     9516    1736789 /lib/security/pam_cap.so
cron      7995       root  mem       REG        8,2   104116    1737607 /lib/i386-linux-gnu/libselinux.so.1
cron      7995       root  mem       REG        8,2     9608    1737785 /lib/i386-linux-gnu/libpam_misc.so.0.82.0
cron      7995       root  mem       REG        8,2    46644    1737786 /lib/i386-linux-gnu/libpam.so.0.82.3
cron      7995       root  mem       REG        8,2    38404    1737638 /lib/security/pam_gnome_keyring.so
cron      7995       root  mem       REG        8,7   146220     310442 /usr/lib/libsmime3.so
cron      7995       root  mem       REG        8,2    79476    1737619 /lib/i386-linux-gnu/libz.so.1.2.3.4
cron      7995       root  mem       REG        8,7  1107684     310294 /usr/lib/libnss3.so
cron      7995       root    0r      CHR        1,3      0t0       4375 /dev/null
cron      7995       root    1w      CHR        1,3      0t0       4375 /dev/null
cron      7995       root    2w      CHR        1,3      0t0       4375 /dev/null
cron      7995       root    5u      REG        8,6   855368         18 /tmp/tmpfauJh7C (deleted)
cron      7995       root    6u     unix 0xca4e7200      0t0      78667 socket


cat /usr/sbin/cron


ELF&#65533;&#65533;4&#65533;&#65533;4(44&#65533;4&#65533;44&#65533;4&#65533;&#65533;&#65533;,&#65533;,&#65533; &#65533; &#65533;&#65533;HH&#65533;H&#65533;DDQ&#65533;tdR&#65533;td &#65533;&#65533;/lib/ld-linux.so.2GNUGNU&#65533;&#65533;&#65533;&#65533;&#65533;NO|&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;t
  0?f&#65533;S-&#65533;'7&#65533;&#65533;0&#65533;&#65533;&#65533;l8&#65533;&#65533;&#65533;S&#65533;Sl&#65533;&#65533;&#65533;&#65533;&#65533;{>K&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;[M&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;&#65533;&#65533;_a&#65533;&#65533;&#65533;N&#65533;2${T
&#65533;07tE`	s&#65533;`&#65533;my&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;T&#65533;t&#65533;
                                                                                                         &#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;
        ^L&#65533;&#65533;libpam.so.0__gmon_start___Jv_RegisterClassespam_open_sessionpam_close_sessionpam_set_itempam_setcredpam_startpam_strerrorpam_acct_mgmtpam_getenvlistpam_endlibselinux.so.1getcon_initis_selinux_enabledsecurity_getenforceget_ordered_context_list_with_levelsecurity_compute_avfgetfileconfreeconsetexeccongetseuserbynamefreeconary_finilibc.so.6_IO_stdin_usedsetuidfflushreaddir_IO_putcsetlocalefopenstrncmpftruncatewaitregexecpipe__strdupperrorclosedirinitgroupsftellstrncpysignalputsforksigprocmask__stack_chk_fail__lxstatmkdirreallocabortstdin_exitgetpidflockrewindgmtimestrtokstrtolendpwentexeclefgetsgetpwnamcallocstrlenungetctmpfilesigemptysetopenlogmemset__errno_locationfseekchdir__syslog_chkgetoptdup2__fprintf_chksigaddsetgetgrnamstdoutfputc__isoc99_fscanffclosemallocumaskstrcasecmpsetegidgetgidnl_langinfoopendir__ctype_b_locregcompoptargstderr__snprintf_chkseteuidgetuidgetegidexecvpfreopencreat__fxstatfilenogethostnamechownfwritefreadgeteuidwaitpidlocaltimestrchrfdopensleep__ctype_toupper_loc__strcpy_chksetsidfcntl__sprintf_chk__xstatgetdtablesizeaccess_IO_getcsetgid__strcat_chkstrcmp__libc_start_mainferrorsetenvcloselogfree_edata__bss_startLIBPAM_1.0GLIBC_2.4GLIBC_2.3GLIBC_2.1GLIBC_2.3.4GLIBC_2.7GLIBC_2.0H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; `/h	dii

how to do next step?

---

### Post by sisco311 on 2011-08-22
From **man cron**
```
       cron then wakes up every minute, examining all stored crontabs,  check&#8208;
       ing  each  command  to  see  if it should be run in the current minute.
       When executing commands, any output is  mailed  to  the  owner  of  the
       crontab (or to the user named in the MAILTO environment variable in the
       crontab, if such exists).  [b]The children copies of  cron  running  these
       processes  have their name coerced to uppercase, as will be seen in the
       syslog and ps output.[/b]

```

---

