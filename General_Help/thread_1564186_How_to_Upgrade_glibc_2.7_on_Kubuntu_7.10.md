---
title: "How to Upgrade glibc_2.7 on Kubuntu 7.10"
date: 2010-08-30
forum: General Help
---

### Post by o_swas on 2010-08-30
Hello,

I'm using Kubuntu 7.10 on my notebook and it's been working great ever since I installed it.  

I'm trying to install a new development tool.  Starting the tool fails with this error message:


Couldn't load file: /home/ryan/.titanium/runtime/linux/1.0.0/libkhost.so, error: /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.7' not found (required by /home/ryan/.titanium/runtime/linux/1.0.0/libproxy.so.0)


I think it's saying I need a newer version of glibc installed on my system.

Is there a safe, easy way to upgrade my Kubuntu 7.10 installation to use glibc_2.7?  I don't want to reinstall the entire OS to get a newer version of the library as I have a perfectly good environment right now.  

Thank you!!!

-Ryan

---

### Post by regala on 2010-08-30
> **o_swas said:**
> Hello,

I'm using Kubuntu 7.10 on my notebook and it's been working great ever since I installed it.  

I'm trying to install a new development tool.  Starting the tool fails with this error message:


Couldn't load file: /home/ryan/.titanium/runtime/linux/1.0.0/libkhost.so, error: /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.7' not found (required by /home/ryan/.titanium/runtime/linux/1.0.0/libproxy.so.0)


I think it's saying I need a newer version of glibc installed on my system.

Is there a safe, easy way to upgrade my Kubuntu 7.10 installation to use glibc_2.7?  I don't want to reinstall the entire OS to get a newer version of the library as I have a perfectly good environment right now.  

Thank you!!!

-Ryan

short answer: no, you can't, the only way is to upgrade to another version of Ubuntu. Glibc is one of the components you don't want to mess up with and Ubuntu supports only one version of glibc for each release of Ubuntu (the GLIBC_2_7 symbol is one reason for example, as any shared executable on your system needs is, and should stop working is libc is broken)

---

