---
title: "Firefox gnome-vfs related hang"
date: 2009-07-24
forum: General Help
---

### Post by heluani on 2009-07-24
Hello there, not an Ubuntu question but lots of smart people here, one might now the problem.

I built Firefox 3.5.1 against xulrunner 1.9.1.1 from sources and it hangs essentially whenever I access the filesystem (opening Edit->Preferences, File-->Save as, browsing the filesystem, always in the same directories, etc)

I think I narrowed it down to the calls to gnome-vfs modules (in particular libfile.so) but I just don't know how to solve this

linux x86_64 Multilib Kernel 2.6.29.5, gnome-vfs-2.24.1 

Here's a trace when hung (opening Edit-->Preferences)
```
(gdb) where
#0  __nptl_setxid (cmdp=0x7fff1c1baea0) at allocatestack.c:1105
#1  0x00007f71e4017a44 in *__GI_seteuid (uid=<value optimized out>)
    at ../sysdeps/unix/sysv/linux/seteuid.c:44
#2  0x00007f71d8b9fda0 in gnome_vfs_add_module_to_hash_table (
    name=0x7f71cb3fede8 "file") at gnome-vfs-method.c:368
#3  0x00007f71d8b9ff1e in gnome_vfs_transform_get (
    name=0x7fff1c1baec0 "õÿÿÿÀ\005") at gnome-vfs-method.c:450
#4  0x00007f71d8bad852 in gnome_vfs_uri_new_private (
    text_uri=0x7f71cbf482e8 "file:///home/heluani/Downloads/", 
    allow_unknown_methods=0, allow_unsafe_methods=<value optimized out>, 
    allow_transforms=<value optimized out>) at gnome-vfs-uri.c:573
#5  0x00007f71d8ba9179 in gnome_vfs_get_file_info (
    text_uri=0x7fff1c1baec0 "õÿÿÿÀ\005", info=0x80, options=4294967295)
    at gnome-vfs-ops.c:304
#6  0x00007f71d5ce0e64 in ?? ()
   from /opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/components/libimgicon.so
#7  0x00007f71d5ce1265 in ?? ()
   from /opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/components/libimgicon.so
#8  0x00007f71d5cdf11c in ?? ()
   from /opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/components/libimgicon.so
#9  0x00007f71e1bf5a3a in ?? ()
   from /opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/libxul.so
#10 0x00007f71e1be29cc in ?? ()
   from /opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/libxul.so
#11 0x00007f71e1d1be2e in ?? ()
   from /opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/libxul.so

```
Here is what strace tells in that hang (the more relevant part towards the end)
(should probably remove private data :) )
```

...
...
futex(0x7f454d47b10c, FUTEX_CMP_REQUEUE_PRIVATE, 1, 2147483647, 0x7f454d4631f8, 144) = 1
futex(0x7f454706d4f8, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x7f455b6b8bcc, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x7f455b6b8bc8, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
write(2, "WARNING: redundant multiplexed do"..., 148WARNING: redundant multiplexed document?: 'docMapEntry->mString == nsnull', file /home/heluani/mozilla-1.9.1/xpcom/io/nsFastLoadFile.cpp, line 1404
) = 148
write(54, "\0\0\0\3\0\0\0(\0\0\0!\0\0\0\7\336\224r\320\2004\21\323\223\231\0\20K\240\375@\7"..., 2588) = 2588
lseek(54, 0, SEEK_SET)                  = 0
write(54, "XPCOM\nMozFASL\r\n\32\0\0\0\0\0\0\0\5\0\20\222z\0\20\234\226"..., 32) = 32
lseek(31, 0, SEEK_SET)                  = 0
read(31, "XPCOM\nMozFASL\r\n\32\0\0\0\0\0\0\0\5\0\20\222z\0\20\234\226\376"..., 49152) = 49152
read(31, ":\0\1QC\5\303\0\0\0\260\260c\3\f\263\2725c\3c\6c\t\263c\3c\6c\0253\0"..., 49152) = 49152
read(31, "\270\0\16V\0\4V\0\0077:\0\1V\0\6V\0\0107\23\7\0\33V\0\2\270\0\32V\0\4"..., 49152) = 49152
read(31, "\0\0\2\0\0\0C\0c\0\4\0\0\0\"\0\0\0@\0m\0o\0z\0i\0l\0l\0a"..., 49152) = 49152
read(31, "\0W\0\2Q\323\0\1\0\16W\0\3Q\323\0\1\0\17W\0\4Q;\0\0205\0\21\270\0\22V"..., 49152) = 49152
read(31, "\0.\0o\0r\0g\0/\0k\0e\0y\0m\0a\0s\0t\0e\0r\0/\0g\0"..., 49152) = 49152
read(31, "\0u\0D\0r\0o\0p\0H\0a\0n\0d\0l\0e\0r\0\4\0\0\0\7\0\0\0"..., 49152) = 49152
read(31, "\0l\0t\0B\0r\0o\0w\0s\0e\0r\0D\0o\0n\0t\0A\0s\0k\0"..., 49152) = 49152
read(31, "\0i\0n\0t\0P\0r\0e\0v\0i\0e\0w\0\0\0\0\0\0\300\0\0\t\0\255\336"..., 49152) = 49152
read(31, "\0d\0e\0\4\0\0\0\16\0\0\0s\0a\0v\0e\0d\0-\0i\0c\0o\0n\0"..., 49152) = 49152
read(31, "\0s\0t\0a\0n\0c\0e\0\4\0\0\0\21\0\0\0n\0s\0I\0S\0u\0p\0"..., 49152) = 49152
read(31, "\f3\0\264\260\260c\3\310`\v\v\263\313\260a\1\311`\n\0\0\0\0\0#\0\0\0chro"..., 49152) = 49152
read(31, "\0r\0\0\0\4\0\0\0\4\0\0\0z\0o\0o\0m\0\4\0\0\0\5\0\0\0r\0e\0"..., 49152) = 49152
read(31, "\0\t\0\255\336O\0\0\0\0\0\0\0\2640\0\0\t\0\0\0-\0\0\0\1\0\0\0\1\0\0\0"..., 49152) = 49152
read(31, "\276\200\2\250\276\200\2\254\276\200\2\260\276\200\2\272\276\200\2\313\276\200\2\323\276\200\2\350\276\200\2\375\276"..., 49152) = 49152
read(31, "/browser/content/nsContextMenu.js"..., 49152) = 49152
read(31, "\0a\0U\0R\0L\0\3\0\0\0i\0o\0s\0\0\0\3\0\0\0u\0r\0i\0\0\0"..., 49152) = 49152
read(31, "t\0I\0n\0d\0e\0x\0\4\0\0\0\7\0\0\0c\0o\0l\0u\0m\0n\0s"..., 49152) = 49152
read(31, "\0+\0\0\0\27\0k\0e\0y\0_\0s\0w\0i\0t\0c\0h\0T\0e\0x\0"..., 49152) = 49152
read(31, "\0u\0m\0n\0s\0\0\0=\0h\0t\0t\0p\0:\0/\0/\0w\0w\0w\0"..., 49152) = 49152
read(31, "\0_\0s\0e\0t\0D\0e\0t\0a\0i\0l\0s\0F\0i\0e\0l\0d\0"..., 49152) = 49152
read(31, "\0o\0m\0m\0o\0n\0D\0i\0a\0l\0o\0g\0O\0n\0E\0x\0t\0"..., 49152) = 49152
read(31, "\0\25\0p\0r\0i\0v\0a\0c\0y\0.\0c\0p\0d\0.\0p\0a\0s\0"..., 49152) = 7318
read(31, ""..., 49150)                  = 0
lseek(54, 16, SEEK_SET)                 = 16
write(54, "\333E\254\305"..., 4)        = 4
write(54, ""..., 0)                     = 0
close(54)                               = 0
close(31)                               = 0
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\1\30\r\0&\4`\2!\4`\2\0\0\0\0\1\0\1\0\0\0\1\0!\0\0\0\32(\0\0\0"..., 1360}, {NULL, 0}, {""..., 0}], 3) = 1360
read(3, 0x7f455b685074, 4096)           = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=18, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=30, events=POLLIN}, {fd=19, events=POLLIN}], 10, 0) = 1 ([{fd=19, revents=POLLIN}])
read(19, "\372"..., 1)                  = 1
poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"\22\0\v\0\32\4`\2\370\0\0\0\351\0\0\0\10\0\1\0\23\0\0\0Firefox P"..., 4264}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 28672}, {""..., 0}], 3) = 32936
write(20, "\372"..., 1)                 = 1
stat("/opt/firefox-3.5.1/lib64/firefox-3.5.1/chrome/en-US.jar", {st_mode=S_IFREG|0664, st_size=155544, ...}) = 0
open("/opt/firefox-3.5.1/lib64/firefox-3.5.1/chrome/en-US.jar", O_RDONLY) = 31
lseek(31, 5743, SEEK_SET)               = 5743
read(31, "PK\3\4\24\0\0\0\0\0/\220\365:\307\223\21\5\t\1\0\0\t\1\0\0\31\0\0\0"..., 30) = 30
lseek(31, 5798, SEEK_SET)               = 5798
read(31, "<!ENTITY  brandShortName        \""..., 265) = 265
close(31)                               = 0
stat("/opt/firefox-3.5.1/lib64/firefox-3.5.1/chrome/en-US.jar", {st_mode=S_IFREG|0664, st_size=155544, ...}) = 0
open("/opt/firefox-3.5.1/lib64/firefox-3.5.1/chrome/en-US.jar", O_RDONLY) = 31
lseek(31, 118954, SEEK_SET)             = 118954
read(31, "PK\3\4\24\0\0\0\0\0U\220\365:\253\243\367\16\275\6\0\0\275\6\0\0#\0\0\0"..., 30) = 30
lseek(31, 119019, SEEK_SET)             = 119019
read(31, "<!ENTITY startup.label           "..., 1725) = 1725
close(31)                               = 0
futex(0x7f454d47b10c, FUTEX_CMP_REQUEUE_PRIVATE, 1, 2147483647, 0x7f454d4631f8, 146) = 1
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", {st_mode=S_IFREG|0664, st_size=2002311, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", O_RDONLY) = 31
lseek(31, 1001889, SEEK_SET)            = 1001889
read(31, "PK\3\4\24\0\0\0\0\0\3\215\365:\374\"\3617\326\5\0\0\326\5\0\0$\0\0\0"..., 30) = 30
lseek(31, 1001955, SEEK_SET)            = 1001955
read(31, "<?xml version=\"1.0\"?>\n\n<bindings "..., 1494) = 1494
close(31)                               = 0
mmap(NULL, 1048576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f45452ac000
munmap(0x7f45452ac000, 1048576)         = 0
mmap(0x7f4545300000, 1048576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f45452ac000
munmap(0x7f45452ac000, 1048576)         = 0
mmap(NULL, 2097152, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f45451ac000
munmap(0x7f45451ac000, 2097152)         = 0
mmap(0x7f4545200000, 1048576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4545200000
madvise(0x7f4545200000, 1048576, MADV_DONTNEED) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", {st_mode=S_IFREG|0664, st_size=415915, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", O_RDONLY) = 31
lseek(31, 264241, SEEK_SET)             = 264241
read(31, "PK\3\4\24\0\0\0\0\0\4\215\365:\5\"-<\23\t\0\0\23\t\0\0 \0\0\0"..., 30) = 30
lseek(31, 264303, SEEK_SET)             = 264303
read(31, "/* ***** BEGIN LICENSE BLOCK ****"..., 2323) = 2323
close(31)                               = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", {st_mode=S_IFREG|0664, st_size=2002311, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", O_RDONLY) = 31
lseek(31, 1051955, SEEK_SET)            = 1051955
read(31, "PK\3\4\24\0\0\0\0\0\3\215\365: \35\216\232;X\0\0;X\0\0$\0\0\0"..., 30) = 30
lseek(31, 1052021, SEEK_SET)            = 1052021
read(31, "<?xml version=\"1.0\"?>\n\n<bindings "..., 22587) = 22587
close(31)                               = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", {st_mode=S_IFREG|0664, st_size=415915, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", O_RDONLY) = 31
lseek(31, 196624, SEEK_SET)             = 196624
read(31, "PK\3\4\24\0\0\0\0\0\4\215\365:\26|\216\351H\22\0\0H\22\0\0 \0\0\0"..., 30) = 30
lseek(31, 196686, SEEK_SET)             = 196686
read(31, "/* ***** BEGIN LICENSE BLOCK ****"..., 4680) = 4680
close(31)                               = 0
uname({sys="Linux", node="campari", ...}) = 0
write(2, "WARNING: recurring into frame con"..., 177WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026
) = 177
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", {st_mode=S_IFREG|0664, st_size=2002311, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", O_RDONLY) = 31
lseek(31, 838247, SEEK_SET)             = 838247
read(31, "PK\3\4\24\0\0\0\0\0\3\215\365:I\326\311\240-\f\0\0-\f\0\0$\0\0\0"..., 30) = 30
lseek(31, 838313, SEEK_SET)             = 838313
read(31, "<?xml version=\"1.0\"?>\n\n<bindings "..., 3117) = 3117
close(31)                               = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", {st_mode=S_IFREG|0664, st_size=415915, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", O_RDONLY) = 31
lseek(31, 229977, SEEK_SET)             = 229977
read(31, "PK\3\4\24\0\0\0\0\0\4\215\365:\22\334\313Fy\20\0\0y\20\0\0 \0\0\0"..., 30) = 30
lseek(31, 230039, SEEK_SET)             = 230039
read(31, "/* ***** BEGIN LICENSE BLOCK ****"..., 4217) = 4217
close(31)                               = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", {st_mode=S_IFREG|0664, st_size=415915, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", O_RDONLY) = 31
lseek(31, 24605, SEEK_SET)              = 24605
read(31, "PK\3\4\24\0\0\0\0\0\4\215\365:/\234\340\215I\t\0\0I\t\0\0&\0\0\0"..., 30) = 30
lseek(31, 24673, SEEK_SET)              = 24673
read(31, "<?xml version=\"1.0\"?>\n\n<bindings "..., 2377) = 2377
close(31)                               = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", {st_mode=S_IFREG|0664, st_size=2002311, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/toolkit.jar", O_RDONLY) = 31
lseek(31, 933332, SEEK_SET)             = 933332
read(31, "PK\3\4\24\0\0\0\0\0\3\215\365:R\10\267V\220\v\0\0\220\v\0\0%\0\0\0"..., 30) = 30
lseek(31, 933399, SEEK_SET)             = 933399
read(31, "<?xml version=\"1.0\"?>\n\n<bindings "..., 2960) = 2960
close(31)                               = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", {st_mode=S_IFREG|0664, st_size=415915, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/classic.jar", O_RDONLY) = 31
lseek(31, 22322, SEEK_SET)              = 22322
read(31, "PK\3\4\24\0\0\0\0\0\4\215\365:\341\340\354-\254\10\0\0\254\10\0\0!\0\0\0"..., 30) = 30
lseek(31, 22385, SEEK_SET)              = 22385
read(31, "/*\n# -*- Mode: Java; tab-width: 4"..., 2220) = 2220
close(31)                               = 0
write(2, "WARNING: recurring into frame con"..., 177WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026
) = 177
futex(0x7f454d47b10c, FUTEX_CMP_REQUEUE_PRIVATE, 1, 2147483647, 0x7f454d4631f8, 148) = 1
open("/home/heluani/.config/user-dirs.dirs", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/home/heluani/Desktop", F_OK)   = 0
open("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite", O_RDWR|O_CREAT, 0644) = 31
fcntl(31, F_GETFD)                      = 0
fcntl(31, F_SETFD, FD_CLOEXEC)          = 0
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 0, SEEK_SET)                  = 0
read(31, "SQLite format 3\0\4\0\1\1\0@  \0\0\0\2\0\0\0\0\0"..., 100) = 100
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 0, SEEK_SET)                  = 0
read(31, "SQLite format 3\0\4\0\1\1\0@  \0\0\0\2\0\0\0\0\0"..., 1024) = 1024
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=1073741825, len=1}) = 0
open("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", O_RDWR|O_CREAT, 0644) = 54
open("/home/heluani/.mozilla/firefox/oamb7vuq.default", O_RDONLY) = 55
fcntl(55, F_GETFD)                      = 0
fcntl(55, F_SETFD, FD_CLOEXEC)          = 0
fcntl(54, F_GETFD)                      = 0
fcntl(54, F_SETFD, FD_CLOEXEC)          = 0
lseek(54, 0, SEEK_SET)                  = 0
write(54, "\331\325\5\371 \241c\327\0\0\0\0\226o\365t\0\0\0\2\0\0\2\0\0\0\4\0\0\0\0\0\0"..., 512) = 512
lseek(31, 1024, SEEK_SET)               = 1024
read(31, "\r\0\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1024) = 1024
close(55)                               = 0
close(54)                               = 0
unlink("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal") = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=2}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=1073741825, len=1}) = 0
open("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", O_RDWR|O_CREAT, 0644) = 54
open("/home/heluani/.mozilla/firefox/oamb7vuq.default", O_RDONLY) = 55
fcntl(55, F_GETFD)                      = 0
fcntl(55, F_SETFD, FD_CLOEXEC)          = 0
fcntl(54, F_GETFD)                      = 0
fcntl(54, F_SETFD, FD_CLOEXEC)          = 0
lseek(54, 0, SEEK_SET)                  = 0
write(54, "\331\325\5\371 \241c\327\0\0\0\0\336\210\304%\0\0\0\2\0\0\2\0\0\0\4\0\0\0\0\0\0"..., 512) = 512
close(55)                               = 0
close(54)                               = 0
unlink("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal") = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=2}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=1073741825, len=1}) = 0
open("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", O_RDWR|O_CREAT, 0644) = 54
open("/home/heluani/.mozilla/firefox/oamb7vuq.default", O_RDONLY) = 55
fcntl(55, F_GETFD)                      = 0
fcntl(55, F_SETFD, FD_CLOEXEC)          = 0
fcntl(54, F_GETFD)                      = 0
fcntl(54, F_SETFD, FD_CLOEXEC)          = 0
lseek(54, 0, SEEK_SET)                  = 0
write(54, "\331\325\5\371 \241c\327\0\0\0\0\17%Q\"\0\0\0\2\0\0\2\0\0\0\4\0\0\0\0\0\0"..., 512) = 512
close(55)                               = 0
close(54)                               = 0
unlink("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal") = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=2}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
fcntl(31, F_SETLK, {type=F_RDLCK, whence=SEEK_SET, start=1073741826, len=510}) = 0
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=1073741824, len=1}) = 0
access("/home/heluani/.mozilla/firefox/oamb7vuq.default/downloads.sqlite-journal", F_OK) = -1 ENOENT (No such file or directory)
fstat(31, {st_mode=S_IFREG|0644, st_size=2048, ...}) = 0
lseek(31, 24, SEEK_SET)                 = 24
read(31, "\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0\0"..., 16) = 16
fcntl(31, F_SETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/en-US.jar", {st_mode=S_IFREG|0664, st_size=321895, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/chrome/en-US.jar", O_RDONLY) = 54
lseek(54, 163982, SEEK_SET)             = 163982
read(54, "PK\3\4\24\0\0\0\0\0\3\215\365:?\312\25\333\351\27\0\0\351\27\0\0003\0\0\0"..., 30) = 30
lseek(54, 164063, SEEK_SET)             = 164063
read(54, "# LOCALIZATION NOTE (seconds, min"..., 6121) = 6121
close(54)                               = 0
open("/home/heluani/.config/user-dirs.dirs", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/components/necko_file.xpt", {st_mode=S_IFREG|0664, st_size=437, ...}) = 0
open("/opt/xulrunner-1.9.1.1/lib64/xulrunner-1.9.1.1/components/necko_file.xpt", O_RDONLY) = 54
read(54, "XPCOM\nTypeLib\r\n\32\1\2\0\6\0\0\1\265\0\0\0\"\0\0\0\311\200"..., 437) = 437
close(54)                               = 0
stat("/opt/firefox-3.5.1/lib64/firefox-3.5.1/chrome/en-US.jar", {st_mode=S_IFREG|0664, st_size=155544, ...}) = 0
open("/opt/firefox-3.5.1/lib64/firefox-3.5.1/chrome/en-US.jar", O_RDONLY) = 54
lseek(54, 123673, SEEK_SET)             = 123673
read(54, "PK\3\4\24\0\0\0\0\0U\220\365:\353\252\265#(\20\0\0(\20\0\0001\0\0\0"..., 30) = 30
lseek(54, 123752, SEEK_SET)             = 123752
read(54, "#### Security\n\n# LOCALIZATION NOT"..., 4136) = 4136
close(54)                               = 0
open("/home/heluani/.config/user-dirs.dirs", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/home/heluani/Downloads", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
stat("/home/heluani/.gnome2/vfs/modules", 0x7fff3d4907f0) = -1 ENOENT (No such file or directory)
stat("/etc/gnome/gnome-vfs-2.0/modules", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
geteuid()                               = 1000
getegid()                               = 1000
getuid()                                = 1000
tgkill(15961, 15972, SIGRT_1)           = 0
tgkill(15961, 15971, SIGRT_1)           = 0
tgkill(15961, 15970, SIGRT_1)           = 0
tgkill(15961, 15969, SIGRT_1)           = 0
tgkill(15961, 15968, SIGRT_1)           = 0
tgkill(15961, 15966, SIGRT_1)           = 0
tgkill(15961, 15965, SIGRT_1)           = 0
tgkill(15961, 15964, SIGRT_1)           = 0
tgkill(15961, 15963, SIGRT_1)           = 0
tgkill(15961, 15962, SIGRT_1)           = 0
futex(0x7fff3d4908c0, FUTEX_WAIT_PRIVATE, 4294967286, NULL

```
Here's what console says about the same hang
```

WARNING: NS_ENSURE_SUCCESS(rv, rv) failed with result 0x80004005: file /home/heluani/mozilla-1.9.1/toolkit/xre/nsXREDirProvider.cpp, line 1151
WARNING: NS_ENSURE_TRUE(mHiddenWindow) failed: file /home/heluani/mozilla-1.9.1/xpfe/appshell/src/nsAppShellService.cpp, line 396
++WEBSHELL 0x7f03cce27000 == 1
++DOMWINDOW == 1 (0x7f03cce2a458) [serial = 1] [outer = (nil)]
++WEBSHELL 0x7f03bdfa4000 == 2
++DOMWINDOW == 2 (0x7f03bdfa5458) [serial = 2] [outer = (nil)]
++DOMWINDOW == 3 (0x7f03bdfa7458) [serial = 3] [outer = 0x7f03bdfa5400]
++DOMWINDOW == 4 (0x7f03bddb0058) [serial = 4] [outer = 0x7f03cce2a400]
++WEBSHELL 0x7f03be07a400 == 3
++DOMWINDOW == 5 (0x7f03be07b058) [serial = 5] [outer = (nil)]
++WEBSHELL 0x7f03bdbac800 == 4
WARNING: NS_ENSURE_TRUE(browserChrome) failed: file /home/heluani/mozilla-1.9.1/docshell/base/nsDocShell.cpp, line 9291
WARNING: Something wrong when creating the docshell for a frameloader!: file /home/heluani/mozilla-1.9.1/content/base/src/nsFrameLoader.cpp, line 902
WARNING: NS_ENSURE_SUCCESS(rv, rv) failed with result 0x80004005: file /home/heluani/mozilla-1.9.1/content/base/src/nsFrameLoader.cpp, line 926
WARNING: NS_ENSURE_SUCCESS(rv, rv) failed with result 0x80004005: file /home/heluani/mozilla-1.9.1/content/base/src/nsFrameLoader.cpp, line 182
++WEBSHELL 0x7f03bca09c00 == 5
++DOMWINDOW == 6 (0x7f03bcb75458) [serial = 6] [outer = (nil)]
WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026
WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026
++DOMWINDOW == 7 (0x7f03bbd15858) [serial = 7] [outer = 0x7f03be07b000]
++DOMWINDOW == 8 (0x7f03bc5a2858) [serial = 8] [outer = 0x7f03bcb75400]
++DOMWINDOW == 9 (0x7f03b8cb1458) [serial = 9] [outer = 0x7f03bcb75400]
WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026
WARNING: NS_ENSURE_TRUE(sgo || !hasHadScriptObject) failed: file /home/heluani/mozilla-1.9.1/content/base/src/nsContentUtils.cpp, line 4514
WARNING: NS_ENSURE_SUCCESS(rv, 0) failed with result 0x8000FFFF: file /home/heluani/mozilla-1.9.1/content/base/src/nsContentUtils.cpp, line 2717
++WEBSHELL 0x7f03b8a4dc00 == 6
++DOMWINDOW == 10 (0x7f03c0542c58) [serial = 10] [outer = (nil)]
++DOMWINDOW == 11 (0x7f03b8944c58) [serial = 11] [outer = 0x7f03c0542c00]
WARNING: redundant multiplexed document?: 'docMapEntry->mString == nsnull', file /home/heluani/mozilla-1.9.1/xpcom/io/nsFastLoadFile.cpp, line 1404
WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026
WARNING: recurring into frame construction: 'mPresContext->mLayoutPhaseCount[eLayoutPhase_FrameC] == 0', file /home/heluani/mozilla-1.9.1/layout/base/nsPresContext.h, line 1026

```
Not a version issue cause same results with FF3.5, FF3.0.11

Any idea will be greatly appreciated!
R.

---

### Post by heluani on 2009-07-24
Actually, I found the same kind of problem on f-spot, there's something wrong with my installation and can't get a hold on it. Here's a trace of f-spot trying to import a file, it hangs also at the same spot:

```

(gdb) where
#0  __nptl_setxid (cmdp=0x7fff52551340) at allocatestack.c:1105
#1  0x00007f2d84372a44 in *__GI_seteuid (uid=<value optimized out>)
    at ../sysdeps/unix/sysv/linux/seteuid.c:44
#2  0x00007f2d7e16e680 in gnome_vfs_add_module_to_hash_table (
    name=0x1d2cac0 "file") at gnome-vfs-method.c:368
#3  0x00007f2d7e16e7fe in gnome_vfs_transform_get (
    name=0x7fff52551360 "ùÿÿÿ\034\016") at gnome-vfs-method.c:450
#4  0x00007f2d7e17c132 in gnome_vfs_uri_new_private (
    text_uri=0x2194270 "file:///home/heluani/19/p7190989.jpg", 
    allow_unknown_methods=0, allow_unsafe_methods=<value optimized out>, 
    allow_transforms=<value optimized out>) at gnome-vfs-uri.c:573
#5  0x00000000407e55d6 in ?? ()

```

---

### Post by heluani on 2009-07-28
Although this is unlikely, just in case someone encounters the same problem. This is caused by a bad patch in eglibc 2.10.1 breaking gnome-vfs, this is already solved in trunk.

R.

---

