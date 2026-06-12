---
title: "Compile error"
date: 2006-05-08
forum: General Help
---

### Post by jonnyfive on 2006-05-08
I am trying to compile a program called [blue frog]("http://www.bluesecurity.com/") It's a program that has to do with preventing spam. So far things have gone ok, but when I run ./buildfrog.sh it does some stuff and then stops here
```
-DLREXLIB_PCRE -c  -o "kit.o" ./kit.cpp
gcc -O2 -fPIC -O -D_REENTRANT -I"../../thirdparty/zlib-1.2.3" -I"../../thirdparty/openssl-0.9.8a/include" -I"../../thirdparty/curl-7.15.1/include" -I"../../thirdparty/lua-5.0.2/include" -I".." -I"../../my_includes" -DCDA_VERSION=1.9.1.1150 -DLREXLIB_PCRE -c  -o "lua_helper.o" ./lua_helper.cpp
../lib/bitlib/lbitlib.c: In function ‘int bit_lshift(lua_State*)’:
../lib/bitlib/lbitlib.c:49: error: ‘UInteger’ cannot be used as a function
../lib/bitlib/lbitlib.c: In function ‘int bit_rshift(lua_State*)’:
../lib/bitlib/lbitlib.c:50: error: ‘UInteger’ cannot be used as a function
../lib/bitlib/lbitlib.c:50: error: ‘UInteger’ cannot be used as a function
../lib/bitlib/lbitlib.c: In function ‘int bit_arshift(lua_State*)’:
../lib/bitlib/lbitlib.c:51: error: ‘UInteger’ cannot be used as a function
./lua_helper.cpp: In function ‘int thread_sleep(lua_State*)’:
./lua_helper.cpp:165: warning: converting to ‘int’ from ‘lua_Number’
make[1]: *** [lua_helper.o] Error 1
make[1]: Leaving directory `/home/adam/Desktop/bluefrog-src-1.9.1.1150/src/lib'
make: *** [cda_lib] Error 2

```

I don't know what causes this error or how to fix it.

---

### Post by julipanno on 2006-05-08
Have you tried the rpm? You can find it here:
[http://sourceforge.net/project/showfiles.php?group_id=153754](http://sourceforge.net/project/showfiles.php?group_id=153754)

To convert and install:
```

sudo alien nameofrpmfile.rpm
sudo dpkg -i nameofresultingdebfile.deb
```
you need to install alien if you haven't already:
```
sudo apt-get install alien
```
Works fine on both breezy and dapper..


peace,
Stian

---

### Post by kaveraj on 2006-05-13
When you say it works fine, what do you mean? Do you get a tray icon or console mesgs confirming that reports are being submitted.

When I give bluefrog (installed with alien) in console, I get

```
[05/13/06 13:51:46] Modules directory: /usr/bin/
[05/13/06 13:51:46] Config directory: /home/kaveraj/.bluefrog
[05/13/06 13:51:46] Logs directory: /home/kaveraj/.bluefrog/logs

```

There is some network activity intially, but is stops eventually.

But the bothering thing is that one of my CPU's gets completely used at 100% for the entire time the program is run. This behaviour suggests that something is not right.

The log files don't seem to be useful with seemingly hypertext gibberish..

```
<i> 05/13/06 13:45:29-0xb7d0e6c0 ConsoleFrog handle_gaul_events: event=+ rank (msg:
<html><head><title>Blue Security</title>^M;^M;^M;^M;<style type="text/css">^M;  bod
y {^M;          margin:20px;^M;         background-color:#FFFFFF;^M;    }^M;^M; h2{
;               font-family:'Times New Roman';^M;               font-size:32pt;^M;
                font-weight:bold;^M;            color:#0078ae;^M;       }^M;
<i> 05/13/06 13:45:29-0xb7d0e6c0 ConsoleFrog handle_gaul_events: event=+ rank (msg:
<html><head><title>Blue Security</title>^M;^M;^M;^M;<style type="text/css">^M;  bod
y {^M;          margin:20px;^M;         background-color:#FFFFFF;^M;    }^M;^M; h2{
;               font-family:'Times New Roman';^M;               font-size:32pt;^M;
                font-weight:bold;^M;            color:#0078ae;^M;       }^M;
```


PS:

I got a diff set of errors when I tried compiling
```
./crypto_utils.cpp: In static member function 'static bool CryptoUtils::is_buffer_authentic_sha256(const char*, int, const char*)':
./crypto_utils.cpp:116: error: 'SHA256_DIGEST_LENGTH' was not declared in this scope
./crypto_utils.cpp:116: error: 'md' was not declared in this scope
./crypto_utils.cpp:116: error: 'SHA256' was not declared in this scope
make[1]: *** [crypto_utils.o] Error 1
```

---

### Post by julipanno on 2006-05-13
[QUOTE=kaveraj]When you say it works fine, what do you mean? Do you get a tray icon or console mesgs confirming that reports are being submitted.

When I give bluefrog (installed with alien) in console, I get

```
[05/13/06 13:51:46] Modules directory: /usr/bin/
[05/13/06 13:51:46] Config directory: /home/kaveraj/.bluefrog
[05/13/06 13:51:46] Logs directory: /home/kaveraj/.bluefrog/logs

```

There is some network activity intially, but is stops eventually.

But the bothering thing is that one of my CPU's gets completely used at 100% for the entire time the program is run. This behaviour suggests that something is not right.

The log files don't seem to be useful with seemingly hypertext gibberish..[/QUOTE]

I'm not really sure my Bluefrog does what it's supposed to do either; there's no indication that it reports anything, but I do get the same terminal feedback as you. I remember having read on Blue Security's site that this is what you're supposed to see until the frog eventually is called up for action. There is no tray icon, and the program will be idle most of the time. It doesn't use much cpu when I run it though, so you might have some error if that's the case for you.

It is also possible to run bluefrog as a daemon, by using the -d option:
```
bluefrog -d
```
maybe it will use less cpu that way...

---

### Post by kaveraj on 2006-05-16
This time when I ran bluefrog, it ran without hogging the CPU. Don't know how but the problem seems to have solved.

I also monitored the firewall for outgoing requests and saw bluefrog making external connections occassionally. Hence I think that we can safely assume bluefrog is working correctly.

I am adding it to the startup pgms list.\\:D/

---

