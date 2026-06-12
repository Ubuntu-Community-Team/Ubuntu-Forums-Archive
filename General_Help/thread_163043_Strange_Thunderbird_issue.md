---
title: "Strange Thunderbird issue"
date: 2006-04-20
forum: General Help
---

### Post by gorgor_bay on 2006-04-20
Here is my problem, I spent hours browsing around and trying to find an answer, but I found nothing. So here I come :

I'm using since a few months Thunderbird both on Linux and Windows with a shared profile folder.
This morning, I launched Thunderbird under Windows. Once back to Ubuntu, Thunderbird doesn't want to launch anymore. The error message is :
```
selected locale: fr-FR
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 *** Failed to load overlay chrome://spf/content/spf.xul
*** Failed to load overlay chrome://spf/content/statusoverlay.xul
```
I'm using Breezy for amd64 k8, and the Windows Thunderbird version is 1.5 whereas the Ubuntu one is 1.0
Everything went fine until today, I had many switched between Linux & Windows, but this time all went wrong.
I still can access my mails under Windows but this is highly upseting as I wish I could use Windows as few as possible.

Here is a screenshot of Thuderbird stuck :
[[img=http://img85.imageshack.us/img85/4869/capture8fr.th.png]](http://img85.imageshack.us/my.php?image=capture8fr.png)

I tryed backing up my profle under windows, reinstalling it.
I tryed uninstalling Thunderbird under Ubuntu, reinstalling it and going through the profile exchange process again.
I checked the character encoding also...

Anybody has a hint ?

---

### Post by oberoc on 2006-04-20
See if this mailing list post assists you in solving your problem:
[http://linuxfromscratch.org/pipermail/blfs-support/2004-March/049052.html](http://linuxfromscratch.org/pipermail/blfs-support/2004-March/049052.html)

-Tino

---

### Post by gorgor_bay on 2006-04-20
I allready saw this page while browsing for a solution. They do talk about a different chrome issue, and the way to solve it is changing the permissions on the files in the chrome folder... I did it but nothing changed

---

### Post by oberoc on 2006-04-20
When was the last time that you used this in linux? And what, if any, system updates happened on your Windows and/or Linux side? Very rarely does the sw break for no reason. Also, do an strace on the thunderbird process, that might shed some light on it.

-Tino

---

### Post by oberoc on 2006-04-20
Two avenues to explore down:

What if any Windows/Linux updates have happened since the last successful running of Thunderbird on the Linux side?

Do an strace of the Thunderbird app and see where it chokes.

-Tino

---

### Post by gorgor_bay on 2006-04-20
[QUOTE=oberoc]When was the last time that you used this in linux?
[/QUOTE]

Last time I used Thunderbird in Linux was yesterday night.

[QUOTE=oberoc]what, if any, system updates happened on your Windows and/or Linux side?
-Tino[/QUOTE]

No system update since yesterday on Linux. 
But I did applied the latest windows updates since I last used Thunderbird in Windows.

Here comes the strace : 
```
execve("/usr/bin/mozilla-thunderbird", ["mozilla-thunderbird"], [/* 30 vars */]) = 0
uname({sys="Linux", node="laptop", ...}) = 0
brk(0)                                  = 0x5c1000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac1000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=59060, ...}) = 0
mmap(NULL, 59060, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libncurses.so.5", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \372\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=373480, ...}) = 0
mmap(NULL, 1423696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaabc3000
mprotect(0x2aaaaac10000, 1108304, PROT_NONE) = 0
mmap(0x2aaaaad10000, 57344, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4d000) = 0x2aaaaad10000
mmap(0x2aaaaad1e000, 2384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaaad1e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libdl.so.2", O_RDONLY)       = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\17\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=10376, ...}) = 0
mmap(NULL, 1056984, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaad1f000
mprotect(0x2aaaaad21000, 1048792, PROT_NONE) = 0
mmap(0x2aaaaae20000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x2aaaaae20000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\305\1\0"..., 640) = 640
lseek(3, 624, SEEK_SET)                 = 624
read(3, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\6\0\0\0"..., 32) = 32
fstat(3, {st_mode=S_IFREG|0644, st_size=1262872, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaae22000
mmap(NULL, 2322312, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaae23000
mprotect(0x2aaaaaf51000, 1085320, PROT_NONE) = 0
mmap(0x2aaaab050000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12d000) = 0x2aaaab050000
mmap(0x2aaaab056000, 16264, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaab056000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab05a000
mprotect(0x2aaaab050000, 12288, PROT_READ) = 0
arch_prctl(ARCH_SET_FS, 0x2aaaab05a6d0) = 0
munmap(0x2aaaaaac3000, 59060)           = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
open("/dev/tty", O_RDWR|O_NONBLOCK)     = 3
close(3)                                = 0
open("/usr/lib/locale/locale-archive", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1677952, ...}) = 0
mmap(NULL, 1677952, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaab05b000
close(3)                                = 0
brk(0)                                  = 0x5c1000
brk(0x5c2000)                           = 0x5c2000
brk(0x5c3000)                           = 0x5c3000
brk(0x5c4000)                           = 0x5c4000
getuid()                                = 1000
getgid()                                = 1000
geteuid()                               = 1000
getegid()                               = 1000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x5c5000)                           = 0x5c5000
open("/etc/mtab", O_RDONLY)             = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=700, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab1f5000
read(3, "/dev/hda8 / ext3 rw,errors=remou"..., 4096) = 700
close(3)                                = 0
munmap(0x2aaaab1f5000, 4096)            = 0
open("/proc/meminfo", O_RDONLY)         = 3
fstat(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab1f5000
read(3, "MemTotal:      1021084 kB\nMemFre"..., 1024) = 604
close(3)                                = 0
munmap(0x2aaaab1f5000, 4096)            = 0
brk(0x5c6000)                           = 0x5c6000
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigaction(SIGQUIT, {SIG_IGN}, {SIG_DFL}, 8) = 0
uname({sys="Linux", node="laptop", ...}) = 0
brk(0x5c7000)                           = 0x5c7000
brk(0x5c8000)                           = 0x5c8000
stat("/home/leo", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
getpid()                                = 8652
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
brk(0x5c9000)                           = 0x5c9000
open("/usr/lib/gconv/gconv-modules", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=45568, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab1f5000
read(3, "# GNU libc iconv configuration.\n"..., 4096) = 4096
brk(0x5ca000)                           = 0x5ca000
brk(0x5cb000)                           = 0x5cb000
read(3, "lias\tJS//\t\t\tJUS_I.B1.002//\nalias"..., 4096) = 4096
brk(0x5cc000)                           = 0x5cc000
brk(0x5cd000)                           = 0x5cd000
brk(0x5ce000)                           = 0x5ce000
read(3, "ule\tINTERNAL\t\tISO-8859-3//\t\tISO8"..., 4096) = 4096
brk(0x5cf000)                           = 0x5cf000
brk(0x5d0000)                           = 0x5d0000
brk(0x5d1000)                           = 0x5d1000
brk(0x5d2000)                           = 0x5d2000
read(3, "lias\tISO-IR-199//\t\tISO-8859-14//"..., 4096) = 4096
brk(0x5d3000)                           = 0x5d3000
brk(0x5d4000)                           = 0x5d4000
brk(0x5d5000)                           = 0x5d5000
read(3, "\t\tto\t\t\tmodule\t\tcost\nalias\tCSEBCD"..., 4096) = 4096
brk(0x5d6000)                           = 0x5d6000
brk(0x5d7000)                           = 0x5d7000
brk(0x5d8000)                           = 0x5d8000
read(3, "ule\t\tcost\nalias\tCP284//\t\t\tIBM284"..., 4096) = 4096
brk(0x5d9000)                           = 0x5d9000
brk(0x5da000)                           = 0x5da000
brk(0x5db000)                           = 0x5db000
brk(0x5dc000)                           = 0x5dc000
read(3, "lias\tCP864//\t\t\tIBM864//\nalias\t86"..., 4096) = 4096
brk(0x5dd000)                           = 0x5dd000
brk(0x5de000)                           = 0x5de000
brk(0x5df000)                           = 0x5df000
read(3, "module\tIBM937//\t\tINTERNAL\t\tIBM93"..., 4096) = 4096
brk(0x5e0000)                           = 0x5e0000
brk(0x5e1000)                           = 0x5e1000
brk(0x5e2000)                           = 0x5e2000
brk(0x5e3000)                           = 0x5e3000
read(3, "\tEUC-JP//\nalias\tUJIS//\t\t\tEUC-JP/"..., 4096) = 4096
brk(0x5e4000)                           = 0x5e4000
brk(0x5e5000)                           = 0x5e5000
brk(0x5e6000)                           = 0x5e6000
read(3, "module\t\tcost\nalias\tISO-IR-143//\t"..., 4096) = 4096
brk(0x5e7000)                           = 0x5e7000
brk(0x5e8000)                           = 0x5e8000
brk(0x5e9000)                           = 0x5e9000
read(3, "-BOX//\nmodule\tISO_10367-BOX//\t\tI"..., 4096) = 4096
brk(0x5ea000)                           = 0x5ea000
brk(0x5eb000)                           = 0x5eb000
brk(0x5ec000)                           = 0x5ec000
read(3, "module\tINTERNAL\t\tEUC-JISX0213//\t"..., 4096) = 512
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x2aaaab1f5000, 4096)            = 0
brk(0x5ed000)                           = 0x5ed000
open("/usr/lib/gconv/ISO8859-1.so", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\6\0\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=10144, ...}) = 0
brk(0x5ee000)                           = 0x5ee000
mmap(NULL, 1056832, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab1f5000
mprotect(0x2aaaab1f7000, 1048640, PROT_NONE) = 0
mmap(0x2aaaab2f6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x2aaaab2f6000
close(3)                                = 0
getppid()                               = 8651
brk(0x5ef000)                           = 0x5ef000
brk(0x5f0000)                           = 0x5f0000
getpgrp()                               = 8651
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
open("/usr/bin/mozilla-thunderbird", O_RDONLY) = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffffc85a10) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "#!/bin/bash\n#\n# The contents of "..., 80) = 80
lseek(3, 0, SEEK_SET)                   = 0
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
dup2(3, 255)                            = 255
close(3)                                = 0
fcntl(255, F_SETFD, FD_CLOEXEC)         = 0
fcntl(255, F_GETFL)                     = 0x8000 (flags O_RDONLY|O_LARGEFILE)
fstat(255, {st_mode=S_IFREG|0755, st_size=10584, ...}) = 0
lseek(255, 0, SEEK_CUR)                 = 0
brk(0x5f2000)                           = 0x5f2000
brk(0x5f3000)                           = 0x5f3000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "#!/bin/bash\n#\n# The contents of "..., 8176) = 8176
brk(0x5f4000)                           = 0x5f4000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x5f5000)                           = 0x5f5000
brk(0x5f6000)                           = 0x5f6000
brk(0x5f7000)                           = 0x5f7000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x5f8000)                           = 0x5f8000
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -5722, SEEK_CUR)             = 2454
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8653
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8653
wait4(-1, 0x7fffffc84fc4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "/usr/bin\n", 128)              = 9
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "progbase=`basename \"$progname\"`\n"..., 8176) = 8130
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -8098, SEEK_CUR)             = 2486
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8654
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8654
wait4(-1, 0x7fffffc84fc4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "mozilla-thunderbird\n", 128)   = 20
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "run_moz=\"$curdir/run-mozilla.sh\""..., 8176) = 8098
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x5f9000)                           = 0x5f9000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/usr/bin/run-mozilla.sh", 0x7fffffc85110) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -7587, SEEK_CUR)             = 2997
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8655
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8655
wait4(-1, 0x7fffffc84194, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "/home/leo\n", 128)             = 10
brk(0x5fa000)                           = 0x5fa000
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
lstat("/usr/bin/mozilla-thunderbird", {st_mode=S_IFREG|0755, st_size=10584, ...}) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
stat("/home", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/home/leo", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
chdir("/home/leo")                      = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "if [ $found = 0 ]; then\n  # Chec"..., 8176) = 7587
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/usr/lib/mozilla-thunderbird/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10989, ...}) = 0
open("/proc/sys/kernel/ngroups_max", O_RDONLY) = 3
read(3, "65536\n", 31)                  = 6
close(3)                                = 0
brk(0x67a000)                           = 0x67a000
getgroups(65536, [4, 20, 24, 25, 29, 30, 44, 46, 104, 105, 106, 1000]) = 12
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -6693, SEEK_CUR)             = 3891
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8656
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "0\n", 128)                     = 2
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8656
wait4(-1, 0x7fffffc850d4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 2
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "\n###############################"..., 8176) = 6693
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -5673, SEEK_CUR)             = 4911
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8663
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, NULL) = 8663
wait4(-1, 0x7fffffc84ce4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "0\n", 128)                     = 2
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8664
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, NULL) = 8664
wait4(-1, 0x7fffffc84914, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "0\n", 128)                     = 2
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "################################"..., 8176) = 5673
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -4147, SEEK_CUR)             = 6437
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8665
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, NULL) = 8665
wait4(-1, 0x7fffffc850d4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "for i in $HOOKS; do\n  $i\ndone\n\n\n"..., 8176) = 4147
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x67b000)                           = 0x67b000
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0

