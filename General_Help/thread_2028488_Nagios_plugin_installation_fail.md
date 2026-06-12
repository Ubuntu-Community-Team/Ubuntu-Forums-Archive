---
title: "Nagios plugin installation fail"
date: 2012-07-18
forum: General Help
---

### Post by enterdavertex on 2012-07-18
actually it give me that error into nagios, which I considere not understandable... could someone explain me what to do exactly and why is this happening ? 

it does this error when I type the command "sudo make"....


make[2]: *** [check_http.o] Error 1
make[2]: Leaving directory `/home/nicadmin/nagios-plugins-1.4.16/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nicadmin/nagios-plugins-1.4.16'
make: *** [all] Error 2
nicadmin@nicadmin-ubuntu:~/nagios-plugins-1.4.16$

---

### Post by Sergius14 on 2012-07-18
Run ./configure and then attach it here.

./configure > configure.out

And attach configure.out in this post.


There shoud be a clue about what is happening.

---

### Post by enterdavertex on 2012-07-18
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether gcc needs -traditional... no
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether gcc and cc understand -c and -o together... yes
checking for error_at_line... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for working strtod... yes
checking for python... /usr/bin/python
checking for sh... /bin/sh
checking for perl... /usr/bin/perl
checking for libgnutls-config... no
checking for hostname... /bin/hostname
checking for basename... /usr/bin/basename
checking for main in -ldce... no
checking for main in -lnsl... yes
checking for socket in -lsocket... no
checking for main in -lresolv... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for floor in -lm... yes
checking mp.h usability... no
checking mp.h presence... no
checking for mp.h... no
checking for pow in -lbsd... no
checking for plan_tests in -ltap... no
checking for main in -lcrypt... yes
checking for PQsetdbLogin in -lpq... no
checking for rc_read_config in -lradiusclient... no
checking for rc_read_config in -lradiusclient-ng... no
checking for main in -lldap... no
checking linux/hdreg.h usability... yes
checking linux/hdreg.h presence... yes
checking for linux/hdreg.h... yes
checking linux/types.h usability... yes
checking linux/types.h presence... yes
checking for linux/types.h... yes
checking for mysql_config... no
checking for IPv6 support... yes
checking krb5.h usability... no
checking krb5.h presence... no
checking for krb5.h... no
checking krb5.h usability... no
checking krb5.h presence... no
checking for krb5.h... no
checking for dlopen in -ldl... yes
checking for shl_load in -ldl... no
checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
checking openssl/x509.h usability... no
checking openssl/x509.h presence... no
checking for openssl/x509.h... no
checking openssl/rsa.h usability... no
checking openssl/rsa.h presence... no
checking for openssl/rsa.h... no
checking openssl/pem.h usability... no
checking openssl/pem.h presence... no
checking for openssl/pem.h... no
checking openssl/crypto.h usability... no
checking openssl/crypto.h presence... no
checking for openssl/crypto.h... no
checking openssl/err.h usability... no
checking openssl/err.h presence... no
checking for openssl/err.h... no
checking ssl.h usability... no
checking ssl.h presence... no
checking for ssl.h... no
checking x509.h usability... no
checking x509.h presence... no
checking for x509.h... no
checking rsa.h usability... no
checking rsa.h presence... no
checking for rsa.h... no
checking pem.h usability... no
checking pem.h presence... no
checking for pem.h... no
checking crypto.h usability... no
checking crypto.h presence... no
checking for crypto.h... no
checking err.h usability... yes
checking err.h presence... yes
checking for err.h... yes
checking for CRYPTO_lock in -lcrypto... no
checking gnutls/openssl.h usability... no
checking gnutls/openssl.h presence... no
checking for gnutls/openssl.h... no
checking whether time.h and sys/time.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking uio.h usability... no
checking uio.h presence... no
checking for uio.h... no
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking features.h usability... yes
checking features.h presence... yes
checking for features.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/unistd.h usability... yes
checking sys/unistd.h presence... yes
checking for sys/unistd.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking for size_t... yes
checking return type of signal handlers... void
checking for va_copy... yes
checking for memmove... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... yes
checking for floor... no
checking for poll... yes
checking return type of socket size... int
checking for ps... /bin/ps
checking for ps syntax... /bin/ps axwo 'stat uid pid ppid vsz rss pcpu comm args'
checking for ping... /bin/ping
checking for ping6... /bin/ping6
checking for ICMP ping syntax... /bin/ping -n -U -w %d -c %d %s
checking for ICMPv6 ping syntax... /bin/ping6 -n -U -w %d -c %d %s
checking for nslookup... /usr/bin/nslookup
checking for nslookup syntax... /usr/bin/nslookup -sil
checking for number of cpus... sysconf(_SC_NPROCESSORS_CONF)
checking for uptime... /usr/bin/uptime
checking for rpcinfo... no
checking for lmstat... no
checking for smbclient... /usr/bin/smbclient
checking for who... /usr/bin/who
checking for snmpget... no
checking for snmpgetnext... no
checking for quakestat... no
checking for qstat... no
checking for fping... no
checking for ssh... /usr/bin/ssh
checking for mailq... no
checking for qmail-qstat... no
checking for swap... no
checking for swapinfo... no
checking for lsps... no
checking for sys/stat.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for sys/swap.h... yes
checking whether swapctl is declared... no
checking for swaptbl_t... no
checking for swapent_t... no
checking for struct swapent.se_nblks... no
checking for /proc/meminfo... found /proc/meminfo
checking for dig... /usr/bin/dig
checking for apt-get... /usr/bin/apt-get
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for main in -lpthread... yes
checking for working alloca.h... yes
checking for alloca... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for errno.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking for sys/param.h... (cached) yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/fs_types.h usability... no
checking sys/fs_types.h presence... no
checking for sys/fs_types.h... no
checking for sys/socket.h... (cached) yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for math.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for unistd.h... (cached) yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking for stdint.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for sys/time.h... (cached) yes
checking wctype.h usability... yes
checking wctype.h presence... yes
checking for wctype.h... yes
checking whether the preprocessor supports include_next... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking whether <wchar.h> uses 'inline' correctly... yes
checking for btowc... yes
checking for dup2... yes
checking for fcntl... yes
checking for getdtablesize... yes
checking for mbsinit... yes
checking for mbrtowc... yes
checking for mprotect... yes
checking for memchr... yes
checking for alarm... yes
checking for nl_langinfo... yes
checking for lstat... yes
checking for isblank... yes
checking for iswctype... yes
checking for wcscoll... yes
checking for setenv... yes
checking for strdup... (cached) yes
checking for strndup... yes
checking for localtime_r... yes
checking for timegm... yes
checking for pipe... yes
checking for vasnprintf... no
checking for wcrtomb... yes
checking for iswcntrl... yes
checking for iswblank... yes
checking for nl_langinfo and CODESET... yes
checking for a traditional french locale... none
checking whether byte ordering is bigendian... no
checking whether system is Windows or MSDOS... no
checking whether // is distinct from /... no
checking if environ is properly declared... yes
checking for complete errno.h... yes
checking whether strerror_r is declared... yes
checking for strerror_r... yes
checking whether strerror_r returns char *... yes
checking for working fcntl.h... yes
checking for mode_t... yes
checking for promoted mode_t type... mode_t
checking whether <sys/socket.h> is self-contained... yes
checking for shutdown... yes
checking whether <sys/socket.h> defines the SHUT_* macros... yes
checking for struct sockaddr_storage... yes
checking for sa_family_t... yes
checking whether socket is declared without a macro... no
checking whether connect is declared without a macro... no
checking whether accept is declared without a macro... no
checking whether bind is declared without a macro... no
checking whether getpeername is declared without a macro... no
checking whether getsockname is declared without a macro... no
checking whether getsockopt is declared without a macro... no
checking whether listen is declared without a macro... no
checking whether recv is declared without a macro... no
checking whether send is declared without a macro... no
checking whether recvfrom is declared without a macro... no
checking whether sendto is declared without a macro... no
checking whether setsockopt is declared without a macro... no
checking whether shutdown is declared without a macro... no
checking whether accept4 is declared without a macro... no
checking whether getaddrinfo is declared without a macro... yes
checking whether freeaddrinfo is declared without a macro... yes
checking whether gai_strerror is declared without a macro... yes
checking whether getnameinfo is declared without a macro... yes
checking for library containing gethostbyname... none required
checking for gethostbyname... yes
checking for library containing getservbyname... none required
checking for getservbyname... yes
checking for IPv4 sockets... yes
checking for IPv6 sockets... yes
checking for library containing inet_ntop... none required
checking whether inet_ntop is declared... yes
checking for getopt.h... (cached) yes
checking for getopt_long_only... yes
checking whether optreset is declared... no
checking whether getopt_clip is declared... no
checking whether getopt is POSIX compatible... yes
checking for working GNU getopt function... yes
checking whether getenv is declared... yes
checking whether getc_unlocked is declared... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking for wchar_t... yes
checking whether NULL can be used in arbitrary expressions... yes
checking whether malloc, realloc, calloc are POSIX compliant... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for long long int... yes
checking for mbstate_t... yes
checking for a traditional japanese locale... none
checking for a transitional chinese locale... none
checking for a french Unicode locale... none
checking for mmap... yes
checking for MAP_ANONYMOUS... yes
checking whether memchr works... yes
checking for ssize_t... yes
checking whether setenv validates arguments... yes
checking search.h usability... yes
checking search.h presence... yes
checking for search.h... yes
checking for tsearch... yes
checking whether snprintf is declared... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for unsigned long long int... yes
checking whether C symbols are prefixed with underscore at the linker level... no
checking whether strdup is declared... yes
checking for working strerror function... yes
checking whether memmem is declared without a macro... yes
checking whether mempcpy is declared without a macro... yes
checking whether memrchr is declared without a macro... yes
checking whether rawmemchr is declared without a macro... yes
checking whether stpcpy is declared without a macro... yes
checking whether stpncpy is declared without a macro... yes
checking whether strchrnul is declared without a macro... yes
checking whether strdup is declared without a macro... yes
checking whether strncat is declared without a macro... yes
checking whether strndup is declared without a macro... yes
checking whether strnlen is declared without a macro... yes
checking whether strpbrk is declared without a macro... yes
checking whether strsep is declared without a macro... yes
checking whether strcasestr is declared without a macro... yes
checking whether strtok_r is declared without a macro... yes
checking whether strsignal is declared without a macro... yes
checking whether strverscmp is declared without a macro... yes
checking whether strndup is declared... (cached) yes
checking whether strnlen is declared... (cached) yes
checking whether stat file-mode macros are broken... no
checking for struct timespec in <time.h>... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether snprintf returns a byte count as in C99... yes
checking for snprintf... yes
checking for strnlen... yes
checking for wcslen... yes
checking for wcsnlen... yes
checking for mbrtowc... (cached) yes
checking for wcrtomb... (cached) yes
checking whether _snprintf is declared... no
checking whether vsnprintf is declared... yes
checking for alloca as a compiler built-in... yes
checking whether inet_ntop is declared without a macro... yes
checking whether inet_pton is declared without a macro... yes
checking whether btowc(0) is correct... yes
checking whether btowc(EOF) is correct... guessing yes
checking whether // is distinct from /... (cached) no
checking whether dup2 works... yes
checking for error_at_line... (cached) yes
checking whether fcntl handles F_DUPFD correctly... yes
checking whether fcntl understands F_DUPFD_CLOEXEC... needs runtime check
checking whether fcntl is declared without a macro... yes
checking whether openat is declared without a macro... yes
checking whether floorf is declared... yes
checking for sys/mount.h... yes
configure: checking how to get file system space usage
checking for statvfs function (SVR4)... no
checking for 3-argument statfs function (DEC OSF/1)... no
checking for two-argument statfs with statfs.bsize member (AIX, 4.3BSD)... yes
checking dustat.h usability... no
checking dustat.h presence... no
checking for dustat.h... no
checking sys/fs/s5param.h usability... no
checking sys/fs/s5param.h presence... no
checking for sys/fs/s5param.h... no
checking sys/filsys.h usability... no
checking sys/filsys.h presence... no
checking for sys/filsys.h... no
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking for statfs that truncates block counts... no
configure: checking how to do getaddrinfo, freeaddrinfo and getnameinfo
checking for library containing getaddrinfo... none required
checking for getaddrinfo... yes
checking for gai_strerror (possibly via ws2tcpip.h)... yes
checking for struct sockaddr.sa_len... no
checking whether getaddrinfo is declared... (cached) yes
checking whether freeaddrinfo is declared... (cached) yes
checking whether gai_strerror is declared... (cached) yes
checking whether getnameinfo is declared... (cached) yes
checking for struct addrinfo... yes
checking for gethostname... yes
checking for HOST_NAME_MAX... yes
checking for getloadavg... yes
checking for pstat_getdynamic... no
checking for kstat_open in -lkstat... no
checking for perfstat_cpu_total in -lperfstat... no
checking for getloadavg... yes
checking whether getloadavg requires setgid... no
checking sys/loadavg.h usability... no
checking sys/loadavg.h presence... no
checking for sys/loadavg.h... no
checking whether getloadavg is declared... yes
checking for library containing gethostbyname... (cached) none required
checking for gethostbyname... (cached) yes
checking for library containing inet_ntop... (cached) none required
checking whether inet_ntop is declared... (cached) yes
checking whether the compiler generally respects inline... yes
checking whether langinfo.h defines CODESET... yes
checking whether langinfo.h defines ERA... yes
checking whether nl_langinfo is declared without a macro... yes
checking whether locale.h conforms to POSIX:2001... yes
checking whether locale.h defines locale_t... yes
checking whether duplocale is declared without a macro... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... (cached) yes
checking whether NAN macro works... yes
checking whether HUGE_VAL works... yes
checking whether acosl is declared without a macro... yes
checking whether asinl is declared without a macro... yes
checking whether atanl is declared without a macro... yes
checking whether ceilf is declared without a macro... yes
checking whether ceill is declared without a macro... yes
checking whether cosl is declared without a macro... yes
checking whether expl is declared without a macro... yes
checking whether floorf is declared without a macro... yes
checking whether floorl is declared without a macro... yes
checking whether frexpl is declared without a macro... yes
checking whether ldexpl is declared without a macro... yes
checking whether logb is declared without a macro... yes
checking whether logl is declared without a macro... yes
checking whether round is declared without a macro... yes
checking whether roundf is declared without a macro... yes
checking whether roundl is declared without a macro... yes
checking whether sinl is declared without a macro... yes
checking whether sqrtl is declared without a macro... yes
checking whether tanl is declared without a macro... yes
checking whether trunc is declared without a macro... yes
checking whether truncf is declared without a macro... yes
checking whether truncl is declared without a macro... yes
checking whether mbrtowc handles incomplete characters... guessing yes
checking whether mbrtowc works as well as mbtowc... guessing yes
checking whether mbrtowc handles a NULL string argument... guessing yes
checking whether mbrtowc has a correct return value... guessing yes
checking whether mbrtowc returns 0 when parsing a NUL character... guessing yes
checking whether mbrtowc handles incomplete characters... (cached) guessing yes
checking whether mbrtowc works as well as mbtowc... (cached) guessing yes
checking for working mktime... yes
checking for listmntent... no
checking for getmntinfo... no
checking for sys/ucred.h... no
checking for sys/mount.h... (cached) yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking for sys/fs_types.h... (cached) no
checking for struct fsstat.f_fstypename... no
checking for library containing getmntent... none required
checking for getmntent... yes
checking for listmntent of Cray/Unicos-9... no
checking for mntctl function and struct vmount... no
checking for one-argument getmntent function... yes
checking sys/mntent.h usability... no
checking sys/mntent.h presence... no
checking for sys/mntent.h... no
checking for struct statfs.f_fstypename... no
checking whether getaddrinfo is declared without a macro... (cached) yes
checking whether freeaddrinfo is declared without a macro... (cached) yes
checking whether gai_strerror is declared without a macro... (cached) yes
checking whether getnameinfo is declared without a macro... (cached) yes
checking whether <netinet/in.h> is self-contained... yes
checking whether open recognizes a trailing slash... yes
checking for working re_compile_pattern... yes
checking for library containing getservbyname... (cached) none required
checking for getservbyname... (cached) yes
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for snprintf... (cached) yes
checking whether snprintf respects a size of 1... yes
checking for library containing setsockopt... none needed
checking for socklen_t... yes
checking for ssize_t... (cached) yes
checking whether stat handles trailing slashes on directories... yes
checking whether stat handles trailing slashes on files... yes
checking whether NULL can be used in arbitrary expressions... (cached) yes
checking whether stdint.h conforms to C99... yes
checking whether dprintf is declared without a macro... yes
checking whether fpurge is declared without a macro... no
checking whether fseeko is declared without a macro... yes
checking whether ftello is declared without a macro... yes
checking whether getdelim is declared without a macro... yes
checking whether getline is declared without a macro... yes
checking whether popen is declared without a macro... yes
checking whether renameat is declared without a macro... yes
checking whether snprintf is declared without a macro... yes
checking whether tmpfile is declared without a macro... yes
checking whether vdprintf is declared without a macro... yes
checking whether vsnprintf is declared without a macro... yes
checking for random.h... no
checking for struct random_data... yes
checking whether atoll is declared without a macro... yes
checking whether canonicalize_file_name is declared without a macro... yes
checking whether getloadavg is declared without a macro... yes
checking whether getsubopt is declared without a macro... yes
checking whether grantpt is declared without a macro... yes
checking whether mkdtemp is declared without a macro... yes
checking whether mkostemp is declared without a macro... yes
checking whether mkostemps is declared without a macro... yes
checking whether mkstemp is declared without a macro... yes
checking whether mkstemps is declared without a macro... yes
checking whether ptsname is declared without a macro... yes
checking whether random_r is declared without a macro... yes
checking whether initstat_r is declared without a macro... no
checking whether srandom_r is declared without a macro... yes
checking whether setstate_r is declared without a macro... yes
checking whether realpath is declared without a macro... yes
checking whether rpmatch is declared without a macro... yes
checking whether setenv is declared without a macro... yes
checking whether strtod is declared without a macro... yes
checking whether strtoll is declared without a macro... yes
checking whether strtoull is declared without a macro... yes
checking whether unlockpt is declared without a macro... yes
checking whether unsetenv is declared without a macro... yes
checking for working strndup... yes
checking for working strnlen... yes
checking for strsep... yes
checking whether <sys/socket.h> is self-contained... (cached) yes
checking for shutdown... (cached) yes
checking whether <sys/socket.h> defines the SHUT_* macros... (cached) yes
checking for struct sockaddr_storage... (cached) yes
checking for sa_family_t... (cached) yes
checking whether socket is declared without a macro... (cached) no
checking whether connect is declared without a macro... (cached) no
checking whether accept is declared without a macro... (cached) no
checking whether bind is declared without a macro... (cached) no
checking whether getpeername is declared without a macro... (cached) no
checking whether getsockname is declared without a macro... (cached) no
checking whether getsockopt is declared without a macro... (cached) no
checking whether listen is declared without a macro... (cached) no
checking whether recv is declared without a macro... (cached) no
checking whether send is declared without a macro... (cached) no
checking whether recvfrom is declared without a macro... (cached) no
checking whether sendto is declared without a macro... (cached) no
checking whether setsockopt is declared without a macro... (cached) no
checking whether shutdown is declared without a macro... (cached) no
checking whether accept4 is declared without a macro... (cached) no
checking for nlink_t... yes
checking whether fchmodat is declared without a macro... yes
checking whether fstatat is declared without a macro... yes
checking whether futimens is declared without a macro... yes
checking whether lchmod is declared without a macro... yes
checking whether lstat is declared without a macro... yes
checking whether mkdirat is declared without a macro... yes
checking whether mkfifo is declared without a macro... yes
checking whether mkfifoat is declared without a macro... yes
checking whether mknod is declared without a macro... yes
checking whether mknodat is declared without a macro... yes
checking whether stat is declared without a macro... yes
checking whether utimensat is declared without a macro... yes
checking whether localtime_r is compatible with its POSIX signature... yes
checking whether chown is declared without a macro... yes
checking whether dup2 is declared without a macro... yes
checking whether dup3 is declared without a macro... yes
checking whether environ is declared without a macro... yes
checking whether euidaccess is declared without a macro... yes
checking whether faccessat is declared without a macro... yes
checking whether fchdir is declared without a macro... yes
checking whether fchownat is declared without a macro... yes
checking whether fsync is declared without a macro... yes
checking whether ftruncate is declared without a macro... yes
checking whether getcwd is declared without a macro... yes
checking whether getdomainname is declared without a macro... yes
checking whether getdtablesize is declared without a macro... yes
checking whether getgroups is declared without a macro... yes
checking whether gethostname is declared without a macro... yes
checking whether getlogin is declared without a macro... yes
checking whether getlogin_r is declared without a macro... yes
checking whether getpagesize is declared without a macro... yes
checking whether getusershell is declared without a macro... yes
checking whether setusershell is declared without a macro... yes
checking whether endusershell is declared without a macro... yes
checking whether lchown is declared without a macro... yes
checking whether link is declared without a macro... yes
checking whether linkat is declared without a macro... yes
checking whether lseek is declared without a macro... yes
checking whether pipe2 is declared without a macro... yes
checking whether pread is declared without a macro... yes
checking whether pwrite is declared without a macro... yes
checking whether readlink is declared without a macro... yes
checking whether readlinkat is declared without a macro... yes
checking whether rmdir is declared without a macro... yes
checking whether sleep is declared without a macro... yes
checking whether symlink is declared without a macro... yes
checking whether symlinkat is declared without a macro... yes
checking whether ttyname_r is declared without a macro... yes
checking whether unlink is declared without a macro... yes
checking whether unlinkat is declared without a macro... yes
checking whether usleep is declared without a macro... yes
checking for unsetenv... yes
checking for unsetenv() return type... int
checking whether unsetenv works on duplicates... yes
checking for ptrdiff_t... yes
checking for vasprintf... yes
checking for vsnprintf... yes
checking whether snprintf respects a size of 1... (cached) yes
checking whether btowc is declared without a macro... yes
checking whether wctob is declared without a macro... yes
checking whether mbsinit is declared without a macro... yes
checking whether mbrtowc is declared without a macro... yes
checking whether mbrlen is declared without a macro... yes
checking whether mbsrtowcs is declared without a macro... yes
checking whether mbsnrtowcs is declared without a macro... yes
checking whether wcrtomb is declared without a macro... yes
checking whether wcsrtombs is declared without a macro... yes
checking whether wcsnrtombs is declared without a macro... yes
checking whether wcwidth is declared without a macro... yes
checking whether mbrtowc handles incomplete characters... (cached) guessing yes
checking whether mbrtowc works as well as mbtowc... (cached) guessing yes
checking whether wcrtomb return value is correct... guessing yes
checking whether iswcntrl works... yes
checking for stdint.h... (cached) yes
configure: creating ./config.status
config.status: creating gl/Makefile
config.status: creating nagios-plugins.spec
config.status: creating Makefile
config.status: creating tap/Makefile
config.status: creating lib/Makefile
config.status: creating plugins/Makefile
config.status: creating lib/tests/Makefile
config.status: creating plugins-root/Makefile
config.status: creating plugins-scripts/Makefile
config.status: creating plugins-scripts/subst
config.status: creating plugins-scripts/utils.pm
config.status: creating plugins-scripts/utils.sh
config.status: creating perlmods/Makefile
config.status: creating command.cfg
config.status: creating test.pl
config.status: creating pkg/solaris/pkginfo
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
            --with-apt-get-command: /usr/bin/apt-get
              --with-ping6-command: /bin/ping6 -n -U -w %d -c %d %s
               --with-ping-command: /bin/ping -n -U -w %d -c %d %s
                       --with-ipv6: yes
                      --with-mysql: no
                    --with-openssl: no
                     --with-gnutls: no
               --enable-extra-opts: no
                       --with-perl: /usr/bin/perl
             --enable-perl-modules: no
                     --with-cgiurl: /nagios/cgi-bin
               --with-trusted-path: /bin:/sbin:/usr/bin:/usr/sbin
                   --enable-libtap: no

---

### Post by Sergius14 on 2012-07-18
Do have already running a Nagios Server, right?


You may have to create before a user and group (or use user/group that already have been created)


./configure --with-nagios-user=nagios --with-nagios-group=nagios  make  make install



Check this Guide: [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)

---

### Post by enterdavertex on 2012-07-19
in fact the server is currently running with no plugins, I have no idea how to fix this kind of error... all recursive , chek_http.o ...

---

### Post by GTmG on 2012-09-25
Before configure the source install **libssl-dev**:
```
#apt-get install libssl-dev
```After that:
> #./configure --with-nagios-user=nagios --with-nagios-group=nagios
#make
#make installAnd that package (libssl-dev) solve your problema with check_http.


Sorry for answer too late :P
but this may help anyone with same problem.

---

### Post by illerngw on 2012-10-07
> **GTmG said:**
> 
Sorry for answer too late :P
but this may help anyone with same problem.

Worked like a charm, thank you very much. :guitar:
/illern

---

### Post by pela020 on 2013-02-27
> **GTmG said:**
> Before configure the source install **libssl-dev**:
```
#apt-get install libssl-dev
```After that:
And that package (libssl-dev) solve your problema with check_http.


Sorry for answer too late :P
but this may help anyone with same problem.
This helped a lot. Thank you!

---

