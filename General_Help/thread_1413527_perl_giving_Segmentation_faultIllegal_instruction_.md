---
title: "perl giving Segmentation fault/Illegal instruction can`t install new packages"
date: 2010-02-22
forum: General Help
---

### Post by urielka on 2010-02-22
After digging in on why apt-get crash all the time while trying to install programs i found out that the problem is perl.
running:
```
perl -e 'print "test"'
```
works ok but running:
```
perl -e 'use strict;'
```
will give me either "Segmentation fault" or "Illegal instruction".

Please help me resolve this as i don`t want to reinstall all the system.
by the way i tried reinstalling perl but with no luck.
I think the problem is with this line:
```
ioctl(4, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffcc1c3300) = -1 ENOTTY (Inappropriate ioctl for device)
```

here is the strace on perl(Illegal instruction):
```

execve("/usr/bin/perl", ["perl", "-e", "use strict;"], [/* 22 vars */]) = 0                                                  
brk(0)                                  = 0x11e6000                                                                          
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a4715000                                    
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a4713000                                    
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)                                              
open("/etc/ld.so.cache", O_RDONLY)      = 3                                                                                  
fstat(3, {st_mode=S_IFREG|0644, st_size=137456, ...}) = 0                                                                    
mmap(NULL, 137456, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a46f1000                                                            
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/usr/lib/libperl.so.5.10", O_RDONLY) = 3                                                                               
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\211\3\0\0\0\0\0"..., 832) = 832                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=1479240, ...}) = 0                                                                   
mmap(NULL, 3574888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08a418f000                                   
mprotect(0x7f08a42f0000, 2093056, PROT_NONE) = 0                                                                             
mmap(0x7f08a44ef000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x160000) = 0x7f08a44ef000         
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libdl.so.2", O_RDONLY)       = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\r\0\0\0\0\0\0"..., 832) = 832                                    
fstat(3, {st_mode=S_IFREG|0644, st_size=14696, ...}) = 0                                                                     
mmap(NULL, 2109696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08a3f8b000                                   
mprotect(0x7f08a3f8d000, 2097152, PROT_NONE) = 0                                                                             
mmap(0x7f08a418d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f08a418d000            
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libm.so.6", O_RDONLY)        = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p>\0\0\0\0\0\0"..., 832) = 832                                        
fstat(3, {st_mode=S_IFREG|0644, st_size=538920, ...}) = 0                                                                    
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a46f0000                                    
mmap(NULL, 2633944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08a3d07000                                   
mprotect(0x7f08a3d89000, 2097152, PROT_NONE) = 0                                                                             
mmap(0x7f08a3f89000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x82000) = 0x7f08a3f89000           
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libpthread.so.0", O_RDONLY)  = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340X\0\0\0\0\0\0"..., 832) = 832                                     
fstat(3, {st_mode=S_IFREG|0755, st_size=131174, ...}) = 0                                                                    
mmap(NULL, 2208640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08a3aeb000                                   
mprotect(0x7f08a3b02000, 2093056, PROT_NONE) = 0                                                                             
mmap(0x7f08a3d01000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f08a3d01000           
mmap(0x7f08a3d03000, 13184, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f08a3d03000               
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libc.so.6", O_RDONLY)        = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\353\1\0\0\0\0\0"..., 832) = 832                                  
fstat(3, {st_mode=S_IFREG|0755, st_size=1490312, ...}) = 0                                                                   
mmap(NULL, 3598344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08a377c000                                   
mprotect(0x7f08a38e2000, 2093056, PROT_NONE) = 0                                                                             
mmap(0x7f08a3ae1000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x165000) = 0x7f08a3ae1000         
mmap(0x7f08a3ae6000, 18440, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f08a3ae6000               
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libcrypt.so.1", O_RDONLY)    = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\n\0\0\0\0\0\0"..., 832) = 832                                       
fstat(3, {st_mode=S_IFREG|0644, st_size=43296, ...}) = 0                                                                     
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a46ef000                                    
mmap(NULL, 2326976, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08a3543000                                   
mprotect(0x7f08a354c000, 2097152, PROT_NONE) = 0                                                                             
mmap(0x7f08a374c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9000) = 0x7f08a374c000            
mmap(0x7f08a374e000, 184768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f08a374e000              
close(3)                                = 0                                                                                  
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a46ee000                                    
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a46ed000                                    
arch_prctl(ARCH_SET_FS, 0x7f08a46ed6f0) = 0                                                                                  
mprotect(0x7f08a374c000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08a3ae1000, 16384, PROT_READ) = 0                                                                               
mprotect(0x7f08a3d01000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08a3f89000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08a418d000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08a44ef000, 16384, PROT_READ) = 0                                                                               
mprotect(0x601000, 4096, PROT_READ)     = 0                                                                                  
mprotect(0x7f08a4716000, 4096, PROT_READ) = 0                                                                                
munmap(0x7f08a46f1000, 137456)          = 0                                                                                  
set_tid_address(0x7f08a46ed7c0)         = 12085                                                                              
set_robust_list(0x7f08a46ed7d0, 0x18)   = 0                                                                                  
futex(0x7fffcc1c3f5c, FUTEX_WAKE_PRIVATE, 1) = 0                                                                             
futex(0x7fffcc1c3f5c, 0x189 /* FUTEX_??? */, 1, NULL, 7f08a46ed6f0) = -1 EAGAIN (Resource temporarily unavailable)           
rt_sigaction(SIGRTMIN, {0x7f08a3af0760, [], SA_RESTORER|SA_SIGINFO, 0x7f08a3afa190}, NULL, 8) = 0                            
rt_sigaction(SIGRT_1, {0x7f08a3af07f0, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7f08a3afa190}, NULL, 8) = 0                  
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0                                                                       
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0                                                    
rt_sigaction(SIGFPE, {0x1, [FPE], SA_RESTORER|SA_RESTART, 0x7f08a37af530}, {SIG_DFL, [], 0}, 8) = 0                          
brk(0)                                  = 0x11e6000                                                                          
brk(0x1207000)                          = 0x1207000                                                                          
getuid()                                = 0                                                                                  
geteuid()                               = 0                                                                                  
getgid()                                = 0                                                                                  
getegid()                               = 0                                                                                  
open("/usr/lib/locale/locale-archive", O_RDONLY) = -1 ENOENT (No such file or directory)                                     
open("/usr/share/locale/locale.alias", O_RDONLY) = 3                                                                         
fstat(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0                                                                      
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08a4712000                                    
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570                                                                 
read(3, "", 4096)                       = 0                                                                                  
close(3)                                = 0                                                                                  
munmap(0x7f08a4712000, 4096)            = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)                      
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 3                                                           
fstat(3, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0                                                                       
mmap(NULL, 373, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4712000                                                               
close(3)                                = 0                                                                                  
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 3                                                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0                                                                     
mmap(NULL, 26048, PROT_READ, MAP_SHARED, 3, 0) = 0x7f08a470b000                                                              
close(3)                                = 0                                                                                  
futex(0x7f08a3ae5f60, FUTEX_WAKE_PRIVATE, 2147483647) = 0                                                                    
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)                         
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 3                                                              
fstat(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0                                                                        
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a470a000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)                           
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 3                                                                
fstat(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0                                                                        
mmap(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4709000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)                             
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 3                                                                  
fstat(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0                                                                       
mmap(NULL, 155, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4708000                                                               
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)                                
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 3                                                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0                                                                        
mmap(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4707000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)                               
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 3                                                                    
fstat(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0                                                                        
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4706000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)                            
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 3                                                                 
fstat(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0                                                                      
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3                                                 
fstat(3, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0                                                                        
mmap(NULL, 52, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4705000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)                            
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 3                                                                 
fstat(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0                                                                       
mmap(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4704000                                                               
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=966938, ...}) = 0
mmap(NULL, 966938, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4600000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
mmap(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4703000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a4702000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=256316, ...}) = 0
mmap(NULL, 256316, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08a45c1000
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "_O\236\224", 4)                = 4
close(3)                                = 0
brk(0x1228000)                          = 0x1228000
readlink("/proc/self/exe", "/usr/bin/perl", 4095) = 13
stat("/usr/local/lib/site_perl/5.10.0/x86_64-linux-gnu-thread-multi", 0x7fffcc1c3be0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/site_perl/5.10.0", 0x7fffcc1c3be0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/site_perl/x86_64-linux-gnu-thread-multi", 0x7fffcc1c3be0) = -1 ENOENT (No such file or directory)
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
lseek(0, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
lseek(1, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
ioctl(2, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
lseek(2, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
open("/dev/null", O_RDONLY)             = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffcc1c3a80) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
fstat(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 3), ...}) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0
stat("/etc/perl/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/etc/perl/strict.pm", 0x7fffcc1c3590) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.10.0/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.10.0/strict.pm", 0x7fffcc1c3590) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.10.0/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.10.0/strict.pm", 0x7fffcc1c3590) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/strict.pm", 0x7fffcc1c3590) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/strict.pm", 0x7fffcc1c3590) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.10/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.10/strict.pm", 0x7fffcc1c3590) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.10/strict.pmc", 0x7fffcc1c3640) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.10/strict.pm", {st_mode=S_IFREG|0644, st_size=879, ...}) = 0
open("/usr/share/perl/5.10/strict.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffcc1c3300) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "package strict;\n\n$strict::VERSIO"..., 4096) = 879
--- SIGILL (Illegal instruction) @ 0 (0) ---
+++ killed by SIGILL +++

```

and now for Segmentation fault:
```

execve("/usr/bin/perl", ["perl", "-e", "use strict;"], [/* 22 vars */]) = 0                                                  
brk(0)                                  = 0x858000                                                                           
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad602000                                    
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad600000                                    
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)                                              
open("/etc/ld.so.cache", O_RDONLY)      = 3                                                                                  
fstat(3, {st_mode=S_IFREG|0644, st_size=137456, ...}) = 0                                                                    
mmap(NULL, 137456, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5de000                                                            
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/usr/lib/libperl.so.5.10", O_RDONLY) = 3                                                                               
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\211\3\0\0\0\0\0"..., 832) = 832                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=1479240, ...}) = 0                                                                   
mmap(NULL, 3574888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08ad07c000                                   
mprotect(0x7f08ad1dd000, 2093056, PROT_NONE) = 0                                                                             
mmap(0x7f08ad3dc000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x160000) = 0x7f08ad3dc000         
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libdl.so.2", O_RDONLY)       = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\r\0\0\0\0\0\0"..., 832) = 832                                    
fstat(3, {st_mode=S_IFREG|0644, st_size=14696, ...}) = 0                                                                     
mmap(NULL, 2109696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08ace78000                                   
mprotect(0x7f08ace7a000, 2097152, PROT_NONE) = 0                                                                             
mmap(0x7f08ad07a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f08ad07a000            
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libm.so.6", O_RDONLY)        = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p>\0\0\0\0\0\0"..., 832) = 832                                        
fstat(3, {st_mode=S_IFREG|0644, st_size=538920, ...}) = 0                                                                    
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad5dd000                                    
mmap(NULL, 2633944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08acbf4000                                   
mprotect(0x7f08acc76000, 2097152, PROT_NONE) = 0                                                                             
mmap(0x7f08ace76000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x82000) = 0x7f08ace76000           
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libpthread.so.0", O_RDONLY)  = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340X\0\0\0\0\0\0"..., 832) = 832                                     
fstat(3, {st_mode=S_IFREG|0755, st_size=131174, ...}) = 0                                                                    
mmap(NULL, 2208640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08ac9d8000                                   
mprotect(0x7f08ac9ef000, 2093056, PROT_NONE) = 0                                                                             
mmap(0x7f08acbee000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f08acbee000           
mmap(0x7f08acbf0000, 13184, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f08acbf0000               
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libc.so.6", O_RDONLY)        = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\353\1\0\0\0\0\0"..., 832) = 832                                  
fstat(3, {st_mode=S_IFREG|0755, st_size=1490312, ...}) = 0                                                                   
mmap(NULL, 3598344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08ac669000                                   
mprotect(0x7f08ac7cf000, 2093056, PROT_NONE) = 0                                                                             
mmap(0x7f08ac9ce000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x165000) = 0x7f08ac9ce000         
mmap(0x7f08ac9d3000, 18440, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f08ac9d3000               
close(3)                                = 0                                                                                  
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)                                              
open("/lib/libcrypt.so.1", O_RDONLY)    = 3                                                                                  
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\n\0\0\0\0\0\0"..., 832) = 832                                       
fstat(3, {st_mode=S_IFREG|0644, st_size=43296, ...}) = 0                                                                     
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad5dc000                                    
mmap(NULL, 2326976, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f08ac430000                                   
mprotect(0x7f08ac439000, 2097152, PROT_NONE) = 0                                                                             
mmap(0x7f08ac639000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9000) = 0x7f08ac639000            
mmap(0x7f08ac63b000, 184768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f08ac63b000              
close(3)                                = 0                                                                                  
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad5db000                                    
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad5da000                                    
arch_prctl(ARCH_SET_FS, 0x7f08ad5da6f0) = 0                                                                                  
mprotect(0x7f08ac639000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08ac9ce000, 16384, PROT_READ) = 0                                                                               
mprotect(0x7f08acbee000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08ace76000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08ad07a000, 4096, PROT_READ) = 0                                                                                
mprotect(0x7f08ad3dc000, 16384, PROT_READ) = 0                                                                               
mprotect(0x601000, 4096, PROT_READ)     = 0                                                                                  
mprotect(0x7f08ad603000, 4096, PROT_READ) = 0                                                                                
munmap(0x7f08ad5de000, 137456)          = 0                                                                                  
set_tid_address(0x7f08ad5da7c0)         = 12083                                                                              
set_robust_list(0x7f08ad5da7d0, 0x18)   = 0                                                                                  
futex(0x7ffffe32210c, FUTEX_WAKE_PRIVATE, 1) = 0                                                                             
futex(0x7ffffe32210c, 0x189 /* FUTEX_??? */, 1, NULL, 7f08ad5da6f0) = -1 EAGAIN (Resource temporarily unavailable)           
rt_sigaction(SIGRTMIN, {0x7f08ac9dd760, [], SA_RESTORER|SA_SIGINFO, 0x7f08ac9e7190}, NULL, 8) = 0                            
rt_sigaction(SIGRT_1, {0x7f08ac9dd7f0, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7f08ac9e7190}, NULL, 8) = 0                  
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0                                                                       
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0                                                    
rt_sigaction(SIGFPE, {0x1, [FPE], SA_RESTORER|SA_RESTART, 0x7f08ac69c530}, {SIG_DFL, [], 0}, 8) = 0                          
brk(0)                                  = 0x858000                                                                           
brk(0x879000)                           = 0x879000                                                                           
getuid()                                = 0                                                                                  
geteuid()                               = 0                                                                                  
getgid()                                = 0                                                                                  
getegid()                               = 0                                                                                  
open("/usr/lib/locale/locale-archive", O_RDONLY) = -1 ENOENT (No such file or directory)                                     
open("/usr/share/locale/locale.alias", O_RDONLY) = 3                                                                         
fstat(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0                                                                      
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f08ad5ff000                                    
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570                                                                 
read(3, "", 4096)                       = 0                                                                                  
close(3)                                = 0                                                                                  
munmap(0x7f08ad5ff000, 4096)            = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)                      
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 3                                                           
fstat(3, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0                                                                       
mmap(NULL, 373, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5ff000                                                               
close(3)                                = 0                                                                                  
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 3                                                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0                                                                     
mmap(NULL, 26048, PROT_READ, MAP_SHARED, 3, 0) = 0x7f08ad5f8000                                                              
close(3)                                = 0                                                                                  
futex(0x7f08ac9d2f60, FUTEX_WAKE_PRIVATE, 2147483647) = 0                                                                    
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)                         
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 3                                                              
fstat(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0                                                                        
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f7000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)                           
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 3                                                                
fstat(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0                                                                        
mmap(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f6000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)                             
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 3                                                                  
fstat(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0                                                                       
mmap(NULL, 155, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f5000                                                               
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)                                
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 3                                                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0                                                                        
mmap(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f4000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)                               
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 3                                                                    
fstat(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0                                                                        
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f3000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)                            
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 3                                                                 
fstat(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0                                                                      
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3                                                 
fstat(3, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0                                                                        
mmap(NULL, 52, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f2000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)                            
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 3                                                                 
fstat(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0                                                                       
mmap(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f1000                                                               
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)                             
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 3                                                                  
fstat(3, {st_mode=S_IFREG|0644, st_size=966938, ...}) = 0                                                                    
mmap(NULL, 966938, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad4ed000                                                            
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)                                
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3                                                                     
fstat(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0                                                                      
mmap(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5f0000                                                              
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)                             
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3                                                                  
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0                                                                        
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad5ef000                                                                
close(3)                                = 0                                                                                  
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)                               
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3                                                                    
fstat(3, {st_mode=S_IFREG|0644, st_size=256316, ...}) = 0                                                                    
mmap(NULL, 256316, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f08ad4ae000                                                            
close(3)                                = 0                                                                                  
open("/dev/urandom", O_RDONLY)          = 3                                                                                  
read(3, "\361z\351v", 4)                = 4                                                                                  
close(3)                                = 0                                                                                  
brk(0x89a000)                           = 0x89a000                                                                           
readlink("/proc/self/exe", "/usr/bin/perl", 4095) = 13                                                                       
stat("/usr/local/lib/site_perl/5.10.0/x86_64-linux-gnu-thread-multi", 0x7ffffe321d90) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/site_perl/5.10.0", 0x7ffffe321d90) = -1 ENOENT (No such file or directory)                              
stat("/usr/local/lib/site_perl/x86_64-linux-gnu-thread-multi", 0x7ffffe321d90) = -1 ENOENT (No such file or directory)       
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0                                             
lseek(0, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)                                                           
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0                                             
lseek(1, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)                                                           
ioctl(2, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0                                             
lseek(2, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)                                                           
open("/dev/null", O_RDONLY)             = 3                                                                                  
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7ffffe321c30) = -1 ENOTTY (Inappropriate ioctl for device)                         
lseek(3, 0, SEEK_CUR)                   = 0                                                                                  
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0                                                                                  
fstat(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 3), ...}) = 0                                                             
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0                                                                         
stat("/etc/perl/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                                         
stat("/etc/perl/strict.pm", 0x7ffffe321740) = -1 ENOENT (No such file or directory)                                          
stat("/usr/local/lib/perl/5.10.0/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                        
stat("/usr/local/lib/perl/5.10.0/strict.pm", 0x7ffffe321740) = -1 ENOENT (No such file or directory)                         
stat("/usr/local/share/perl/5.10.0/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                      
stat("/usr/local/share/perl/5.10.0/strict.pm", 0x7ffffe321740) = -1 ENOENT (No such file or directory)                       
stat("/usr/lib/perl5/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                                    
stat("/usr/lib/perl5/strict.pm", 0x7ffffe321740) = -1 ENOENT (No such file or directory)                                     
stat("/usr/share/perl5/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                                  
stat("/usr/share/perl5/strict.pm", 0x7ffffe321740) = -1 ENOENT (No such file or directory)                                   
stat("/usr/lib/perl/5.10/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                                
stat("/usr/lib/perl/5.10/strict.pm", 0x7ffffe321740) = -1 ENOENT (No such file or directory)                                 
stat("/usr/share/perl/5.10/strict.pmc", 0x7ffffe3217f0) = -1 ENOENT (No such file or directory)                              
stat("/usr/share/perl/5.10/strict.pm", {st_mode=S_IFREG|0644, st_size=879, ...}) = 0                                         
open("/usr/share/perl/5.10/strict.pm", O_RDONLY) = 4                                                                         
ioctl(4, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7ffffe3214b0) = -1 ENOTTY (Inappropriate ioctl for device)                         
lseek(4, 0, SEEK_CUR)                   = 0                                                                                  
read(4, "package strict;\n\n$strict::VERSIO"..., 4096) = 879                                                                 
lseek(4, 878, SEEK_SET)                 = 878                                                                                
lseek(4, 0, SEEK_CUR)                   = 878                                                                                
close(4)                                = 0                                                                                  
--- SIGSEGV (Segmentation fault) @ 0 (0) ---                                                                                 
+++ killed by SIGSEGV +++    

```

---

