---
title: "Problem when using scons"
date: 2010-10-07
forum: General Help
---

### Post by iroy2000 on 2010-10-07
I'm trying to build Titanium in Ubuntu 10.04

When I use the scon, I have the following error, anyone know what is that?? And how to fix that??  Thanks for the help ~

g++ -o build/linux/objs/libkroll/javascript/kjs_util.os -c -pthread -fPIC -m32 -Wall -Werror -fno-common -fvisibility=hidden -g -DOS_LINUX=1 -D_OS_NAME=linux -D_PRODUCT_VERSION=1.1.0 -D_PRODUCT_NAME=Titanium -D_GLOBAL_NS_VARNAME=Titanium -D_CONFIG_FILENAME=tiapp.xml -D_BOOT_RUNTIME_FLAG= -D_BOOT_HOME_FLAG= -D_DISTRIBUTION_URL=api.appcelerator.net -D_CRASH_REPORT_URL=api.appcelerator.net/p/v1/app-crash-report -DOS_32=1 -DDEBUG=1 -DKROLL_API_EXPORT=1 -D_REENTRANT -I. -Ikroll -Ibuild/linux/sdk/include -Ikroll/thirdparty-linux-i386-r35/poco/include -Ikroll/thirdparty-linux-i386-r35/webkit/include -Ikroll/thirdparty-linux-i386-r35/webkit/include/glib-2.0 -I/usr/include/libxml2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 kroll/libkroll/javascript/kjs_util.cpp
kroll/libkroll/javascript/kjs_util.cpp:11:42: error: JavascriptCore/JSBasePrivate.h: No such file or directory
kroll/libkroll/javascript/kjs_util.cpp: In function 'const OpaqueJSValue* kroll::KJSUtil::ToJSValue(kroll::KValueRef, const OpaqueJSContext*)':
kroll/libkroll/javascript/kjs_util.cpp:175: error: 'JSReportExtraMemoryCost' was not declared in this scope
scons: *** [build/linux/objs/libkroll/javascript/kjs_util.os] Error 1
scons: building terminated because of errors.

---

