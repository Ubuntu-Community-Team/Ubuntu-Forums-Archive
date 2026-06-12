---
title: "kernel building error kernel-package=12.032"
date: 2010-10-05
forum: General Help
---

### Post by usui on 2010-10-05
Hello,

I installed ubuntu on my laptop recently and would like to have trim support.
(Because I have a ssd drive (crucial c-300 256gb).
The current kernel that I am using is the 2.6.32 (standard lucid kernel I believe).
Unfortunately TRIM support is only available from 2.6.33 and up. 
So I thought I'd install a new kernel using this howto:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
Unfortunately I get on error when I do:
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headersThe error is the following:

chmod 755 /home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/DEBIAN/postrm
sed -e 's/=V/2.6.36-rc4-custom+/g'       -e 's/=IB//g'       \
        -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=KPV/12.032/g'                       \
        -e 's/=K/vmlinuz/g'           \
        -e 's/=I/YES/g'     -e 's,=D,/boot,g'         \
        -e 's/=MD//g'                     \
        -e 's@=MK@@g' -e 's@=A@amd64@g'   \
        -e 's@=M@@g'    -e 's/=OF//g'    \
        -e 's/=S//g' -e 's@=B@x86_64@g'     \
     ./debian/pkg/image/preinst > /home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/DEBIAN/preinst
chmod 755 /home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/DEBIAN/preinst
sed -e 's/=V/2.6.36-rc4-custom+/g'    -e 's/=IB//g'    \
        -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=KPV/12.032/g'                       \
        -e 's/=K/vmlinuz/g'           \
        -e 's/=I/YES/g'     -e 's,=D,/boot,g'         \
        -e 's/=MD//g'                     \
        -e 's@=MK@@g' -e 's@=A@amd64@g'   \
        -e 's@=M@@g'    -e 's/=OF//g'    \
        -e 's/=S//g' -e 's@=B@x86_64@g'     \
     ./debian/pkg/image/prerm > /home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/DEBIAN/prerm
chmod 755 /home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/DEBIAN/prerm
po2debconf debian/[templates.in]("http://templates.in/") > debian/templates.l10n
sed -e 's/=V/2.6.36-rc4-custom/g'    -e 's/=IB//g'    \
        -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=KPV/12.032/g'                       \
        -e 's/=K/vmlinuz/g'           \
        -e 's@=MK@@g' -e 's@=A@amd64@g'   \
        -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
        -e 's/=MD//g'                                \
        -e 's@=M@@g'    -e 's/=OF//g'    \
        -e 's/=S//g' -e 's@=B@x86_64@g'     \
     ./debian/templates.l10n   > ./debian/templates.master
install -p    -o root -g root  -m  644 ./debian/templates.master /home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/DEBIAN/templates
dpkg-gencontrol -DArchitecture=amd64 -isp         \
            -plinux-image-2.6.36-rc4-custom+ -P/home/usui/kernel/linux-2.6/debian/linux-image-2.6.36-rc4-custom+/
dpkg-gencontrol: error: package linux-image-2.6.36-rc4-custom+ not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.36-rc4-custom+] Error 255
make[2]: Leaving directory `/home/usui/kernel/linux-2.6'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.36-rc4-custom+] Error 2
make[1]: Leaving directory `/home/usui/kernel/linux-2.6'
make: *** [kernel_image] Error 2
usui@usui-clevo:~/kernel/linux-2.6$ 

So I looked for a solution and found that it is probably linked to my package-kernel package.

[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/58307](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/58307)

However I don't seem to be able to install package-kernel-12.036.

usui@usui-clevo:~$ sudo apt-get install kernel-package=12.036
[sudo] password for usui: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '12.036' for 'kernel-package' was not found

I already tried adding a ppa which had the file but not for lucid though:

[https://launchpad.net/~brian-rogers/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Ebrian-rogers/+archive/ppa?field.series_filter=")

but I still couldn't install it.
So if anyone knows how I can install that package please let me know.
Anyway thank you for reading my problem even if you don't know the 
solution. I'm still kinda new to Ubuntu but I've been using Gentoo for 
nearly a decade (just saying in case the ppa trick doesn't make any sense.)


Thank you.

Regards,

Usui

---

### Post by usui on 2010-10-07
Nevermind, I just heard that TRIM has been backported to 2.6.32.

Usui

---

