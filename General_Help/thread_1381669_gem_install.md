---
title: "gem install"
date: 2010-01-15
forum: General Help
---

### Post by pendulous on 2010-01-15
Unable to gem install eventmachine


```
name@name-desktop:/$ sudo gem install eventmachine
Building native extensions.  This could take a while...
ERROR:  Error installing eventmachine:
    ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install eventmachine
checking for rb_trap_immediate in ruby.h,rubysig.h... yes
checking for rb_thread_blocking_region()... no
checking for inotify_init() in sys/inotify.h... yes
checking for writev() in sys/uio.h... yes
checking for rb_thread_check_ints()... no
checking for rb_time_new()... yes
checking for sys/event.h... no
checking for epoll_create() in sys/epoll.h... yes
checking for main() in -lcrypto... no
creating Makefile

make
g++ -I. -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -DBUILD_FOR_RUBY -DHAVE_RB_TRAP_IMMEDIATE -DHAVE_RBTRAP -DHAVE_INOTIFY_INIT -DHAVE_INOTIFY -DHAVE_WRITEV -DHAVE_WRITEV -DHAVE_RB_TIME_NEW -DOS_UNIX -DHAVE_EPOLL_CREATE -DHAVE_EPOLL -DWITHOUT_SSL -I/include/include    -fPIC -fno-strict-aliasing -g -g -O2  -fPIC    -c sigs.cpp
make: g++: Command not found
make: *** [sigs.o] Error 127


Gem files will remain installed in /var/lib/gems/1.8/gems/eventmachine-0.12.10 for inspection.
Results logged to /var/lib/gems/1.8/gems/eventmachine-0.12.10/ext/gem_make.out
name@name-desktop:/$ 


```added PATH to bashrc and /etc/environment

```
/home/name/.gem/ruby/1.8/bin
```

---

### Post by Tsquad on 2010-01-15
I believe the default is sudo apt-get install eventmachine
Unless you changed your installer.

---

### Post by pendulous on 2010-01-15
oops... forgot to install g++

---

