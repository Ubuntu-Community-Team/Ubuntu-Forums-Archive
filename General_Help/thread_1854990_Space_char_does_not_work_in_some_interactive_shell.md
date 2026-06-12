---
title: "Space char does not work in some interactive shells"
date: 2011-10-05
forum: General Help
---

### Post by Chroto on 2011-10-05
Hey guys.  Really at my wit's end right now and this is my last shot to get this fixed.

I noticed the other day that several different interactive shells were not recognizing a space when I pressed the spacebar.  For example, in python -i 

typing this: import sys
would be this: importsys

In order to use space characters, I need to first press ctrl+v then space in order for the shell to actually read the space character.

This occurs in the following programming shells:
python
irb
sqlite

It DOESNT occur in the following:
php
mysql

I've tried several different window managers (awesome, gnome, xfce), terminals(urxvt, xterm, aterm, gnome-term), shells (bash, zsh, sh).  The problem occurs in all of them.

So that's the problem....

I will admit I am having a lot of trouble understanding how the signal makes it from keyboard to these programs.  I tried writing some quick scripts to listen on stdin, and /dev/tty and they were no help.  Note: these python, ruby are reading stdin just fine during script execution it is ONLY in interactive mode that they can't read spaces.

I thought it might be an issue with my readline dll but I can't even tell for sure if these programs are using readline or something else. 

I tried running ldd on the binary files and it didn't seem like the output from this command showed the full story ( output below )

Oh, I have also tried dropping out of X and running these shells from there.  Same problem.

Here's some system information that I have gathered so far.  Maybe i am going about this the wrong way.  Like I said, I am starting to get the impression I am clueless how keyboard signals get to individual programs If anyone has any ideas, suggestions, or some advice, I would greatly appreciate it.  



```
$ uname -a
Linux gavin 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
```

```
$ ldd /usr/bin/sqlite3
        linux-gate.so.1 =>  (0x00da2000)
        libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00518000)
        libreadline.so.6 => /lib/libreadline.so.6 (0x0073a000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x001c7000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00b77000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00a1e000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x00ddf000)
        /lib/ld-linux.so.2 (0x00b43000)
```

```
$ ldd /usr/bin/ruby
        linux-gate.so.1 =>  (0x007b6000)
        libruby1.8.so.1.8 => /usr/lib/libruby1.8.so.1.8 (0x00c66000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00110000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00ea2000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x002e2000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0x00341000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x005d9000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00129000)
        /lib/ld-linux.so.2 (0x009ab000)
```

```
$ ldd /usr/local/bin/python
        linux-gate.so.1 =>  (0x00321000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00bdd000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00875000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0x00a69000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00722000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00110000)
        /lib/ld-linux.so.2 (0x00271000)
```

```
$ ldd /usr/bin/php
        linux-gate.so.1 =>  (0x0086b000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0x00aa7000)
        libz.so.1 => /lib/libz.so.1 (0x0074a000)
        libedit.so.2 => /usr/lib/libedit.so.2 (0x00623000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x00a34000)
        libssl.so.0.9.8 => /lib/i686/cmov/libssl.so.0.9.8 (0x0080e000)
        libdb-4.8.so => /usr/lib/libdb-4.8.so (0x00ca0000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x005df000)
        libpcre.so.3 => /lib/libpcre.so.3 (0x00110000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x007c7000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00bd0000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x004a8000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0x00fd2000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00303000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x00ef7000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x00141000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0x00226000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00354000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0086c000)
        libcrypto.so.0.9.8 => /lib/i686/cmov/libcrypto.so.0.9.8 (0x00fe9000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x0016500
```

```
$ ldd /usr/bin/mysql
        linux-gate.so.1 =>  (0x00f3c000)
        libreadline.so.6 => /lib/libreadline.so.6 (0x007e0000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x00d72000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x003a7000)
        libmysqlclient.so.16 => /usr/lib/libmysqlclient.so.16 (0x003c0000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0x00110000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0x00142000)
        libz.so.1 => /lib/libz.so.1 (0x005d8000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00c20000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00b05000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x007a3000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00159000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00bf0000)
        /lib/ld-linux.so.2 (0x002b9000)
```


```
$ python --version
Python 2.7
```

```
$ ruby --version
ruby 1.8.7 (2010-01-10 patchlevel 249) [i486-linux]
```

```
$ sqlite3 -version
3.6.22
```

```
$ mysql --version
mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (i486) using readline 6.1
```

From /etc/console/boottime.kmap.gz:
```
keycode  57 = space           
	control	keycode  57 = nul             
	alt	keycode  57 = Meta_space      
	shift	alt	keycode  57 = Meta_space      
	control	alt	keycode  57 = Meta_nul 
```

```
$ showkey -a

Press any keys - Ctrl-D will terminate this program

         32 0040 0x20
```

```
   $ sudo showkey -s
kb mode was RAW
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
0x9c 
0xb9 
0xb9 
0xb9 
```


```
$ sudo showkey -k
kb mode was RAW
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
keycode  28 release
 keycode  57 press
keycode  57 release
```

---

