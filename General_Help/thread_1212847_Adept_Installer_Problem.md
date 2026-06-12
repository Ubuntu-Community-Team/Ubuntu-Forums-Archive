---
title: "Adept Installer Problem"
date: 2009-07-14
forum: General Help
---

### Post by anandj10 on 2009-07-14
The adept installer in kubuntu is not working. whenvever I try to open it, it crashes.. i had put a wrong source line. forgot to add comments. I added after that is shows in terminal line 1 too long whenver i try to run it.

this is what i am getting

anandj10@anandj10-laptop:~$ adept
Constructing PkgSystem
PkgSystem Score:32
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Line 1 too long in source list /etc/apt/sources.list.
E: Line 1 too long in source list /etc/apt/sources.list.
terminate called after throwing an instance of 'wibble::exception::System'
 what(): Success. Context:
 The list of sources could not be read.
KCrash: Application 'adept' crashing...
sock_file=/home/anandj10/.kde/socket-anandj10-laptop/kdeinit4__0

& this is the report

 p, li { white-space: pre-wrap; }  Application: Adept (adept), signal SIGABRT
 
 Thread 1 (Thread 0xb5dadb50 (LWP 12913)):
 [KCrash Handler]
 #6  0xb8006430 in __kernel_vsyscall ()
 #7  0xb72f26d0 in raise () from /lib/tls/i686/cmov/libc.so.6
 #8  0xb72f4098 in abort () from /lib/tls/i686/cmov/libc.so.6
 #9  0xb751c8f8 in __gnu_cxx::__verbose_terminate_handler () from /usr/lib/libstdc++.so.6
 #10 0xb751a7d5 in ?? () from /usr/lib/libstdc++.so.6
 #11 0xb751a812 in std::terminate () from /usr/lib/libstdc++.so.6
 #12 0xb751a8cb in __cxa_rethrow () from /usr/lib/libstdc++.so.6
 #13 0xb71e7068 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
 #14 0xb71e7932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
 #15 0xb71ec0a7 in ?? () from /usr/lib/libQtCore.so.4
 #16 0xb71ec1cc in ?? () from /usr/lib/libQtCore.so.4
 #17 0xb71e115f in QObject::event () from /usr/lib/libQtCore.so.4
 #18 0xb67d8e9c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #19 0xb67e119e in QApplication::notify () from /usr/lib/libQtGui.so.4
 #20 0xb797d94d in KApplication::notify () from /usr/lib/libkdeui.so.5
 #21 0xb71d0a3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #22 0xb71ffd71 in ?? () from /usr/lib/libQtCore.so.4
 #23 0xb71fc4e0 in ?? () from /usr/lib/libQtCore.so.4
 #24 0xb6117b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
 #25 0xb611b0eb in ?? () from /usr/lib/libglib-2.0.so.0
 #26 0xb611b268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #27 0xb71fc438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #28 0xb687a365 in ?? () from /usr/lib/libQtGui.so.4
 #29 0xb71cf06a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
 #30 0xb71cf4aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
 #31 0xb71d1959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
 #32 0xb67d8d17 in QApplication::exec () from /usr/lib/libQtGui.so.4
 #33 0x080c64f2 in ?? ()
 #34 0xb72dd775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
 #35 0x08093fd1 in _start ()


any help

---

