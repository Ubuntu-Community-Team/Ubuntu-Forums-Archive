---
title: "Thunderbird segfault"
date: 2011-01-09
forum: General Help
---

### Post by canni on 2011-01-09
Hey all, my thunderbird crashes few seconds after it boots up regardless of in safe mode or normal, here is a strace log:
[http://pastebin.com/tccfYwcD](http://pastebin.com/tccfYwcD)

I've searched google and forums about this problem, but any of found answers did not helped me :/

I've tried:

- nscd daemon install solutions posted earlier
- fresh clean instal of ubuntu 10.10 and thunderbird 3.1.7 from repos on a VM - problem still exists
- removed all thunderbrid related dot files and dot dirs, and setup profile from beginning
- Remove thunderbird and related stuff with apt purge, and install tb from official .deb package

None of these steps helps me, tb still crashes with segmentation fault :/

I use gmail IMAP account, I've searched and found few other tips on google, but with no success.

If You guys need some more info for this let me know.

TB: 3.1.7 from repos and official package
Ubuntu 10.10 with medibuntu repos, fully updated

Best Regards,
canni

---

### Post by lidex on 2011-01-09
Are you sharing a profile? I have had no such errors with 3.1.7
Try renaming your profile, then uninstall. Next run these commands:
```
sudo updatedb
locate thunderbird
```
Now delete anything you find from the locate command. Re-install t-bird from the ubuntu repo.

---

### Post by canni on 2011-01-09
Heh still no luck...

I've done:

sudo apt-get purge thunderbird
sudo updatedb
locate thunderbird
rm -rf found results (even apt cached packages, icons etc.)

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install thunderbird thunderbird-gnome-support

few seconds after creation of gmail account, a crash happens :/

I've even tried to remove mails from web gui, that came after first notice of problem, still no luck.

I'm not using any network fs, and not sharing this account with anyone, and I do not use filesystem or home encryption either just clean install :/

---

### Post by lidex on 2011-01-09
So t-bird is fine until you create the imap account? Try running it from the terminal, then create the account to reproduce the error and post the error output.

---

### Post by canni on 2011-01-10
The result from:

thunderbird -safe-mode > tb.log 2>&1

is only: Segmentation fault

---

### Post by lidex on 2011-01-11
Your strace is for t-bird in safe mode-almost. Try it again with this syntax:
```
thunderbird --safe-mode
```
and
```
strace thunderbird --safe-mode
```
My safe mode strace:
```
lidex@lidex-laptop:~$ strace thunderbird --safe-mode
execve("/usr/bin/thunderbird", ["thunderbird", "--safe-mode"], [/* 39 vars */]) = 0
brk(0)                                  = 0x21ba000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f936f2b9000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=114842, ...}) = 0
mmap(NULL, 114842, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f936f29c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\356\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f936ed18000
mprotect(0x7f936ee92000, 2093056, PROT_NONE) = 0
mmap(0x7f936f091000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7f936f091000
mmap(0x7f936f096000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f936f096000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f936f29b000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f936f29a000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f936f299000
arch_prctl(ARCH_SET_FS, 0x7f936f29a700) = 0
mprotect(0x7f936f091000, 16384, PROT_READ) = 0
mprotect(0x618000, 4096, PROT_READ)     = 0
mprotect(0x7f936f2bb000, 4096, PROT_READ) = 0
munmap(0x7f936f29c000, 114842)          = 0
getpid()                                = 5832
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTORER|SA_RESTART, 0x7f936ed4bc20}, {SIG_DFL, [], 0}, 8) = 0
geteuid()                               = 1000
brk(0)                                  = 0x21ba000
brk(0x21db000)                          = 0x21db000
getppid()                               = 5831
stat("/home/lidex", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/thunderbird", O_RDONLY)  = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x40f790, ~[RTMIN RT_1], SA_RESTORER, 0x7f936ed4bc20}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_IGN, [], 0}, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7f936ed4bc20}, NULL, 8) = 0
read(10, "#!/bin/sh\n\n# Firefox launcher co"..., 8192) = 4162
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f936f29a9d0) = 5833
close(4)                                = 0
read(3, "/usr/bin/thunderbird\n", 128)  = 21
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5833
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f936f29a9d0) = 5834
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5834
stat("/usr/lib/thunderbird-3.1.7/thunderbird", {st_mode=S_IFREG|0755, st_size=3941, ...}) = 0
stat("/home/lidex/.thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat("/home/lidex/.thunderbird-3.1", 0x7fff79f16200) = -1 ENOENT (No such file or directory)
stat("/home/lidex/.thunderbird-3.0-replaced", 0x7fff79f161e0) = -1 ENOENT (No such file or directory)
execve("/usr/lib/thunderbird-3.1.7/thunderbird", ["/usr/lib/thunderbird-3.1.7/thund"..., "--safe-mode"], [/* 41 vars */]) = 0
brk(0)                                  = 0x13e6000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f35aa1c9000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=114842, ...}) = 0
mmap(NULL, 114842, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f35aa1ac000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\356\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f35a9c28000
mprotect(0x7f35a9da2000, 2093056, PROT_NONE) = 0
mmap(0x7f35a9fa1000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7f35a9fa1000
mmap(0x7f35a9fa6000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f35a9fa6000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f35aa1ab000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f35aa1aa000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f35aa1a9000
arch_prctl(ARCH_SET_FS, 0x7f35aa1aa700) = 0
mprotect(0x7f35a9fa1000, 16384, PROT_READ) = 0
mprotect(0x618000, 4096, PROT_READ)     = 0
mprotect(0x7f35aa1cb000, 4096, PROT_READ) = 0
munmap(0x7f35aa1ac000, 114842)          = 0
getpid()                                = 5832
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTORER|SA_RESTART, 0x7f35a9c5bc20}, {SIG_DFL, [], 0}, 8) = 0
geteuid()                               = 1000
brk(0)                                  = 0x13e6000
brk(0x1407000)                          = 0x1407000
getppid()                               = 5831
stat("/home/lidex", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/thunderbird-3.1.7/thunderbird", O_RDONLY) = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x40f790, ~[RTMIN RT_1], SA_RESTORER, 0x7f35a9c5bc20}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_IGN, [], 0}, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7f35a9c5bc20}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 3941
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f35aa1aa9d0) = 5835
close(4)                                = 0
read(3, "/usr/lib/thunderbird-3.1.7\n", 128) = 27
read(3, "", 128)                        = 0
close(3)                                = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5835
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f35aa1aa9d0) = 5836
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5836
stat("/usr/lib/thunderbird-3.1.7/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10461, ...}) = 0
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
getgroups(0, NULL)                      = 8
getgroups(8, [4, 20, 24, 46, 105, 119, 122, 1000]) = 8
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f35aa1aa9d0) = 5837
close(4)                                = 0
read(3, "1\n", 128)                     = 2
read(3, "", 128)                        = 0
close(3)                                = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5837
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f35aa1aa9d0) = 5838
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5838
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(0)                           = ?
lidex@lidex-laptop:~$ 

```

---

### Post by canni on 2011-01-11
There is no difference in output with --safe-mode and -safe-mode switches, here is an strace log:

```
execve("/usr/bin/thunderbird", ["thunderbird", "--safe-mode"], [/* 31 vars */]) = 0
brk(0)                                  = 0x94c9000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb771c000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=66955, ...}) = 0
mmap2(NULL, 66955, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb770b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@n\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1421892, ...}) = 0
mmap2(NULL, 1427880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x86b000
mmap2(0x9c2000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x157) = 0x9c2000
mmap2(0x9c5000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x9c5000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb770a000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb770a8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x9c2000, 8192, PROT_READ)     = 0
mprotect(0x805c000, 4096, PROT_READ)    = 0
mprotect(0x9f8000, 4096, PROT_READ)     = 0
munmap(0xb770b000, 66955)               = 0
getpid()                                = 3435
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x94c9000
brk(0x94ea000)                          = 0x94ea000
getppid()                               = 3434
stat64("/home/canni", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/thunderbird", O_RDONLY)  = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x8056690, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\n\n# Firefox launcher co"..., 8192) = 4162
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb770a938) = 3436
close(4)                                = 0
read(3, "/usr/bin/thunderbird\n", 128)  = 21
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3436
--- SIGCHLD (Child exited) @ 0 (0) ---
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb770a938) = 3437
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3437
--- SIGCHLD (Child exited) @ 0 (0) ---
stat64("/usr/lib/thunderbird-3.1.7/thunderbird", {st_mode=S_IFREG|0755, st_size=3941, ...}) = 0
stat64("/home/canni/.thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat64("/home/canni/.thunderbird-3.1", 0xbfb96060) = -1 ENOENT (No such file or directory)
stat64("/home/canni/.thunderbird-3.0-replaced", 0xbfb96060) = -1 ENOENT (No such file or directory)
execve("/usr/lib/thunderbird-3.1.7/thunderbird", ["/usr/lib/thunderbird-3.1.7/thund"..., "--safe-mode"], [/* 33 vars */]) = 0
brk(0)                                  = 0x9c81000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78ce000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=66955, ...}) = 0
mmap2(NULL, 66955, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb78bd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@n\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1421892, ...}) = 0
mmap2(NULL, 1427880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xcde000
mmap2(0xe35000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x157) = 0xe35000
mmap2(0xe38000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xe38000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78bc000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb78bc8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xe35000, 8192, PROT_READ)     = 0
mprotect(0x805c000, 4096, PROT_READ)    = 0
mprotect(0xea1000, 4096, PROT_READ)     = 0
munmap(0xb78bd000, 66955)               = 0
getpid()                                = 3435
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x9c81000
brk(0x9ca2000)                          = 0x9ca2000
getppid()                               = 3434
stat64("/home/canni", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/thunderbird-3.1.7/thunderbird", O_RDONLY) = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x8056690, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 3941
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb78bc938) = 3438
close(4)                                = 0
read(3, "/usr/lib/thunderbird-3.1.7\n", 128) = 27
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3438
--- SIGCHLD (Child exited) @ 0 (0) ---
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb78bc938) = 3439
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3439
--- SIGCHLD (Child exited) @ 0 (0) ---
stat64("/usr/lib/thunderbird-3.1.7/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10461, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 8
getgroups32(8, [4, 20, 24, 46, 111, 119, 122, 1000]) = 8
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb78bc938) = 3440
close(4)                                = 0
read(3, "1\n", 128)                     = 2
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3440
--- SIGCHLD (Child exited) @ 0 (0) ---
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb78bc938) = 3441
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 139}], 0, NULL) = 3441
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(139)                         = ?
```

---

### Post by canni on 2011-01-11
I've figure out that this problem only exists, when I setup my gmail IMAP account, other providers IMAP accounts do not produce those problems, and with Gmail POP access it works...

---

### Post by lidex on 2011-01-13
Strange. Probably should report a bug. It works fine for me though. Maybe your server settings have something to do with it.

---

