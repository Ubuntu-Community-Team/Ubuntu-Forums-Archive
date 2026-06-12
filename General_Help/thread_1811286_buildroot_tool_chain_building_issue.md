---
title: "buildroot tool chain building issue"
date: 2011-07-24
forum: General Help
---

### Post by Dave1024 on 2011-07-24
[SIZE=3]Hi,

I download the source code for buildroot and try to create a tool chain for arm platform. The following i specified in the menuconfig 

Target Arch:: arm
Architecture Variant  :: generic_armD
Build Option :: Default
Tool Chain Option

ToolChainType :: buildroot toolchain
uclibc ;; 0.9.31.x
kernel : 2.6.38.x
binutils :: 2.21
gcc ;; 4.3.x

Package Selection 
busybox 1.18.x

This web site help me to know which libs want to download
[http://code.google.com/p/buildroot/wiki/BuildingonUbuntu](http://code.google.com/p/buildroot/wiki/BuildingonUbuntu)

But in the ./output/host/usr/bin have all the binary files. But when i compile a simple "hello world" program i got the error as command not found

```

:arm-linux-gcc
:arm-linux-gcc: command not found

```

what is the reason for showing this issue. 
Thanks  :)Dave







[/SIZE]

---