```

---

### Post by gorgor_bay on 2006-04-20
And the rest of the strace :

```
lseek(255, -3908, SEEK_CUR)             = 6676
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8667
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "en:US\nfr:FR\n", 128)          = 12
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8667
wait4(-1, 0x7fffffc85064, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "DEFAULT_LOCALE=$(cat $LOCALES_DI"..., 8176) = 3908
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -3826, SEEK_CUR)             = 6758
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8671
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "en:US\n", 128)                 = 6
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8671
wait4(-1, 0x7fffffc85064, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "                                "..., 8176) = 3826
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -2974, SEEK_CUR)             = 7610
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8676
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8676
wait4(-1, 0x7fffffc83154, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "en\n", 128)                    = 3
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8677
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8677
wait4(-1, 0x7fffffc83174, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "US\n", 128)                    = 3
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8678
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, NULL) = 8678
wait4(-1, 0x7fffffc83bd4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "\n", 128)                      = 1
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8679
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8679
wait4(-1, 0x7fffffc83154, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "fr\n", 128)                    = 3
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8680
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8680
wait4(-1, 0x7fffffc83174, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "FR\n", 128)                    = 3
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8681
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 8681
wait4(-1, 0x7fffffc83bd4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0)                         = 0
rt_sigaction(SIGCHLD, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, {0x434aa0, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
close(4)                                = 0
read(3, "fr_FR\n", 128)                 = 6
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "                                "..., 8176) = 2974
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
write(1, "selected locale: fr-FR\n", 23) = 23
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x67c000)                           = 0x67c000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x67d000)                           = 0x67d000
open("/usr/lib/mozilla-thunderbird/init.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = -1 ENOENT (No such file or directory)
open("/home/leo/.mozilla-thunderbird/init.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/usr/lib/mozilla-thunderbird/init.d/S*", 0x7fffffc83b50) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/home/leo/.mozilla-thunderbird/init.d/S*", 0x7fffffc83b50) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x67e000)                           = 0x67e000
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -92, SEEK_CUR)               = 10492
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab05a760) = 8682
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, {SIG_DFL}, 8) = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 8682
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, 0x7fffffc853d4, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0xffffffffffffffff)        = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x433720, [], SA_RESTORER, 0x2aaaaae521d0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "\nexitcode=$?\n\n## Stop addon scri"..., 8176) = 92
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
open("/home/leo/.mozilla-thunderbird/init.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = -1 ENOENT (No such file or directory)
open("/usr/lib/mozilla-thunderbird/init.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/home/leo/.mozilla-thunderbird/init.d/K*", 0x7fffffc83b50) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/usr/lib/mozilla-thunderbird/init.d/K*", 0x7fffffc83b50) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
exit_group(0)                           = ?
```

---

### Post by gorgor_bay on 2006-04-20
I don't know how to see where any error occurs within those strace outputs...

---

### Post by gorgor_bay on 2006-04-21
anybody ? :confused:

---

