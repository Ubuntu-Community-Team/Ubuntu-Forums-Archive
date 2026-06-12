---
title: "Confusion - which package?"
date: 2011-12-20
forum: General Help
---

### Post by ratcheer on 2011-12-20
This morning, when I ran my daily safe-upgrade, it informed me that packages lzma and xz-lzma are recommended, but not installed. So, after the safe-upgrade completed, I attempted to install them.

But, they conflict with each other. When I told it to install both, it only installed lzma. When I installed xz-lzma, it removed lzma.

So, which one should I have? Or, do I need either?

lzma - Description: Compression method of 7z format in 7-Zip program

xa-lzma - Description: XZ-format compression utilities - compatibility commands

Tim

---

### Post by matt_symes on 2011-12-20
Hi

On my precise install.

```
matthew@matthew-Aspire-7540:~/virtual_machines$ dpkg -l lzma
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
un  lzma                                 <none>                               (no description available)
matthew@matthew-Aspire-7540:~/virtual_machines$
``````
matthew@matthew-Aspire-7540:~/virtual_machines$ dpkg -l xz-lzma
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
ii  xz-lzma                              **5.1.1alpha+20110809-3**                XZ-format compression utilities - compatibility commands
matthew@matthew-Aspire-7540:~/virtual_machines$ 
```Only the xz-lzma variant is installed.

The dependencies, reverse dependencies and what they provide.

```


matthew@matthew-Aspire-7540:~/virtual_machines$ **apt-cache showpkg lzma**
Package: lzma
Versions: 
4.43-14ubuntu2 (/var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
                  MD5: db0010bbf7323fc6c0be1f533fdee6a3
 Description Language: en
                 File: /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: db0010bbf7323fc6c0be1f533fdee6a3


Reverse Depends: 
  multisystem,lzma
  zeroinstall-injector,lzma
  uck,lzma
  reprepro,lzma
  newlib-source,lzma
  lzma-alone,lzma 4.43-13
  lzma-alone,lzma 4.43-13
  libcupt2-0,lzma
  flexbackup,lzma 4.43-2
  dtrx,lzma
  dell-recovery,lzma
  debdelta,lzma
  bikeshed,lzma
  atool,lzma
  xz-lzma,lzma
  software-center,lzma
  livecd-rootfs,lzma
  file-roller,lzma
  casper,lzma
  apt,lzma
  alien,lzma
Dependencies: 
4.43-14ubuntu2 - libc6 (2 2.4) libgcc1 (2 1:4.1.1) libstdc++6 (2 4.4.0) 
Provides: 
4.43-14ubuntu2 - 
[B]Reverse Provides: 
xz-lzma 5.1.1alpha+20110809-3[/B]
matthew@matthew-Aspire-7540:~/virtual_machines$ 
``````

matthew@matthew-Aspire-7540:~/virtual_machines$ **apt-cache showpkg xz-lzma**
Package: xz-lzma
Versions: 
5.1.1alpha+20110809-3 (/var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
                  MD5: 6daf7c69c842e737a8d7d34ce9a6794a
 Description Language: en
                 File: /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: 6daf7c69c842e737a8d7d34ce9a6794a


Reverse Depends: 
  xzdec,xz-lzma 4.999.9beta+20091004-1
  xzdec,xz-lzma 4.999.9beta+20091004-1
  lubuntu-desktop,xz-lzma
  gdebi-core,xz-lzma
  dell-recovery,xz-lzma
  xz-utils,xz-lzma 4.999.9beta+20091004-1
  xz-utils,xz-lzma 4.999.9beta+20091004-1
  xz-utils,xz-lzma
  python-apt,xz-lzma
Dependencies: 
5.1.1alpha+20110809-3 - xz-utils (0 (null)) lzma (0 (null)) lzip (3 1.8~rc2) lzip (3 1.8~rc2) 
Provides: 
**5.1.1alpha+20110809-3 - lzma **
Reverse Provides: 
matthew@matthew-Aspire-7540:~/virtual_machines$
```Kind regards

---

### Post by ratcheer on 2011-12-20
Thanks. You provided excellent info. Right now, I have the xz-lzma installed. I don't use any of that stuff and have gotten along without it in the past, so I;ll probably just remove it.

Tim

---

