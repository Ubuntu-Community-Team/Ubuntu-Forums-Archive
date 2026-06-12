---
title: "Hardy: Five minute Firefox load times?"
date: 2009-12-26
forum: General Help
---

### Post by Ragueneau on 2009-12-26
I keep a machine at my parents house for causal browsing and scanning/printing usage, and as I stopped in for Christmas this year I found that the browser was practically useless: five minute load times, extreme instability when loaded, and safe mode or deleted profiles notwithstanding I can almost never get a stable browsing environment.  I don't have any plugins in /usr/lib/mozilla-firefox/plugins, and I deleted the .mozilla folder in the user profile in question.  Finally, trying Firefox 3.0.16 from Hardy backports (which may not be different anyway) or Firefox 3.5.6 from getfirefox.com don't show any different results; everything is updated.

What's the best way to start debugging this?

---

### Post by lrcaballero on 2009-12-26
Try Chrome (google) it is mighty fast.... and/or try Opera is also better than Firefox..I have all 3 in my laptop and I prefer Chrome then Opera.

Good Luck,


Luis

---

### Post by Barriehie on 2009-12-26
I was running Opera for a bit but it was kind of buggy.  I always come back to FF.  What kind of ping response are you getting to websites? Point being is it your network connection/provider, hardware, or software.  Has it ever worked as you expect it to?

Barrie

---

### Post by john newbuntu on 2009-12-26
Run it through 'strace' in a terminal and see if you spot anything.
strace firefox
or
strace -o output firefox

---

### Post by lrcaballero on 2009-12-26
Opera has worked perfect for me, but now that I just installed Chrome, is mighty fast just like in Windows (wife & Kid) use windows, but to answer your question the ping is do to my provider been Cox in USA, in less than 2 seconds loads up any page..... Try chrome you'll like it.

Luis

---

### Post by lovinglinux on 2009-12-26
> **Ragueneau said:**
> I keep a machine at my parents house for causal browsing and scanning/printing usage, and as I stopped in for Christmas this year I found that the browser was practically useless: five minute load times, extreme instability when loaded, and safe mode or deleted profiles notwithstanding I can almost never get a stable browsing environment.  I don't have any plugins in /usr/lib/mozilla-firefox/plugins, and I deleted the .mozilla folder in the user profile in question.  Finally, trying Firefox 3.0.16 from Hardy backports (which may not be different anyway) or Firefox 3.5.6 from getfirefox.com don't show any different results; everything is updated.

What's the best way to start debugging this?

If you have tried different versions, deleted the profile, started Firefox in safe mode and get the same results, then I would look for the problem somewhere else. Perhaps you have a hard drive issue. When Firefox starts, it will perform some necessary tasks, so if you have a hd issue, it could be taking too much time to perform the necessary data reading before starting.

It could be also a default setting causing the problem, in which case you wouldn't see any difference with a clean profile.

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Particularly, solutions FOT005 and FOT010 from the troubleshooting section. That might help, since both deal with default settings that can cause problems.

---

### Post by Ragueneau on 2009-12-28
Hi everyone,

It's not a network problem, as ping, dns, wget and everything via Chrome seems to work well.  I tried the Firefox troubleshooting items, but disabling ipv6 didn't seem to help, and I couldn't keep it from crashing long enough to disable safe browsing.  I did try installing and running epiphany-browser, and it behaves similarly (maybe a bug in gecko?).

Strace yields the following:
```
execve("/usr/bin/firefox", ["firefox"], [/* 30 vars */]) = 0
brk(0)                                  = 0x805e000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fe0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=54996, ...}) = 0
mmap2(NULL, 54996, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fd2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260e\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1364388, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fd1000
mmap2(NULL, 1369712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e82000
mmap2(0xb7fcb000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x149) = 0xb7fcb000
mmap2(0xb7fce000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fce000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e81000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7e816b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7fcb000, 4096, PROT_READ)   = 0
munmap(0xb7fd2000, 54996)               = 0
getpid()                                = 6276
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x805e000
brk(0x807f000)                          = 0x807f000
getppid()                               = 6275
stat64("/home/carolann", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/firefox", O_RDONLY)      = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x8055a30, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 3883
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6277
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/usr/bin\n", 128)              = 9
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6277
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6278
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "firefox\n", 128)               = 8
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6278
stat64("/usr/bin/run-mozilla.sh", 0xbffb4a18) = -1 ENOENT (No such file or directory)
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6279
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/home/carolann\n", 128)        = 15
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6279
lstat64("/usr/bin/firefox", {st_mode=S_IFLNK|0777, st_size=20, ...}) = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6280
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "firefox\n", 128)               = 8
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6280
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6281
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/usr/bin\n", 128)              = 9
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6281
chdir("/usr/bin")                       = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6282
close(4)                                = 0
read(3, "/opt/firefox/firefox\n", 128)  = 21
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6282
--- SIGCHLD (Child exited) @ 0 (0) ---
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6285
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "firefox\n", 128)               = 8
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6285
stat64("/opt/firefox/firefox", {st_mode=S_IFREG|0755, st_size=3883, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 13
getgroups32(13, [4, 20, 24, 25, 29, 30, 44, 46, 105, 107, 109, 115, 1000]) = 13
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6286
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/opt/firefox\n", 128)          = 13
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6286
stat64("/opt/firefox/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10450, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 13
getgroups32(13, [4, 20, 24, 25, 29, 30, 44, 46, 105, 107, 109, 115, 1000]) = 13
chdir("/opt/firefox")                   = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6287
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/opt/firefox\n", 128)          = 13
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6287
chdir("/home/carolann")                 = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e816f8) = 6288
wait4(-1, 0xbffb4bf0, 0, NULL)          = ? ERESTARTSYS (To be restarted)
--- SIGWINCH (Window changed) @ 0 (0) ---
wait4(-1, 0xbffb4bf0, 0, NULL)          = ? ERESTARTSYS (To be restarted)
--- SIGWINCH (Window changed) @ 0 (0) ---
wait4(-1, 
```

It's worth noting I didn't cut anything off, that's just where the trace is when it crashes, and it's reproducible.

---

