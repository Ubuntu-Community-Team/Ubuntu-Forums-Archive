---
title: "weird rkhunter output."
date: 2009-11-26
forum: General Help
---

### Post by The Funkbomb on 2009-11-26
I ran rkhunter -c to do a quick check.

I've never gotten so many warnings before.

```
[18:26:05] Running Rootkit Hunter version 1.3.4 on patrick-desktop
[18:26:05]
[18:26:05] Info: Start date is Thu Nov 26 18:26:05 EST 2009
[18:26:05]
[18:26:05] Checking configuration file and command-line options...
[18:26:05] Info: Detected operating system is 'Linux'
[18:26:05] Info: Found O/S name: Ubuntu 9.10
[18:26:05] Info: Command line is /usr/bin/rkhunter -c
[18:26:05] Info: Environment shell is /bin/bash; rkhunter is using dash
[18:26:05] Info: Using configuration file '/etc/rkhunter.conf'
[18:26:05] Info: Installation directory is '/usr'
[18:26:05] Info: Using language 'en'
[18:26:05] Info: Using '/var/lib/rkhunter/db' as the database directory
[18:26:05] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[18:26:05] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[18:26:05] Info: Using '/' as the root directory by default
[18:26:05] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[18:26:05] Info: No mail-on-warning address configured
[18:26:05] Info: X will be automatically detected
[18:26:05] Info: Using second color set
[18:26:05] Info: Found the 'diff' command: /usr/bin/diff
[18:26:05] Info: Found the 'file' command: /usr/bin/file
[18:26:05] Info: Found the 'find' command: /usr/bin/find
[18:26:05] Info: Found the 'ifconfig' command: /sbin/ifconfig
[18:26:05] Info: Found the 'ip' command: /sbin/ip
[18:26:05] Info: Found the 'ldd' command: /usr/bin/ldd
[18:26:05] Info: Found the 'lsattr' command: /usr/bin/lsattr
[18:26:05] Info: Found the 'lsmod' command: /sbin/lsmod
[18:26:05] Info: Found the 'lsof' command: /usr/bin/lsof
[18:26:05] Info: Found the 'mktemp' command: /bin/mktemp
[18:26:05] Info: Found the 'netstat' command: /bin/netstat
[18:26:05] Info: Found the 'perl' command: /usr/bin/perl
[18:26:05] Info: Found the 'ps' command: /bin/ps
[18:26:05] Info: Found the 'pwd' command: /bin/pwd
[18:26:05] Info: Found the 'readlink' command: /bin/readlink
[18:26:05] Info: Found the 'sort' command: /usr/bin/sort
[18:26:05] Info: Found the 'stat' command: /usr/bin/stat
[18:26:05] Info: Found the 'strings' command: /usr/bin/strings
[18:26:05] Info: Found the 'uniq' command: /usr/bin/uniq
[18:26:05] Info: System is not using prelinking
[18:26:05] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[18:26:05] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[18:26:05] Info: Stored hash values did not use a package manager
[18:26:05] Info: The hash function field index is set to 1
[18:26:05] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[18:26:05] Info: Previous file attributes were stored
[18:26:05] Info: Enabled tests are: all
[18:26:05] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[18:26:05] Info: Found ksym file '/proc/kallsyms'
[18:26:05]
[18:26:05] Checking if the O/S has changed since last time...
[18:26:05] Info: Nothing seems to have changed
[18:26:05]
[18:26:05] Starting system checks...
[18:26:05]
[18:26:05] Checking system commands...
[18:26:05] Info: Starting test name 'system_commands'
[18:26:05]
[18:26:05] Performing 'strings' command checks
[18:26:05] Info: Starting test name 'strings'
[18:26:05] Scanning for string /usr/sbin/ntpsx               [ OK ]
[18:26:05] Scanning for string /usr/lib/.../ls               [ OK ]
[18:26:05] Scanning for string /usr/lib/.../netstat          [ OK ]
[18:26:05] Scanning for string /usr/lib/.../lsof             [ OK ]
[18:26:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[18:26:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[18:26:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[18:26:05] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[18:26:05] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[18:26:06] Scanning for string /usr/lib/.../psr              [ OK ]
[18:26:06] Scanning for string /usr/lib/.../find             [ OK ]
[18:26:06] Scanning for string /usr/lib/.../pstree           [ OK ]
[18:26:06] Scanning for string /usr/lib/.../slocate          [ OK ]
[18:26:06] Scanning for string /usr/lib/.../du               [ OK ]
[18:26:06] Scanning for string /usr/lib/.../top              [ OK ]
[18:26:06] Scanning for string /usr/lib/...                  [ OK ]
[18:26:06] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[18:26:06] Scanning for string /usr/lib/.bkit-               [ OK ]
[18:26:06] Scanning for string /tmp/.bkp                     [ OK ]
[18:26:06] Scanning for string /tmp/.cinik                   [ OK ]
[18:26:06] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[18:26:06] Scanning for string /lib/.sso                     [ OK ]
[18:26:06] Scanning for string /lib/.so                      [ OK ]
[18:26:06] Scanning for string /var/run/...dica/clean        [ OK ]
[18:26:06] Scanning for string /var/run/...dica/xl           [ OK ]
[18:26:06] Scanning for string /var/run/...dica/xdr          [ OK ]
[18:26:06] Scanning for string /var/run/...dica/psg          [ OK ]
[18:26:06] Scanning for string /var/run/...dica/secure       [ OK ]
[18:26:06] Scanning for string /var/run/...dica/rdx          [ OK ]
[18:26:06] Scanning for string /var/run/...dica/va           [ OK ]
[18:26:06] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[18:26:06] Scanning for string /usr/bin/.etc                 [ OK ]
[18:26:06] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[18:26:06] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[18:26:06] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[18:26:06] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[18:26:06] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[18:26:06] Scanning for string /bin/sysback                  [ OK ]
[18:26:06] Scanning for string /usr/local/bin/sysback        [ OK ]
[18:26:06] Scanning for string /usr/lib/.tbd                 [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[18:26:06] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[18:26:06] Scanning for string /usr/info/.torn/sh*           [ OK ]
[18:26:07] Scanning for string /usr/src/.****/.1addr         [ OK ]
[18:26:07] Scanning for string /usr/src/.****/.1file         [ OK ]
[18:26:07] Scanning for string /usr/src/.****/.1proc         [ OK ]
[18:26:07] Scanning for string /usr/src/.****/.1logz         [ OK ]
[18:26:07] Scanning for string /usr/info/.t0rn               [ OK ]
[18:26:07] Scanning for string /dev/.lib                     [ OK ]
[18:26:07] Scanning for string /dev/.lib/lib                 [ OK ]
[18:26:07] Scanning for string /dev/.lib/lib/lib             [ OK ]
[18:26:07] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[18:26:07] Scanning for string /dev/.lib/lib/scan            [ OK ]
[18:26:07] Scanning for string /usr/src/.****                [ OK ]
[18:26:07] Scanning for string /usr/man/man1/man1            [ OK ]
[18:26:07] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[18:26:07] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[18:26:07] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[18:26:07]
[18:26:07] Performing 'shared libraries' checks
[18:26:07] Info: Starting test name 'shared_libs'
[18:26:07] Checking for preloading variables                 [ None found ]
[18:26:07] Checking for preload file                         [ Not found ]
[18:26:07] Info: Starting test name 'shared_libs_path'
[18:26:07] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[18:26:07]
[18:26:07] Performing file properties checks
[18:26:07] Info: Starting test name 'properties'
[18:26:07] Checking for prerequisites                        [ OK ]
[18:26:07] /bin/bash                                         [ OK ]
[18:26:07] /bin/cat                                          [ OK ]
[18:26:07] /bin/chmod                                        [ OK ]
[18:26:07] /bin/chown                                        [ OK ]
[18:26:07] /bin/cp                                           [ OK ]
[18:26:07] /bin/date                                         [ OK ]
[18:26:07] /bin/df                                           [ OK ]
[18:26:07] /bin/dmesg                                        [ OK ]
[18:26:08] /bin/echo                                         [ OK ]
[18:26:08] /bin/ed                                           [ OK ]
[18:26:08] /bin/egrep                                        [ OK ]
[18:26:08] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[18:26:08] /bin/fgrep                                        [ OK ]
[18:26:08] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[18:26:08] /bin/fuser                                        [ OK ]
[18:26:08] /bin/grep                                         [ OK ]
[18:26:08] /bin/ip                                           [ OK ]
[18:26:08] /bin/kill                                         [ OK ]
[18:26:08] /bin/less                                         [ OK ]
[18:26:08] /bin/login                                        [ OK ]
[18:26:08] /bin/ls                                           [ OK ]
[18:26:08] /bin/lsmod                                        [ OK ]
[18:26:08] /bin/mktemp                                       [ OK ]
[18:26:08] /bin/more                                         [ OK ]
[18:26:08] /bin/mount                                        [ OK ]
[18:26:08] /bin/mv                                           [ OK ]
[18:26:08] /bin/netstat                                      [ OK ]
[18:26:09] /bin/ps                                           [ OK ]
[18:26:09] /bin/pwd                                          [ OK ]
[18:26:09] /bin/readlink                                     [ OK ]
[18:26:09] /bin/sed                                          [ OK ]
[18:26:09] /bin/sh                                           [ OK ]
[18:26:09] /bin/su                                           [ OK ]
[18:26:09] /bin/touch                                        [ OK ]
[18:26:09] /bin/uname                                        [ OK ]
[18:26:09] /bin/which                                        [ OK ]
[18:26:09] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[18:26:09] /bin/dash                                         [ OK ]
[18:26:09] /usr/bin/awk                                      [ OK ]
[18:26:09] /usr/bin/basename                                 [ OK ]
[18:26:09] /usr/bin/chattr                                   [ OK ]
[18:26:09] /usr/bin/cut                                      [ OK ]
[18:26:09] /usr/bin/diff                                     [ OK ]
[18:26:10] /usr/bin/dirname                                  [ OK ]
[18:26:10] /usr/bin/dpkg                                     [ OK ]
[18:26:10] /usr/bin/dpkg-query                               [ OK ]
[18:26:10] /usr/bin/du                                       [ OK ]
[18:26:10] /usr/bin/env                                      [ OK ]
[18:26:10] /usr/bin/file                                     [ OK ]
[18:26:10] /usr/bin/find                                     [ OK ]
[18:26:10] /usr/bin/GET                                      [ OK ]
[18:26:10] /usr/bin/groups                                   [ OK ]
[18:26:10] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[18:26:10] /usr/bin/head                                     [ OK ]
[18:26:10] /usr/bin/id                                       [ OK ]
[18:26:10] /usr/bin/killall                                  [ OK ]
[B][18:26:10] /usr/bin/last                                     [ Warning ]
[18:26:10] Warning: The file properties have changed:
[18:26:10]          File: /usr/bin/last
[18:26:10]          Current inode: 4616    Stored inode: 1662
[18:26:10]          Current file modification time: 1257846438
[18:26:10]          Stored file modification time : 1255965924[/B]
[18:26:10] /usr/bin/lastlog                                  [ OK ]
[18:26:10] /usr/bin/ldd                                      [ OK ]
[18:26:10] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[18:26:10] /usr/bin/less                                     [ OK ]
[18:26:11] /usr/bin/locate                                   [ OK ]
[18:26:11] /usr/bin/logger                                   [ OK ]
[18:26:11] /usr/bin/lsattr                                   [ OK ]
[18:26:11] /usr/bin/lsof                                     [ OK ]
[18:26:11] /usr/bin/mail                                     [ OK ]
[18:26:11] /usr/bin/md5sum                                   [ OK ]
[18:26:11] /usr/bin/mlocate                                  [ OK ]
[18:26:11] /usr/bin/newgrp                                   [ OK ]
[18:26:11] /usr/bin/passwd                                   [ OK ]
[18:26:11] /usr/bin/perl                                     [ OK ]
[18:26:11] /usr/bin/pstree                                   [ OK ]
[18:26:11] /usr/bin/rkhunter                                 [ OK ]
[18:26:11] /usr/bin/runcon                                   [ OK ]
[18:26:11] /usr/bin/sha1sum                                  [ OK ]
[18:26:11] /usr/bin/size                                     [ Warning ]
[B][18:26:11] Warning: The file properties have changed:
[18:26:11]          File: /usr/bin/size
[18:26:11]          Current inode: 11368    Stored inode: 2109
[18:26:11]          Current file modification time: 1256831344
[18:26:11]          Stored file modification time : 1255850129[/B]
[18:26:11] /usr/bin/sort                                     [ OK ]
[18:26:12] /usr/bin/stat                                     [ OK ]
[18:26:12] /usr/bin/strace                                   [ OK ]
[18:26:12] /usr/bin/strings                                  [ Warning ]
[B][18:26:12] Warning: The file properties have changed:
[18:26:12]          File: /usr/bin/strings
[18:26:12]          Current inode: 11371    Stored inode: 2153
[18:26:12]          Current file modification time: 1256831344
[18:26:12]          Stored file modification time : 1255850129[/B]
[18:26:12] /usr/bin/sudo                                     [ OK ]
[18:26:12] /usr/bin/tail                                     [ OK ]
[18:26:12] /usr/bin/test                                     [ OK ]
[18:26:12] /usr/bin/top                                      [ OK ]
[18:26:12] /usr/bin/touch                                    [ OK ]
[18:26:12] /usr/bin/tr                                       [ OK ]
[18:26:12] /usr/bin/uniq                                     [ OK ]
[18:26:12] /usr/bin/users                                    [ OK ]
[18:26:12] /usr/bin/vmstat                                   [ OK ]
[18:26:12] /usr/bin/w                                        [ OK ]
[18:26:12] /usr/bin/watch                                    [ OK ]
[18:26:12] /usr/bin/wc                                       [ OK ]
[18:26:12] /usr/bin/wget                                     [ OK ]
[18:26:12] /usr/bin/whatis                                   [ OK ]
[18:26:13] /usr/bin/whereis                                  [ OK ]
[18:26:13] /usr/bin/which                                    [ OK ]
[18:26:13] /usr/bin/who                                      [ OK ]
[18:26:13] /usr/bin/whoami                                   [ OK ]
[18:26:13] /usr/bin/mawk                                     [ OK ]
[18:26:13] /usr/bin/lwp-request                              [ OK ]
[18:26:13] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[18:26:13] /usr/bin/bsd-mailx                                [ OK ]
[18:26:13] /usr/bin/w.procps                                 [ OK ]
[18:26:13] /sbin/depmod                                      [ OK ]
[18:26:13] /sbin/ifconfig                                    [ OK ]
[18:26:13] /sbin/ifdown                                      [ OK ]
[18:26:13] /sbin/ifup                                        [ OK ]
[18:26:13] /sbin/init                                        [ OK ]
[18:26:13] /sbin/insmod                                      [ OK ]
[18:26:13] /sbin/ip                                          [ OK ]
[18:26:13] /sbin/lsmod                                       [ OK ]
[18:26:14] /sbin/modinfo                                     [ OK ]
[18:26:14] /sbin/modprobe                                    [ OK ]
[18:26:14] /sbin/rmmod                                       [ OK ]
[18:26:14] /sbin/runlevel                                    [ OK ]
[B][18:26:14] /sbin/sulogin                                     [ Warning ]
[18:26:14] Warning: The file properties have changed:
[18:26:14]          File: /sbin/sulogin
[18:26:14]          Current inode: 4620    Stored inode: 1026
[18:26:14]          Current file modification time: 1257846438
[18:26:14]          Stored file modification time : 1255965924[/B]
[18:26:14] /sbin/sysctl                                      [ OK ]
[B][18:26:14] /usr/sbin/adduser                                 [ Warning ]
[18:26:14] Warning: The file properties have changed:
[18:26:14]          File: /usr/sbin/adduser
[18:26:14]          Current hash: ae9336d2700a0d02fa50900f9f9e7a568a0897a5
[18:26:14]          Stored hash : 3b23a07e11395e782cab2d20d71af5f1dc7bb9e9
[18:26:14]          Current inode: 800    Stored inode: 3855
[18:26:14]          Current file modification time: 1257763340
[18:26:14]          Stored file modification time : 1249313589[/B]
[18:26:14] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[18:26:14] /usr/sbin/chroot                                  [ OK ]
[18:26:14] /usr/sbin/cron                                    [ OK ]
[18:26:14] /usr/sbin/groupadd                                [ OK ]
[18:26:14] /usr/sbin/groupdel                                [ OK ]
[18:26:15] /usr/sbin/groupmod                                [ OK ]
[18:26:15] /usr/sbin/grpck                                   [ OK ]
[18:26:15] /usr/sbin/nologin                                 [ OK ]
[18:26:15] /usr/sbin/pwck                                    [ OK ]
[18:26:15] /usr/sbin/rsyslogd                                [ OK ]
[18:26:15] /usr/sbin/tcpd                                    [ OK ]
[18:26:15] /usr/sbin/unhide                                  [ OK ]
[18:26:15] /usr/sbin/useradd                                 [ OK ]
[18:26:15] /usr/sbin/userdel                                 [ OK ]
[18:26:15] /usr/sbin/usermod                                 [ OK ]
[18:26:15] /usr/sbin/vipw                                    [ OK ]
[18:26:15] /usr/sbin/unhide-linux26                          [ OK ]
[18:26:19]
[18:26:19] Checking for rootkits...
[18:26:19] Info: Starting test name 'rootkits'
[18:26:19]
[18:26:19] Performing check of known rootkit files and directories
[18:26:19] Info: Starting test name 'known_rkts'
[18:26:19]
[18:26:19] Checking for 55808 Trojan - Variant A...
[18:26:19]   Checking for file '/tmp/.../r'                  [ Not found ]
[18:26:19]   Checking for file '/tmp/.../a'                  [ Not found ]
[18:26:19] 55808 Trojan - Variant A                          [ Not found ]
[18:26:19]
[18:26:19] Checking for ADM Worm...
[18:26:19]   Checking for string 'w0rm'                      [ Not found ]
[18:26:19] ADM Worm                                          [ Not found ]
[18:26:19]
[18:26:19] Checking for AjaKit Rootkit...
[18:26:19]   Checking for file '/dev/tux/.addr'              [ Not found ]
[18:26:19]   Checking for file '/dev/tux/.proc'              [ Not found ]
[18:26:19]   Checking for file '/dev/tux/.file'              [ Not found ]
[18:26:20]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[18:26:20]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[18:26:20]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[18:26:20]   Checking for directory '/dev/tux'               [ Not found ]
[18:26:20]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[18:26:20] AjaKit Rootkit                                    [ Not found ]
[18:26:20]
[18:26:20] Checking for aPa Kit...
[18:26:20]   Checking for file '/usr/share/.aPa'             [ Not found ]
[18:26:20] aPa Kit                                           [ Not found ]
[18:26:20]
[18:26:20] Checking for Apache Worm...
[18:26:20]   Checking for file '/bin/.log'                   [ Not found ]
[18:26:20] Apache Worm                                       [ Not found ]
[18:26:20]
[18:26:20] Checking for Ambient (ark) Rootkit...
[18:26:20]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[18:26:20]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[18:26:20]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[18:26:20]   Checking for directory '/dev/ptyxx'             [ Not found ]
[18:26:20] Ambient (ark) Rootkit                             [ Not found ]
[18:26:20]
[18:26:20] Checking for Balaur Rootkit...
[18:26:20]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[18:26:20]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[18:26:20]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[18:26:20]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[18:26:20] Balaur Rootkit                                    [ Not found ]
[18:26:20]
[18:26:20] Checking for BeastKit Rootkit...
[18:26:20]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[18:26:20]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[18:26:20]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[18:26:20] BeastKit Rootkit                                  [ Not found ]
[18:26:20]
[18:26:20] Checking for beX2 Rootkit...
[18:26:20]   Checking for directory '/usr/include/bex'       [ Not found ]
[18:26:20] beX2 Rootkit                                      [ Not found ]
[18:26:20]
[18:26:20] Checking for BOBKit Rootkit...
[18:26:20]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../find'           [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../du'             [ Not found ]
[18:26:20]   Checking for file '/usr/lib/.../top'            [ Not found ]
[18:26:20]   Checking for directory '/usr/lib/...'           [ Not found ]
[18:26:20]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[18:26:20]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[18:26:20]   Checking for directory '/tmp/.bkp'              [ Not found ]
[18:26:20] BOBKit Rootkit                                    [ Not found ]
[18:26:21]
[18:26:21] Checking for CiNIK Worm (Slapper.B variant)...
[18:26:21]   Checking for file '/tmp/.cinik'                 [ Not found ]
[18:26:21]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[18:26:21] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[18:26:21]
[18:26:21] Checking for Danny-Boy's Abuse Kit...
[18:26:21]   Checking for file '/dev/mdev'                   [ Not found ]
[18:26:21]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[18:26:21] Danny-Boy's Abuse Kit                             [ Not found ]
[18:26:21]
[18:26:21] Checking for Devil RootKit...
[18:26:21]   Checking for file '/var/lib/games/.src'         [ Not found ]
[18:26:21]   Checking for file '/dev/dsx'                    [ Not found ]
[18:26:21]   Checking for file '/dev/caca'                   [ Not found ]
[18:26:21] Devil RootKit                                     [ Not found ]
[18:26:21]
[18:26:21] Checking for Dica-Kit Rootkit...
[18:26:21]   Checking for file '/lib/.sso'                   [ Not found ]
[18:26:21]   Checking for file '/lib/.so'                    [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/va'         [ Not found ]
[18:26:21]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[18:26:21]   Checking for file '/usr/bin/.etc'               [ Not found ]
[18:26:21]   Checking for directory '/var/run/...dica'       [ Not found ]
[18:26:21]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[18:26:21]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[18:26:21] Dica-Kit Rootkit                                  [ Not found ]
[18:26:21]
[18:26:21] Checking for Dreams Rootkit...
[18:26:21]   Checking for file '/dev/ttyoa'                  [ Not found ]
[18:26:21]   Checking for file '/dev/ttyof'                  [ Not found ]
[18:26:21]   Checking for file '/dev/ttyop'                  [ Not found ]
[18:26:21]   Checking for file '/usr/bin/sense'              [ Not found ]
[18:26:21]   Checking for file '/usr/bin/sl2'                [ Not found ]
[18:26:21]   Checking for file '/usr/bin/logclear'           [ Not found ]
[18:26:21]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[18:26:21]   Checking for file '/usr/bin/snfs'               [ Not found ]
[18:26:21]   Checking for file '/usr/lib/libsss'             [ Not found ]
[18:26:21]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[18:26:21] Dreams Rootkit                                    [ Not found ]
[18:26:21]
[18:26:21] Checking for Duarawkz Rootkit...
[18:26:21]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[18:26:21]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[18:26:21] Duarawkz Rootkit                                  [ Not found ]
[18:26:21]
[18:26:21] Checking for Enye LKM...
[18:26:21]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[18:26:21] Enye LKM                                          [ Not found ]
[18:26:21]
[18:26:21] Checking for Flea Linux Rootkit...
[18:26:21]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[18:26:21]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[18:26:21]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[18:26:21]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[18:26:21]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[18:26:21]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[18:26:21]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[18:26:21]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[18:26:21]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[18:26:21]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[18:26:21]   Checking for directory '/dev/..0'               [ Not found ]
[18:26:21]   Checking for directory '/dev/..0/backup'        [ Not found ]
[18:26:22] Flea Linux Rootkit                                [ Not found ]
[18:26:22]
[18:26:22] Checking for FreeBSD Rootkit...
[18:26:22]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[18:26:22]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[18:26:22]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[18:26:22]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[18:26:22]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[18:26:22]   Checking for file '/bin/sysback'                [ Not found ]
[18:26:22]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[18:26:22]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[18:26:22]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[18:26:22] FreeBSD Rootkit                                   [ Not found ]
[18:26:22]
[18:26:22] Checking for ****`it Rootkit...
[18:26:22]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[18:26:22]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[18:26:22]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[18:26:22]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[18:26:22]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[18:26:22]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[18:26:22]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[18:26:22]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[18:26:22] ****`it Rootkit                                   [ Not found ]
[18:26:22]
[18:26:22] Checking for GasKit Rootkit...
[18:26:22]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[18:26:22]   Checking for directory '/dev/dev'               [ Not found ]
[18:26:22]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[18:26:22]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[18:26:22] GasKit Rootkit                                    [ Not found ]
[18:26:22]
[18:26:22] Checking for Heroin LKM...
[18:26:22]   Checking for kernel symbol 'heroin'             [ Not found ]
[18:26:22] Heroin LKM                                        [ Not found ]
[18:26:22]
[18:26:22] Checking for HjC Kit...
[18:26:22]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[18:26:22] HjC Kit                                           [ Not found ]
[18:26:22]
[18:26:22] Checking for ignoKit Rootkit...
[18:26:22]   Checking for file '/lib/defs/p'                 [ Not found ]
[18:26:22]   Checking for file '/lib/defs/q'                 [ Not found ]
[18:26:22]   Checking for file '/lib/defs/r'                 [ Not found ]
[18:26:22]   Checking for file '/lib/defs/s'                 [ Not found ]
[18:26:22]   Checking for file '/lib/defs/t'                 [ Not found ]
[18:26:22]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[18:26:22]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[18:26:22]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[18:26:22]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[18:26:22]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[18:26:22]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[18:26:22]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[18:26:22]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[18:26:22]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[18:26:22] ignoKit Rootkit                                   [ Not found ]
[18:26:22]
[18:26:22] Checking for ImperalsS-FBRK Rootkit...
[18:26:22]   Checking for directory '/dev/fd/.88'            [ Not found ]
[18:26:22]   Checking for directory '/dev/fd/.99'            [ Not found ]
[18:26:22] ImperalsS-FBRK Rootkit                            [ Not found ]
[18:26:22]
[18:26:22] Checking for IntoXonia-NG Rootkit...
[18:26:23]   Checking for kernel symbol 'funces'             [ Not found ]
[18:26:23]   Checking for kernel symbol 'ixinit'             [ Not found ]
[18:26:23]   Checking for kernel symbol 'tricks'             [ Not found ]
[18:26:23]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[18:26:23]   Checking for kernel symbol 'rootme'             [ Not found ]
[18:26:23]   Checking for kernel symbol 'hide_module'        [ Not found ]
[18:26:23]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[18:26:23] IntoXonia-NG Rootkit                              [ Not found ]
[18:26:23]
[18:26:23] Checking for Irix Rootkit...
[18:26:23]   Checking for directory '/dev/pts/01'            [ Not found ]
[18:26:23]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[18:26:23]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[18:26:23]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[18:26:23] Irix Rootkit                                      [ Not found ]
[18:26:23]
[18:26:23] Checking for Kitko Rootkit...
[18:26:23]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[18:26:23] Kitko Rootkit                                     [ Not found ]
[18:26:23]
[18:26:23] Checking for Knark Rootkit...
[18:26:23]   Checking for file '/proc/knark/pids'            [ Not found ]
[18:26:23]   Checking for directory '/proc/knark'            [ Not found ]
[18:26:23] Knark Rootkit                                     [ Not found ]
[18:26:23]
[18:26:23] Checking for Li0n Worm...
[18:26:23]   Checking for file '/bin/in.telnetd'             [ Not found ]
[18:26:23]   Checking for file '/bin/mjy'                    [ Not found ]
[18:26:23]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[18:26:23]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[18:26:23]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[18:26:23]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[18:26:23] Li0n Worm                                         [ Not found ]
[18:26:23]
[18:26:23] Checking for Lockit / LJK2 Rootkit...
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[18:26:24]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[18:26:24]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[18:26:24] Lockit / LJK2 Rootkit                             [ Not found ]
[18:26:24]
[18:26:24] Checking for Mood-NT Rootkit...
[18:26:24]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[18:26:24]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[18:26:24]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[18:26:24]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[18:26:24]   Checking for directory '/_cthulhu'              [ Not found ]
[18:26:24] Mood-NT Rootkit                                   [ Not found ]
[18:26:24]
[18:26:24] Checking for MRK Rootkit...
[18:26:24]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[18:26:24]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[18:26:24]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[18:26:24]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[18:26:24]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[18:26:24]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[18:26:24] MRK Rootkit                                       [ Not found ]
[18:26:24]
[18:26:24] Checking for Ni0 Rootkit...
[18:26:24]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[18:26:24]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[18:26:24]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[18:26:24]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[18:26:24]   Checking for directory '/tmp/waza'              [ Not found ]
[18:26:24]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[18:26:24]   Checking for directory '/usr/sbin/es'           [ Not found ]
[18:26:24] Ni0 Rootkit                                       [ Not found ]
[18:26:24]
[18:26:24] Checking for Ohhara Rootkit...
[18:26:25]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[18:26:25]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[18:26:25]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[18:26:25]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[18:26:25]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[18:26:25]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[18:26:25]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[18:26:25] Ohhara Rootkit                                    [ Not found ]
[18:26:25]
[18:26:25] Checking for Optic Kit (Tux) Worm...
[18:26:25]   Checking for directory '/dev/tux'               [ Not found ]
[18:26:25]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[18:26:25]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[18:26:25]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[18:26:25] Optic Kit (Tux) Worm                              [ Not found ]
[18:26:25]
[18:26:25] Checking for Oz Rootkit...
[18:26:25]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[18:26:25]   Checking for directory '/dev/.oz'               [ Not found ]
[18:26:25] Oz Rootkit                                        [ Not found ]
[18:26:25]
[18:26:25] Checking for Phalanx Rootkit...
[18:26:25]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[18:26:25]   Checking for file '/etc/host.ph1'               [ Not found ]
[18:26:25]   Checking for file '/bin/host.ph1'               [ Not found ]
[18:26:25]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[18:26:25]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[18:26:25] Phalanx Rootkit                                   [ Not found ]
[18:26:25]
[18:26:25] Checking for Phalanx Rootkit (strings)...
[18:26:25]   Checking for string 'phalanx'                   [ Not found ]
[18:26:25] Phalanx Rootkit (strings)                         [ Not found ]
[18:26:25]
[18:26:25] Checking for Phalanx2 Rootkit...
[18:26:25]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[18:26:25]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[18:26:25]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[18:26:25]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[18:26:25]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[18:26:25]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[18:26:25]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[18:26:25]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[18:26:25]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[18:26:25]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[18:26:25] Phalanx2 Rootkit                                  [ Not found ]
[18:26:25]
[18:26:25] Checking for Phalanx2 Rootkit (extended tests)...
[18:26:25]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[18:26:25]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[18:26:25] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[18:26:25]
[18:26:25] Checking for Portacelo Rootkit...
[18:26:25]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../.p'             [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../getty'          [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../show'           [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[18:26:25]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[18:26:25]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[18:26:25] Portacelo Rootkit                                 [ Not found ]
[18:26:25]
[18:26:25] Checking for R3dstorm Toolkit...
[18:26:25]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[18:26:26]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[18:26:26]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[18:26:26]   Checking for file '/bin/.../see_all'            [ Not found ]
[18:26:26]   Checking for directory '/var/log/tk02'          [ Not found ]
[18:26:26]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[18:26:26]   Checking for directory '/bin/...'               [ Not found ]
[18:26:26] R3dstorm Toolkit                                  [ Not found ]
[18:26:26]
[18:26:26] Checking for RH-Sharpe's Rootkit...
[18:26:26]   Checking for file '/bin/lps'                    [ Not found ]
[18:26:26]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[18:26:26]   Checking for file '/usr/bin/ltop'               [ Not found ]
[18:26:26]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[18:26:26]   Checking for file '/usr/bin/ldu'                [ Not found ]
[18:26:26]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[18:26:26]   Checking for file '/usr/bin/wp'                 [ Not found ]
[18:26:26]   Checking for file '/usr/bin/shad'               [ Not found ]
[18:26:26]   Checking for file '/usr/bin/vadim'              [ Not found ]
[18:26:26]   Checking for file '/usr/bin/slice'              [ Not found ]
[18:26:26]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[18:26:26]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[18:26:26] RH-Sharpe's Rootkit                               [ Not found ]
[18:26:26]
[18:26:26] Checking for RSHA's Rootkit...
[18:26:26]   Checking for file '/bin/kr4p'                   [ Not found ]
[18:26:26]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[18:26:26]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[18:26:26]   Checking for file '/usr/bin/slice2'             [ Not found ]
[18:26:26]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[18:26:26]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[18:26:26]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[18:26:26]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[18:26:26] RSHA's Rootkit                                    [ Not found ]
[18:26:26]
[18:26:26] Checking for Scalper Worm...
[18:26:26]   Checking for file '/tmp/.a'                     [ Not found ]
[18:26:26]   Checking for file '/tmp/.uua'                   [ Not found ]
[18:26:26] Scalper Worm                                      [ Not found ]
[18:26:26]
[18:26:26] Checking for Sebek LKM...
[18:26:26]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[18:26:26] Sebek LKM                                         [ Not found ]
[18:26:26]
[18:26:26] Checking for Shutdown Rootkit...
[18:26:26]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[18:26:26]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[18:26:27]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[18:26:27]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[18:26:27]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[18:26:27]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[18:26:27]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[18:26:27]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[18:26:27] Shutdown Rootkit                                  [ Not found ]
[18:26:27]
[18:26:27] Checking for SHV4 Rootkit...
[18:26:27]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[18:26:27]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[18:26:27]   Checking for file '/lib/lidps1.so'              [ Not found ]
[18:26:27]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[18:26:27]   Checking for directory '/lib/security/.config'  [ Not found ]
[18:26:27]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[18:26:27] SHV4 Rootkit                                      [ Not found ]
[18:26:27]
[18:26:27] Checking for SHV5 Rootkit...
[18:26:27]   Checking for file '/etc/sh.conf'                [ Not found ]
[18:26:27]   Checking for file '/dev/srd0'                   [ Not found ]
[18:26:27]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[18:26:27] SHV5 Rootkit                                      [ Not found ]
[18:26:27]
[18:26:27] Checking for Sin Rootkit...
[18:26:27]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[18:26:27]   Checking for file '/dev/ttyoa'                  [ Not found ]
[18:26:27]   Checking for file '/dev/ttyof'                  [ Not found ]
[18:26:27]   Checking for file '/dev/ttyop'                  [ Not found ]
[18:26:27]   Checking for file '/dev/ttyos'                  [ Not found ]
[18:26:27]   Checking for file '/usr/lib/.lib'               [ Not found ]
[18:26:27]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[18:26:27]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[18:26:27]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[18:26:27]   Checking for file '/usr/man/man1/...'           [ Not found ]
[18:26:27]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[18:26:27]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[18:26:27]   Checking for directory '/usr/lib/sn'            [ Not found ]
[18:26:27]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[18:26:27]   Checking for directory '/dev/.haos'             [ Not found ]
[18:26:27] Sin Rootkit                                       [ Not found ]
[18:26:27]
[18:26:27] Checking for Slapper Worm...
[18:26:27]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[18:26:27]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[18:26:27]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[18:26:27]   Checking for file '/tmp/httpd'                  [ Not found ]
[18:26:27]   Checking for file '/tmp/.unlock'                [ Not found ]
[18:26:27]   Checking for file '/tmp/update'                 [ Not found ]
[18:26:27]   Checking for file '/tmp/.cinik'                 [ Not found ]
[18:26:27]   Checking for file '/tmp/.b'                     [ Not found ]
[18:26:27] Slapper Worm                                      [ Not found ]
[18:26:27]
[18:26:27] Checking for Sneakin Rootkit...
[18:26:27]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[18:26:27] Sneakin Rootkit                                   [ Not found ]
[18:26:27]
[18:26:27] Checking for Suckit Rootkit...
[18:26:27]   Checking for file '/sbin/initsk12'              [ Not found ]
[18:26:27]   Checking for file '/sbin/initxrk'               [ Not found ]
[18:26:27]   Checking for file '/usr/bin/null'               [ Not found ]
[18:26:27]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[18:26:27]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[18:26:27]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[18:26:27]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[18:26:27]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[18:26:28]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[18:26:28]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[18:26:28]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[18:26:28]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[18:26:28]   Checking for directory '/etc/.MG'               [ Not found ]
[18:26:28]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[18:26:28]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[18:26:28] Suckit Rootkit                                    [ Not found ]
[18:26:28]
[18:26:28] Checking for SunOS Rootkit...
[18:26:28]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[18:26:28]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[18:26:28]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[18:26:28]   Checking for file '/bin/xlogin'                 [ Not found ]
[18:26:28]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[18:26:28]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[18:26:28]   Checking for file '/sbin/login'                 [ Not found ]
[18:26:28]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[18:26:28]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[18:26:28]   Checking for file '/dev/kmod'                   [ Not found ]
[18:26:28]   Checking for file '/dev/dos'                    [ Not found ]
[18:26:28] SunOS Rootkit                                     [ Not found ]
[18:26:28]
[18:26:28] Checking for SunOS / NSDAP Rootkit...
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[18:26:28]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[18:26:28]   Checking for file '/usr/lib/lpset'              [ Not found ]
[18:26:28]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[18:26:28] SunOS / NSDAP Rootkit                             [ Not found ]
[18:26:28]
[18:26:28] Checking for Superkit Rootkit...
[18:26:28]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[18:26:28] Superkit Rootkit                                  [ Not found ]
[18:26:28]
[18:26:28] Checking for TBD (Telnet BackDoor)...
[18:26:28]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[18:26:28] TBD (Telnet BackDoor)                             [ Not found ]
[18:26:28]
[18:26:28] Checking for TeLeKiT Rootkit...
[18:26:28]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[18:26:28]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[18:26:28]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[18:26:28]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[18:26:28]   Checking for file '/dev/ptyr'                   [ Not found ]
[18:26:28]   Checking for file '/dev/ptyp'                   [ Not found ]
[18:26:28]   Checking for file '/dev/ptyq'                   [ Not found ]
[18:26:28]   Checking for file '/dev/hda06'                  [ Not found ]
[18:26:28]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[18:26:28]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[18:26:28]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[18:26:28]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[18:26:28] TeLeKiT Rootkit                                   [ Not found ]
[18:26:28]
[18:26:28] Checking for T0rn Rootkit...
[18:26:28]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[18:26:28]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[18:26:28]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[18:26:29]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[18:26:29]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[18:26:29]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[18:26:29]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[18:26:29]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[18:26:29]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[18:26:29]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[18:26:29]   Checking for directory '/dev/.lib'              [ Not found ]
[18:26:29]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[18:26:29]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[18:26:29]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[18:26:29]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[18:26:29]   Checking for directory '/usr/src/.****'         [ Not found ]
[18:26:29]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[18:26:29]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[18:26:29]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[18:26:29]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[18:26:29] T0rn Rootkit                                      [ Not found ]
[18:26:29]
[18:26:29] Checking for Trojanit Kit...
[18:26:29]   Checking for file '/bin/.ls'                    [ Not found ]
[18:26:29]   Checking for file '/bin/.ps'                    [ Not found ]
[18:26:29]   Checking for file '/bin/.netstat'               [ Not found ]
[18:26:29]   Checking for file '/usr/bin/.nop'               [ Not found ]
[18:26:29]   Checking for file '/usr/bin/.who'               [ Not found ]
[18:26:29] Trojanit Kit                                      [ Not found ]
[18:26:29]
[18:26:29] Checking for Tuxtendo Rootkit...
[18:26:29]   Checking for file '/dev/tux/.addr'              [ Not found ]
[18:26:29]   Checking for file '/dev/tux/.cron'              [ Not found ]
[18:26:29]   Checking for file '/dev/tux/.file'              [ Not found ]
[18:26:29]   Checking for file '/dev/tux/.log'               [ Not found ]
[18:26:29]   Checking for file '/dev/tux/.proc'              [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[18:26:29]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[18:26:30]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[18:26:30]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[18:26:30]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[18:26:30]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[18:26:30]   Checking for directory '/dev/tux'               [ Not found ]
[18:26:30]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[18:26:30]   Checking for directory '/dev/tux/backup'        [ Not found ]
[18:26:30] Tuxtendo Rootkit                                  [ Not found ]
[18:26:30]
[18:26:30] Checking for URK Rootkit...
[18:26:30]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[18:26:30]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[18:26:30]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[18:26:30]   Checking for file '/tmp/conf.inf'               [ Not found ]
[18:26:30]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[18:26:30] URK Rootkit                                       [ Not found ]
[18:26:30]
[18:26:30] Checking for Vampire Rootkit...
[18:26:30]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[18:26:30]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[18:26:30]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[18:26:30]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[18:26:30] Vampire Rootkit                                   [ Not found ]
[18:26:30]
[18:26:30] Checking for VcKit Rootkit...
[18:26:30]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[18:26:30]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[18:26:30] VcKit Rootkit                                     [ Not found ]
[18:26:30]
[18:26:30] Checking for Volc Rootkit...
[18:26:30]   Checking for directory '/var/spool/.recent'     [ Not found ]
[18:26:30]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[18:26:30]   Checking for directory '/usr/lib/volc'          [ Not found ]
[18:26:30]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[18:26:30] Volc Rootkit                                      [ Not found ]
[18:26:30]
[18:26:30] Checking for X-Org SunOS Rootkit...
[18:26:30]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[18:26:30]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[18:26:30]   Checking for file '/usr/bin/srload'             [ Not found ]
[18:26:30]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[18:26:30]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[18:26:30]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[18:26:30]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[18:26:30]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[18:26:30]   Checking for directory '/usr/share/man...'      [ Not found ]
[18:26:30] X-Org SunOS Rootkit                               [ Not found ]
[18:26:30]
[18:26:30] Checking for zaRwT.KiT Rootkit...
[18:26:30]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[18:26:30]   Checking for file '/dev/ttyf'                   [ Not found ]
[18:26:30]   Checking for file '/dev/ttyp'                   [ Not found ]
[18:26:30]   Checking for file '/dev/ttyn'                   [ Not found ]
[18:26:30]   Checking for file '/rk/tulz'                    [ Not found ]
[18:26:30]   Checking for directory '/rk'                    [ Not found ]
[18:26:30]   Checking for directory '/dev/rd/s'              [ Not found ]
[18:26:31] zaRwT.KiT Rootkit                                 [ Not found ]
[18:26:31]
[18:26:31] Performing additional rootkit checks
[18:26:31] Info: Starting test name 'additional_rkts'
[18:26:31]
[18:26:31]   Performing Suckit Rookit additional checks
[18:26:31]     Checking hard link count on '/sbin/init'      [ OK ]
[18:26:31]     Checking for hidden file extensions           [ None found ]
[18:26:31]     Running skdet command                         [ Skipped ]
[18:26:31] Info: Unable to find the 'skdet' command
[18:26:31]   Suckit Rookit additional checks                 [ OK ]
[18:26:31]
[18:26:31]   Performing check of possible rootkit files and directories
[18:26:31] Info: Starting test name 'possible_rkt_files'
[18:26:31]     Checking for file '/dev/sdr0'                 [ Not found ]
[18:26:31]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[18:26:31]     Checking for file '/tmp/.bash_history'        [ Not found ]
[18:26:31]     Checking for file '/usr/info/.clib'           [ Not found ]
[18:26:31]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[18:26:31]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[18:26:31]     Checking for file '/sbin/create'              [ Not found ]
[18:26:31]     Checking for file '/dev/ttypz'                [ Not found ]
[18:26:31]     Checking for directory '/usr/bin/take'        [ Not found ]
[18:26:31]     Checking for directory '/usr/src/.lib'        [ Not found ]
[18:26:31]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[18:26:31]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[18:26:31]     Checking for directory '/usr/sbin/...'        [ Not found ]
[18:26:31]     Checking for directory '/usr/share/.gun'      [ Not found ]
[18:26:31]   Checking for possible rootkit files and directories [ None found ]
[18:26:31]
[18:26:31]   Performing check for possible rootkit strings
[18:26:31] Info: Starting test name 'possible_rkt_strings'
[18:26:31] Info: Using system startup paths: /etc/rc.local /etc/init.d
[18:26:31]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[18:26:31]     Checking for string '****'                    [ Not found ]
[18:26:31]     Checking for string 'backdoor'                [ Not found ]
[18:26:31]     Checking for string 'vt200'                   [ Not found ]
[18:26:31]     Checking for string '/usr/bin/xstat'          [ Not found ]
[18:26:31]     Checking for string '/bin/envpc'              [ Not found ]
[18:26:31]     Checking for string 'L4m3r0x'                 [ Not found ]
[18:26:31]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[18:26:31]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[18:26:31]     Checking for string '/dev/sgk'                [ Not found ]
[18:26:31]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[18:26:31]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[18:26:31]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[18:26:31]     Checking for string '/lib/.sso'               [ Not found ]
[18:26:31]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[18:26:31]     Checking for string '/dev/caca'               [ Not found ]
[18:26:32]     Checking for string '/dev/ttyoa'              [ Not found ]
[18:26:32]     Checking for string 'syg'                     [ Not found ]
[18:26:32]     Checking for string '/dev/pts/01'             [ Not found ]
[18:26:32]     Checking for string 'tw33dl3'                 [ Not found ]
[18:26:32]     Checking for string 'psniff'                  [ Not found ]
[18:26:32]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[18:26:32]     Checking for string '/dev/xdta'               [ Not found ]
[18:26:32]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[18:26:32]     Checking for string 'in.inetd'                [ Not found ]
[18:26:32]     Checking for string '#<HIDE_.*>'              [ Not found ]
[18:26:32]     Checking for string 'bin/xchk'                [ Not found ]
[18:26:32]     Checking for string 'bin/xsf'                 [ Not found ]
[18:26:32]   Checking for possible rootkit strings           [ None found ]
[18:26:32]
[18:26:32] Performing malware checks
[18:26:32] Info: Starting test name 'malware'
[18:26:32]
[18:26:32] Info: Test 'deleted_files' disabled at users request.
[18:26:32] Info: Starting test name 'running_procs'
[18:26:33]   Checking running processes for suspicious files [ None found ]
[18:26:33]
[18:26:33] Info: Test 'hidden_procs' disabled at users request.
[18:26:33]
[18:26:33] Info: Test 'suspscan' disabled at users request.
[18:26:33]
[18:26:33]   Performing check for login backdoors
[18:26:33] Info: Starting test name 'other_malware'
[18:26:33]     Checking for '/bin/.login'                    [ Not found ]
[18:26:33]     Checking for '/sbin/.login'                   [ Not found ]
[18:26:33]   Checking for login backdoors                    [ None found ]
[18:26:33]
[18:26:33]   Performing check for suspicious directories
[18:26:33]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[18:26:33]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[18:26:33]   Checking for suspicious directories             [ None found ]
[18:26:33]
[18:26:33]   Checking for software intrusions                [ Skipped ]
[18:26:33] Info: Check skipped - tripwire not installed
[18:26:33]
[18:26:33]   Performing check for sniffer log files
[18:26:33]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[18:26:33]   Checking for sniffer log files                  [ None found ]
[18:26:33]
[18:26:33] Performing trojan specific checks
[18:26:33] Info: Starting test name 'trojans'
[18:26:33] Info: Using inetd configuration file '/etc/inetd.conf'
[18:26:33]   Checking for enabled inetd services             [ OK ]
[18:26:33]
[18:26:33]   Performing check for enabled xinetd services
[18:26:33]   Checking for enabled xinetd services            [ Skipped ]
[18:26:33] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[18:26:33] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[18:26:33]
[18:26:33] Performing Linux specific checks
[18:26:33] Info: Starting test name 'os_specific'
[18:26:33]   Checking loaded kernel modules                  [ OK ]
[18:26:33] Info: Using modules pathname of '/lib/modules/2.6.31-15-generic'
[18:26:33]   Checking kernel module names                    [ OK ]
[18:26:38]
[18:26:38] Checking the network...
[18:26:38] Info: Starting test name 'network'
[18:26:38] Info: Starting test name 'ports'
[18:26:38]
[18:26:38] Performing check for backdoor ports
[18:26:38]   Checking for UDP port 2001                      [ Not found ]
[18:26:38]   Checking for TCP port 2006                      [ Not found ]
[18:26:38]   Checking for TCP port 2128                      [ Not found ]
[18:26:38]   Checking for TCP port 14856                     [ Not found ]
[18:26:39]   Checking for TCP port 47107                     [ Not found ]
[18:26:39]   Checking for TCP port 60922                     [ Not found ]
[18:26:39]
[18:26:39] Performing checks on the network interfaces
[18:26:39] Info: Starting test name 'promisc'
[18:26:39]   Checking for promiscuous interfaces             [ None found ]
[18:26:39]
[18:26:39] Info: Test 'packet_cap_apps' disabled at users request.
[18:26:40]
[18:26:40] Checking the local host...
[18:26:40] Info: Starting test name 'local_host'
[18:26:40]
[18:26:40] Performing system boot checks
[18:26:40] Info: Starting test name 'startup_files'
[18:26:40]   Checking for local host name                    [ Found ]
[18:26:40] Info: Starting test name 'startup_malware'
[18:26:40]   Checking for system startup files               [ Found ]
[18:26:41]   Checking system startup files for malware       [ None found ]
[18:26:41]
[18:26:41] Performing group and account checks
[18:26:41] Info: Starting test name 'group_accounts'
[18:26:41]   Checking for passwd file                        [ Found ]
[18:26:41] Info: Found password file: /etc/passwd
[18:26:41]   Checking for root equivalent (UID 0) accounts   [ None found ]
[18:26:41] Info: Found shadow file: /etc/shadow
[18:26:41]   Checking for passwordless accounts              [ None found ]
[18:26:41] Info: Starting test name 'passwd_changes'
[18:26:41]   Checking for passwd file changes                [ None found ]
[18:26:41] Info: Starting test name 'group_changes'
[18:26:41]   Checking for group file changes                 [ None found ]
[18:26:41]   Checking root account shell history files       [ None found ]
[18:26:41]
[18:26:41] Performing system configuration file checks
[18:26:41] Info: Starting test name 'system_configs'
[18:26:41]   Checking for SSH configuration file             [ Not found ]
[18:26:41]   Checking for running syslog daemon              [ Found ]
[18:26:41]   Checking for syslog configuration file          [ Found ]
[18:26:41] Info: Found syslog configuration file: /etc/rsyslog.conf
[18:26:41]   Checking if syslog remote logging is allowed    [ Not allowed ]
[18:26:41]
[18:26:41] Performing filesystem checks
[18:26:41] Info: Starting test name 'filesystem'
[18:26:41] Info: SCAN_MODE_DEV set to 'THOROUGH'
[B][18:26:41]   Checking /dev for suspicious file types         [ Warning ]
[18:26:41] Warning: Suspicious file types found in /dev:
[18:26:41]          /dev/shm/mono.2618: data
[18:26:41]          /dev/shm/pulse-shm-3622762530: data
[18:26:41]          /dev/shm/pulse-shm-3683134618: data
[18:26:41]          /dev/shm/pulse-shm-1052885481: data
[18:26:41]          /dev/shm/pulse-shm-3233297422: data
[18:26:41]          /dev/shm/pulse-shm-3326625707: data
[18:26:41]   Checking for hidden files and directories       [ Warning ]
[18:26:41] Warning: Hidden directory found: /etc/.java
[18:26:41] Warning: Hidden directory found: /dev/.udev
[18:26:41] Warning: Hidden directory found: /dev/.initramfs[/B]
[18:26:46]
[18:26:46] Checking application versions...
[18:26:47] Info: Starting test name 'apps'
[18:26:47]   Checking version of Exim MTA                    [ OK ]
[18:26:47] Info: Application 'exim' version '4.69' found.
[18:26:47]   Checking version of GnuPG                       [ OK ]
[18:26:47] Info: Application 'gpg' version '1.4.9' found.
[18:26:47] Info: Application 'httpd' not found.
[18:26:47] Info: Application 'named' not found.
[18:26:47]   Checking version of OpenSSL                     [ OK ]
[18:26:47] Info: Application 'openssl' version '0.9.8g' found.
[18:26:47] Info: Application 'php' not found.
[18:26:47] Info: Application 'procmail' not found.
[18:26:47] Info: Application 'proftpd' not found.
[18:26:47] Info: Application 'sshd' not found.
[18:26:47] Info: Applications checked: 3 out of 9
[18:26:47]
[18:26:47] System checks summary
[18:26:47] =====================
[18:26:47]
[18:26:47] File properties checks...
[18:26:47] Files checked: 128
**[18:26:47] Suspect files: 5**
[18:26:47]
[18:26:47] Rootkit checks...
[18:26:47] Rootkits checked : 111
**[18:26:47] Possible rootkits: 0**
[18:26:47]
[18:26:47] Applications checks...
[18:26:47] Applications checked: 3
[18:26:47] Suspect applications: 0
[18:26:47]
[18:26:47] The system checks took: 42 seconds
[18:26:47]
[18:26:47] Info: End date is Thu Nov 26 18:26:47 EST 2009
```

Is this a problem?

---

### Post by The Funkbomb on 2009-11-27
bump

---

### Post by Sin@Sin-Sacrifice on 2009-11-27
Try chkrootkit and see if you get the same hits. If not then it may be a false positive. If you do then you have to figure out if it's something you or a program you installed changed. Or if it is malicious.

---

### Post by rAffe_on_the_run on 2009-12-10
Hello all,

I just ran rkhunter as well (sudo rkhunter --check --pkgmgr dpkg) and got nearly the same warning message about:

Warning: Suspicious file types found in /dev:
   ...
   /dev/shm/mono.2743: data
   ...


Now I am googling away but can't find any clues about this certain warning.
I' just beginning to understand Linux security.
I am running Ubuntu 9.10 with rkhunter 1.3.4.

After running rkhunter, I ran chkrootkit and it did'nt complain.

Where can I get further information?

---

