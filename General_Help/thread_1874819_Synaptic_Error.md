---
title: "Synaptic Error"
date: 2011-11-03
forum: General Help
---

### Post by SpEcIeS on 2011-11-03
After doing todays updates *(2011.11.03)* Synaptic throws off this error:
```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
```
Anyone else seeing this?

---

### Post by phDaemon on 2011-11-03
Everything seems to be running fine here...

Try purging and re-installing?

---

### Post by SpEcIeS on 2011-11-03
Yeah, this was done, but the results are the same. :(

---

### Post by bluexrider on 2011-11-03
> **SpEcIeS said:**
> After doing todays updates *(2011.11.03)* Synaptic throws off this error:
```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
```Anyone else seeing this?


I recognize this as a stack overflow problem but I haven't received this using Synaptic.

Try updating using command-line

---

### Post by alquery on 2011-11-03
I'm having the same problem.

I have tried reinstalling, and there are no new updates.

---

### Post by SpEcIeS on 2011-11-03
;) Did that too as well as a system reboot. Applied a strace and there seems to be a lot of resources missing:
```
execve("/usr/sbin/synaptic", ["synaptic"], [/* 21 vars */]) = 0
brk(0)                                  = 0x2524000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbe000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fecdcf93000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg.so.4.11", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\356\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1155944, ...}) = 0
mmap(NULL, 3252784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdca85000
mprotect(0x7fecdcb9a000, 2097152, PROT_NONE) = 0
mmap(0x7fecdcd9a000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x115000) = 0x7fecdcd9a000
mmap(0x7fecdcd9f000, 560, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecdcd9f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libX11.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\211\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1277312, ...}) = 0
mmap(NULL, 3374288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdc74d000
mprotect(0x7fecdc880000, 2097152, PROT_NONE) = 0
mmap(0x7fecdca80000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x133000) = 0x7fecdca80000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-inst.so.1.3", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0pe\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=80920, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf92000
mmap(NULL, 2175968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdc539000
mprotect(0x7fecdc54b000, 2097152, PROT_NONE) = 0
mmap(0x7fecdc74b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12000) = 0x7fecdc74b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\246\6\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=4432392, ...}) = 0
mmap(NULL, 6537048, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdbefd000
mprotect(0x7fecdc32c000, 2097152, PROT_NONE) = 0
mmap(0x7fecdc52c000, 45056, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x42f000) = 0x7fecdc52c000
mmap(0x7fecdc537000, 8024, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecdc537000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\332\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=728272, ...}) = 0
mmap(NULL, 2824712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdbc4b000
mprotect(0x7fecdbcf8000, 2093056, PROT_NONE) = 0
mmap(0x7fecdbef7000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xac000) = 0x7fecdbef7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300R\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=125992, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf91000
mmap(NULL, 2221552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdba2c000
mprotect(0x7fecdba4a000, 2093056, PROT_NONE) = 0
mmap(0x7fecdbc49000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1d000) = 0x7fecdbc49000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\323\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=302456, ...}) = 0
mmap(NULL, 2398368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdb7e2000
mprotect(0x7fecdb829000, 2097152, PROT_NONE) = 0
mmap(0x7fecdba29000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x47000) = 0x7fecdba29000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\244\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=326984, ...}) = 0
mmap(NULL, 2425496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdb591000
mprotect(0x7fecdb5df000, 2097152, PROT_NONE) = 0
mmap(0x7fecdb7df000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4e000) = 0x7fecdb7df000
mmap(0x7fecdb7e1000, 664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecdb7e1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libglib-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300w\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1003848, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf90000
mmap(NULL, 3101496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdb29b000
mprotect(0x7fecdb38f000, 2093056, PROT_NONE) = 0
mmap(0x7fecdb58e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf3000) = 0x7fecdb58e000
mmap(0x7fecdb590000, 824, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecdb590000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libvte.so.9", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360$\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=657368, ...}) = 0
mmap(NULL, 2753024, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdaffa000
mprotect(0x7fecdb095000, 2097152, PROT_NONE) = 0
mmap(0x7fecdb295000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9b000) = 0x7fecdb295000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/liblaunchpad-integration.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\31\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14808, ...}) = 0
mmap(NULL, 2110072, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdadf6000
mprotect(0x7fecdadf9000, 2093056, PROT_NONE) = 0
mmap(0x7fecdaff8000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fecdaff8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0Pl\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=135500, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf8f000
mmap(NULL, 2212920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecdabd9000
mprotect(0x7fecdabf1000, 2093056, PROT_NONE) = 0
mmap(0x7fecdadf0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7fecdadf0000
mmap(0x7fecdadf2000, 13368, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecdadf2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libept.so.1", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`&\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=339512, ...}) = 0
mmap(NULL, 2434672, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecda986000
mprotect(0x7fecda9d7000, 2097152, PROT_NONE) = 0
mmap(0x7fecdabd7000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x51000) = 0x7fecdabd7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libxapian.so.22", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\264\3\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=2027032, ...}) = 0
mmap(NULL, 4122112, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecda597000
mprotect(0x7fecda77d000, 2097152, PROT_NONE) = 0
mmap(0x7fecda97d000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e6000) = 0x7fecda97d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\244\5\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=991424, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf8e000
mmap(NULL, 3171440, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecda290000
mprotect(0x7fecda378000, 2097152, PROT_NONE) = 0
mmap(0x7fecda578000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe8000) = 0x7fecda578000
mmap(0x7fecda582000, 83056, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecda582000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgcc_s.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260(\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=88384, ...}) = 0
mmap(NULL, 2184216, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecda07a000
mprotect(0x7fecda08f000, 2093056, PROT_NONE) = 0
mmap(0x7fecda28e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14000) = 0x7fecda28e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \24\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1677624, ...}) = 0
mmap(NULL, 3793768, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd9cdb000
mprotect(0x7fecd9e70000, 2093056, PROT_NONE) = 0
mmap(0x7fecda06f000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x194000) = 0x7fecda06f000
mmap(0x7fecda074000, 21352, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecda074000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libutil.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10640, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf8d000
mmap(NULL, 2105608, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd9ad8000
mprotect(0x7fecd9ada000, 2093056, PROT_NONE) = 0
mmap(0x7fecd9cd9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fecd9cd9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\r\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14768, ...}) = 0
mmap(NULL, 2109704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd98d4000
mprotect(0x7fecd98d6000, 2097152, PROT_NONE) = 0
mmap(0x7fecd9ad6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fecd9ad6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P \0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=96816, ...}) = 0
mmap(NULL, 2191920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd96bc000
mprotect(0x7fecd96d3000, 2093056, PROT_NONE) = 0
mmap(0x7fecd98d2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7fecd98d2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\200\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=112992, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf8c000
mmap(NULL, 2208304, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd94a0000
mprotect(0x7fecd94bb000, 2093056, PROT_NONE) = 0
mmap(0x7fecd96ba000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a000) = 0x7fecd96ba000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000H\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=52416, ...}) = 0
mmap(NULL, 2147840, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd9293000
mprotect(0x7fecd929e000, 2097152, PROT_NONE) = 0
mmap(0x7fecd949e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb000) = 0x7fecd949e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXfixes.so.3", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\23\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=22504, ...}) = 0
mmap(NULL, 2117864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd908d000
mprotect(0x7fecd9092000, 2093056, PROT_NONE) = 0
mmap(0x7fecd9291000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0x7fecd9291000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libatk-1.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\221\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=137944, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf8b000
mmap(NULL, 2234424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd8e6b000
mprotect(0x7fecd8e8a000, 2097152, PROT_NONE) = 0
mmap(0x7fecd908a000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f000) = 0x7fecd908a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libcairo.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\310\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=766024, ...}) = 0
mmap(NULL, 2873760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd8bad000
mprotect(0x7fecd8c66000, 2093056, PROT_NONE) = 0
mmap(0x7fecd8e65000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb8000) = 0x7fecd8e65000
mmap(0x7fecd8e68000, 10656, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecd8e68000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\300\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1311808, ...}) = 0
mmap(NULL, 3413456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd886b000
mprotect(0x7fecd89a6000, 2093056, PROT_NONE) = 0
mmap(0x7fecd8ba5000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13a000) = 0x7fecd8ba5000
mmap(0x7fecd8bab000, 5584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecd8bab000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260i\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=176080, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf8a000
mmap(NULL, 2271744, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd8640000
mprotect(0x7fecd866a000, 2093056, PROT_NONE) = 0
mmap(0x7fecd8869000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x29000) = 0x7fecd8869000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libfontconfig.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@^\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=220896, ...}) = 0
mmap(NULL, 2317064, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd840a000
mprotect(0x7fecd843e000, 2097152, PROT_NONE) = 0
mmap(0x7fecd863e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x34000) = 0x7fecd863e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\20\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14472, ...}) = 0
mmap(NULL, 2109880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd8206000
mprotect(0x7fecd8209000, 2093056, PROT_NONE) = 0
mmap(0x7fecd8408000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fecd8408000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360>\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=538928, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf89000
mmap(NULL, 2633960, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd7f82000
mprotect(0x7fecd8005000, 2093056, PROT_NONE) = 0
mmap(0x7fecd8204000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x82000) = 0x7fecd8204000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`4\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=77696, ...}) = 0
mmap(NULL, 2173496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd7d6f000
mprotect(0x7fecd7d81000, 2093056, PROT_NONE) = 0
mmap(0x7fecd7f80000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11000) = 0x7fecd7f80000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXrender.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\30\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=43432, ...}) = 0
mmap(NULL, 2138728, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd7b64000
mprotect(0x7fecd7b6d000, 2097152, PROT_NONE) = 0
mmap(0x7fecd7d6d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9000) = 0x7fecd7d6d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXinerama.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\t\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10360, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf88000
mmap(NULL, 2105640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd7961000
mprotect(0x7fecd7963000, 2093056, PROT_NONE) = 0
mmap(0x7fecd7b62000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fecd7b62000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXi.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\37\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=63800, ...}) = 0
mmap(NULL, 2159232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd7751000
mprotect(0x7fecd7760000, 2093056, PROT_NONE) = 0
mmap(0x7fecd795f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0x7fecd795f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXrandr.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\26\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=34920, ...}) = 0
mmap(NULL, 2130280, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd7548000
mprotect(0x7fecd7550000, 2093056, PROT_NONE) = 0
mmap(0x7fecd774f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7fecd774f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXcursor.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\"\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=39184, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf87000
mmap(NULL, 2134464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd733e000
mprotect(0x7fecd7347000, 2093056, PROT_NONE) = 0
mmap(0x7fecd7546000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0x7fecd7546000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXcomposite.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\v\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10192, ...}) = 0
mmap(NULL, 2105464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd713b000
mprotect(0x7fecd713d000, 2093056, PROT_NONE) = 0
mmap(0x7fecd733c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fecd733c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXdamage.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\n\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10208, ...}) = 0
mmap(NULL, 2105496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd6f38000
mprotect(0x7fecd6f3a000, 2093056, PROT_NONE) = 0
mmap(0x7fecd7139000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fecd7139000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf86000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18824, ...}) = 0
mmap(NULL, 2114128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd6d33000
mprotect(0x7fecd6d37000, 2093056, PROT_NONE) = 0
mmap(0x7fecd6f36000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7fecd6f36000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libffi.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=30896, ...}) = 0
mmap(NULL, 2127264, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd6b2b000
mprotect(0x7fecd6b32000, 2093056, PROT_NONE) = 0
mmap(0x7fecd6d31000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fecd6d31000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpcre.so.3", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=243800, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf85000
mmap(NULL, 2338984, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd68ef000
mprotect(0x7fecd692a000, 2093056, PROT_NONE) = 0
mmap(0x7fecd6b29000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3a000) = 0x7fecd6b29000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/librt.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31752, ...}) = 0
mmap(NULL, 2129016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd66e7000
mprotect(0x7fecd66ee000, 2093056, PROT_NONE) = 0
mmap(0x7fecd68ed000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fecd68ed000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libtinfo.so.5", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\301\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=159200, ...}) = 0
mmap(NULL, 2255936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd64c0000
mprotect(0x7fecd64e2000, 2097152, PROT_NONE) = 0
mmap(0x7fecd66e2000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x22000) = 0x7fecd66e2000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf84000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libuuid.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\24\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18888, ...}) = 0
mmap(NULL, 2113936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd62bb000
mprotect(0x7fecd62bf000, 2093056, PROT_NONE) = 0
mmap(0x7fecd64be000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7fecd64be000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXau.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\r\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10328, ...}) = 0
mmap(NULL, 2105600, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd60b8000
mprotect(0x7fecd60ba000, 2093056, PROT_NONE) = 0
mmap(0x7fecd62b9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fecd62b9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXdmcp.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\20\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=22496, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf83000
mmap(NULL, 2117752, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd5eb2000
mprotect(0x7fecd5eb7000, 2093056, PROT_NONE) = 0
mmap(0x7fecd60b6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0x7fecd60b6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libfreetype.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\261\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=620776, ...}) = 0
mmap(NULL, 2715952, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd5c1a000
mprotect(0x7fecd5cac000, 2093056, PROT_NONE) = 0
mmap(0x7fecd5eab000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x91000) = 0x7fecd5eab000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpixman-1.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\177\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=473344, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf82000
mmap(NULL, 2568624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd59a6000
mprotect(0x7fecd5a14000, 2097152, PROT_NONE) = 0
mmap(0x7fecd5c14000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6e000) = 0x7fecd5c14000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpng12.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`I\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=158680, ...}) = 0
mmap(NULL, 2253856, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd577f000
mprotect(0x7fecd57a5000, 2093056, PROT_NONE) = 0
mmap(0x7fecd59a4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x25000) = 0x7fecd59a4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-shm.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \n\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10248, ...}) = 0
mmap(NULL, 2105424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd557c000
mprotect(0x7fecd557e000, 2093056, PROT_NONE) = 0
mmap(0x7fecd577d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fecd577d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-render.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340,\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=34824, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf81000
mmap(NULL, 2130000, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd5373000
mprotect(0x7fecd537a000, 2097152, PROT_NONE) = 0
mmap(0x7fecd557a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7fecd557a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libselinux.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`Q\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=117720, ...}) = 0
mmap(NULL, 2217512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd5155000
mprotect(0x7fecd5171000, 2093056, PROT_NONE) = 0
mmap(0x7fecd5370000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0x7fecd5370000
mmap(0x7fecd5372000, 1576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecd5372000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libresolv.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P9\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=101192, ...}) = 0
mmap(NULL, 2206328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd4f3a000
mprotect(0x7fecd4f51000, 2097152, PROT_NONE) = 0
mmap(0x7fecd5151000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7fecd5151000
mmap(0x7fecd5153000, 6776, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecd5153000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf80000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libexpat.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\3009\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=169992, ...}) = 0
mmap(NULL, 2265168, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd4d10000
mprotect(0x7fecd4d37000, 2097152, PROT_NONE) = 0
mmap(0x7fecd4f37000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x27000) = 0x7fecd4f37000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf7f000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf7e000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf7d000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf7b000
arch_prctl(ARCH_SET_FS, 0x7fecdcf7b9c0) = 0
mprotect(0x7fecd4f37000, 8192, PROT_READ) = 0
mprotect(0x7fecd5151000, 4096, PROT_READ) = 0
mprotect(0x7fecd5370000, 4096, PROT_READ) = 0
mprotect(0x7fecd557a000, 4096, PROT_READ) = 0
mprotect(0x7fecd577d000, 4096, PROT_READ) = 0
mprotect(0x7fecd59a4000, 4096, PROT_READ) = 0
mprotect(0x7fecd5c14000, 20480, PROT_READ) = 0
mprotect(0x7fecd5eab000, 24576, PROT_READ) = 0
mprotect(0x7fecd60b6000, 4096, PROT_READ) = 0
mprotect(0x7fecd62b9000, 4096, PROT_READ) = 0
mprotect(0x7fecd64be000, 4096, PROT_READ) = 0
mprotect(0x7fecd66e2000, 16384, PROT_READ) = 0
mprotect(0x7fecd68ed000, 4096, PROT_READ) = 0
mprotect(0x7fecd6b29000, 4096, PROT_READ) = 0
mprotect(0x7fecd6d31000, 4096, PROT_READ) = 0
mprotect(0x7fecd6f36000, 4096, PROT_READ) = 0
mprotect(0x7fecd7139000, 4096, PROT_READ) = 0
mprotect(0x7fecd733c000, 4096, PROT_READ) = 0
mprotect(0x7fecd7546000, 4096, PROT_READ) = 0
mprotect(0x7fecd774f000, 4096, PROT_READ) = 0
mprotect(0x7fecd795f000, 4096, PROT_READ) = 0
mprotect(0x7fecd7b62000, 4096, PROT_READ) = 0
mprotect(0x7fecd7d6d000, 4096, PROT_READ) = 0
mprotect(0x7fecd7f80000, 4096, PROT_READ) = 0
mprotect(0x7fecd8204000, 4096, PROT_READ) = 0
mprotect(0x7fecd8408000, 4096, PROT_READ) = 0
mprotect(0x7fecd863e000, 4096, PROT_READ) = 0
mprotect(0x7fecd8869000, 4096, PROT_READ) = 0
mprotect(0x7fecd8ba5000, 16384, PROT_READ) = 0
mprotect(0x7fecd8e65000, 8192, PROT_READ) = 0
mprotect(0x7fecd908a000, 8192, PROT_READ) = 0
mprotect(0x7fecd9291000, 4096, PROT_READ) = 0
mprotect(0x7fecd949e000, 4096, PROT_READ) = 0
mprotect(0x7fecd96ba000, 4096, PROT_READ) = 0
mprotect(0x7fecd98d2000, 4096, PROT_READ) = 0
mprotect(0x7fecd9ad6000, 4096, PROT_READ) = 0
mprotect(0x7fecd9cd9000, 4096, PROT_READ) = 0
mprotect(0x7fecda06f000, 16384, PROT_READ) = 0
mprotect(0x7fecda28e000, 4096, PROT_READ) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf7a000
mprotect(0x7fecda578000, 32768, PROT_READ) = 0
mprotect(0x7fecda97d000, 32768, PROT_READ) = 0
mprotect(0x7fecdabd7000, 4096, PROT_READ) = 0
mprotect(0x7fecdadf0000, 4096, PROT_READ) = 0
mprotect(0x7fecdaff8000, 4096, PROT_READ) = 0
mprotect(0x7fecdb295000, 8192, PROT_READ) = 0
mprotect(0x7fecdb58e000, 4096, PROT_READ) = 0
mprotect(0x7fecdb7df000, 4096, PROT_READ) = 0
mprotect(0x7fecdba29000, 8192, PROT_READ) = 0
mprotect(0x7fecdbc49000, 4096, PROT_READ) = 0
mprotect(0x7fecdbef7000, 16384, PROT_READ) = 0
mprotect(0x7fecdc52c000, 28672, PROT_READ) = 0
mprotect(0x7fecdc74b000, 4096, PROT_READ) = 0
mprotect(0x7fecdca80000, 4096, PROT_READ) = 0
mprotect(0x7fecdcd9a000, 16384, PROT_READ) = 0
mprotect(0x6b5000, 4096, PROT_READ)     = 0
mprotect(0x7fecdcfc0000, 4096, PROT_READ) = 0
munmap(0x7fecdcf93000, 172851)          = 0
set_tid_address(0x7fecdcf7bc90)         = 4244
set_robust_list(0x7fecdcf7bca0, 0x18)   = 0
futex(0x7fff37c313cc, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x7fff37c313cc, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, 7fecdcf7b9c0) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0x7fecdabdf6c0, [], SA_RESTORER|SA_SIGINFO, 0x7fecdabe9060}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7fecdabdf750, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7fecdabe9060}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
statfs("/selinux", {f_type="EXT2_SUPER_MAGIC", f_bsize=4096, f_blocks=153056302, f_bfree=116578826, f_bavail=108804004, f_files=38879232, f_ffree=38543958, f_fsid={1878226418, 1170441016}, f_namelen=255, f_frsize=4096}) = 0
brk(0)                                  = 0x2524000
brk(0x2545000)                          = 0x2545000
open("/proc/filesystems", O_RDONLY)     = 3
fstat(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbd000
read(3, "nodev\tsysfs\nnodev\trootfs\nnodev\tb"..., 1024) = 328
read(3, "", 1024)                       = 0
close(3)                                = 0
munmap(0x7fecdcfbd000, 4096)            = 0
futex(0x7fecda582fb0, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=7224800, ...}) = 0
mmap(NULL, 7224800, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fecd462c000
close(3)                                = 0
getresuid([0], [0], [0])                = 0
getresgid([0], [0], [0])                = 0
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbd000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fecdcfbd000, 4096)            = 0
open("/usr/share/locale/en_CA/LC_MESSAGES/synaptic.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/synaptic.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/synaptic.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/synaptic.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_CA/LC_MESSAGES/gtk20.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/gtk20.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20.mo", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=4214, ...}) = 0
mmap(NULL, 4214, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fecdcfbc000
close(3)                                = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/gtk20.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
futex(0x7fecd9ad70b0, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/share/locale/en_CA/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
sched_getparam(4244, { 0 })             = 0
sched_getscheduler(4244)                = 0 (SCHED_OTHER)
clock_getres(CLOCK_MONOTONIC, {0, 1})   = 0
sched_get_priority_min(SCHED_OTHER)     = 0
sched_get_priority_max(SCHED_OTHER)     = 0
sched_get_priority_max(SCHED_OTHER)     = 0
open("/usr/lib/x86_64-linux-gnu/charset.alias", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbb000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fecdcfbb000, 4096)            = 0
open("/usr/share/X11/locale/locale.alias", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=82081, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbb000
read(3, "#\n#\tThis file contains alias nam"..., 4096) = 4096
read(3, "1\nbr_FR.iso88591\t\t\t\t\tbr_FR.ISO88"..., 4096) = 4096
read(3, "59-1\nde_DE.iso88591\t\t\t\t\tde_DE.IS"..., 4096) = 4096
read(3, "n_ZA.UTF-8\nen_ZW\t\t\t\t\t\ten_ZW.ISO8"..., 4096) = 4096
read(3, "\t\t\tfa_IR.UTF-8\nfa_IR\t\t\t\t\t\tfa_IR."..., 4096) = 4096
read(3, "\the_IL.ISO8859-8\nhe_IL.iso88598\t"..., 4096) = 4096
read(3, "15\t\t\t\tkw_GB.ISO8859-15\nky\t\t\t\t\t\tk"..., 4096) = 4096
read(3, "\t\t\toc_FR.ISO8859-15\noc_FR.ISO-88"..., 4096) = 4096
read(3, "r_RS.UTF-8\nsr_CS.UTF-8@Latn\t\t\t\ts"..., 4096) = 4096
read(3, "GB18030\t\t\t\t\tzh_CN.gb18030\nzh_CN."..., 4096) = 4096
read(3, "\na3_AZ.koi8c:\t\t\t\t\ta3_AZ.KOI8-C\na"..., 4096) = 4096
read(3, "_BA.ISO8859-2\nbs_BA.ISO-8859-2:\t"..., 4096) = 4096
read(3, "DE.ISO8859-15\nde_DE.ISO-8859-15@"..., 4096) = 4096
read(3, "EO.ISO8859-3:\t\t\t\teo_EO.ISO8859-3"..., 4096) = 4096
read(3, ".isiri3342:\t\t\t\tfa_IR.ISIRI-3342\n"..., 4096) = 4096
read(3, "v_GB.ISO8859-15\nhe:\t\t\t\t\t\the_IL.I"..., 4096) = 4096
read(3, "8859-1\nkw_GB.iso88591:\t\t\t\t\tkw_GB"..., 4096) = 4096
read(3, "ny_NO:\t\t\t\t\t\tny_NO.ISO8859-1\nny_N"..., 4096) = 4096
read(3, "goslavia (later CS for Serbia&Mo"..., 4096) = 4096
read(3, ":\t\t\t\twa_BE.ISO8859-15\nwa_BE.ISO-"..., 4096) = 4096
read(3, "9-15\n# Other miscellaneous local"..., 4096) = 161
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fecdcfbb000, 4096)            = 0
open("/usr/share/X11/locale/locale.alias", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=82081, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbb000
read(3, "#\n#\tThis file contains alias nam"..., 4096) = 4096
read(3, "1\nbr_FR.iso88591\t\t\t\t\tbr_FR.ISO88"..., 4096) = 4096
read(3, "59-1\nde_DE.iso88591\t\t\t\t\tde_DE.IS"..., 4096) = 4096
read(3, "n_ZA.UTF-8\nen_ZW\t\t\t\t\t\ten_ZW.ISO8"..., 4096) = 4096
read(3, "\t\t\tfa_IR.UTF-8\nfa_IR\t\t\t\t\t\tfa_IR."..., 4096) = 4096
read(3, "\the_IL.ISO8859-8\nhe_IL.iso88598\t"..., 4096) = 4096
read(3, "15\t\t\t\tkw_GB.ISO8859-15\nky\t\t\t\t\t\tk"..., 4096) = 4096
read(3, "\t\t\toc_FR.ISO8859-15\noc_FR.ISO-88"..., 4096) = 4096
read(3, "r_RS.UTF-8\nsr_CS.UTF-8@Latn\t\t\t\ts"..., 4096) = 4096
read(3, "GB18030\t\t\t\t\tzh_CN.gb18030\nzh_CN."..., 4096) = 4096
read(3, "\na3_AZ.koi8c:\t\t\t\t\ta3_AZ.KOI8-C\na"..., 4096) = 4096
read(3, "_BA.ISO8859-2\nbs_BA.ISO-8859-2:\t"..., 4096) = 4096
read(3, "DE.ISO8859-15\nde_DE.ISO-8859-15@"..., 4096) = 4096
close(3)                                = 0
munmap(0x7fecdcfbb000, 4096)            = 0
open("/usr/share/X11/locale/locale.dir", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=39853, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbb000
read(3, "#\n#\tThis file contains locale da"..., 4096) = 4096
read(3, "LE\t\t\tes_DO.ISO8859-1\niso8859-1/X"..., 4096) = 4096
read(3, " for it, and the GNU C Library\n#"..., 4096) = 4096
read(3, "ALE\t\t\tbr_FR.UTF-8\nen_US.UTF-8/XL"..., 4096) = 4096
read(3, "F-8/XLC_LOCALE\t\t\tml_IN.UTF-8\nen_"..., 4096) = 4096
read(3, ".ISO8859-6\niso8859-6/XLC_LOCALE:"..., 4096) = 4096
read(3, "ISO8859-4\niso8859-13/XLC_LOCALE:"..., 4096) = 4096
read(3, "OCALE:           rw_RW.ISO8859-1"..., 4096) = 4096
read(3, "/XLC_LOCALE:\t\t\tde_DE.UTF-8\nen_US"..., 4096) = 4096
close(3)                                = 0
munmap(0x7fecdcfbb000, 4096)            = 0
access("/usr/share/X11/locale/en_US.UTF-8/XLC_LOCALE", R_OK) = 0
open("/usr/share/X11/locale/en_US.UTF-8/XLC_LOCALE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=4206, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbb000
read(3, "#  XLocale Database Sample for e"..., 4096) = 4096
read(3, "ct_encoding\tJISX0201.1976-0:GR\n}"..., 4096) = 110
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fecdcfbb000, 4096)            = 0
brk(0x2566000)                          = 0x2566000
rt_sigaction(SIGPIPE, {SIG_IGN, [PIPE], SA_RESTORER|SA_RESTART, 0x7fecd9d11420}, {SIG_DFL, [], 0}, 8) = 0
access("/etc/gtk-2.0/gtkrc.64", F_OK)   = -1 ENOENT (No such file or directory)
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfbb000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fecdcfbb000, 4096)            = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fecdcf4f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_compat.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\23\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=35712, ...}) = 0
mmap(NULL, 2131288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd4423000
mprotect(0x7fecd442b000, 2093056, PROT_NONE) = 0
mmap(0x7fecd462a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7fecd462a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p@\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=97256, ...}) = 0
mmap(NULL, 2202328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd4209000
mprotect(0x7fecd4220000, 2093056, PROT_NONE) = 0
mmap(0x7fecd441f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7fecd441f000
mmap(0x7fecd4421000, 6872, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecd4421000
close(3)                                = 0
mprotect(0x7fecd441f000, 4096, PROT_READ) = 0
mprotect(0x7fecd462a000, 4096, PROT_READ) = 0
munmap(0x7fecdcf4f000, 172851)          = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fecdcf4f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_nis.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0` \0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=47696, ...}) = 0
mmap(NULL, 2143552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd3ffd000
mprotect(0x7fecd4007000, 2097152, PROT_NONE) = 0
mmap(0x7fecd4207000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa000) = 0x7fecd4207000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\"\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=51736, ...}) = 0
mmap(NULL, 2148088, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd3df0000
mprotect(0x7fecd3dfc000, 2093056, PROT_NONE) = 0
mmap(0x7fecd3ffb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb000) = 0x7fecd3ffb000
close(3)                                = 0
mprotect(0x7fecd3ffb000, 4096, PROT_READ) = 0
mprotect(0x7fecd4207000, 4096, PROT_READ) = 0
munmap(0x7fecdcf4f000, 172851)          = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
fcntl(3, F_GETFD)                       = 0x1 (flags FD_CLOEXEC)
lseek(3, 0, SEEK_CUR)                   = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=1978, ...}) = 0
mmap(NULL, 1978, PROT_READ, MAP_SHARED, 3, 0) = 0x7fecdcfbb000
lseek(3, 1978, SEEK_SET)                = 1978
munmap(0x7fecdcfbb000, 1978)            = 0
close(3)                                = 0
getuid()                                = 0
uname({sys="Linux", node="horizon", ...}) = 0
access("/root/.gtkrc-2.0.64", F_OK)     = -1 ENOENT (No such file or directory)
stat("/usr/lib/liboverlay-scrollbar-0.2.so.0", {st_mode=S_IFREG|0644, st_size=60736, ...}) = 0
open("/usr/lib/liboverlay-scrollbar-0.2.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 B\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=60736, ...}) = 0
mmap(NULL, 2156008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fecd3be1000
mprotect(0x7fecd3bef000, 2093056, PROT_NONE) = 0
mmap(0x7fecd3dee000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd000) = 0x7fecd3dee000
close(3)                                = 0
mprotect(0x7fecd3dee000, 4096, PROT_READ) = 0
open("/usr/share/locale/en_CA/LC_MESSAGES/gtk20-properties.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/gtk20-properties.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=9654, ...}) = 0
mmap(NULL, 9654, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fecdcfb9000
close(3)                                = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/gtk20-properties.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 3
connect(3, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, 20) = 0
getpeername(3, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, [20]) = 0
uname({sys="Linux", node="horizon", ...}) = 0
access("/home/species/.Xauthority", R_OK)  = 0
open("/home/species/.Xauthority", O_RDONLY) = 4
fstat(4, {st_mode=S_IFREG|0600, st_size=52, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfb8000
read(4, "\1\0\0\7horizon\0\0010\0\22MIT-MAGIC-COOKIE"..., 4096) = 52
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7fecdcfb8000, 4096)            = 0
getsockname(3, {sa_family=AF_FILE, NULL}, [2]) = 0
fcntl(3, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(3, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"l\0\v\0\0\0\22\0\20\0\0\0", 12}, {"", 0}, {"MIT-MAGIC-COOKIE-1", 18}, {"\0\0", 2}, {"\260\323\364\222\230\370\311\6v\363\24\"\2674\227%", 16}, {"", 0}], 6) = 48
read(3, "\1\0\v\0\0\0+\2", 8)           = 8
read(3, "`\350\247\0\0\0 \4\377\377\37\0\0\1\0\0\24\0\377\377\1\7\0\0  \10\377\0\0\0\0"..., 2220) = 2220
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\5\0\f\0\0\0BIG-REQUESTS", 20}], 1) = 20
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\1\0\0\0\0\0\1\221\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\221\0\1\0", 4}], 1)       = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\2\0\0\0\0\0\377\377?\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"7\0\5\0\0\0 \4]\1\0\0\10\0\0\0\377\377\377\0\24\0\6\0]\1\0\0\27\0\0\0"..., 44}, {NULL, 0}, {"", 0}], 3) = 44
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\10\4\0\"\0\0\0\37\0\0\0\0\0\0\0\205\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 168
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\5\0\t\0 \4", 8}, {"XKEYBOARD", 9}, {"\0\0\0", 3}], 3) = 20
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\5\0\0\0\0\0\1\223w\250\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\223\0\2\0\1\0\0\0", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\6\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\20\0\5\0\v\0\0\0UTF8_STRING\0\20\0\6\0\20\0\0\0WM_C"..., 916}, {NULL, 0}, {"", 0}], 3) = 916
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\7\0\0\0\0\0\r\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 1088
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\4\0\5\0\0\0", 8}, {"RANDR", 5}, {"\0\0\0", 3}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0)\0\0\0\0\0\1\231{\262\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\10\0\27\0\0\0", 8}, {"Generic Event Extension", 23}, {"\0", 1}], 3) = 32
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0*\0\0\0\0\0\1\214\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\214\0\2\0\1\0\0\0", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0+\0\0\0\0\0\1\0\0\0\0\0\0\0\0\31^\2\0\0\0\0p\24\177\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\231\0\3\0\1\0\0\0\4\0\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0,\0\0\0\0\0\1\0\0\0\3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\231\31\2\0]\1\0\0", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0-\0\r\0\0\0hS\0\0\355\212\0\0\1\0\1\0\1\0\t\0\223\5L\0\0\0\0\0"..., 4096) = 84
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\231\t\3\0c\1\0\0\355\212\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\31.\0\5\0\0\0hS\0\0b\1\0\0\0\0\0\0\0\0\0\0\0\0\1\0\1\0\0\0"..., 4096) = 52
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\231\24\3\0b\1\0\0\355\212\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0/\0\2\0\0\0hS\0\0\0\0\0\0\220\v\32\4d\1\0\0\1\0\1\0\1\0\1\0"..., 4096) = 40
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\24\4\0\10\0\0\0", 8}, {"XINERAMA", 8}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0000\0\0\0\0\0\1\226\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\24\4\0\10\0\0\0", 8}, {"XINERAMA", 8}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0001\0\0\0\0\0\1\226\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\226\4\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0312\0\0\0\0\0\1\0\0\0\0\0\0\0`|!\2\0\0\0\0\223\5L\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\226\5\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3573\0\4\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\200\357~\0\0\0\0\0"..., 4096) = 48
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\2\5\4\0]\1\0\0\0\10\0\0\0\0\2\0\231\4\3\0]\1\0\0\v\0\0\0\20\0\6\0"..., 96}, {NULL, 0}, {"", 0}], 3) = 96
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0006\0\0\0\0\0000\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 96
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\3\5\2\0]\1\0\0\16\10\2\0]\1\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0009\0\3\0\0\0!\0\0\0\1\0\0\1\377\377\377\377\0\0\0\0\0\1\2\0 \0\0\0"..., 4096) = 76
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\2\5\4\0]\1\0\0\0\10\0\0\0\0\2\0$\4\1\0\27\1\2\0000\1\0\0", 28}, {NULL, 0}, {"", 0}], 3) = 28
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0=\0\0\0\0\0\n\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\2\5\4\0\n\0\0\1\0\10\0\0\0\0B\0%\4\1\0", 20}, {NULL, 0}, {"", 0}], 3) = 20
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\3\5\2\0\n\0\0\1\16\10\2\0\n\0\0\1", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0@\0\3\0\0\0!\0\0\0\1\0\0\1\377\377\377\377\0\0\0\0\0\1\0\0 \0\0\0"..., 4096) = 76
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\17\5\2\0\n\0\0\1", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0B\0\0\0\0\0]\1\0\0]\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\24\0\6\0\n\0\0\0011\1\0\0001\1\0\0\0\0\0\0\377\377\377\377", 24}, {NULL, 0}, {"", 0}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\10C\0u\1\0\0001\1\0\0\0\0\0\0\324\5\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 1524
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
uname({sys="Linux", node="horizon", ...}) = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\1\30\r\0\1\0 \4]\1\0\0\n\0\n\0\n\0\n\0\0\0\1\0!\0\0\0\32(\0\0"..., 532}, {NULL, 0}, {"", 0}], 3) = 532
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0E\0\1\0 \4\34\1\0\0\245\221\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 352
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\7\0\1\0 \0047\1\0\0!\0\0\0 \0\n\0\1\0\0\0\2\0 \4b(\4\0"..., 36}, {"XFIXES", 6}, {"\0\0", 2}], 3) = 44
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0S\0\1\0 \0047\1\0\0\246\221\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 64
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\227\0\3\0\5\0\0\0\0\0\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0U\0\0\0\0\0\5\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\5\0\t\0\0\0", 8}, {"Composite", 9}, {"\0\0\0", 3}], 3) = 20
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0V\0\0\0\0\0\1\233\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\233\0\3\0\0\0\0\0\4\0\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\31W\0\0\0\0\0\0\0\0\0\4\0\0\0\0\31^\2\0\0\0\0p\24\177\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\4\0\6\0\0\0", 8}, {"DAMAGE", 6}, {"\0\0", 2}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0X\0\0\0\0\0\1\234}\265\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\234\0\3\0\1\0\0\0\1\0\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\31Y\0\0\0\0\0\1\0\0\0\1\0\0\0\0\31^\2\0\0\0\0p\24\177\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\34\0Y\0\1\0 \4\213\1\0\0\247\221\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
writev(3, [{"b\0\4\0\5\0\0\0", 8}, {"SHAPE", 5}, {"\0\0\0", 3}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0Z\0\0\0\0\0\1\215b\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\215\0\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0[\0\0\0\0\0\1\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\0\2\0]\1\0\0", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\\\0\0\0\0\0]\1\0\0\37\2\200\1c\2\32\1c\2\32\1\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"+\0\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\2]\0\0\0\0\0\7\0\300\3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
uname({sys="Linux", node="horizon", ...}) = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\t\0\1\0 \4\"\0\0\0\37\0\0\0\10\0\n\0\t\0\0\0synaptic"..., 240}, {NULL, 0}, {"", 0}], 3) = 240
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0^\0\1\0 \4\"\0\0\0\252\221\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 192
brk(0x2587000)                          = 0x2587000
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\3\0\4\0 \4", 8}, {"SYNC", 4}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0f\0\0\0\0\0\1\222u\245\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\222\0\2\0\3\1 \4", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0g\0\0\0\0\0\3\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\3\0\4\0 \4", 8}, {"SYNC", 4}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0h\0\0\0\0\0\1\222u\245\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\4\0\7\0 \4", 8}, {"MIT-SHM", 7}, {"\0", 1}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0i\0\0\0\0\0\1\216c\237\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\216\0\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0j\0\0\0\0\0\1\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
eventfd2(0, O_NONBLOCK|O_CLOEXEC)       = 4
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\6\0\17\0 \4", 8}, {"XInputExtension", 15}, {"\0", 1}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0k\0\0\0\0\0\1\217d\240\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\0\6\0\17\0 \4", 8}, {"XInputExtension", 15}, {"\0", 1}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0l\0\0\0\0\0\1\217d\240\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\217\1\6\0\17\0 \4", 8}, {"XInputExtension", 15}, {"\0", 1}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1m\0\0\0\0\0\2\0\1\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\1\6\0\17\0 \4", 8}, {"XInputExtension", 15}, {"\0", 1}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0n\0\0\0\0\0\1\217d\240\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\217\1\6\0\17\0 \4", 8}, {"XInputExtension", 15}, {"\0", 1}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1o\0\0\0\0\0\2\0\1\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\217\2\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\2p\0\210\0\0\0\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 576
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\217\3\2\0\4\0 \4", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3q\0\2\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 40
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\217\3\2\0\v\0 \4", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3r\0\3\0\0\0\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 44
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\217\3\2\0\f\0 \4", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3s\0\3\0\0\0\5\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 44
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\227\2\4\0\1\0 \4\30\1\0\0\7\0\0\0\27\0\2\0\30\1\0\0", 24}, {NULL, 0}, {"", 0}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0u\0\0\0\0\0\221\0\200\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
open("/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=26066, ...}) = 0
mmap(NULL, 26066, PROT_READ, MAP_SHARED, 5, 0) = 0x7fecdcfb2000
close(5)                                = 0
futex(0x7fecda074190, FUTEX_WAKE_PRIVATE, 2147483647) = 0
lstat("/etc/gtk-2.0/gtkrc", 0x7fff37c30790) = -1 ENOENT (No such file or directory)
access("/etc/gtk-2.0/gtkrc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/etc/gtk-2.0/gtkrc.en", F_OK)   = -1 ENOENT (No such file or directory)
lstat("/root/.gtkrc-2.0", 0x7fff37c30790) = -1 ENOENT (No such file or directory)
access("/root/.gtkrc-2.0.en_CA", F_OK)  = -1 ENOENT (No such file or directory)
access("/root/.gtkrc-2.0.en", F_OK)     = -1 ENOENT (No such file or directory)
access("/root/.themes/Radiance/gtk-2.0/gtkrc", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/gtkrc", F_OK) = 0
lstat("/usr/share/themes/Radiance/gtk-2.0/gtkrc", {st_mode=S_IFREG|0644, st_size=18000, ...}) = 0
open("/usr/share/themes/Radiance/gtk-2.0/gtkrc", O_RDONLY) = 5
read(5, "gtk-color-scheme = \"base_color:#"..., 4000) = 4000
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/x86_64-pc-linux-gnu/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/x86_64-pc-linux-gnu/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libmurrine.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libmurrine.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so", F_OK) = 0
stat("/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so", {st_mode=S_IFREG|0644, st_size=200240, ...}) = 0
open("/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so", O_RDONLY) = 6
read(6, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200V\0\0\0\0\0\0"..., 832) = 832
fstat(6, {st_mode=S_IFREG|0644, st_size=200240, ...}) = 0
mmap(NULL, 2295488, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 6, 0) = 0x7fecd39b0000
mprotect(0x7fecd39df000, 2097152, PROT_NONE) = 0
mmap(0x7fecd3bdf000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 6, 0x2f000) = 0x7fecd3bdf000
close(6)                                = 0
mprotect(0x7fecd3bdf000, 4096, PROT_READ) = 0
read(5, "\"#dfd7cf\", shade (0.96, \"#cdcdcd"..., 4000) = 4000
read(5, "GtkSeparatorMenuItem::horizontal"..., 4000) = 4000
read(5, "###########\n\n# The default style"..., 4000) = 4000
read(5, "################################"..., 4000) = 2000
access("/usr/share/themes/Radiance/gtk-2.0/apps/chromium.rc", F_OK) = 0
lstat("/usr/share/themes/Radiance/gtk-2.0/apps/chromium.rc", {st_mode=S_IFREG|0644, st_size=1081, ...}) = 0
open("/usr/share/themes/Radiance/gtk-2.0/apps/chromium.rc", O_RDONLY) = 6
brk(0x25a8000)                          = 0x25a8000
read(6, "# =============================="..., 4000) = 1081
read(6, "", 4000)                       = 0
close(6)                                = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/chromium.rc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/chromium.rc.en", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/ff.rc", F_OK) = 0
lstat("/usr/share/themes/Radiance/gtk-2.0/apps/ff.rc", {st_mode=S_IFREG|0644, st_size=1002, ...}) = 0
open("/usr/share/themes/Radiance/gtk-2.0/apps/ff.rc", O_RDONLY) = 6
read(6, "# =============================="..., 4000) = 1002
read(6, "", 4000)                       = 0
close(6)                                = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/ff.rc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/ff.rc.en", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc", F_OK) = 0
lstat("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc", {st_mode=S_IFREG|0644, st_size=3065, ...}) = 0
open("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc", O_RDONLY) = 6
read(6, "# =============================="..., 4000) = 3065
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel.png", F_OK) = 0
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libpixmap.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libpixmap.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/engines/libpixmap.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/engines/libpixmap.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/engines/libpixmap.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/engines/libpixmap.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/engines/libpixmap.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/engines/libpixmap.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libpixmap.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/engines/libpixmap.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so", F_OK) = 0
stat("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so", {st_mode=S_IFREG|0644, st_size=43472, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so", O_RDONLY) = 7
read(7, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P#\0\0\0\0\0\0"..., 832) = 832
fstat(7, {st_mode=S_IFREG|0644, st_size=43472, ...}) = 0
mmap(NULL, 2138704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 7, 0) = 0x7fecd37a5000
mprotect(0x7fecd37ae000, 2097152, PROT_NONE) = 0
mmap(0x7fecd39ae000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 7, 0x9000) = 0x7fecd39ae000
close(7)                                = 0
mprotect(0x7fecd39ae000, 4096, PROT_READ) = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel-button-inactive.png", F_OK) = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel-button-hover.png", F_OK) = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel-button-hover.png", F_OK) = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel-button-hover.png", F_OK) = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel-button-active.png", F_OK) = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/img/panel-button-inactive.png", F_OK) = 0
read(6, "", 4000)                       = 0
close(6)                                = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc.en", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-terminal.rc", F_OK) = 0
lstat("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-terminal.rc", {st_mode=S_IFREG|0644, st_size=1011, ...}) = 0
open("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-terminal.rc", O_RDONLY) = 6
read(6, "# =============================="..., 4000) = 1011
read(6, "", 4000)                       = 0
close(6)                                = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-terminal.rc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/gnome-terminal.rc.en", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/nautilus.rc", F_OK) = 0
lstat("/usr/share/themes/Radiance/gtk-2.0/apps/nautilus.rc", {st_mode=S_IFREG|0644, st_size=461, ...}) = 0
open("/usr/share/themes/Radiance/gtk-2.0/apps/nautilus.rc", O_RDONLY) = 6
read(6, "# =============================="..., 4000) = 461
read(6, "", 4000)                       = 0
close(6)                                = 0
access("/usr/share/themes/Radiance/gtk-2.0/apps/nautilus.rc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/apps/nautilus.rc.en", F_OK) = -1 ENOENT (No such file or directory)
read(5, "", 4000)                       = 0
close(5)                                = 0
access("/usr/share/themes/Radiance/gtk-2.0/gtkrc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Radiance/gtk-2.0/gtkrc.en", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.themes/Default/gtk-2.0-key/gtkrc", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Default/gtk-2.0-key/gtkrc", F_OK) = 0
lstat("/usr/share/themes/Default/gtk-2.0-key/gtkrc", {st_mode=S_IFREG|0644, st_size=82, ...}) = 0
open("/usr/share/themes/Default/gtk-2.0-key/gtkrc", O_RDONLY) = 5
read(5, "#\n# Default keybinding set. Empt"..., 4000) = 82
read(5, "", 4000)                       = 0
close(5)                                = 0
access("/usr/share/themes/Default/gtk-2.0-key/gtkrc.en_CA", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Default/gtk-2.0-key/gtkrc.en", F_OK) = -1 ENOENT (No such file or directory)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"b\2\4\0\6\0 \4", 8}, {"RENDER", 6}, {"\0\0", 2}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0v\0\0\0\0\0\1\230\0\255\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\0\3\0\0\0\0\0\v\0\0\0\230\1\1\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0w\0\0\0\0\0\0\0\0\0\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 1588
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
uname({sys="Linux", node="horizon", ...}) = 0
open("/home/species/.Xdefaults-horizon", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/x86_64-pc-linux-gnu/modules/libgail.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/x86_64-pc-linux-gnu/modules/libgail.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libgail.so", F_OK) = 0
stat("/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libgail.so", {st_mode=S_IFREG|0644, st_size=318192, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libgail.so", O_RDONLY) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\366\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=318192, ...}) = 0
mmap(NULL, 2414920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fecd3557000
mprotect(0x7fecd35a3000, 2093056, PROT_NONE) = 0
mmap(0x7fecd37a2000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x4b000) = 0x7fecd37a2000
close(5)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fecdcf4f000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgailutil.so.18", O_RDONLY) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340'\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=31304, ...}) = 0
mmap(NULL, 2126568, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fecd334f000
mprotect(0x7fecd3356000, 2093056, PROT_NONE) = 0
mmap(0x7fecd3555000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x6000) = 0x7fecd3555000
close(5)                                = 0
mprotect(0x7fecd3555000, 4096, PROT_READ) = 0
mprotect(0x7fecd37a2000, 4096, PROT_READ) = 0
munmap(0x7fecdcf4f000, 172851)          = 0
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/2.10.0/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/x86_64-pc-linux-gnu/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/root/.gtk-2.0/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/x86_64-pc-linux-gnu/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/x86_64-pc-linux-gnu/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/x86_64-pc-linux-gnu/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/2.10.0/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/x86_64-pc-linux-gnu/modules/libatk-bridge.so", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/x86_64-pc-linux-gnu/modules/libatk-bridge.la", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/gtk-2.0/modules/libatk-bridge.so", F_OK) = 0
stat("/usr/lib/gtk-2.0/modules/libatk-bridge.so", {st_mode=S_IFREG|0644, st_size=176016, ...}) = 0
open("/usr/lib/gtk-2.0/modules/libatk-bridge.so", O_RDONLY) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\264\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=176016, ...}) = 0
mmap(NULL, 2272112, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fecd3124000
mprotect(0x7fecd314d000, 2093056, PROT_NONE) = 0
mmap(0x7fecd334c000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x28000) = 0x7fecd334c000
close(5)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fecdcf4f000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libatspi.so.0", O_RDONLY) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\244\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=138840, ...}) = 0
mmap(NULL, 2234432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fecd2f02000
mprotect(0x7fecd2f23000, 2093056, PROT_NONE) = 0
mmap(0x7fecd3122000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x20000) = 0x7fecd3122000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdbus-1.so.3", O_RDONLY) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240g\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=272296, ...}) = 0
mmap(NULL, 2368416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7fecd2cbf000
mprotect(0x7fecd2d01000, 2093056, PROT_NONE) = 0
mmap(0x7fecd2f00000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x41000) = 0x7fecd2f00000
close(5)                                = 0
mprotect(0x7fecd2f00000, 4096, PROT_READ) = 0
mprotect(0x7fecd3122000, 4096, PROT_READ) = 0
mprotect(0x7fecd334c000, 4096, PROT_READ) = 0
munmap(0x7fecdcf4f000, 172851)          = 0
brk(0x25c9000)                          = 0x25c9000
open("/usr/share/locale/en_CA/LC_MESSAGES/atk10.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/atk10.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/atk10.mo", O_RDONLY) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=2135, ...}) = 0
mmap(NULL, 2135, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7fecdcfb1000
close(5)                                = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/atk10.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 5
connect(5, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, 20) = 0
getpeername(5, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, [20]) = 0
uname({sys="Linux", node="horizon", ...}) = 0
access("/home/species/.Xauthority", R_OK)  = 0
open("/home/species/.Xauthority", O_RDONLY) = 6
fstat(6, {st_mode=S_IFREG|0600, st_size=52, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfb0000
read(6, "\1\0\0\7horizon\0\0010\0\22MIT-MAGIC-COOKIE"..., 4096) = 52
read(6, "", 4096)                       = 0
close(6)                                = 0
munmap(0x7fecdcfb0000, 4096)            = 0
getsockname(5, {sa_family=AF_FILE, NULL}, [2]) = 0
fcntl(5, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(5, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
fcntl(5, F_SETFD, FD_CLOEXEC)           = 0
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"l\0\v\0\0\0\22\0\20\0\0\0", 12}, {"", 0}, {"MIT-MAGIC-COOKIE-1", 18}, {"\0\0", 2}, {"\260\323\364\222\230\370\311\6v\363\24\"\2674\227%", 16}, {"", 0}], 6) = 48
read(5, "\1\0\v\0\0\0+\2", 8)           = 8
read(5, "`\350\247\0\0\0@\4\377\377\37\0\0\1\0\0\24\0\377\377\1\7\0\0  \10\377\0\0\0\0"..., 2220) = 2220
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"b\0\5\0\f\0\0\0BIG-REQUESTS", 20}], 1) = 20
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\0\1\0\0\0\0\0\1\221\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"\221\0\1\0", 4}], 1)       = 4
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\0\2\0\0\0\0\0\377\377?\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"7\0\5\0\0\0@\4]\1\0\0\10\0\0\0\377\377\377\0\24\0\6\0]\1\0\0\27\0\0\0"..., 44}, {NULL, 0}, {"", 0}], 3) = 44
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\10\4\0\"\0\0\0\37\0\0\0\0\0\0\0\205\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 168
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"b\0\5\0\t\0@\4", 8}, {"XKEYBOARD", 9}, {"\0\0\0", 3}], 3) = 20
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\0\5\0\0\0\0\0\1\223w\250\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"\223\0\2\0\1\0\0\0", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\1\6\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"\20\0\5\0\n\0\0\0AT_SPI_BUS\377\0", 20}, {NULL, 0}, {"", 0}], 3) = 20
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\0\7\0\0\0\0\0[\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"\24\0\6\0]\1\0\0[\1\0\0\37\0\0\0\0\0\0\0\0 \0\0", 24}, {NULL, 0}, {"", 0}], 3) = 24
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\10\10\0\22\0\0\0\37\0\0\0\0\0\0\0H\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 104
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
writev(5, [{"<\0\2\0\0\0@\4+\1\1\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "\1\2\n\0\0\0\0\0\7\0\300\3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x25b2854, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
close(5)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 5
connect(5, {sa_family=AF_FILE, path=@"/tmp/dbus-kCw6N7Jm5d"}, 23) = 0
fcntl(5, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(5, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
geteuid()                               = 0
getsockname(5, {sa_family=AF_FILE, NULL}, [2]) = 0
poll([{fd=5, events=POLLOUT}], 1, 0)    = 1 ([{fd=5, revents=POLLOUT}])
sendto(5, "\0", 1, MSG_NOSIGNAL, NULL, 0) = 1
sendto(5, "AUTH EXTERNAL 30\r\n", 18, MSG_NOSIGNAL, NULL, 0) = 18
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "OK a10b9186008bad915a7c3ee300000"..., 2048) = 37
poll([{fd=5, events=POLLOUT}], 1, -1)   = 1 ([{fd=5, revents=POLLOUT}])
sendto(5, "NEGOTIATE_UNIX_FD\r\n", 19, MSG_NOSIGNAL, NULL, 0) = 19
poll([{fd=5, events=POLLIN}], 1, -1)    = 1 ([{fd=5, revents=POLLIN}])
read(5, "AGREE_UNIX_FD\r\n", 2048)      = 15
poll([{fd=5, events=POLLOUT}], 1, -1)   = 1 ([{fd=5, revents=POLLOUT}])
sendto(5, "BEGIN\r\n", 7, MSG_NOSIGNAL, NULL, 0) = 7
poll([{fd=5, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=5, revents=POLLOUT}])
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\0\0\0\0\1\0\0\0n\0\0\0\1\1o\0\25\0\0\0/org/fre"..., 128}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 128
poll([{fd=5, events=POLLIN}], 1, 25000) = 1 ([{fd=5, revents=POLLIN}])
recvmsg(5, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\n\0\0\0\1\0\0\0=\0\0\0\6\1s\0\5\0\0\0:1.36\0\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 260
recvmsg(5, 0x7fff37c305d0, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
eventfd2(0, O_NONBLOCK|O_CLOEXEC)       = 6
fstat(5, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl(5, F_GETFL)                       = 0x802 (flags O_RDWR|O_NONBLOCK)
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\1\1Y\0\0\0\2\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/fre"..., 144}, {"T\0\0\0type='signal', interface='or"..., 89}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 233
clock_getres(CLOCK_MONOTONIC, {0, 1})   = 0
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\0010\0\0\0\3\0\0\0\202\0\0\0\1\1o\0\37\0\0\0/org/a11"..., 152}, {"\5\0\0\0:1.36\0\0\0\37\0\0\0/org/a11y/atspi/"..., 48}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 200
mkdir("/tmp/at-spi2/", 01777)           = -1 EEXIST (File exists)
chmod("/tmp/at-spi2/", 01777)           = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 7
stat("/tmp/at-spi2/socket-4244-1804289383", 0x7fff37c30680) = -1 ENOENT (No such file or directory)
setsockopt(7, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
bind(7, {sa_family=AF_FILE, path="/tmp/at-spi2/socket-4244-1804289383"}, 37) = 0
listen(7, 30)                           = 0
fcntl(7, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(7, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
chmod("/tmp/at-spi2/socket-4244-1804289383", 0777) = 0
open("/dev/urandom", O_RDONLY)          = 8
read(8, "Xl\207\351\251\245{\220\366\253\377w", 12) = 12
close(8)                                = 0
fstat(7, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl(7, F_GETFL)                       = 0x802 (flags O_RDWR|O_NONBLOCK)
getuid()                                = 0
stat("/var/lib/apt/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
brk(0x25ea000)                          = 0x25ea000
open("/etc/apt/apt.conf.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 8
fcntl(8, F_GETFD)                       = 0x1 (flags FD_CLOEXEC)
getdents(8, /* 14 entries */, 32768)    = 464
getdents(8, /* 0 entries */, 32768)     = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/00trustcdrom", O_RDONLY) = 8
read(8, "APT::Authentication::TrustCDROM "..., 8191) = 40
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/01autoremove", O_RDONLY) = 8
read(8, "APT\n{\n  NeverAutoRemove\n  {\n\t\"^f"..., 8191) = 430
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/05aptitude", O_RDONLY) = 8
read(8, "aptitude::Keep-Unused-Pattern \"^"..., 8191) = 157
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/10periodic", O_RDONLY) = 8
read(8, "APT::Periodic::Update-Package-Li"..., 8191) = 129
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/15update-stamp", O_RDONLY) = 8
read(8, "APT::Update::Post-Invoke-Success"..., 8191) = 108
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/20archive", O_RDONLY) = 8
read(8, "APT::Archives::MaxAge \"30\";\nAPT:"..., 8191) = 85
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/20changelog", O_RDONLY) = 8
read(8, "// Server information for apt-ch"..., 8191) = 123
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/20dbus", O_RDONLY) = 8
read(8, "// Notify all clients to reload "..., 8191) = 243
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/50unattended-upgrades", O_RDONLY) = 8
read(8, "// Automatically upgrade package"..., 8191) = 1921
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY) = 8
read(8, "// Pre-configure all packages wi"..., 8191) = 182
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/99synaptic", O_RDONLY) = 8
read(8, "APT::Install-Recommends \"true\";\n", 8191) = 32
read(8, "", 8191)                       = 0
close(8)                                = 0
open("/etc/apt/apt.conf.d/99update-notifier", O_RDONLY) = 8
read(8, "DPkg::Post-Invoke {\"if [ -d /var"..., 8191) = 231
read(8, "", 8191)                       = 0
close(8)                                = 0
stat("/etc/apt/apt.conf", 0x7fff37c30ad0) = -1 ENOENT (No such file or directory)
stat("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=2423558, ...}) = 0
stat("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=249328, ...}) = 0
stat("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=11, ...}) = 0
stat("", 0x7fff37c30e10)                = -1 ENOENT (No such file or directory)
getuid()                                = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 8
lseek(8, 0, SEEK_CUR)                   = 0
fstat(8, {st_mode=S_IFREG|0644, st_size=1978, ...}) = 0
mmap(NULL, 1978, PROT_READ, MAP_SHARED, 8, 0) = 0x7fecdcfb0000
lseek(8, 1978, SEEK_SET)                = 1978
munmap(0x7fecdcfb0000, 1978)            = 0
close(8)                                = 0
stat("/root/.synaptic", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
open("/root/.synaptic/synaptic.conf", O_RDONLY) = 8
read(8, "Synaptic \"\" {\n  ViewMode \"1\";\n  "..., 8191) = 1709
read(8, "", 8191)                       = 0
close(8)                                = 0
getuid()                                = 0
getuid()                                = 0
getuid()                                = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 8
lseek(8, 0, SEEK_CUR)                   = 0
fstat(8, {st_mode=S_IFREG|0644, st_size=1978, ...}) = 0
mmap(NULL, 1978, PROT_READ, MAP_SHARED, 8, 0) = 0x7fecdcfb0000
lseek(8, 1978, SEEK_SET)                = 1978
munmap(0x7fecdcfb0000, 1978)            = 0
close(8)                                = 0
stat("/root/.synaptic", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
getuid()                                = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 8
lseek(8, 0, SEEK_CUR)                   = 0
fstat(8, {st_mode=S_IFREG|0644, st_size=1978, ...}) = 0
mmap(NULL, 1978, PROT_READ, MAP_SHARED, 8, 0) = 0x7fecdcfb0000
lseek(8, 1978, SEEK_SET)                = 1978
munmap(0x7fecdcfb0000, 1978)            = 0
close(8)                                = 0
stat("/root/.synaptic", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
open("/root/.synaptic/lock", O_RDONLY)  = 8
fcntl(8, F_GETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0, pid=18446744073116829751}) = 0
close(8)                                = 0
open("/var/lib/dpkg/lock", O_RDONLY)    = 8
fcntl(8, F_GETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0, pid=4}) = 0
close(8)                                = 0
open("/root/.synaptic/lock", O_RDWR|O_CREAT|O_NOFOLLOW, 0640) = 8
fcntl(8, F_SETFD, FD_CLOEXEC)           = 0
fcntl(8, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
open("/root/.synaptic/options", O_RDONLY) = 9
read(9, "", 8191)                       = 0
getuid()                                = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 10
lseek(10, 0, SEEK_CUR)                  = 0
fstat(10, {st_mode=S_IFREG|0644, st_size=1978, ...}) = 0
mmap(NULL, 1978, PROT_READ, MAP_SHARED, 10, 0) = 0x7fecdcfb0000
lseek(10, 1978, SEEK_SET)               = 1978
munmap(0x7fecdcfb0000, 1978)            = 0
close(10)                               = 0
stat("/root/.synaptic", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat("/root/.synaptic/preferences", 0x7fff37c30190) = -1 ENOENT (No such file or directory)
stat("/var/lib/synaptic", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/var/lib/synaptic/preferences", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
open("/var/lib/synaptic/preferences", O_RDONLY) = 10
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
read(10, "", 32768)                     = 0
stat("/usr/bin/deborphan", 0x7fff37c30030) = -1 ENOENT (No such file or directory)
open("/var/lib/dpkg/info", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 11
getdents(11, /* 741 entries */, 32768)  = 32760
getdents(11, /* 735 entries */, 32768)  = 32768
getdents(11, /* 735 entries */, 32768)  = 32728
getdents(11, /* 739 entries */, 32768)  = 32768
getdents(11, /* 740 entries */, 32768)  = 32760
getdents(11, /* 740 entries */, 32768)  = 32728
getdents(11, /* 741 entries */, 32768)  = 32760
getdents(11, /* 734 entries */, 32768)  = 32768
getdents(11, /* 736 entries */, 32768)  = 32760
getdents(11, /* 735 entries */, 32768)  = 32760
getdents(11, /* 740 entries */, 32768)  = 32760
getdents(11, /* 739 entries */, 32768)  = 32728
getdents(11, /* 738 entries */, 32768)  = 32744
getdents(11, /* 336 entries */, 32768)  = 14840
getdents(11, /* 0 entries */, 32768)    = 0
close(11)                               = 0
close(10)                               = 0
close(9)                                = 0
pipe2([9, 10], O_CLOEXEC)               = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fecdcf7bc90) = 4245
close(10)                               = 0
fcntl(9, F_SETFD, 0)                    = 0
fstat(9, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfb0000
read(9, "oneiric\n", 4096)              = 8
close(9)                                = 0
wait4(4245, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 4245
--- SIGCHLD (Child exited) @ 0 (0) ---
munmap(0x7fecdcfb0000, 4096)            = 0
open("/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=4486, ...}) = 0
read(9, "# GdkPixbuf Image Loader Modules"..., 1024) = 1024
read(9, "oaders/libpixbufloader-tiff.so\"\n"..., 1024) = 1024
read(9, "ers/libpixbufloader-svg.so\"\n\"svg"..., 1024) = 1024
read(9, "\"gif\" 4 \"gdk-pixbuf\" \"The GIF im"..., 1024) = 1024
read(9, "xxx    \" 100\n\"abcdidat\" \"xxxx   "..., 1024) = 390
read(9, "", 1024)                       = 0
close(9)                                = 0
stat("/root/.icons/ubuntu-mono-light", 0x7fff37c30c30) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/ubuntu-mono-light", 0x7fff37c30c30) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/ubuntu-mono-light", 0x7fff37c30c30) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/ubuntu-mono-light", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/share/pixmaps/ubuntu-mono-light", 0x7fff37c30c30) = -1 ENOENT (No such file or directory)
stat("/usr/share/pixmaps/ubuntu-mono-light", 0x7fff37c30c30) = -1 ENOENT (No such file or directory)
stat("/root/.icons/ubuntu-mono-light/index.theme", 0x7fff37c30b10) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/ubuntu-mono-light/index.theme", 0x7fff37c30b10) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/ubuntu-mono-light/index.theme", 0x7fff37c30b10) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/ubuntu-mono-light/index.theme", {st_mode=S_IFREG|0644, st_size=2002, ...}) = 0
open("/usr/share/icons/ubuntu-mono-light/index.theme", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2002, ...}) = 0
read(9, "[Icon Theme]\nName=Ubuntu-Mono-Li"..., 4096) = 2002
read(9, "", 4096)                       = 0
open("/usr/share/locale/en_CA/LC_MESSAGES/glib20.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/glib20.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/glib20.mo", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=1602, ...}) = 0
mmap(NULL, 1602, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7fecdcfb0000
close(10)                               = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/glib20.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
close(9)                                = 0
stat("/usr/share/icons/ubuntu-mono-light/actions/16", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/share/icons/ubuntu-mono-light", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/share/icons/ubuntu-mono-light/icon-theme.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=142240, ...}) = 0
open("/usr/share/icons/ubuntu-mono-light/icon-theme.cache", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=142240, ...}) = 0
mmap(NULL, 142240, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7fecdcf57000
close(10)                               = 0
close(9)                                = 0
stat("/root/.icons/Humanity", 0x7fff37c30ae0) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/Humanity", 0x7fff37c30ae0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/Humanity", 0x7fff37c30ae0) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/Humanity", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/share/pixmaps/Humanity", 0x7fff37c30ae0) = -1 ENOENT (No such file or directory)
stat("/usr/share/pixmaps/Humanity", 0x7fff37c30ae0) = -1 ENOENT (No such file or directory)
stat("/root/.icons/Humanity/index.theme", 0x7fff37c309c0) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/Humanity/index.theme", 0x7fff37c309c0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/Humanity/index.theme", 0x7fff37c309c0) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/Humanity/index.theme", {st_mode=S_IFREG|0644, st_size=4239, ...}) = 0
open("/usr/share/icons/Humanity/index.theme", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=4239, ...}) = 0
read(9, "[Icon Theme]\nName=Humanity\nComme"..., 4096) = 4096
read(9, "ixed\n\n[stock/24]\nSize=24\nContext"..., 4096) = 143
read(9, "", 4096)                       = 0
close(9)                                = 0
brk(0x260b000)                          = 0x260b000
stat("/usr/share/icons/Humanity/actions/16", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
stat("/usr/share/icons/Humanity", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/share/icons/Humanity/icon-theme.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=954180, ...}) = 0
open("/usr/share/icons/Humanity/icon-theme.cache", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=954180, ...}) = 0
mmap(NULL, 954180, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7fecdce6e000
close(10)                               = 0
close(9)                                = 0
stat("/root/.icons/gnome", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/gnome", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/gnome", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/gnome", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/share/pixmaps/gnome", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/usr/share/pixmaps/gnome", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/root/.icons/gnome/index.theme", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/gnome/index.theme", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/gnome/index.theme", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/gnome/index.theme", {st_mode=S_IFREG|0644, st_size=11409, ...}) = 0
open("/usr/share/icons/gnome/index.theme", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=11409, ...}) = 0
read(9, "[Icon Theme]\nName=GNOME\nName[af]"..., 4096) = 4096
read(9, " \340\244\252\340\245\215\340\244\260\340\244\270\340\244\202\340\244\227\nComment[mg]="..., 4096) = 4096
read(9, "2\nType=Fixed\n\n[22x22/categories]"..., 4096) = 3217
read(9, "", 4096)                       = 0
close(9)                                = 0
stat("/usr/share/icons/gnome/8x8/emblems", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/share/icons/gnome", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/share/icons/gnome/icon-theme.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=60181836, ...}) = 0
open("/usr/share/icons/gnome/icon-theme.cache", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=60181836, ...}) = 0
mmap(NULL, 60181836, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7feccf35a000
close(10)                               = 0
close(9)                                = 0
brk(0x262c000)                          = 0x262c000
stat("/root/.icons/hicolor", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/hicolor", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/share/icons/hicolor", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/share/pixmaps/hicolor", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/usr/share/pixmaps/hicolor", 0x7fff37c30990) = -1 ENOENT (No such file or directory)
stat("/root/.icons/hicolor/index.theme", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons/hicolor/index.theme", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/index.theme", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/hicolor/index.theme", {st_mode=S_IFREG|0644, st_size=24671, ...}) = 0
open("/usr/share/icons/hicolor/index.theme", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=24671, ...}) = 0
read(9, "[Icon Theme]\nName=Hicolor\nCommen"..., 4096) = 4096
read(9, "ems,192x192/intl,192x192/mimetyp"..., 4096) = 4096
read(9, "ize=24\nContext=Applications\nType"..., 4096) = 4096
read(9, "nimations]\nSize=48\nContext=Anima"..., 4096) = 4096
read(9, "d\n\n[96x96/actions]\nSize=96\nConte"..., 4096) = 4096
brk(0x264d000)                          = 0x264d000
read(9, "2\nContext=Stock\nType=Threshold\n\n"..., 4096) = 4096
read(9, "pe=Scalable\n\n[scalable/stock/tex"..., 4096) = 95
read(9, "", 4096)                       = 0
close(9)                                = 0
stat("/usr/local/share/icons/hicolor/16x16/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/share/icons/hicolor/16x16/actions", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/share/icons/hicolor", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/share/icons/hicolor/icon-theme.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=18233176, ...}) = 0
open("/usr/share/icons/hicolor/icon-theme.cache", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=18233176, ...}) = 0
mmap(NULL, 18233176, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7fecce1f6000
close(10)                               = 0
close(9)                                = 0
stat("/usr/local/share/icons/hicolor/16x16/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/16x16/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
brk(0x266e000)                          = 0x266e000
stat("/usr/local/share/icons/hicolor/22x22/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/22x22/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/24x24/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/32x32/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/36x36/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/48x48/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/64x64/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
brk(0x268f000)                          = 0x268f000
stat("/usr/local/share/icons/hicolor/72x72/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/72x72/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/96x96/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/apps", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/share/icons/hicolor", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/local/share/icons/hicolor/icon-theme.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share/icons/hicolor/128x128/apps", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
getdents(9, /* 2 entries */, 32768)     = 48
getdents(9, /* 0 entries */, 32768)     = 0
close(9)                                = 0
stat("/usr/local/share/icons/hicolor/128x128/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/128x128/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/192x192/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/256x256/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/actions", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/animations", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/apps", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/categories", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/devices", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/emblems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/emotes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/filesystems", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/intl", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/mimetypes", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/places", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/status", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/chart", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/code", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/data", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/form", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/image", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/io", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/media", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/navigation", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/net", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/object", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/table", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons/hicolor/scalable/stock/text", 0x7fff37c30870) = -1 ENOENT (No such file or directory)
stat("/root/.icons", 0x7fff37c30d40)    = -1 ENOENT (No such file or directory)
stat("/root/.local/share/icons", 0x7fff37c30d40) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/icons", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/share/icons", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/local/share/icons/icon-theme.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share/icons", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
brk(0x26b5000)                          = 0x26b5000
getdents(9, /* 3 entries */, 32768)     = 80
getdents(9, /* 0 entries */, 32768)     = 0
brk(0x26ad000)                          = 0x26ad000
close(9)                                = 0
stat("/usr/share/icons", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/share/icons", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/share/icons/icon-theme.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
getdents(9, /* 26 entries */, 32768)    = 888
getdents(9, /* 0 entries */, 32768)     = 0
close(9)                                = 0
stat("/usr/local/share/pixmaps", 0x7fff37c30d40) = -1 ENOENT (No such file or directory)
stat("/usr/share/pixmaps", {st_mode=S_IFDIR|0755, st_size=12288, ...}) = 0
stat("/usr/share/pixmaps", {st_mode=S_IFDIR|0755, st_size=12288, ...}) = 0
open("/usr/share/pixmaps/icon-theme.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/pixmaps", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
getdents(9, /* 189 entries */, 32768)   = 7352
getdents(9, /* 0 entries */, 32768)     = 0
close(9)                                = 0
open("/usr/lib/x86_64-linux-gnu/gio/modules", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
stat("/usr/lib/x86_64-linux-gnu/gio/modules/giomodule.cache", {st_mode=S_IFREG|0644, st_size=111, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/gio/modules/giomodule.cache", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=111, ...}) = 0
read(10, "libgiolibproxy.so: gio-proxy-res"..., 111) = 111
close(10)                               = 0
getdents(9, /* 6 entries */, 32768)     = 208
stat("/usr/lib/x86_64-linux-gnu/gio/modules/libgiolibproxy.so", {st_mode=S_IFREG|0644, st_size=14472, ...}) = 0
stat("/usr/lib/x86_64-linux-gnu/gio/modules/libgiognutls.so", {st_mode=S_IFREG|0644, st_size=73608, ...}) = 0
stat("/usr/lib/x86_64-linux-gnu/gio/modules/libgiognomeproxy.so", {st_mode=S_IFREG|0644, st_size=18808, ...}) = 0
getdents(9, /* 0 entries */, 32768)     = 0
close(9)                                = 0
open("/usr/lib/gio/modules", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
stat("/usr/lib/gio/modules/giomodule.cache", {st_mode=S_IFREG|0644, st_size=159, ...}) = 0
open("/usr/lib/gio/modules/giomodule.cache", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=159, ...}) = 0
read(10, "libgvfsdbus.so: gio-vfs,gio-volu"..., 159) = 159
close(10)                               = 0
getdents(9, /* 8 entries */, 32768)     = 304
stat("/usr/lib/gio/modules/libgvfsdbus.so", {st_mode=S_IFREG|0644, st_size=177128, ...}) = 0
stat("/usr/lib/gio/modules/libdconfsettings.so", {st_mode=S_IFREG|0644, st_size=35528, ...}) = 0
stat("/usr/lib/gio/modules/libgioremote-volume-monitor.so", {st_mode=S_IFREG|0644, st_size=81064, ...}) = 0
getdents(9, /* 0 entries */, 32768)     = 0
close(9)                                = 0
stat("/usr/lib/gio/modules/libgvfsdbus.so", {st_mode=S_IFREG|0644, st_size=177128, ...}) = 0
open("/usr/lib/gio/modules/libgvfsdbus.so", O_RDONLY) = 9
read(9, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\210\0\0\0\0\0\0"..., 832) = 832
fstat(9, {st_mode=S_IFREG|0644, st_size=177128, ...}) = 0
mmap(NULL, 2273376, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0x7feccdfca000
mprotect(0x7feccdff3000, 2097152, PROT_NONE) = 0
mmap(0x7fecce1f3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x29000) = 0x7fecce1f3000
mmap(0x7fecce1f5000, 96, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fecce1f5000
close(9)                                = 0
open("/usr/lib/gvfs/tls/x86_64/libgvfscommon.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/gvfs/tls/x86_64", 0x7fff37c30220) = -1 ENOENT (No such file or directory)
open("/usr/lib/gvfs/tls/libgvfscommon.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/gvfs/tls", 0x7fff37c30220) = -1 ENOENT (No such file or directory)
open("/usr/lib/gvfs/x86_64/libgvfscommon.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/gvfs/x86_64", 0x7fff37c30220) = -1 ENOENT (No such file or directory)
open("/usr/lib/gvfs/libgvfscommon.so", O_RDONLY) = 9
read(9, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\207\0\0\0\0\0\0"..., 832) = 832
fstat(9, {st_mode=S_IFREG|0644, st_size=94552, ...}) = 0
mmap(NULL, 2189984, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0x7feccddb3000
mprotect(0x7feccddc9000, 2093056, PROT_NONE) = 0
mmap(0x7feccdfc8000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x15000) = 0x7feccdfc8000
close(9)                                = 0
open("/usr/lib/gvfs/libudev.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 9, 0) = 0x7fecdce43000
close(9)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libudev.so.0", O_RDONLY) = 9
read(9, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2401\0\0\0\0\0\0"..., 832) = 832
fstat(9, {st_mode=S_IFREG|0644, st_size=55176, ...}) = 0
mmap(NULL, 2150448, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0x7feccdba5000
mprotect(0x7feccdbb2000, 2093056, PROT_NONE) = 0
mmap(0x7feccddb1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0xc000) = 0x7feccddb1000
close(9)                                = 0
mprotect(0x7feccddb1000, 4096, PROT_READ) = 0
mprotect(0x7feccdfc8000, 4096, PROT_READ) = 0
mprotect(0x7fecce1f3000, 4096, PROT_READ) = 0
munmap(0x7fecdce43000, 172851)          = 0
munmap(0x7feccdfca000, 2273376)         = 0
munmap(0x7feccddb3000, 2189984)         = 0
munmap(0x7feccdba5000, 2150448)         = 0
lstat("/usr/share/icons/Humanity/actions/16/package-install.svg", {st_mode=S_IFREG|0644, st_size=1686, ...}) = 0
stat("/home/species/.local/share//mime/mime.cache", {st_mode=S_IFREG|0664, st_size=1088, ...}) = 0
stat("/home/species/.local/share//mime/mime.cache", {st_mode=S_IFREG|0664, st_size=1088, ...}) = 0
open("/home/species/.local/share//mime/mime.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0664, st_size=1088, ...}) = 0
mmap(NULL, 1088, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcfaf000
close(9)                                = 0
stat("/usr/local/share//mime/mime.cache", 0x7fff37c2fa70) = -1 ENOENT (No such file or directory)
stat("/usr/local/share//mime/globs2", 0x7fff37c2fa70) = -1 ENOENT (No such file or directory)
stat("/usr/local/share//mime/globs", 0x7fff37c2fa70) = -1 ENOENT (No such file or directory)
stat("/usr/local/share//mime/magic", 0x7fff37c2fa70) = -1 ENOENT (No such file or directory)
open("/usr/local/share//mime/aliases", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share//mime/subclasses", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share//mime/icons", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share//mime/generic-icons", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/share//mime/mime.cache", {st_mode=S_IFREG|0644, st_size=118340, ...}) = 0
open("/usr/share//mime/mime.cache", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=118340, ...}) = 0
mmap(NULL, 118340, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdce51000
close(9)                                = 0
open("/usr/share/icons/Humanity/actions/16/package-install.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1686, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1686
stat("/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so", {st_mode=S_IFREG|0644, st_size=10464, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so", O_RDONLY) = 10
read(10, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\n\0\0\0\0\0\0"..., 832) = 832
fstat(10, {st_mode=S_IFREG|0644, st_size=10464, ...}) = 0
mmap(NULL, 2105720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 10, 0) = 0x7feccdff3000
mprotect(0x7feccdff5000, 2093056, PROT_NONE) = 0
mmap(0x7fecce1f4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 10, 0x1000) = 0x7fecce1f4000
close(10)                               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7fecdce26000
close(10)                               = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/librsvg-2.so.2", O_RDONLY) = 10
read(10, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20~\0\0\0\0\0\0"..., 832) = 832
fstat(10, {st_mode=S_IFREG|0644, st_size=221504, ...}) = 0
mmap(NULL, 2317032, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 10, 0) = 0x7feccddbd000
mprotect(0x7feccddf1000, 2097152, PROT_NONE) = 0
mmap(0x7feccdff1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 10, 0x34000) = 0x7feccdff1000
close(10)                               = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libcroco-0.6.so.3", O_RDONLY) = 10
read(10, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\226\0\0\0\0\0\0"..., 832) = 832
fstat(10, {st_mode=S_IFREG|0644, st_size=232104, ...}) = 0
mmap(NULL, 2327232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 10, 0) = 0x7feccdb84000
mprotect(0x7feccdbba000, 2093056, PROT_NONE) = 0
mmap(0x7feccddb9000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 10, 0x35000) = 0x7feccddb9000
close(10)                               = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libxml2.so.2", O_RDONLY) = 10
read(10, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\302\2\0\0\0\0\0"..., 832) = 832
fstat(10, {st_mode=S_IFREG|0644, st_size=1417272, ...}) = 0
mmap(NULL, 3517752, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 10, 0) = 0x7feccd829000
mprotect(0x7feccd97a000, 2093056, PROT_NONE) = 0
mmap(0x7feccdb79000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 10, 0x150000) = 0x7feccdb79000
mmap(0x7feccdb83000, 3384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7feccdb83000
close(10)                               = 0
mprotect(0x7feccdb79000, 32768, PROT_READ) = 0
mprotect(0x7feccddb9000, 4096, PROT_READ) = 0
mprotect(0x7feccdff1000, 4096, PROT_READ) = 0
mprotect(0x7fecce1f4000, 4096, PROT_READ) = 0
munmap(0x7fecdce26000, 172851)          = 0
futex(0x7feccdb83a28, FUTEX_WAKE_PRIVATE, 2147483647) = 0
read(9, "", 65536)                      = 0
open("/usr/share/locale/en_CA/LC_MESSAGES/gdk-pixbuf.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/gdk-pixbuf.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/gdk-pixbuf.mo", O_RDONLY) = 10
fstat(10, {st_mode=S_IFREG|0644, st_size=1907, ...}) = 0
mmap(NULL, 1907, PROT_READ, MAP_PRIVATE, 10, 0) = 0x7fecdcfae000
close(10)                               = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/gdk-pixbuf.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-reinstall.svg", {st_mode=S_IFREG|0644, st_size=1725, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-reinstall.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1725, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1725
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-upgrade.svg", {st_mode=S_IFREG|0644, st_size=1692, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-upgrade.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1692, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1692
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-downgrade.svg", {st_mode=S_IFREG|0644, st_size=3523, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-downgrade.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=3523, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3523
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-remove.svg", {st_mode=S_IFREG|0644, st_size=3690, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-remove.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=3690, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3690
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-purge.svg", {st_mode=S_IFREG|0644, st_size=3842, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-purge.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=3842, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3842
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-available.svg", {st_mode=S_IFREG|0644, st_size=1538, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-available.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1538, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1538
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-available-locked.svg", {st_mode=S_IFREG|0644, st_size=1835, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-available-locked.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1835, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1835
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-installed-updated.svg", {st_mode=S_IFREG|0644, st_size=2348, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-installed-updated.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2348, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 2348
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-installed-outdated.svg", {st_mode=S_IFREG|0644, st_size=4356, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-installed-outdated.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=4356, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 4356
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-installed-locked.svg", {st_mode=S_IFREG|0644, st_size=2645, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-installed-locked.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2645, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 2645
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-broken.svg", {st_mode=S_IFREG|0644, st_size=4053, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-broken.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=4053, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 4053
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/Humanity/actions/16/package-new.svg", {st_mode=S_IFREG|0644, st_size=2513, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-new.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2513, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 2513
read(9, "", 65536)                      = 0
close(9)                                = 0
lstat("/usr/share/icons/ubuntu-mono-light/actions/16/package-supported.svg", {st_mode=S_IFREG|0644, st_size=2329, ...}) = 0
open("/usr/share/icons/ubuntu-mono-light/actions/16/package-supported.svg", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2329, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 2329
read(9, "", 65536)                      = 0
close(9)                                = 0
stat("/root/.synaptic/filters", 0x7fff37c30dc0) = -1 ENOENT (No such file or directory)
stat("/var/lib/apt-xapian-index/index", {st_mode=S_IFREG|0644, st_size=41, ...}) = 0
open("/var/lib/apt-xapian-index/index", O_RDONLY) = 9
read(9, "auto /var/cache/apt-xapian-index"..., 8191) = 41
stat("/var/cache/apt-xapian-index/index.1", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/var/cache/apt-xapian-index/index.1/iamchert", {st_mode=S_IFREG|0644, st_size=28, ...}) = 0
open("/var/cache/apt-xapian-index/index.1/iamchert", O_RDONLY) = 10
read(10, "IAmChert\26\255\371\v\364\275\347\200\311\212@\262\233N\270\271\316\201\t\17", 29) = 28
read(10, "", 1)                         = 0
close(10)                               = 0
open("/var/cache/apt-xapian-index/index.1/record.DB", O_RDONLY) = 10
open("/var/cache/apt-xapian-index/index.1/record.baseA", O_RDONLY) = 11
read(11, "\f\5\200@\6\1\31\202\270\3\302\1\0\0\f\377\377\377\377\377\377\377\377\377\377\377\377\357\367\375\377\377"..., 1024) = 41
read(11, "", 983)                       = 0
close(11)                               = 0
open("/var/cache/apt-xapian-index/index.1/record.baseB", O_RDONLY) = 11
read(11, "\v\5\200@\6\1\31\202\270\3\302\1\0\0\v\377\377\377\377\377\377\377\377\377\377\377\377\357\367\375\377\377"..., 1024) = 41
read(11, "", 983)                       = 0
close(11)                               = 0
pread(10, "\0\0\0\6\1\25\311\25\311\1\207\37\371\37\356\37\343\37\330\37\315\37\302\37\267\37\254\37\241\37\226\37"..., 8192, 49152) = 8192
open("/var/cache/apt-xapian-index/index.1/spelling.DB", O_RDONLY) = 11
open("/var/cache/apt-xapian-index/index.1/spelling.baseA", O_RDONLY) = 12
read(12, "\f\5\200@\240\2\1B\365\352\2\215\4\0\0\f\0\0\0\0\0\204\0\0\0\200\0\300\377\377\377\377"..., 1024) = 83
read(12, "", 941)                       = 0
close(12)                               = 0
open("/var/cache/apt-xapian-index/index.1/spelling.baseB", O_RDONLY) = 12
read(12, "\v\5\200@\240\2\1B\365\352\2\215\4\0\0\v\0\0\0\0\0\204\0\0\0\200\0\300\377\377\377\377"..., 1024) = 83
read(12, "", 941)                       = 0
close(12)                               = 0
pread(11, "\0\0\0\6\1\n\337\n\337\2\311\37\371\33\"\37\355\33\26\37\341\33\n\37\325\32\376\37\311\32\362\37"..., 8192, 2359296) = 8192
open("/var/cache/apt-xapian-index/index.1/synonym.DB", O_RDONLY) = 12
open("/var/cache/apt-xapian-index/index.1/synonym.baseA", O_RDONLY) = 13
read(13, "\f\5\200@\1\0\1\5\1\0\0\f\2\f", 1024) = 14
read(13, "", 1010)                      = 0
close(13)                               = 0
open("/var/cache/apt-xapian-index/index.1/synonym.baseB", O_RDONLY) = 13
read(13, "\v\5\200@\0\0\1\5\0\0\0\v\1\v", 1024) = 14
read(13, "", 1010)                      = 0
close(13)                               = 0
pread(12, "\0\0\0\f\0\37\36\37\36\0\27\37\371\0375\37Y\37\327\37\204\37\257\0\0\0\0\0\0\0\0\0"..., 8192, 8192) = 8192
open("/var/cache/apt-xapian-index/index.1/termlist.DB", O_RDONLY) = 13
open("/var/cache/apt-xapian-index/index.1/termlist.baseA", O_RDONLY) = 14
read(14, "\f\5\200@\203\1\2\331\4\204\360\6\301%\0\0\f\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377"..., 1024) = 619
read(14, "", 405)                       = 0
close(14)                               = 0
open("/var/cache/apt-xapian-index/index.1/termlist.baseB", O_RDONLY) = 14
read(14, "\v\5\200@\203\1\2\331\4\204\360\6\301%\0\0\v\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377"..., 1024) = 619
read(14, "", 405)                       = 0
close(14)                               = 0
pread(13, "\0\0\0\6\2\37:\37:\0'\37\371\37\356\37\330\37\343\37\315\37\265\37\301\37\251\37\221\37\235\37"..., 8192, 1073152) = 8192
open("/var/cache/apt-xapian-index/index.1/position.DB", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/var/cache/apt-xapian-index/index.1/postlist.DB", O_RDONLY) = 14
open("/var/cache/apt-xapian-index/index.1/postlist.baseA", O_RDONLY) = 15
read(15, "\f\5\200@\4\2\200\6\236\272\17\377/\0\0\f\277\357\377\177\177s\377\377\377\377\377\377\377\377\377\377"..., 1024) = 785
read(15, "", 239)                       = 0
close(15)                               = 0
open("/var/cache/apt-xapian-index/index.1/postlist.baseB", O_RDONLY) = 15
read(15, "\v\5\200@\4\2\200\6\236\272\17\377/\0\0\v\277\357\377\177\177s\377\377\377\377\377\377\377\377\377\377"..., 1024) = 785
read(15, "", 239)                       = 0
close(15)                               = 0
brk(0x26cf000)                          = 0x26cf000
pread(14, "\0\0\0\6\2\36\335\36\335\0%\37\371\37B\37\2\37\233\37\37\37\326\37x\37\312\37h\37\276\37"..., 8192, 32768) = 8192
pread(14, "\0\0\0\6\1\r\216\r\216\2[\37\371\37\353\37\335\37\320\37\303\37\265\37\250\37\232\37\215\37\177\37"..., 8192, 49045504) = 8192
pread(14, "\0\0\0\6\0\25*\26\304\0!\37\371\26\361\37\324\26\274\25\357\25\332\37h\26u\25e\25K\27"..., 8192, 49037312) = 8192
read(9, "", 8191)                       = 0
close(9)                                = 0
pipe2([9, 15], O_CLOEXEC)               = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fecdcf7bc90) = 4247
close(15)                               = 0
fcntl(9, F_SETFD, 0)                    = 0
fstat(9, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfad000
read(9, "oneiric\n", 4096)              = 8
close(9)                                = 0
wait4(4247, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 4247
--- SIGCHLD (Child exited) @ 0 (0) ---
munmap(0x7fecdcfad000, 4096)            = 0
open("/home/species/.icons/DMZ-Black/cursors/watch", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/species/.icons/DMZ-Black/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-Black/cursors/watch", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=488576, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfad000
read(9, "Xcur\20\0\0\0\0\0\1\0]\0\0\0\2\0\375\377\30\0\0\0l\4\0\0\2\0\375\377"..., 4096) = 4096
lseek(9, 0, SEEK_SET)                   = 0
read(9, "Xcur\20\0\0\0\0\0\1\0]\0\0\0\2\0\375\377\30\0\0\0l\4\0\0\2\0\375\377"..., 4096) = 4096
lseek(9, 4096, SEEK_SET)                = 4096
read(9, "\0\0\0\0\23\23\23\24\347\347\347\357\202\202\202\377\253\253\253\377\257\257\257\377\257\257\257\377\251\251\251\377"..., 4096) = 4096
lseek(9, 8192, SEEK_SET)                = 8192
lseek(9, 8192, SEEK_SET)                = 8192
read(9, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 4096
lseek(9, 12288, SEEK_SET)               = 12288
read(9, "\37\37\37\377\22\22\22\377\16\16\16\377\f\f\f\377\v\v\v\377\f\f\f\377\16\16\16\377\27\27\27\377"..., 4096) = 4096
lseek(9, 16384, SEEK_SET)               = 16384
lseek(9, 16384, SEEK_SET)               = 16384
read(9, "kkk\377{{{\377sss\377ZZZ\377XXX\377XXX\377XXX\377YYY\377"..., 4096) = 4096
lseek(9, 20480, SEEK_SET)               = 20480
lseek(9, 20480, SEEK_SET)               = 20480
read(9, "\23\23\23\24\347\347\347\357\202\202\202\377\254\254\254\377\261\261\261\377\257\257\257\377\256\256\256\377\272\272\272\377"..., 4096) = 4096
lseek(9, 24576, SEEK_SET)               = 24576
lseek(9, 24576, SEEK_SET)               = 24576
read(9, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 4096
lseek(9, 28672, SEEK_SET)               = 28672
read(9, "\22\22\22\377\16\16\16\377\f\f\f\377\v\v\v\377\f\f\f\377\16\16\16\377\27\27\27\377\215\215\215\375"..., 4096) = 4096
lseek(9, 32768, SEEK_SET)               = 32768
lseek(9, 32768, SEEK_SET)               = 32768
read(9, "zzz\377sss\377ZZZ\377XXX\377XXX\377XXX\377YYY\377[[[\377"..., 4096) = 4096
lseek(9, 36864, SEEK_SET)               = 36864
lseek(9, 36864, SEEK_SET)               = 36864
read(9, "\347\347\347\357\202\202\202\377\254\254\254\377\261\261\261\377\257\257\257\377\257\257\257\377\256\256\256\377\256\256\256\377"..., 4096) = 4096
lseek(9, 40960, SEEK_SET)               = 40960
lseek(9, 40960, SEEK_SET)               = 40960
read(9, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 4096
lseek(9, 45056, SEEK_SET)               = 45056
read(9, "\16\16\16\377\35\35\35\377\32\32\32\377\f\f\f\377\16\16\16\377\27\27\27\377\215\215\215\375\351\351\351\372"..., 4096) = 4096
lseek(9, 49152, SEEK_SET)               = 49152
lseek(9, 49152, SEEK_SET)               = 49152
read(9, "rrr\377YYY\377XXX\377XXX\377XXX\377YYY\377YYY\377nnn\377"..., 4096) = 4096
lseek(9, 53248, SEEK_SET)               = 53248
lseek(9, 53248, SEEK_SET)               = 53248
read(9, "\202\202\202\377\254\254\254\377\261\261\261\377\257\257\257\377\257\257\257\377\254\254\254\377\254\254\254\377\256\256\256\377"..., 4096) = 4096
lseek(9, 57344, SEEK_SET)               = 57344
lseek(9, 57344, SEEK_SET)               = 57344
read(9, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 4096
lseek(9, 61440, SEEK_SET)               = 61440
read(9, "\f\f\f\377\v\v\v\377\f\f\f\377\16\16\16\377\27\27\27\377\215\215\215\375\351\351\351\372HHH\255"..., 4096) = 4096
lseek(9, 65536, SEEK_SET)               = 65536
lseek(9, 65536, SEEK_SET)               = 65536
read(9, "[[[\377XXX\377XXX\377XXX\377YYY\377YYY\377nnn\377vvv\377"..., 4096) = 4096
lseek(9, 69632, SEEK_SET)               = 69632
lseek(9, 69632, SEEK_SET)               = 69632
read(9, "\254\254\254\377\261\261\261\377\257\257\257\377\256\256\256\377\247\247\247\377\251\251\251\377\256\256\256\377\257\257\257\377"..., 4096) = 4096
lseek(9, 73728, SEEK_SET)               = 73728
close(9)                                = 0
munmap(0x7fecdcfad000, 4096)            = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"-\0\5\0\3\0 \4\6\0\0\0cursor\2\0005 \4\0\4\0 \4]\1\0\0"..., 14596}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 2304}, {"", 0}], 3) = 16900
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"<\0\2\0\35\0 \4\230\4\5\0\36\0 \4\34\0 \4 \1\0\0\0\0\0\0006\1\2\0"..., 14636}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 2304}, {"", 0}], 3) = 16940
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"<\0\2\0009\0 \4\230\4\5\0:\0 \0048\0 \4 \1\0\0\0\0\0\0006\1\2\0"..., 14636}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 2304}, {"", 0}], 3) = 16940
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"<\0\2\0U\0 \4\230\4\5\0V\0 \4T\0 \4 \1\0\0\0\0\0\0006\1\2\0"..., 14636}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 2304}, {"", 0}], 3) = 16940
stat("gtkbuilder/window_main.ui", 0x7fff37c30e10) = -1 ENOENT (No such file or directory)
open("/usr/share/synaptic/gtkbuilder/window_main.ui", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=115835, ...}) = 0
read(9, "<?xml version=\"1.0\" encoding=\"UT"..., 115835) = 115835
close(9)                                = 0
brk(0x26f1000)                          = 0x26f1000
brk(0x26ef000)                          = 0x26ef000
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1`\0\0\0\4\0\0\0v\0\0\0\1\1o\0\34\0\0\0/org/a11"..., 136}, {"\17\0\0\0accessible-name\0\0\0\0\0\0\0\0\0\1s\0\0"..., 96}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 232
open("/dev/urandom", O_RDONLY)          = 9
read(9, "Z\233\206\302\22%\3748\205\3618mL\231N\325", 16) = 16
close(9)                                = 0
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1h\0\0\0\5\0\0\0v\0\0\0\1\1o\0\34\0\0\0/org/a11"..., 136}, {"\17\0\0\0accessible-name\0\0\0\0\0\0\0\0\0\1s\0\0"..., 104}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 240
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1`\0\0\0\6\0\0\0v\0\0\0\1\1o\0\34\0\0\0/org/a11"..., 136}, {"\17\0\0\0accessible-name\0\0\0\0\0\0\0\0\0\1s\0\0"..., 96}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 232
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1`\0\0\0\7\0\0\0v\0\0\0\1\1o\0\34\0\0\0/org/a11"..., 136}, {"\17\0\0\0accessible-name\0\0\0\0\0\0\0\0\0\1s\0\0"..., 96}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 232
brk(0x2710000)                          = 0x2710000
open("/etc/pango/pangorc", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/root/.pangorc", O_RDONLY)        = -1 ENOENT (No such file or directory)
access("/usr/lib64/pango/1.6.0/module-files.d", R_OK|X_OK) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/pango/1.6.0/module-files.d", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
getdents(9, /* 3 entries */, 32768)     = 96
open("/usr/lib/x86_64-linux-gnu/pango/1.6.0/module-files.d/libpango1.0-0.modules", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=4331, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcfad000
read(15, "# automatically generated by dh_"..., 4096) = 4096
read(15, "gnu/pango/1.6.0/modules/pango-ha"..., 4096) = 235
read(15, "", 4096)                      = 0
read(15, "", 4096)                      = 0
close(15)                               = 0
munmap(0x7fecdcfad000, 4096)            = 0
getdents(9, /* 0 entries */, 32768)     = 0
close(9)                                = 0
open("/etc/pango/pango.modules", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
open("/etc/pango/pango.modules", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/fonts/fonts.conf", R_OK)   = 0
stat("/etc/fonts/fonts.conf", {st_mode=S_IFREG|0644, st_size=5287, ...}) = 0
open("/etc/fonts/fonts.conf", O_RDONLY) = 9
read(9, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 5287
access("/etc/fonts/conf.d", R_OK)       = 0
stat("/etc/fonts/conf.d", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/fonts/conf.d", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 15
getdents(15, /* 42 entries */, 32768)   = 1832
getdents(15, /* 0 entries */, 32768)    = 0
access("/etc/fonts/conf.d/10-antialias.conf", R_OK) = 0
stat("/etc/fonts/conf.d/10-antialias.conf", {st_mode=S_IFREG|0644, st_size=223, ...}) = 0
open("/etc/fonts/conf.d/10-antialias.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 223
brk(0x2731000)                          = 0x2731000
read(16, "", 8192)                      = 0
brk(0x272e000)                          = 0x272e000
close(16)                               = 0
access("/etc/fonts/conf.d/10-hinting-slight.conf", R_OK) = 0
stat("/etc/fonts/conf.d/10-hinting-slight.conf", {st_mode=S_IFREG|0644, st_size=229, ...}) = 0
open("/etc/fonts/conf.d/10-hinting-slight.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 229
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/10-hinting.conf", R_OK) = 0
stat("/etc/fonts/conf.d/10-hinting.conf", {st_mode=S_IFREG|0644, st_size=212, ...}) = 0
open("/etc/fonts/conf.d/10-hinting.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 212
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/11-lcd-filter-lcddefault.conf", R_OK) = 0
stat("/etc/fonts/conf.d/11-lcd-filter-lcddefault.conf", {st_mode=S_IFREG|0644, st_size=305, ...}) = 0
open("/etc/fonts/conf.d/11-lcd-filter-lcddefault.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 305
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/20-fix-globaladvance.conf", R_OK) = 0
stat("/etc/fonts/conf.d/20-fix-globaladvance.conf", {st_mode=S_IFREG|0644, st_size=912, ...}) = 0
open("/etc/fonts/conf.d/20-fix-globaladvance.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 912
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/20-unhint-small-vera.conf", R_OK) = 0
stat("/etc/fonts/conf.d/20-unhint-small-vera.conf", {st_mode=S_IFREG|0644, st_size=1157, ...}) = 0
open("/etc/fonts/conf.d/20-unhint-small-vera.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1157
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/30-defoma.conf", R_OK) = 0
stat("/etc/fonts/conf.d/30-defoma.conf", {st_mode=S_IFREG|0644, st_size=1899, ...}) = 0
open("/etc/fonts/conf.d/30-defoma.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1899
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/30-metric-aliases.conf", R_OK) = 0
stat("/etc/fonts/conf.d/30-metric-aliases.conf", {st_mode=S_IFREG|0644, st_size=3939, ...}) = 0
open("/etc/fonts/conf.d/30-metric-aliases.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 3939
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/30-urw-aliases.conf", R_OK) = 0
stat("/etc/fonts/conf.d/30-urw-aliases.conf", {st_mode=S_IFREG|0644, st_size=1164, ...}) = 0
open("/etc/fonts/conf.d/30-urw-aliases.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1164
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/40-nonlatin.conf", R_OK) = 0
stat("/etc/fonts/conf.d/40-nonlatin.conf", {st_mode=S_IFREG|0644, st_size=2103, ...}) = 0
open("/etc/fonts/conf.d/40-nonlatin.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 2103
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/44-wqy-zenhei.conf", R_OK) = 0
stat("/etc/fonts/conf.d/44-wqy-zenhei.conf", {st_mode=S_IFREG|0644, st_size=1924, ...}) = 0
open("/etc/fonts/conf.d/44-wqy-zenhei.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1924
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/45-latin.conf", R_OK) = 0
stat("/etc/fonts/conf.d/45-latin.conf", {st_mode=S_IFREG|0644, st_size=1837, ...}) = 0
open("/etc/fonts/conf.d/45-latin.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1837
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/49-sansserif.conf", R_OK) = 0
stat("/etc/fonts/conf.d/49-sansserif.conf", {st_mode=S_IFREG|0644, st_size=545, ...}) = 0
open("/etc/fonts/conf.d/49-sansserif.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 545
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/50-user.conf", R_OK) = 0
stat("/etc/fonts/conf.d/50-user.conf", {st_mode=S_IFREG|0644, st_size=245, ...}) = 0
open("/etc/fonts/conf.d/50-user.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 245
access("/home/species/.fonts.conf.d", R_OK) = -1 ENOENT (No such file or directory)
access("/home/species/.fonts.conf", R_OK)  = -1 ENOENT (No such file or directory)
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/51-local.conf", R_OK) = 0
stat("/etc/fonts/conf.d/51-local.conf", {st_mode=S_IFREG|0644, st_size=189, ...}) = 0
open("/etc/fonts/conf.d/51-local.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 189
access("/etc/fonts/local.conf", R_OK)   = -1 ENOENT (No such file or directory)
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/53-monospace-lcd-filter.conf", R_OK) = 0
stat("/etc/fonts/conf.d/53-monospace-lcd-filter.conf", {st_mode=S_IFREG|0644, st_size=608, ...}) = 0
open("/etc/fonts/conf.d/53-monospace-lcd-filter.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 608
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/59-ttf-droid-serif-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/59-ttf-droid-serif-fonts.conf", {st_mode=S_IFREG|0644, st_size=329, ...}) = 0
open("/etc/fonts/conf.d/59-ttf-droid-serif-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\" encoding=\"UT"..., 8192) = 329
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/60-latin.conf", R_OK) = 0
stat("/etc/fonts/conf.d/60-latin.conf", {st_mode=S_IFREG|0644, st_size=1701, ...}) = 0
open("/etc/fonts/conf.d/60-latin.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1701
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/60-ttf-droid-sans-mono-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/60-ttf-droid-sans-mono-fonts.conf", {st_mode=S_IFREG|0644, st_size=345, ...}) = 0
open("/etc/fonts/conf.d/60-ttf-droid-sans-mono-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\" encoding=\"UT"..., 8192) = 345
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/64-ttf-thai-tlwg.conf", R_OK) = 0
stat("/etc/fonts/conf.d/64-ttf-thai-tlwg.conf", {st_mode=S_IFREG|0644, st_size=549, ...}) = 0
open("/etc/fonts/conf.d/64-ttf-thai-tlwg.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 549
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/65-fonts-persian.conf", R_OK) = 0
stat("/etc/fonts/conf.d/65-fonts-persian.conf", {st_mode=S_IFREG|0644, st_size=9880, ...}) = 0
open("/etc/fonts/conf.d/65-fonts-persian.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 8192
read(16, "s>\n\n\t<!-- Persian fantasy fonts "..., 8192) = 1688
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/65-khmer.conf", R_OK) = 0
stat("/etc/fonts/conf.d/65-khmer.conf", {st_mode=S_IFREG|0644, st_size=539, ...}) = 0
open("/etc/fonts/conf.d/65-khmer.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 539
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/65-nonlatin.conf", R_OK) = 0
stat("/etc/fonts/conf.d/65-nonlatin.conf", {st_mode=S_IFREG|0644, st_size=7706, ...}) = 0
open("/etc/fonts/conf.d/65-nonlatin.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 7706
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/65-ttf-droid-sans-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/65-ttf-droid-sans-fonts.conf", {st_mode=S_IFREG|0644, st_size=3452, ...}) = 0
open("/etc/fonts/conf.d/65-ttf-droid-sans-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 3452
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/69-unifont.conf", R_OK) = 0
stat("/etc/fonts/conf.d/69-unifont.conf", {st_mode=S_IFREG|0644, st_size=672, ...}) = 0
open("/etc/fonts/conf.d/69-unifont.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 672
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/70-no-bitmaps.conf", R_OK) = 0
stat("/etc/fonts/conf.d/70-no-bitmaps.conf", {st_mode=S_IFREG|0644, st_size=263, ...}) = 0
open("/etc/fonts/conf.d/70-no-bitmaps.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 263
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/80-delicious.conf", R_OK) = 0
stat("/etc/fonts/conf.d/80-delicious.conf", {st_mode=S_IFREG|0644, st_size=388, ...}) = 0
open("/etc/fonts/conf.d/80-delicious.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 388
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/89-ttf-thai-tlwg-synthetic.conf", R_OK) = 0
stat("/etc/fonts/conf.d/89-ttf-thai-tlwg-synthetic.conf", {st_mode=S_IFREG|0644, st_size=2928, ...}) = 0
open("/etc/fonts/conf.d/89-ttf-thai-tlwg-synthetic.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 2928
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-synthetic.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-synthetic.conf", {st_mode=S_IFREG|0644, st_size=1691, ...}) = 0
open("/etc/fonts/conf.d/90-synthetic.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1691
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-bengali-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-bengali-fonts.conf", {st_mode=S_IFREG|0644, st_size=1064, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-bengali-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1064
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-devanagari-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-devanagari-fonts.conf", {st_mode=S_IFREG|0644, st_size=5083, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-devanagari-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 5083
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-gujarati-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-gujarati-fonts.conf", {st_mode=S_IFREG|0644, st_size=693, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-gujarati-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 693
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-kannada-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-kannada-fonts.conf", {st_mode=S_IFREG|0644, st_size=684, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-kannada-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 684
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-malayalam-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-malayalam-fonts.conf", {st_mode=S_IFREG|0644, st_size=1072, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-malayalam-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1072
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-oriya-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-oriya-fonts.conf", {st_mode=S_IFREG|0644, st_size=678, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-oriya-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 678
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-punjabi-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-punjabi-fonts.conf", {st_mode=S_IFREG|0644, st_size=689, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-punjabi-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 689
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-tamil-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-tamil-fonts.conf", {st_mode=S_IFREG|0644, st_size=1362, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-tamil-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 1362
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/90-ttf-telugu-fonts.conf", R_OK) = 0
stat("/etc/fonts/conf.d/90-ttf-telugu-fonts.conf", {st_mode=S_IFREG|0644, st_size=687, ...}) = 0
open("/etc/fonts/conf.d/90-ttf-telugu-fonts.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 687
read(16, "", 8192)                      = 0
close(16)                               = 0
access("/etc/fonts/conf.d/99pdftoopvp.conf", R_OK) = 0
stat("/etc/fonts/conf.d/99pdftoopvp.conf", {st_mode=S_IFREG|0644, st_size=366, ...}) = 0
open("/etc/fonts/conf.d/99pdftoopvp.conf", O_RDONLY) = 16
read(16, "<?xml version=\"1.0\"?>\n<!DOCTYPE "..., 8192) = 366
read(16, "", 8192)                      = 0
close(16)                               = 0
close(15)                               = 0
read(9, "", 8192)                       = 0
close(9)                                = 0
stat("/usr/share/fonts", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/3830d5c3ddfd5cd38a049b759396e72e-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=232, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0\350\0\0\0\0\0\0\0008\0\0\0\0\0\0\0P\0\0\0\0\0\0\0"..., 232) = 232
close(9)                                = 0
stat("/usr/X11R6/lib/X11/fonts", 0x7fff37c2fc40) = -1 ENOENT (No such file or directory)
stat("/usr/X11R6/lib/X11/fonts", 0x7fff37c2fcd0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/fonts", {st_mode=S_IFDIR|S_ISGID|0775, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/4c599c202bc5c08e2d34565a40eac3b2-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=96, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0`\0\0\0\0\0\0\0008\0\0\0\0\0\0\0P\0\0\0\0\0\0\0"..., 96) = 96
close(9)                                = 0
stat("/home/species/.fonts", 0x7fff37c2fc40) = -1 ENOENT (No such file or directory)
stat("/home/species/.fonts", 0x7fff37c2fcd0) = -1 ENOENT (No such file or directory)
stat("/usr/share/fonts/X11", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/c855463f699352c367813e37f3f70ea7-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=256, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0\0\1\0\0\0\0\0\0008\0\0\0\0\0\0\0P\0\0\0\0\0\0\0"..., 256) = 256
close(9)                                = 0
stat("/usr/share/fonts/cmap", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/57e423e26b20ab21d0f2f29c145174c3-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=192, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0\300\0\0\0\0\0\0\0008\0\0\0\0\0\0\0P\0\0\0\0\0\0\0"..., 192) = 192
close(9)                                = 0
stat("/usr/share/fonts/truetype", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=13112, ...}) = 0
mmap(NULL, 13112, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcfaa000
close(9)                                = 0
stat("/usr/share/fonts/type1", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/d82eb4fd963d448e2fcb7d7b793b5df3-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=176, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0\260\0\0\0\0\0\0\0008\0\0\0\0\0\0\0P\0\0\0\0\0\0\0"..., 176) = 176
close(9)                                = 0
stat("/usr/share/fonts/X11/Type1", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=41880, ...}) = 0
mmap(NULL, 41880, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcf9f000
close(9)                                = 0
stat("/usr/share/fonts/X11/encodings", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/707971e003b4ae6c8121c3a920e507f5-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=152, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0\230\0\0\0\0\0\0\0008\0\0\0\0\0\0\0X\0\0\0\0\0\0\0"..., 152) = 152
close(9)                                = 0
stat("/usr/share/fonts/X11/misc", {st_mode=S_IFDIR|0755, st_size=36864, ...}) = 0
open("/var/cache/fontconfig/cabbd14511b9e8a55e92af97fb3a0461-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=104, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0h\0\0\0\0\0\0\0008\0\0\0\0\0\0\0X\0\0\0\0\0\0\0"..., 104) = 104
close(9)                                = 0
stat("/usr/share/fonts/X11/util", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/fe547fea3a41b43a38975d292a2b19c7-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=104, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0h\0\0\0\0\0\0\0008\0\0\0\0\0\0\0X\0\0\0\0\0\0\0"..., 104) = 104
close(9)                                = 0
stat("/usr/share/fonts/cmap/adobe-japan1", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/d3e5c4ee2ceb1fc347f91d4cefc53bc0-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=112, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0p\0\0\0\0\0\0\0008\0\0\0\0\0\0\0`\0\0\0\0\0\0\0"..., 112) = 112
close(9)                                = 0
stat("/usr/share/fonts/cmap/gs-cjk-resource", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/15dd9cd3d124d3de2d4110f6dde97c23-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=112, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0p\0\0\0\0\0\0\0008\0\0\0\0\0\0\0`\0\0\0\0\0\0\0"..., 112) = 112
close(9)                                = 0
stat("/usr/share/fonts/truetype/fonts-horai-umefont", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=28880, ...}) = 0
mmap(NULL, 28880, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcf97000
close(9)                                = 0
stat("/usr/share/fonts/truetype/freefont", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=63856, ...}) = 0
mmap(NULL, 63856, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdce41000
close(9)                                = 0
stat("/usr/share/fonts/truetype/msttcorefonts", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=186864, ...}) = 0
mmap(NULL, 186864, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdce13000
close(9)                                = 0
stat("/usr/share/fonts/truetype/openoffice", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2192, ...}) = 0
mmap(NULL, 2192, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdce12000
close(9)                                = 0
stat("/usr/share/fonts/truetype/takao", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=12160, ...}) = 0
mmap(NULL, 12160, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdce0f000
close(9)                                = 0
stat("/usr/share/fonts/truetype/thai", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=63840, ...}) = 0
mmap(NULL, 63840, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdff000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-dejavu", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=35304, ...}) = 0
mmap(NULL, 35304, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdf6000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-droid", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=20944, ...}) = 0
mmap(NULL, 20944, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdf0000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-indic-fonts-core", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=22520, ...}) = 0
mmap(NULL, 22520, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdea000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-kacst-one", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1600, ...}) = 0
mmap(NULL, 1600, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcde9000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-khmeros-core", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2984, ...}) = 0
mmap(NULL, 2984, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcde8000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-lao", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1640, ...}) = 0
mmap(NULL, 1640, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcde7000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-liberation", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=19464, ...}) = 0
mmap(NULL, 19464, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcde2000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-punjabi-fonts", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=2984, ...}) = 0
mmap(NULL, 2984, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcde1000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-sil-gentium", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=5480, ...}) = 0
mmap(NULL, 5480, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcddf000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ttf-sil-gentium-basic", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/ea47318ec9849e1a71e80a5d69d13859-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=9896, ...}) = 0
mmap(NULL, 9896, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcddc000
close(9)                                = 0
stat("/usr/share/fonts/truetype/ubuntu-font-family", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=14392, ...}) = 0
mmap(NULL, 14392, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdd8000
close(9)                                = 0
stat("/usr/share/fonts/truetype/unfonts", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=11328, ...}) = 0
mmap(NULL, 11328, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdd5000
close(9)                                = 0
stat("/usr/share/fonts/truetype/wqy", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=16128, ...}) = 0
mmap(NULL, 16128, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdd1000
close(9)                                = 0
stat("/usr/share/fonts/type1/gsfonts", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=34040, ...}) = 0
mmap(NULL, 34040, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdc8000
close(9)                                = 0
stat("/usr/share/fonts/type1/mathml", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1472, ...}) = 0
mmap(NULL, 1472, PROT_READ, MAP_SHARED, 9, 0) = 0x7fecdcdc7000
close(9)                                = 0
stat("/usr/share/fonts/X11/encodings/large", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/cache/fontconfig/6333f38776742d18e214673cd2c24e34-le64.cache-3", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=112, ...}) = 0
read(9, "\4\374\2\374\3\0\0\0p\0\0\0\0\0\0\0008\0\0\0\0\0\0\0`\0\0\0\0\0\0\0"..., 112) = 112
close(9)                                = 0
stat("/usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so", {st_mode=S_IFREG|0644, st_size=10904, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so", O_RDONLY) = 9
read(9, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\20\0\0\0\0\0\0"..., 832) = 832
fstat(9, {st_mode=S_IFREG|0644, st_size=10904, ...}) = 0
mmap(NULL, 2106168, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0x7feccd626000
mprotect(0x7feccd628000, 2093056, PROT_NONE) = 0
mmap(0x7feccd827000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x1000) = 0x7feccd827000
close(9)                                = 0
mprotect(0x7feccd827000, 4096, PROT_READ) = 0
open("/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf", O_RDONLY) = 9
fcntl(9, F_SETFD, FD_CLOEXEC)           = 0
fstat(9, {st_mode=S_IFREG|0644, st_size=353824, ...}) = 0
mmap(NULL, 353824, PROT_READ, MAP_PRIVATE, 9, 0) = 0x7feccd5cf000
close(9)                                = 0
open("/proc/meminfo", O_RDONLY)         = 9
fstat(9, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf96000
read(9, "MemTotal:        3090228 kB\nMemF"..., 1024) = 1024
close(9)                                = 0
munmap(0x7fecdcf96000, 4096)            = 0
open("/usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf", O_RDONLY) = 9
fcntl(9, F_SETFD, FD_CLOEXEC)           = 0
fstat(9, {st_mode=S_IFREG|0644, st_size=333636, ...}) = 0
mmap(NULL, 333636, PROT_READ, MAP_PRIVATE, 9, 0) = 0x7feccd57d000
close(9)                                = 0
brk(0x274f000)                          = 0x274f000
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1`\0\0\0\10\0\0\0v\0\0\0\1\1o\0\34\0\0\0/org/a11"..., 136}, {"\17\0\0\0accessible-name\0\0\0\0\0\0\0\0\0\1s\0\0"..., 96}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 232
brk(0x2772000)                          = 0x2772000
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"<\0\2\0q\0 \4\230\4\5\0r\0 \4p\0 \4 \1\0\0\0\0\0\0006\1\2\0"..., 7852}, {NULL, 0}, {"", 0}], 3) = 7852
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3\223\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\223\10\7\0\0\1G\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 28}, {NULL, 0}, {"", 0}], 3) = 28
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3\224\1X\4\0\0\0\0\10\377G\0\0\31\31\0104\1\370\0\0\0\0\0\0\0\0\0\0\10"..., 4096) = 4096
read(3, "\216\377\10\20\0\0\0\0\1\1\1\0\33\377\10\20\0\0\0\0\1\1\1\0_\377\10\20\0\0\0\0"..., 384) = 384
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\223\21\3\0\3\0G\0\0\30\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3\225\1\16\0\0\0\0\30\0\0\10\377\31\1\377\37\10\370\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 88
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\20\0\3\0\4\0G\0Meta", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\226\1\0\0\0\0\217\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\20\0\4\0\5\0G\0Super\0\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\227\1\0\0\0\0\220\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\20\0\4\0\5\0G\0Hyper\0\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0\230\1\0\0\0\0\221\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
access("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/gtk.immodules.64", F_OK) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/gtk.immodules", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=1749, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf96000
read(9, "# GTK+ Input Method Modules file"..., 4096) = 1749
read(9, "", 4096)                       = 0
read(9, "", 4096)                       = 0
close(9)                                = 0
munmap(0x7fecdcf96000, 4096)            = 0
stat("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so", {st_mode=S_IFREG|0644, st_size=27448, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so", O_RDONLY) = 9
read(9, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`'\0\0\0\0\0\0"..., 832) = 832
fstat(9, {st_mode=S_IFREG|0644, st_size=27448, ...}) = 0
mmap(NULL, 2122712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0x7feccd376000
mprotect(0x7feccd37c000, 2093056, PROT_NONE) = 0
mmap(0x7feccd57b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x5000) = 0x7feccd57b000
close(9)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=172851, ...}) = 0
mmap(NULL, 172851, PROT_READ, MAP_PRIVATE, 9, 0) = 0x7feccd34b000
close(9)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libibus-1.0.so.0", O_RDONLY) = 9
read(9, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\313\0\0\0\0\0\0"..., 832) = 832
fstat(9, {st_mode=S_IFREG|0644, st_size=271216, ...}) = 0
mmap(NULL, 2368504, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0x7feccd108000
mprotect(0x7feccd148000, 2097152, PROT_NONE) = 0
mmap(0x7feccd348000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x40000) = 0x7feccd348000
mmap(0x7feccd34a000, 1016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7feccd34a000
close(9)                                = 0
mprotect(0x7feccd348000, 4096, PROT_READ) = 0
mprotect(0x7feccd57b000, 4096, PROT_READ) = 0
munmap(0x7feccd34b000, 172851)          = 0
open("/var/lib/dbus/machine-id", O_RDONLY) = 9
fstat(9, {st_mode=S_IFREG|0644, st_size=33, ...}) = 0
read(9, "6e3a694924188906d4093c6702696be1"..., 33) = 33
close(9)                                = 0
access("/root", F_OK)                   = 0
stat("/root", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
access("/root/.config", F_OK)           = 0
stat("/root/.config", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
access("/root/.config/ibus", F_OK)      = 0
stat("/root/.config/ibus", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
access("/root/.config/ibus/bus", F_OK)  = 0
stat("/root/.config/ibus/bus", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
chmod("/root/.config/ibus/bus", 0700)   = 0
stat("/root/.config/ibus/bus", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
getuid()                                = 0
open("/root/.config/ibus/bus/6e3a694924188906d4093c6702696be1-unix-0", O_RDONLY) = -1 ENOENT (No such file or directory)
inotify_init1(O_CLOEXEC)                = 9
fstat(9, {st_mode=0600, st_size=0, ...}) = 0
fcntl(9, F_GETFL)                       = 0 (flags O_RDONLY)
fcntl(9, F_SETFL, O_RDONLY|O_NONBLOCK)  = 0
inotify_add_watch(9, "/root/.config/ibus/bus", IN_MODIFY|IN_ATTRIB|IN_CLOSE_WRITE|IN_MOVED_FROM|IN_MOVED_TO|IN_CREATE|IN_DELETE|IN_DELETE_SELF|IN_MOVE_SELF|IN_UNMOUNT|IN_ONLYDIR) = 1
brk(0x2793000)                          = 0x2793000
stat("/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so", {st_mode=S_IFREG|0644, st_size=26960, ...}) = 0
open("/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so", O_RDONLY) = 15
read(15, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\24\0\0\0\0\0\0"..., 832) = 832
fstat(15, {st_mode=S_IFREG|0644, st_size=26960, ...}) = 0
mmap(NULL, 2122208, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 15, 0) = 0x7fecccf01000
mprotect(0x7fecccf07000, 2093056, PROT_NONE) = 0
mmap(0x7feccd106000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 15, 0x5000) = 0x7feccd106000
close(15)                               = 0
mprotect(0x7feccd106000, 4096, PROT_READ) = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"+\0\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\2\231\1\0\0\0\0\7\0\300\3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}], 5, 0) = 1 ([{fd=5, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}], 5, 0) = 1 ([{fd=5, revents=POLLIN}])
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(5, {msg_name(0)=NULL, msg_iov(1)=[{"l\1\0\0010\0\0\0\325\1\0\0\215\0\0\0\1\1o\0\37\0\0\0/org/a11"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 328
recvmsg(5, 0x7fff37c30b30, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\2\1\1\0\0\0\0\t\0\0\0\30\0\0\0\6\1s\0\4\0\0\0:1.1\0\0\0\0"..., 40}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 40
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\0\0\0\0\n\0\0\0\204\0\0\0\1\1o\0\30\0\0\0/org/a11"..., 152}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 152
poll([{fd=5, events=POLLIN}], 1, 5000)  = 1 ([{fd=5, revents=POLLIN}])
recvmsg(5, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\10\0\0\0\327\1\0\0005\0\0\0\6\1s\0\5\0\0\0:1.36\0\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 80
recvmsg(5, 0x7fff37c307c0, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"$\0\1\0&\0\2\0]\1\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\233\1\0\0\0\0]\1\0\0\37\2\200\1c\2\32\1c\2\32\1\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\0\2\0\37\2\200\1", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\234\1\0\0\0\0]\1\0\0 \2\200\1c\2\32\1(\2\365\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\0\2\0 \2\200\1", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\235\1\0\0\0\0]\1\0\0\6\0\300\3c\2\32\1 \2\330\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\0\2\0\6\0\300\3", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\236\1\0\0\0\0]\1\0\0\0\0\0\0c\2\32\1 \2\330\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"%\0\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
lstat("/usr/share/icons/Humanity/actions/16/system-upgrade.svg", {st_mode=S_IFLNK|0777, st_size=32, ...}) = 0
stat("/usr/share/icons/Humanity/actions/16/system-upgrade.svg", {st_mode=S_IFREG|0644, st_size=4726, ...}) = 0
readlink("/usr/share/icons/Humanity/actions/16/system-upgrade.svg", "../../apps/16/system-upgrade.svg", 256) = 32
open("/usr/share/icons/Humanity/actions/16/system-upgrade.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=4726, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 4726
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-available.svg", {st_mode=S_IFREG|0644, st_size=1538, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-available.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1538, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1538
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-install.svg", {st_mode=S_IFREG|0644, st_size=1686, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-install.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1686, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1686
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-reinstall.svg", {st_mode=S_IFREG|0644, st_size=1725, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-reinstall.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1725, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1725
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-upgrade.svg", {st_mode=S_IFREG|0644, st_size=1692, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-upgrade.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1692, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1692
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-remove.svg", {st_mode=S_IFREG|0644, st_size=3690, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-remove.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=3690, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3690
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-purge.svg", {st_mode=S_IFREG|0644, st_size=3842, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-purge.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=3842, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3842
read(15, "", 65536)                     = 0
close(15)                               = 0
stat("/usr/bin/tasksel", {st_mode=S_IFREG|0755, st_size=22694, ...}) = 0
lstat("/usr/share/icons/Humanity/actions/24/view-refresh.svg", {st_mode=S_IFREG|0644, st_size=11124, ...}) = 0
open("/usr/share/icons/Humanity/actions/24/view-refresh.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=11124, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 11124
brk(0x27b4000)                          = 0x27b4000
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", {st_mode=S_IFLNK|0777, st_size=32, ...}) = 0
stat("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", {st_mode=S_IFREG|0644, st_size=5055, ...}) = 0
readlink("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", "../../apps/24/system-upgrade.svg"..., 256) = 32
open("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=5055, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 5055
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/24/gtk-apply.svg", {st_mode=S_IFLNK|0777, st_size=16, ...}) = 0
stat("/usr/share/icons/Humanity/actions/24/gtk-apply.svg", {st_mode=S_IFREG|0644, st_size=2420, ...}) = 0
readlink("/usr/share/icons/Humanity/actions/24/gtk-apply.svg", "dialog-apply.svg", 256) = 16
open("/usr/share/icons/Humanity/actions/24/gtk-apply.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=2420, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 2420
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/24/document-properties.svg", {st_mode=S_IFREG|0644, st_size=3540, ...}) = 0
open("/usr/share/icons/Humanity/actions/24/document-properties.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=3540, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3540
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/gnome/24x24/actions/edit-find.png", {st_mode=S_IFREG|0644, st_size=1517, ...}) = 0
open("/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf", O_RDONLY) = 15
fcntl(15, F_SETFD, FD_CLOEXEC)          = 0
fstat(15, {st_mode=S_IFREG|0644, st_size=333616, ...}) = 0
mmap(NULL, 333616, PROT_READ, MAP_PRIVATE, 15, 0) = 0x7feccceaf000
close(15)                               = 0
lstat("/usr/share/icons/Humanity/status/32/dialog-information.svg", {st_mode=S_IFLNK|0777, st_size=29, ...}) = 0
stat("/usr/share/icons/Humanity/status/32/dialog-information.svg", {st_mode=S_IFREG|0644, st_size=7223, ...}) = 0
readlink("/usr/share/icons/Humanity/status/32/dialog-information.svg", "../../actions/32/gtk-info.svg", 256) = 29
open("/usr/share/icons/Humanity/status/32/dialog-information.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=7223, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 7223
brk(0x27d5000)                          = 0x27d5000
read(15, "", 65536)                     = 0
close(15)                               = 0
uname({sys="Linux", node="horizon", ...}) = 0
shmget(IPC_PRIVATE, 393216, IPC_CREAT|0600) = 589829
shmat(589829, 0, 0)                     = ?
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\1\30\r\0\201\0 \4]\1\0\0\0\0\0\0d\4B\3\0\0\1\0!\0\0\0\32(\0\0"..., 10828}, {NULL, 0}, {"", 0}], 3) = 10828
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0\241\1\201\0 \4\34\1\0\0\320\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 576
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
shmctl(589829, IPC_RMID, 0)             = 0
open("/home/species/.icons/DMZ-Black/cursors/bottom_right_corner", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/species/.icons/DMZ-Black/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-Black/cursors/bottom_right_corner", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=15776, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf96000
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
lseek(15, 0, SEEK_SET)                  = 0
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
close(15)                               = 0
munmap(0x7fecdcf96000, 4096)            = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\216\3\n\0\244\0 \4\245\0 \4\0\6@\0\0\0\0\0000\0000\0\0\0\0\0\30\2\0\0"..., 3608}, {NULL, 0}, {"", 0}], 3) = 3608
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\3\7\2\36\0\0\0\17\0\0\0\0\0\0\0\0x\363\1\0\0\0\0000\203\363\1\0\0\0\0"..., 4096) = 152
read(3, "\34\0\7\2\201\0 \4\213\1\0\0\324\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
uname({sys="Linux", node="horizon", ...}) = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\4\3\2\0\270\0 \4\22\0\30\0\201\0 \4(\0\0\0)\0\0\0 \0\0\0\22\0\0\0"..., 980}, {NULL, 0}, {"", 0}], 3) = 980
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0\t\2\201\0 \4(\0\0\0\327\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 416
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\7\0\305\0 \4+\1\0\0\4\0\0\0 \0\0\0\1\0\0\0j\1\0\0\20\0\6\0"..., 52}, {NULL, 0}, {"", 0}], 3) = 52
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\26\0&\2\201\0 \4\201\0 \4\1\0 \0045\6F\0d\4B\3\0\0\0\0\0\0\0\0", 4096) = 32
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0'\2\305\0 \4+\1\0\0\331\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 64
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\24\0\6\0\305\0 \4\236\1\0\0\0\0\0\0\0\0\0\0\5\0\0\0", 24}, {NULL, 0}, {"", 0}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\0)\2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
open("/home/species/.icons/DMZ-Black/cursors/xterm", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/species/.icons/DMZ-Black/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-Black/cursors/xterm", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=15776, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf96000
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
lseek(15, 0, SEEK_SET)                  = 0
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
close(15)                               = 0
munmap(0x7fecdcf96000, 4096)            = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\34\0)\2\305\0 \4\213\1\0\0\333\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
writev(3, [{"\22\0\v\0\305\0 \4\236\1\0\0\236\1\0\0 \0\0\0\5\0\0\0\2\0\0\0\0\0\0\0"..., 2836}, {NULL, 0}, {"", 0}], 3) = 2836
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0*\2\305\0 \4\236\1\0\0\334\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 224
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, "\34\0B\2\305\0 \4\213\1\0\0\335\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
open("/home/species/.icons/DMZ-Black/cursors/sb_h_double_arrow", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/species/.icons/DMZ-Black/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-Black/cursors/sb_h_double_arrow", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=15776, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf96000
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
lseek(15, 0, SEEK_SET)                  = 0
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
close(15)                               = 0
munmap(0x7fecdcf96000, 4096)            = 0
open("/home/species/.icons/DMZ-Black/cursors/sb_v_double_arrow", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/species/.icons/DMZ-Black/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-Black/cursors/sb_v_double_arrow", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=15776, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecdcf96000
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
lseek(15, 0, SEEK_SET)                  = 0
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0\0\0\2\0\375\377"..., 4096) = 4096
close(15)                               = 0
munmap(0x7fecdcf96000, 4096)            = 0
brk(0x27f8000)                          = 0x27f8000
brk(0x27f1000)                          = 0x27f1000
brk(0x27ee000)                          = 0x27ee000
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\n\0\201\0 \4M\1\0\0M\1\0\0\10\0\0\0\20\0\0\0l\0\5\0\0\0\0\0"..., 12456}, {NULL, 0}, {"", 0}], 3) = 12456
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0C\2\201\0 \4M\1\0\0\343\223\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 128
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"(\0\4\0\201\0 \4]\1\0\0\0\0\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\245\2\0\0\0\0\10\1\200\0015\6F\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
shmget(IPC_PRIVATE, 393216, IPC_CREAT|0600) = 622598
shmat(622598, 0, 0)                     = ?
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"5\30\4\0\376\0 \4\201\0 \4d\4B\3\230\4\5\0\377\0 \4\376\0 \4$\1\0\0"..., 8788}, {NULL, 0}, {"", 0}], 3) = 8788
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\2\17\3\0\0\0\0\7\0\300\3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
shmctl(622598, IPC_RMID, 0)             = 0
mmap(NULL, 139264, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecccdcd000
brk(0x2815000)                          = 0x2815000
brk(0x2812000)                          = 0x2812000
munmap(0x7fecccdcd000, 139264)          = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\25\0\17\3\201\0 \4\201\0 \4\203\2\200\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 160
writev(3, [{"5 \4\0\27\1 \4]\1\0\0\30\0\30\0\230\4\5\0\30\1 \4\27\1 \0044\1\0\0"..., 336}, {"\0\34;\0\0006;\0\0\0041\0\0\34;\0\0n0\0\0006;\0\0\0041\0\0\34;\0"..., 28440}, {"", 0}], 3) = 28776
mmap(NULL, 233472, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecccdb6000
mmap(NULL, 311296, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fecccd6a000
munmap(0x7fecccd6a000, 311296)          = 0
brk(0x283d000)                          = 0x283d000
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\226\0\17\3\201\0 \4\201\0 \4\1\0 \4\0\0\0\0d\4B\3\0\0\0\0\0\0\0\0"..., 4096) = 288
writev(3, [{"5\30\4\0\36\1 \4\376\0 \4\1\0\1\0\230\4\5\0\37\1 \4\36\1 \4$\1\0\0"..., 2668}, {"\0\20;\0\0*;\0\0\10\203\0\0\20;\0\0r\202\0\0*;\0\0\10\203\0\0\20;\0"..., 61920}, {"", 0}], 3) = 64588
munmap(0x7fecccdb6000, 233472)          = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0\24\1 \4\0\0\0\0e\0009\0|\0\22\0\230\24\223\0!\1 \4\1\0\0\0"..., 3792}, {"\0\34;\0\0006;\0\0\4\34\1\0\34;\0\0n\33\1\0006;\0\0\4\34\1\0\34;\0"..., 18240}, {"", 0}], 3) = 22032
brk(0x286c000)                          = 0x286c000
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\34\0;\3\201\0 \4J\1\0\0\7\224\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 64
writev(3, [{"\230\6\5\0\24\1 \4\0\0\0\0\355\0009\0H\0\22\0\230\24u\0!\1 \4\1\0\0\0"..., 860}, {"\0\0<\0\0\t<\0\0\330\203\1\0\0<\0\0\250\203\1\0\t<\0\0\330\203\1\0\0<\0"..., 38680}, {"", 0}], 3) = 39540
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0;\3\201\0 \4\37\1\0\0\16\224\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 64
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0;\3\201\0 \4\262\1\0\0)\224\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0;\3\201\0 \4\332\1\0\0001\224\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0\24\1 \4\0\0\0\0M\0019\0H\0\22\0\230\24k\0!\1 \4\1\0\0\0"..., 3380}, {"\0<-\0\0V-\0\0\10\252\2\0<-\0\0r\251\2\0V-\0\0\10\252\2\0<-\0"..., 29080}, {"", 0}], 3) = 32460
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0\24\1 \4\0\0\0\0\202\2\36\0-\0-\0\230\24k\0!\1 \4\1\0\0\0"..., 10984}, {"\0@\5\0\0Z\5\0\0\370<\0\0@\5\0\0b<\0\0Z\5\0\0\370<\0\0@\5\0"..., 9720}, {"", 0}], 3) = 20704
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0.\1 \4\0\0\0\0-\0\3\0\33\0\22\0\230\24a\0!\1 \4\1\0\0\0"..., 520}, {"\0\20\5\0\0*\5\0\0\10q\0\0\20\5\0\0rp\0\0*\5\0\0\10q\0\0\20\5\0"..., 36480}, {"", 0}], 3) = 37000
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0.\1 \4\0\0\0\0V\0\3\0008\0\22\0\230\27\v\0\3\1 \4 \1 \4"..., 136}, {"\0\0\6\0\0\t\6\0\0\330\271\0\0\0\6\0\0\250\271\0\0\t\6\0\0\330\271\0\0\0\6\0"..., 35320}, {"", 0}], 3) = 35456
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0.\1 \4\0\0\0\0\234\0\3\0007\0\22\0\230\24O\0!\1 \4\1\0\0\0"..., 15400}, {"\0\0\304\2\0\1\304\2\0\200\v\0\0\0\304\2\0t\v\0\0\1\304\2\0\200\230\0\0\0\304\2"..., 3720}, {"", 0}], 3) = 19120
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\7\2\0001\1 \0046\0\2\0000\1 \0045\10\4\0002\1 \4\376\0 \4\224\0\31\0"..., 2928}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 14800}, {"", 0}], 3) = 17728
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0=\1 \4<\1 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0/\1 \4"..., 15504}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 14800}, {"", 0}], 3) = 30304
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0R\1 \4Q\1 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0/\1 \4"..., 15876}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 14800}, {"", 0}], 3) = 30676
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0g\1 \4f\1 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0/\1 \4"..., 14956}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 14800}, {"", 0}], 3) = 29756
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0|\1 \4{\1 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0/\1 \4"..., 14684}, {"cefuikl|ikl{ijk{hjkzhijzhijzhijz"..., 14800}, {"", 0}], 3) = 29484
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0\217\1 \4\216\1 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0/\1 \4"..., 16288}, {"\0\0\30\1\0\3\30\1\0\200\270\1\0\0\30\1\0g\270\1\0\3\30\1\0\200\27\2\0\0\30\1"..., 1000}, {"", 0}], 3) = 17288
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\7\2\0\257\1 \0046\1\2\0\256\1 \4\230\n\0\1\3\0\0\0\253\1 \4/\1 \4"..., 15788}, {NULL, 0}, {"", 0}], 3) = 15788
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\24\0\6\0\201\0 \4\37\1\0\0\4\0\0\0\0\0\0\0\377\377\377\377", 24}, {NULL, 0}, {"", 0}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1 \340\5\0\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\34\0\340\5\201\0 \4\216\1\0\0y\224\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
writev(3, [{"*\2\3\0\202\0 \4\376\223\v\0+\0\1\0\24\0\6\0\201\0 \4\31\1\0\0\6\0\0\0"..., 40}, {NULL, 0}, {"", 0}], 3) = 40
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\n\2\341\5\201\0 \4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 132
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\24\0\6\0\201\0 \4\37\1\0\0\4\0\0\0\0\0\0\0\377\377\377\377", 24}, {NULL, 0}, {"", 0}], 3) = 24
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1 \344\5\0\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"5\30\4\0\277\1 \4\201\0 \4\240\0\33\0\230\4\5\0\300\1 \4\277\1 \4$\1\0\0"..., 6604}, {NULL, 0}, {"", 0}], 3) = 6604
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0\344\5\201\0 \4\216\1\0\0\200\224\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"$\30\1\0&\1\2\0]\1\0\0", 12}, {NULL, 0}, {"", 0}], 3) = 12
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\5\6\0\0\0\0]\1\0\0\37\2\200\1c\2\32\1c\2\32\1\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\30\2\0\37\2\200\1", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\6\6\0\0\0\0]\1\0\0 \2\200\1c\2\32\1(\2\365\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\30\2\0 \2\200\1", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\7\6\0\0\0\0]\1\0\0\6\0\300\3c\2\32\1 \2\330\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"&\30\2\0\6\0\300\3", 8}, {NULL, 0}, {"", 0}], 3) = 8
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\1\1\10\6\0\0\0\0]\1\0\0\0\0\0\0c\2\32\1 \2\330\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"%\30\1\0", 4}, {NULL, 0}, {"", 0}], 3) = 4
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\v\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\f\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\274\1\0\0\r\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 444}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 580
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\274\1\0\0\16\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 444}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 580
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\f\2\0\0\17\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 524}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 660
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\20\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1x\1\0\0\21\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 376}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 512
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\22\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\f\2\0\0\23\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 524}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 660
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\24\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1x\1\0\0\25\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 376}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 512
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\26\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\3\0\0\27\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 820}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 956
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\364\3\0\0\30\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 1012}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 1148
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1T\4\0\0\31\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 1108}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 1244
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\250\2\0\0\32\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 680}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 816
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\2\0\0\33\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 532}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 668
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\274\1\0\0\34\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 444}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 580
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\35\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1x\1\0\0\36\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 376}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 512
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\37\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\3\0\0 \0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 820}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 956
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\364\3\0\0!\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 1012}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 1148
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1T\4\0\0\"\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 1108}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 1244
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\250\2\0\0#\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 680}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 816
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\2\0\0$\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 532}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 668
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\274\1\0\0%\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 444}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 580
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0&\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1x\1\0\0'\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 376}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 512
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0(\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0)\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0*\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0+\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0,\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\254\1\0\0-\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 428}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 564
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\234\1\0\0.\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 412}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 548
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0/\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0000\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0001\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0002\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0003\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0004\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0005\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0006\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0007\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0008\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0009\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0:\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0;\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0<\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0=\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0>\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0?\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0@\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0A\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0B\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0C\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0D\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0E\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0F\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0G\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0H\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0I\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0J\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0K\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0L\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0M\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0N\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0O\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0P\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0Q\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0R\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0S\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0T\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0U\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0V\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\2\0\0W\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 580}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 716
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0X\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0Y\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0Z\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0[\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\2\0\0\\\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 540}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 676
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0]\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0^\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0_\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0`\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\354\1\0\0a\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 492}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 628
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0b\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\f\2\0\0c\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 524}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 660
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0d\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0e\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0f\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0g\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0h\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0i\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\254\1\0\0j\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 428}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 564
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\234\1\0\0k\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 412}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 548
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0l\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0m\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0n\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0o\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0p\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0q\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0r\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0s\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0t\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0u\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0v\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0w\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0x\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0y\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0z\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0{\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0|\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0}\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0~\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\177\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\200\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\201\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\202\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0\203\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0\204\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0\205\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\206\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\207\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0\210\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0\211\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\212\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\213\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0\214\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\215\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\216\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0\217\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\220\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0\221\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\222\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0010\1\0\0\223\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 304}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 440
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\2\0\0\224\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 580}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 716
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\225\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\226\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\227\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\230\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\2\0\0\231\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 540}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 676
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\232\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\233\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\234\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\235\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\354\1\0\0\236\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 492}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 628
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\237\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\f\2\0\0\240\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 524}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 660
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\241\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0\242\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\243\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\244\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\245\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\246\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\247\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\250\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\251\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\252\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\253\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\254\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\255\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1 \1\0\0\256\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 288}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 424
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\257\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\260\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\261\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\262\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\263\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1X\1\0\0\264\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 344}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 480
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\265\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1X\1\0\0\266\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 344}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 480
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1T\1\0\0\267\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 340}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 476
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\270\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1L\1\0\0\271\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 332}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 468
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0\272\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\273\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\274\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1L\1\0\0\275\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 332}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 468
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\276\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\277\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\300\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\301\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\302\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\303\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\304\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\305\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\306\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\307\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\310\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\311\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1 \1\0\0\312\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 288}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 424
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\313\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\374\0\0\0\314\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 252}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 388
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\315\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\316\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\317\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1X\1\0\0\320\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\35\0\0\0/org/a11y/atspi/"..., 344}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 480
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\321\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1X\1\0\0\322\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 344}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 480
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1T\1\0\0\323\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 340}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 476
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\324\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1L\1\0\0\325\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 332}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 468
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0\326\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\327\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\330\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1L\1\0\0\331\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 332}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 468
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\332\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\260\1\0\0\333\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 432}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 568
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1t\1\0\0\334\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 372}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 508
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1h\1\0\0\335\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 360}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 496
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1h\1\0\0\336\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 360}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 496
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1`\1\0\0\337\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 352}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 488
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\340\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\341\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\342\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\343\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\344\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\345\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\346\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\260\1\0\0\347\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 432}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 568
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1t\1\0\0\350\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 372}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 508
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1h\1\0\0\351\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 360}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 496
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1h\1\0\0\352\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 360}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 496
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1`\1\0\0\353\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\34\0\0\0/org/a11y/atspi/"..., 352}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 488
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\354\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\355\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\356\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\357\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\360\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\361\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\362\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\363\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\364\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1t\1\0\0\365\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 372}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 508
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\366\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\367\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1$\1\0\0\370\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 292}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 428
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\371\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0\372\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\373\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\374\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1t\1\0\0\375\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 372}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 508
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\376\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\377\0\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1$\1\0\0\0\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 292}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 428
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\1\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0\2\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\3\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\214\1\0\0\4\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 396}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 532
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\334\1\0\0\5\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 476}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 612
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\334\1\0\0\6\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 476}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 612
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\7\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0\10\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\214\1\0\0\t\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 396}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 532
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\334\1\0\0\n\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 476}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 612
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\334\1\0\0\v\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 476}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 612
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\f\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\3\0\0\r\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 828}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 964
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\16\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\17\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0\20\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\21\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\22\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0\23\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\24\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\25\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\26\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\27\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\30\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\31\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\3\0\0\32\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 828}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 964
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\33\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0\34\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1<\1\0\0\35\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 316}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 452
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\36\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\37\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1@\1\0\0 \1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 320}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 456
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0!\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\"\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0#\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0$\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0%\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0&\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0'\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0(\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0)\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0*\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0+\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0,\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0-\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0.\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0/\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0000\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0001\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0002\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1$\1\0\0003\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 292}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 428
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0004\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0005\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0006\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0007\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0008\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0009\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0:\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0;\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1 \1\0\0<\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 288}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 424
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\210\1\0\0=\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 392}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 528
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0>\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0?\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0@\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0A\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0B\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0C\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0D\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0E\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0F\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0G\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0H\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0I\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1$\1\0\0J\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 292}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 428
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0K\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0L\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0M\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0N\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0O\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\\\1\0\0P\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 348}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 484
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0Q\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0R\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1 \1\0\0S\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 288}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 424
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\210\1\0\0T\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 392}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 528
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0U\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0V\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0W\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0X\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\274\1\0\0Y\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 444}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 580
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0Z\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\2\0\0[\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 540}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 676
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0\\\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0]\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0^\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0_\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0`\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0a\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0b\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0014\1\0\0c\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 308}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 444
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0d\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0e\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0f\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\274\1\0\0g\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 444}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 580
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0h\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\2\0\0i\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 540}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 676
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0j\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0k\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0l\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1,\1\0\0m\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 300}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 436
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0n\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0o\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0p\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0q\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0r\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0s\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0t\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0u\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0v\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0w\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0x\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0y\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0z\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0{\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0|\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0}\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0~\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0\177\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0\200\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0\201\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0\202\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\24\1\0\0\203\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 276}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 412
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0\204\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\30\1\0\0\205\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 280}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 416
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1\34\1\0\0\206\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 284}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 420
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\207\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\0018\1\0\0\210\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 312}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 448
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1L\1\0\0\211\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 332}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 468
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1H\1\0\0\212\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 328}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 464
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\213\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1P\1\0\0\214\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 336}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 472
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1L\1\0\0\215\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 332}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 468
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\216\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\217\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\220\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
sendmsg(5, {msg_name(0)=NULL, msg_iov(2)=[{"l\4\1\1D\1\0\0\221\1\0\0x\0\0\0\1\1o\0\25\0\0\0/org/a11"..., 136}, {"\5\0\0\0:1.36\0\0\0\36\0\0\0/org/a11y/atspi/"..., 324}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 460
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}], 5, 0) = 0 (Timeout)
access("/usr/local/sbin/launchpad-integration", X_OK) = -1 ENOENT (No such file or directory)
access("/usr/local/bin/launchpad-integration", X_OK) = -1 ENOENT (No such file or directory)
access("/usr/sbin/launchpad-integration", X_OK) = -1 ENOENT (No such file or directory)
access("/usr/bin/launchpad-integration", X_OK) = 0
getuid()                                = 0
stat("/usr/bin/launchpad-integration", {st_mode=S_IFREG|0755, st_size=234, ...}) = 0
stat("/usr/bin/launchpad-integration", {st_mode=S_IFREG|0755, st_size=234, ...}) = 0
lstat("/usr/share/icons/Humanity/apps/16/lpi-help.svg", {st_mode=S_IFREG|0644, st_size=10261, ...}) = 0
open("/usr/share/icons/Humanity/apps/16/lpi-help.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=10261, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 10261
brk(0x288d000)                          = 0x288d000
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/apps/16/lpi-translate.svg", {st_mode=S_IFLNK|0777, st_size=30, ...}) = 0
stat("/usr/share/icons/Humanity/apps/16/lpi-translate.svg", {st_mode=S_IFREG|0644, st_size=5581, ...}) = 0
readlink("/usr/share/icons/Humanity/apps/16/lpi-translate.svg", "preferences-desktop-locale.svg", 256) = 30
open("/usr/share/icons/Humanity/apps/16/lpi-translate.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=5581, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 5581
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/apps/16/lpi-bug.svg", {st_mode=S_IFREG|0644, st_size=2549, ...}) = 0
open("/usr/share/icons/Humanity/apps/16/lpi-bug.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=2549, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 2549
read(15, "", 65536)                     = 0
close(15)                               = 0
open("/usr/share/locale/en_CA/LC_MESSAGES/launchpad-integration.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/launchpad-integration.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_CA/LC_MESSAGES/launchpad-integration.mo", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=509, ...}) = 0
mmap(NULL, 509, PROT_READ, MAP_PRIVATE, 15, 0) = 0x7fecccdee000
close(15)                               = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/launchpad-integration.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
lstat("/usr/share/icons/Humanity/actions/16/package-install.svg", {st_mode=S_IFREG|0644, st_size=1686, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-install.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1686, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1686
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-reinstall.svg", {st_mode=S_IFREG|0644, st_size=1725, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-reinstall.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1725, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1725
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-upgrade.svg", {st_mode=S_IFREG|0644, st_size=1692, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-upgrade.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=1692, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 1692
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-remove.svg", {st_mode=S_IFREG|0644, st_size=3690, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-remove.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=3690, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3690
read(15, "", 65536)                     = 0
close(15)                               = 0
lstat("/usr/share/icons/Humanity/actions/16/package-purge.svg", {st_mode=S_IFREG|0644, st_size=3842, ...}) = 0
open("/usr/share/icons/Humanity/actions/16/package-purge.svg", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=3842, ...}) = 0
read(15, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 3842
read(15, "", 65536)                     = 0
close(15)                               = 0
stat("/usr/sbin/update-apt-xapian-index", {st_mode=S_IFREG|0755, st_size=3521, ...}) = 0
getuid()                                = 0
stat("/usr/sbin/update-apt-xapian-index", {st_mode=S_IFREG|0755, st_size=3521, ...}) = 0
stat("/var/cache/apt/pkgcache.bin", {st_mode=S_IFREG|0644, st_size=35579920, ...}) = 0
stat("/var/lib/apt-xapian-index/update-timestamp", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
pipe([15, 16])                          = 0
fstat(15, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
fcntl(15, F_GETFL)                      = 0 (flags O_RDONLY)
rt_sigaction(SIGUSR1, {0x418770, [USR1], SA_RESTORER|SA_RESTART, 0x7fecd9d11420}, {SIG_DFL, [], 0}, 8) = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\r\0\201\0 \4\34\1\0\0\r\1\0\0\10\4\5\0\31\0\0\0Synaptic"..., 212}, {NULL, 0}, {"", 0}], 3) = 212
poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])
read(3, "\34\0\n\6\201\0 \4\34\1\0\0 \225\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 4096) = 160
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
lstat("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", {st_mode=S_IFLNK|0777, st_size=32, ...}) = 0
stat("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", {st_mode=S_IFREG|0644, st_size=5055, ...}) = 0
readlink("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", "../../apps/24/system-upgrade.svg"..., 256) = 32
open("/usr/share/icons/Humanity/actions/24/system-upgrade.svg", O_RDONLY) = 17
fstat(17, {st_mode=S_IFREG|0644, st_size=5055, ...}) = 0
read(17, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 5055
brk(0x28ae000)                          = 0x28ae000
read(17, "", 65536)                     = 0
close(17)                               = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\30\0\201\0 \4(\0\0\0)\0\0\0 \4\5\0\22\0\0\0\20\2\0\0\0\0\0\0"..., 16380}, {"\346\0003\0w\3\31\0", 8}, {"", 0}], 3) = 16388
brk(0x28e4000)                          = 0x28e4000
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLIN|POLLOUT}])
read(3, "\34\0\17\6\201\0 \4(\0\0\0-\225\v\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
writev(3, [{"F\0\5\0\305\1 \4\210\0 \4\332\0023\0P\0\31\0008\0\4\0\210\0 \4\0\0\10\0"..., 13908}, {"\0<\17\0\0V\17\0\0\10\266\1\0<\17\0\0r\265\1\0V\17\0\0\10\266\1\0<\17\0"..., 29080}, {"", 0}], 3) = 42988
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\6\5\0\355\1 \4\0\0\0\0\216\1\7\0-\0\37\0\230\27\v\0\3\0 \4 \1 \4"..., 8568}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 21300}, {"", 0}], 3) = 29868
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0\f\2 \4\v\2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0\376\1 \4"..., 14920}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 21300}, {"", 0}], 3) = 36220
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0!\2 \4 \2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0\376\1 \4"..., 14928}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 21300}, {"", 0}], 3) = 36228
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0006\2 \0045\2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0\376\1 \4"..., 14920}, {"noputvw|uuv{tuv{stuzstuzstuzsttz"..., 21300}, {"", 0}], 3) = 36220
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0K\2 \4J\2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0\376\1 \4"..., 14648}, {"cefuikl|ikl{ijk{hjkzhijzhijzhijz"..., 21300}, {"", 0}], 3) = 35948
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0^\2 \4]\2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0\376\1 \4"..., 16040}, {"\260\271\303\377\260\271\303\377\260\271\303\377\260\271\303\377\260\271\303\377\260\271\303\377\260\271\303\377\260\271\303\377"..., 416}, {"", 0}], 3) = 16456
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0{\2 \4z\2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\5\4\0{\2 \4"..., 6800}, {"EFFGUUVWabbdijjlnooqqrrtttuwuvvy"..., 31064}, {"", 0}], 3) = 37864
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\4\6\0\207\2 \4\206\2 \4 \1\0\0\0\1\0\0\1\0\0\0\230\6\5\0\376\1 \4"..., 16028}, {"\0\0e\2\0\3e\2\0\200b\2\0\0e\2\0gb\2\0\3e\2\0\200\237\2\0\0e\2"..., 1000}, {"", 0}], 3) = 17028
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\7\2\0\234\2 \0046\2\2\0\233\2 \4\230\n\0\1\3\0\0\0\253\1 \4\376\1 \4"..., 16152}, {"\0\0c\2\0\3c\2\0\200\351\0\0\0c\2\0g\351\0\0\3c\2\0\200:\1\0\0c\2"..., 1000}, {"", 0}], 3) = 17152
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\230\7\2\0\254\2 \0046\2\2\0\253\2 \4\230\n\0\1\3\0\0\0\241\1 \4\376\1 \4"..., 2120}, {NULL, 0}, {"", 0}], 3) = 2120
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 1 ([{fd=3, revents=POLLIN}])
read(3, "\16\0\22\n\201\0 \4\0\0>\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096) = 32
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"5\30\4\0\256\2 \4\201\0 \4\232\0\25\0\230\4\5\0\257\2 \4\256\2 \4$\1\0\0"..., 280}, {NULL, 0}, {"", 0}], 3) = 280
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
read(3, 0x254e2c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=9, events=POLLIN}, {fd=5, events=POLLIN}, {fd=15, events=POLLIN}], 6, 0) = 0 (Timeout)
futex(0x7fecda28f1a4, FUTEX_WAKE_PRIVATE, 2147483647) = 0
write(2, "terminate called after throwing "..., 48terminate called after throwing an instance of ') = 48
write(2, "std::out_of_range", 17std::out_of_range)       = 17
write(2, "'\n", 2'
)                      = 2
write(2, "  what():  ", 11  what():  )             = 11
write(2, "vector::_M_range_check", 22vector::_M_range_check)  = 22
write(2, "\n", 1
)                       = 1
rt_sigprocmask(SIG_UNBLOCK, [ABRT], NULL, 8) = 0
tgkill(4244, 4244, SIGABRT)             = 0
--- SIGABRT (Aborted) @ 0 (0) ---
+++ killed by SIGABRT +++
```

---

### Post by alquery on 2011-11-03
I forgot to mention - have you seen the comments at [Bug #807771]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/807771")? They seem to have some potential solutions there. Also, [this forum post]("http://ubuntuforums.org/showthread.php?t=1854470") might help.

---

### Post by SpEcIeS on 2011-11-04
That did it. Thank-you. :) I would not have put those two together.
```
Launch 'gnome-control-center'
Open 'Universal Access'
and set 'Screen Reader' to 'OFF'
```

---

