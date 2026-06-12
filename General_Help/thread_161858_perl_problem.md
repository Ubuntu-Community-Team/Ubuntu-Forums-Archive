---
title: "perl problem"
date: 2006-04-17
forum: General Help
---

### Post by tgone on 2006-04-17
Hello,

I'm trying to install a Perl module but I'm getting the following error:

```
ubuntu@ubuntu:~/Desktop/HTML-Parser-3.51$ perl Makefile.PL
Writing Makefile for HTML::Parser
ubuntu@ubuntu:~/Desktop/HTML-Parser-3.51$ make
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"3.51\" -DXS_VERSION=\"3.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -DMARKED_SECTION Parser.c
In file included from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perl.h:382:24: error: sys/types.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:413:19: error: ctype.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:425:23: error: locale.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:442:20: error: setjmp.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:448:26: error: sys/param.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:453:23: error: stdlib.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:458:23: error: unistd.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:731:23: error: string.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:880:27: error: netinet/in.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:884:26: error: arpa/inet.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:894:25: error: sys/stat.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:916:21: error: time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:923:25: error: sys/time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:930:27: error: sys/times.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:937:19: error: errno.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:952:25: error: sys/socket.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:979:21: error: netdb.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1081:24: error: sys/ioctl.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1110:23: error: dirent.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:11,
                 from /usr/lib/perl/5.8/CORE/perl.h:1446,
                 from Parser.xs:19:
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2056,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/handy.h:121:25: error: inttypes.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2220,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/unixish.h:106:21: error: signal.h: No such file or directory
In file included from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perl.h:2322:33: error: pthread.h: No such file or directory
In file included from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perl.h:2324: error: syntax error before ‘perl_os_thread’
/usr/lib/perl/5.8/CORE/perl.h:2324: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:2325: error: syntax error before ‘perl_mutex’
/usr/lib/perl/5.8/CORE/perl.h:2325: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:2326: error: syntax error before ‘perl_cond’
/usr/lib/perl/5.8/CORE/perl.h:2326: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:2327: error: syntax error before ‘perl_key’
/usr/lib/perl/5.8/CORE/perl.h:2327: warning: data definition has no type or storage class
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2579,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perlio.h:65:19: error: stdio.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2579,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perlio.h:253: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/perlio.h:256: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/perlio.h:256: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perlio.h:259: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/perlio.h:259: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perlio.h:262: error: syntax error before ‘FILE’
In file included from /usr/lib/perl/5.8/CORE/perl.h:2593,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/sv.h:389: error: syntax error before ‘DIR’
/usr/lib/perl/5.8/CORE/sv.h:389: warning: no semicolon at end of struct or union
/usr/lib/perl/5.8/CORE/sv.h:389: warning: no semicolon at end of struct or union
/usr/lib/perl/5.8/CORE/sv.h:391: error: syntax error before ‘}’ token
/usr/lib/perl/5.8/CORE/sv.h:391: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/sv.h:405: error: syntax error before ‘}’ token
In file included from /usr/lib/perl/5.8/CORE/op.h:496,
                 from /usr/lib/perl/5.8/CORE/perl.h:2600,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/reentr.h:71:20: error: pwd.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:74:20: error: grp.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:84:26: error: crypt.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:89:27: error: shadow.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/op.h:496,
                 from /usr/lib/perl/5.8/CORE/perl.h:2600,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/reentr.h:611: error: field ‘_crypt_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:619: error: field ‘_drand48_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:623: error: field ‘_grent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:634: error: field ‘_hostent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:653: error: field ‘_netent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:668: error: field ‘_protoent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:683: error: field ‘_pwent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:694: error: field ‘_servent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:709: error: field ‘_spent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:720: error: field ‘_gmtime_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:723: error: field ‘_localtime_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:770: error: field ‘_random_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:771: error: syntax error before ‘int32_t’
/usr/lib/perl/5.8/CORE/reentr.h:771: warning: no semicolon at end of struct or union
/usr/lib/perl/5.8/CORE/reentr.h:779: error: syntax error before ‘}’ token
/usr/lib/perl/5.8/CORE/reentr.h:779: warning: data definition has no type or storage class
In file included from /usr/lib/perl/5.8/CORE/perl.h:2602,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/av.h:13: error: syntax error before ‘ssize_t’
/usr/lib/perl/5.8/CORE/av.h:13: warning: no semicolon at end of struct or union
/usr/lib/perl/5.8/CORE/av.h:14: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/av.h:23: error: syntax error before ‘}’ token
In file included from /usr/lib/perl/5.8/CORE/perl.h:2605,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/scope.h:232: error: syntax error before ‘sigjmp_buf’
/usr/lib/perl/5.8/CORE/scope.h:232: warning: no semicolon at end of struct or union
/usr/lib/perl/5.8/CORE/scope.h:239: error: syntax error before ‘}’ token
In file included from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perl.h:2777: error: syntax error before ‘getuid’
/usr/lib/perl/5.8/CORE/perl.h:2777: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:2778: error: syntax error before ‘geteuid’
/usr/lib/perl/5.8/CORE/perl.h:2778: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:2779: error: syntax error before ‘getgid’
/usr/lib/perl/5.8/CORE/perl.h:2779: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:2780: error: syntax error before ‘getegid’
/usr/lib/perl/5.8/CORE/perl.h:2780: warning: data definition has no type or storage class
In file included from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perl.h:3093:22: error: math.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:3732,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/thrdvar.h:85: error: field ‘Tstatbuf’ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:86: error: field ‘Tstatcache’ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:91: error: field ‘Ttimesbuf’ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:140: error: field ‘Tstart_env’ has incomplete type
In file included from /usr/lib/perl/5.8/CORE/perl.h:3734,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: syntax error before ‘time_t’
/usr/lib/perl/5.8/CORE/intrpvar.h:66: warning: no semicolon at end of struct or union
/usr/lib/perl/5.8/CORE/intrpvar.h:237: error: syntax error before ‘Iuid’
/usr/lib/perl/5.8/CORE/intrpvar.h:237: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:238: error: syntax error before ‘Ieuid’
/usr/lib/perl/5.8/CORE/intrpvar.h:238: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:239: error: syntax error before ‘Igid’
/usr/lib/perl/5.8/CORE/intrpvar.h:239: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:240: error: syntax error before ‘Iegid’
/usr/lib/perl/5.8/CORE/intrpvar.h:240: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:497: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:497: warning: data definition has no type or storage classIn file included from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perl.h:3740: error: syntax error before ‘}’ token
In file included from /usr/lib/perl/5.8/CORE/perl.h:3811,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/proto.h:90: error: syntax error before ‘mode_t’
/usr/lib/perl/5.8/CORE/proto.h:199: error: syntax error before ‘off64_t’
/usr/lib/perl/5.8/CORE/proto.h:201: error: syntax error before ‘Perl_do_sysseek’
/usr/lib/perl/5.8/CORE/proto.h:201: error: syntax error before ‘off64_t’
/usr/lib/perl/5.8/CORE/proto.h:201: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:202: error: syntax error before ‘Perl_do_tell’
/usr/lib/perl/5.8/CORE/proto.h:202: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:284: error: syntax error before ‘gid_t’
/usr/lib/perl/5.8/CORE/proto.h:456: error: syntax error before ‘Perl_my_fork’
/usr/lib/perl/5.8/CORE/proto.h:456: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:582: error: syntax error before ‘pid_t’
/usr/lib/perl/5.8/CORE/proto.h:815: error: syntax error before ‘pid_t’
/usr/lib/perl/5.8/CORE/proto.h:916: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/proto.h:916: error: syntax error before ‘DIR’
/usr/lib/perl/5.8/CORE/proto.h:916: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:1305: error: syntax error before ‘Perl_PerlIO_read’
/usr/lib/perl/5.8/CORE/proto.h:1305: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:1306: error: syntax error before ‘Perl_PerlIO_write’
/usr/lib/perl/5.8/CORE/proto.h:1306: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:1307: error: syntax error before ‘Perl_PerlIO_unread’
/usr/lib/perl/5.8/CORE/proto.h:1307: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:1308: error: syntax error before ‘Perl_PerlIO_tell’
/usr/lib/perl/5.8/CORE/proto.h:1308: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/proto.h:1309: error: syntax error before ‘off64_t’
In file included from /usr/lib/perl/5.8/CORE/perl.h:3849,
                 from Parser.xs:19:
/usr/lib/perl/5.8/CORE/perlvars.h:31: error: syntax error before ‘PL_thr_key’
/usr/lib/perl/5.8/CORE/perlvars.h:31: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perlvars.h:48: error: syntax error before ‘PL_op_mutex’
/usr/lib/perl/5.8/CORE/perlvars.h:48: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perlvars.h:52: error: syntax error before ‘PL_dollarzero_mutex’
/usr/lib/perl/5.8/CORE/perlvars.h:52: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perl.h:4366:24: error: sys/ipc.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:4367:24: error: sys/sem.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:4492:24: error: sys/file.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:37,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:320,
                 from Parser.xs:20:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:66: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/intrpvar.h:237: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:237: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:238: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:238: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:239: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:239: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:240: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:240: warning: data definition has no type or storage class/usr/lib/perl/5.8/CORE/intrpvar.h:497: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:497: warning: data definition has no type or storage classIn file included from /usr/lib/perl/5.8/CORE/perlapi.h:38,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:320,
                 from Parser.xs:20:
/usr/lib/perl/5.8/CORE/perlvars.h:31: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/perlvars.h:31: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perlvars.h:48: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/perlvars.h:48: warning: data definition has no type or storage class
/usr/lib/perl/5.8/CORE/perlvars.h:52: error: syntax error before ‘*’ token
/usr/lib/perl/5.8/CORE/perlvars.h:52: warning: data definition has no type or storage class
In file included from Parser.xs:114:
util.c: In function ‘grow_gap’:
util.c:60: warning: incompatible implicit declaration of built-in function ‘memmove’
util.c: In function ‘decode_entities’:
util.c:106: warning: incompatible implicit declaration of built-in function ‘strchr’
In file included from Parser.xs:115:
hparser.c: In function ‘report_event’:
hparser.c:192: warning: incompatible implicit declaration of built-in function ‘strlen’
Parser.xs: In function ‘XS_HTML__Parser__alloc_pstate’:
Parser.xs:232: warning: incompatible implicit declaration of built-in function ‘memset’
make: *** [Parser.o] Error 1

```

I have no idea what this means and I've tried searching Google with no luck. Any ideas? I just installed GCC so maybe I need to configure it?

---

### Post by dickohead on 2006-04-17
sudo make?

---

### Post by tgone on 2006-04-18
I tried sudo make and I still have the same error...

---

### Post by tgone on 2006-04-18
nevermind, i fixed it by installing some more gcc packages

---

### Post by bapple03 on 2006-06-25
I'm having the same problem.  What packages did you install to fix the issue?

---

### Post by exilist on 2006-08-22
this should help:
apt-get install libc6-dev

---

