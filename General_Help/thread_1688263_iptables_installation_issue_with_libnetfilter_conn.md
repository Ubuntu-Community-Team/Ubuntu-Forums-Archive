---
title: "iptables installation issue with libnetfilter_conntrack"
date: 2011-02-15
forum: General Help
---

### Post by fw_exp on 2011-02-15
Hi,
I'm trying to install iptables on my machine and keep running into issues with the libnetfilter_conntrack-0.9.0 installation that's required before iptables can be installed correctly.

When I run ./config in my libnetfilter_conntrack-0.9.0 directory, I get the following error:

on checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBNFNETLINK... no
configure: error: Cannot find libnfnetlink >= 1.0.0

So I check the pkg-config to see what the issues with the libnfnetlink install:
 
fw_exp:/# pkg-config libnfnetlink --print-errors
Package libnfnetlink was not found in the pkg-config search path.
Perhaps you should add the directory containing `libnfnetlink.pc'
to the PKG_CONFIG_PATH environment variable

I verify that the *.pc file is there:

fw_exp:/# ls -l usr/local/lib/pkgconfig/libnfnetlink.pc
-rw-r--r--  1 root staff 349 2011-02-15 07:39 usr/local/lib/pkgconfig/libnfnetlink.pc

When I open the file I can see that it's pointing to the correct version:

# libnfnetlink pkg-config file

prefix=/usr/local
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include

Name: libnfnetlink
Description: Low-level netfilter netlink communication library
URL: [http://netfilter.org/projects/libnfnetlink/](http://netfilter.org/projects/libnfnetlink/)
Version: 1.0.0
Requires:
Conflicts:
Libs: -L${libdir} -lnfnetlink
Cflags: -I${includedir}

After reading the pkg-config man page, I noticed that /var/lib/dpkg/info/pkg-config.list didn't have a link to /usr/local/lib/pkgconfig/, so I added that line to /var/lib/dpkg/info/pkg-config.list and tried the ./configure again with the same results.

I then, based on some research, tried to force it to search that directory:

PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

then 

export PKG_CONFIG_PATH

but again the same results.

Is there another workaround?

I've found similar issues on different discussion boards but their troubles always end at the last export.

Is there another workaround?

---

### Post by fw_exp on 2011-02-15
Never mind.

I did another pkg-config libnfnetlink --print-errors after the export and found that it didn't like the URL... line, so I commented that out and it ./configure'd okay.

---

