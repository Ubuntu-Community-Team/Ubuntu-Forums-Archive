---
title: "Thunderbird won't start after upgrade"
date: 2010-07-07
forum: General Help
---

### Post by kwalker on 2010-07-07
I posted about this in another forum on this board but then discovered it was about Ubuntuzilla which I don't use.  Sorry to duplicate the issue here.

Tonight I did the usual apt-get update/upgrade and it installed a newer version of Thunderbird.

Synaptic says the version I have is 3.0.5+build2+nobin.

Their is a bug ([http://ubuntuforums.org/showpost.php?p=9538228&postcount=25](http://ubuntuforums.org/showpost.php?p=9538228&postcount=25)) that refers to an  upstream directory which I don't have. Apparently some recent upgrades have produced some kind of circular link.  I am not sure whether that is the problem I have but this is supposed to give the answer.  Not sure whether it does but here is some terminal output:

kgw@kgw-desktop:~$ ls -ld ~/.*thunderbird*
lrwxrwxrwx 1 kgw kgw 22 2010-04-22 20:48 /home/kgw/.mozilla-thunderbird -> /home/kgw/.thunderbird
drwx------ 3 kgw kgw 4096 2009-12-08 14:34 /home/kgw/.thunderbird

When I click on the Thunderbird icon, there is an item that appears in the bar at the bottom of my screen that says Thunderbird and it produces a tiny vertical bar at the top of my screen that can be dragged into a an application window that is blank.

Oddly, when I asked firefox to send a link (forgetting that thunderbird wasn't working) it popped up the usual box to send an email and let me send it. The main screen of thunderbird still won't start. No idea what to make of all of this.

Any suggestions?  Anyone else having this problem? Thanks in advance for any help.

---

### Post by philinux on 2010-07-07
kwalker,

Run it from a terminal then you can see any error messages.

---

### Post by kwalker on 2010-07-07
I had tried that, it produces the same result, no error message:

kgw@kgw-desktop:~$ thunderbird
kgw@kgw-desktop:~$ 

I have put a bit more detail of it here:
[http://guide.ubuntuforums.org/showthread.php?t=1525651](http://guide.ubuntuforums.org/showthread.php?t=1525651)

---

### Post by philinux on 2010-07-07
Try safe mode.

```
thunderbird -safe-mode
```

---

### Post by kwalker on 2010-07-07
Thanks but same result

kgw@kgw-desktop:~$ 
kgw@kgw-desktop:~$ thunderbird -safe-mode
kgw@kgw-desktop:~$

---

### Post by gronbaek on 2010-07-07
I'm affected in the same way as kwalker. No error is show in terminal and safe mode doesn't help.

I was running Thunderbird when the updates were being installed and that left Thunderbird unresponsive. Not hanging / un-answering, but simply not reacting to buttons. After closing Thunderbird is not possible to restart Thunderbird.

I just noticed that when trying to start Thunderbird, a small (1 px width) window opens. If expanding the window, it is just blank with the Thunderbird name in the title bar. Nothing else.

---

### Post by philinux on 2010-07-07
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

[http://www.google.com/search?q=thunderbird+profile+manager&hl=en&source=lnt&sa=X&ei=Tko0TNWRCJHw0wSp0unPCg&ved=0CAYQpwU](http://www.google.com/search?q=thunderbird+profile+manager&hl=en&source=lnt&sa=X&ei=Tko0TNWRCJHw0wSp0unPCg&ved=0CAYQpwU)

---

### Post by Einmaliger on 2010-07-07
Same problem here. No error messages, just an empty frame, even when started with "--safe-mode" or "-ProfileManager". Probably the solution involves deleting some files from the profile folder.  But which ones? Surely we could simply delete the .thunderbird folder and reconfigure everything (as I only use IMAP, no mails would be lost), but that doesn't seem a good option to me.

[Update: even after renaming ~/.thunderbird, the application does not start]

---

### Post by Einmaliger on 2010-07-07
Maybe the strace helps?

```
execve("/usr/bin/thunderbird", ["thunderbird"], [/* 40 vars */]) = 0
brk(0)                                  = 0x1622000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fde3885a000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=138109, ...}) = 0
mmap(NULL, 138109, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fde38838000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\355\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fde382b9000
mprotect(0x7fde38433000, 2093056, PROT_NONE) = 0
mmap(0x7fde38632000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7fde38632000
mmap(0x7fde38637000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fde38637000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fde38837000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fde38836000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fde38835000
arch_prctl(ARCH_SET_FS, 0x7fde38836700) = 0
mprotect(0x7fde38632000, 16384, PROT_READ) = 0
mprotect(0x617000, 4096, PROT_READ)     = 0
mprotect(0x7fde3885c000, 4096, PROT_READ) = 0
munmap(0x7fde38838000, 138109)          = 0
getpid()                                = 5949
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTORER|SA_RESTART, 0x7fde382ecaf0}, {SIG_DFL, [], 0}, 8) = 0
geteuid()                               = 1000
brk(0)                                  = 0x1622000
brk(0x1643000)                          = 0x1643000
getppid()                               = 5948
stat("/tmp", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=20480, ...}) = 0
stat(".", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=20480, ...}) = 0
open("/usr/bin/thunderbird", O_RDONLY)  = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x408189, ~[RTMIN RT_1], SA_RESTORER, 0x7fde382ecaf0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7fde382ecaf0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7fde382ecaf0}, NULL, 8) = 0
read(10, "#!/bin/sh\n\n# Firefox launcher co"..., 8192) = 4842
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fde388369d0) = 5950
close(4)                                = 0
read(3, "/usr/bin/thunderbird\n", 128)  = 21
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5950
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fde388369d0) = 5951
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
close(3)                                = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5951
stat("/usr/lib/thunderbird-3.0.5/thunderbird", {st_mode=S_IFREG|0755, st_size=3885, ...}) = 0
stat("/home/smueller/.mozilla-thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
lstat("/home/smueller/.mozilla-thunderbird", {st_mode=S_IFLNK|0777, st_size=27, ...}) = 0
stat("/home/smueller/.thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat("/home/smueller/.thunderbird-3.0", 0x7fff9e5fb390) = -1 ENOENT (No such file or directory)
stat("/home/smueller/.thunderbird-2.0-replaced", 0x7fff9e5fb350) = -1 ENOENT (No such file or directory)
lstat("/home/smueller/.mozilla-thunderbird", {st_mode=S_IFLNK|0777, st_size=27, ...}) = 0
stat("/home/smueller/.mozilla-thunderbird", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
execve("/usr/lib/thunderbird-3.0.5/thunderbird", ["/usr/lib/thunderbird-3.0.5/thund"...], [/* 41 vars */]) = 0
brk(0)                                  = 0x10b6000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f16848da000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=138109, ...}) = 0
mmap(NULL, 138109, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f16848b8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\355\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1572232, ...}) = 0
mmap(NULL, 3680296, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f1684339000
mprotect(0x7f16844b3000, 2093056, PROT_NONE) = 0
mmap(0x7f16846b2000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x179000) = 0x7f16846b2000
mmap(0x7f16846b7000, 18472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f16846b7000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f16848b7000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f16848b6000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f16848b5000
arch_prctl(ARCH_SET_FS, 0x7f16848b6700) = 0
mprotect(0x7f16846b2000, 16384, PROT_READ) = 0
mprotect(0x617000, 4096, PROT_READ)     = 0
mprotect(0x7f16848dc000, 4096, PROT_READ) = 0
munmap(0x7f16848b8000, 138109)          = 0
getpid()                                = 5949
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTORER|SA_RESTART, 0x7f168436caf0}, {SIG_DFL, [], 0}, 8) = 0
geteuid()                               = 1000
brk(0)                                  = 0x10b6000
brk(0x10d7000)                          = 0x10d7000
getppid()                               = 5948
stat("/tmp", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=20480, ...}) = 0
stat(".", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=20480, ...}) = 0
open("/usr/lib/thunderbird-3.0.5/thunderbird", O_RDONLY) = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x408189, ~[RTMIN RT_1], SA_RESTORER, 0x7f168436caf0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7f168436caf0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7f168436caf0}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 3885
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f16848b69d0) = 5952
close(4)                                = 0
read(3, "/usr/lib/thunderbird-3.0.5\n", 128) = 27
read(3, "", 128)                        = 0
close(3)                                = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5952
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f16848b69d0) = 5953
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5953
stat("/usr/lib/thunderbird-3.0.5/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10450, ...}) = 0
geteuid()                               = 1000
getgid()                                = 500
getegid()                               = 500
getgroups(0, NULL)                      = 8
getgroups(8, [4, 20, 24, 46, 112, 119, 120, 500]) = 8
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f16848b69d0) = 5954
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5954
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(0)                           = ?

```

---

### Post by philinux on 2010-07-07
einmaliger,

Info from the first post.

```
ls  -d ~/.*thunderbird*
```

Lets see what you got.

---

### Post by Einmaliger on 2010-07-07
```
$ ls -ld ~/.*thunderbird
lrwxrwxrwx 1 smueller seceng    27 2010-07-07 13:16 /home/smueller/.mozilla-thunderbird -> /home/smueller/.thunderbird
drwx------ 5 smueller mueller 4096 2010-07-07 13:16 /home/smueller/.thunderbird

```

Deleting the link .mozilla-thunderbird or copying/mving the folder .thunderbird to .mozilla-thunderbird doesn't change anything, either. As stated before, even without a .*thunderbird directory, the application does not start. I also tried various combinations of removing installed thunderbird-locale- packages and removing/reinstalling the core thunderbird package. I'm lost. Any ideas where to look for the cause of the problem?

---

### Post by philinux on 2010-07-07
> **Einmaliger said:**
> ```
$ ls -ld ~/.*thunderbird
lrwxrwxrwx 1 smueller seceng    27 2010-07-07 13:16 /home/smueller/.mozilla-thunderbird -> /home/smueller/.thunderbird
drwx------ 5 smueller mueller 4096 2010-07-07 13:16 /home/smueller/.thunderbird

```

Deleting the link .mozilla-thunderbird or copying/mving the folder .thunderbird to .mozilla-thunderbird doesn't change anything, either. As stated before, even without a .*thunderbird directory, the application does not start. I also tried various combinations of removing installed thunderbird-locale- packages and removing/reinstalling the core thunderbird package. I'm lost. Any ideas where to look for the cause of the problem?

No. I've even had a look on launchpad to see if anyone else bugged this.

Looks like it needs a bug report doing.
```
ubuntu-bug thunderbird
```
How about using synaptic to go back a version?

I switched to evolution last year so TB not installed here at all.

---

### Post by Einmaliger on 2010-07-07
> **philinux said:**
> Looks like it needs a bug report doing.
Bug report filed: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/602672](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/602672)

> How about using synaptic to go back a version?
Yes, that seems to be the viable only solution at this point.

Thanks for your help!

---

### Post by kwalker on 2010-07-08
> **philinux said:**
> 
How about using synaptic to go back a version?


That works here.

---

### Post by philinux on 2010-07-08
> **kwalker said:**
> That works here.

Go to the bug report and change it's status to confirmed.

Under status click on New and there's a pull down.

---

### Post by kwalker on 2010-07-09
A new upgrade today seems to have fixed this for me.

---

