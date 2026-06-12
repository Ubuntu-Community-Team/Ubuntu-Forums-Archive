---
title: "disable_functions == Assinstance Needed"
date: 2010-12-21
forum: General Help
---

### Post by Faks on 2010-12-21
**Server os ubuntu server with ubuntu desktop .**

** Here is code from php.ini**
```
disable_functions = "php_uname,readfile, getmyuid, getmypid, passthru, curl_exec , curl_multi_exec , parse_ini_file , leak, listen, diskfreespace, tmpfile, link, ignore_user_abord, shell_exec, dl, set_time_limit, exec, system, highlight_file, source, show_source, fpaththru, virtual, posix_ctermid, posix_getcwd, posix_getegid, posix_geteuid, posix_getgid, posix_getgrgid, posix_getgrnam, posix_getgroups, posix_getlogin, posix_getpgid, posix_getpgrp, posix_getpid, posix, _getppid, posix_getpwnam, posix_getpwuid, posix_getrlimit, posix_getsid, posix_getuid, posix_isatty, posix_kill, posix_mkfifo, posix_setegid, posix_seteuid, posix_setgid, posix_setpgid, posix_setsid, posix_setuid, posix_times, posix_ttyname, posix_uname, proc_open, proc_close, proc_get_status, proc_nice, proc_terminate, phpinfo, popen, pcntl_exec, chgrp, ini_alter, mysql_pconnect,fwrite,fopen,fread,disk_total_space,disk_free_space,rename,delete, define_syslog_variables, eval, fp, fput, ftp_connect, ftp_exec, ftp_get, ftp_login, ftp_nb_fput, ftp_put, ftp_raw, ftp_rawlist, ini_get_all, ini_restore, inject_code, openlog, phpAds_remoteInfo, phpAds_XmlRpc, phpAds_xmlrpcDecode, phpAds_xmlrpcEncode, syslog, xmlrpc_entity_decode,phpversion,override_function,getmygid,ini_get,opendir,get_current_user,is_writable,getcwd,realpath,is_file,fgets,dir,get_cfg_var,fsockopen"

```**phpmyadmin import error**
Could not load import plugins, please check your installation!

** phpmyadmin export error**
Could not load export plugins, please check your installation!

[B]i have been reading code (phpmyadmin) and couldn't find right function to allow read plugins for phpmyadmin sow i decided to create tread here maybe somebody else has brighter head then mine or i am simply missing something as usually ^^.
[/B]

---

### Post by Faks on 2010-12-21
**BUMP** :popcorn:

---

### Post by Faks on 2010-12-22
bump come on nobody knows the solution ? ;)

---

### Post by Faks on 2010-12-23
bump :(

---

### Post by Faks on 2010-12-29
[B]For Everybody else this should example don't screw around like i did :) sow please don't block !
is_file,init_get functions and have n1 day bye !
[/B]

---

### Post by andisusilo on 2012-03-21
Delete ini_get_all and ini_get
just it, and you can import from phpmyadmin,,,

---

