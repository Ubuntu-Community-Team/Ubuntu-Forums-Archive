---
title: "Wine issues"
date: 2010-10-12
forum: General Help
---

### Post by taunnt on 2010-10-12
Hello, I was trying to install an windows app and it got an error while installing. Now wine takes forever to launch an app. I fif a strace wine and got this:

How can I correct this?

Thanks

execve("/usr/bin/wine", ["wine"], [/* 37 vars */]) = 0
[ Process PID=5917 runs in 32 bit mode. ]
brk(0)                                  = 0x7d319000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7771000
readlink("/proc/self/exe", "/usr/bin/wine", 4096) = 13
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/i686/sse2/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/i686/sse2/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/i686/sse2/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/i686/sse2", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/i686/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/i686/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/i686/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/i686", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/sse2/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/sse2/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/sse2/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/sse2", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/tls/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/tls", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/i686/sse2/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/i686/sse2/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/i686/sse2/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/i686/sse2", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/i686/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/i686/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/i686/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/i686", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/sse2/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/sse2/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/sse2/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/sse2", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/../lib32/cmov/libwine.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/bin/../lib32/cmov", 0xffde6c18) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/libwine.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3403\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1210044, ...}) = 0
mmap2(NULL, 1287648, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7636000
mmap2(0xf775c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x126) = 0xfffffffff775c000
mmap2(0xf775e000, 75232, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff775e000
close(3)                                = 0
open("/usr/bin/../lib32/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=157806, ...}) = 0
mmap2(NULL, 157806, PROT_READ, MAP_PRIVATE, 3, 0) = 0xfffffffff760f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 J\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=116528, ...}) = 0
mmap2(NULL, 98792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff75f6000
mmap2(0xf760b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xfffffffff760b000
mmap2(0xf760d000, 4584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff760d000
close(3)                                = 0
open("/usr/bin/../lib32/sse2/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/bin/../lib32/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/libc.so.6", O_RDONLY)      = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff75f5000
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff749b000
mprotect(0xf75ee000, 4096, PROT_NONE)   = 0
mmap2(0xf75ef000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0xfffffffff75ef000
mmap2(0xf75f2000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff75f2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/libdl.so.2", O_RDONLY)     = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7497000
mmap2(0xf7499000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xfffffffff7499000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7496000
set_thread_area(0xffde709c)             = 0
mprotect(0xf7499000, 4096, PROT_READ)   = 0
mprotect(0xf75ef000, 8192, PROT_READ)   = 0
mprotect(0xf760b000, 4096, PROT_READ)   = 0
mprotect(0xf775c000, 4096, PROT_READ)   = 0
mprotect(0x7bf02000, 4096, PROT_READ)   = 0
mprotect(0xf7790000, 4096, PROT_READ)   = 0
munmap(0xf760f000, 157806)              = 0
set_tid_address(0xf7496728)             = 5917
set_robust_list(0xf7496730, 0xc)        = 0
futex(0xffde71d0, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0xffde71d0, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, ffde71e0) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xf75fa410, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xf75fa8f0, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=-4286578688, rlim_max=-621285693884202992}) = 0
uname({sys="Linux", , ...})   = 0
brk(0)                                  = 0x7d319000
brk(0x7d33a000)                         = 0x7d33a000
write(2, "Usage: wine PROGRAM [ARGUMENTS.."..., 200Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
) = 200
exit_group(1)                           = ?

---

