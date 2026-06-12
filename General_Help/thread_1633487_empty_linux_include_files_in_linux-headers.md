---
title: "empty linux include files in linux-headers"
date: 2010-11-29
forum: General Help
---

### Post by goooo on 2010-11-29
Hi,
while trying to build a package (honeyd), I got errors regarding missing include files.
After a quick look I found that the package [FONT=Courier New]linux-headers-2.6.35-23-generic_2.6.35-23.40_amd64.deb[/FONT] only contains empty include files under include/config:

[FONT=Courier New]$ ls -l /usr/src/linux-headers-2.6.35-23-generic/include/config/
-rw-r--r--  1 root root     0 2010-11-18 03:12 3c359.h
drwxr-xr-x  2 root root  4096 2010-11-29 15:34 60xx
-rw-r--r--  1 root root     0 2010-11-18 03:12 64bit.h
-rw-r--r--  1 root root     0 2010-11-18 03:12 6pack.h
-rw-r--r--  1 root root     0 2010-11-18 03:12 8139cp.h
drwxr-xr-x  2 root root  4096 2010-11-29 15:34 8139too
-rw-r--r--  1 root root     0 2010-11-18 03:12 8139too.h[/FONT]
.......................

Is this expected? Are there any workarounds?

PS: the package control file states that I can find information in debian.README.gz BUT that file is nonexistent:

Package: linux-headers-2.6.35-23-generic                                                                                                                                            
Source: linux                                                                                                                                                                       
Version: 2.6.35-23.40                                                                                                                                                               
Architecture: amd64                                                                                                                                                                 
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>                                                                                                                       
Installed-Size: 9936                                                                                                                                                                
Depends: coreutils | fileutils (>= 4.0), linux-headers-2.6.35-23, libc6 (>= 2.7)                                                                                                    
Provides: linux-headers, linux-headers-2.6                                                                                                                                          
Section: devel                                                                                                                                                                      
Priority: optional                                                                                                                                                                  
Description: Linux kernel headers for version 2.6.35 on x86/x86_64                                                                                                                  
 This package provides kernel header files for version 2.6.35 on                                                                                                                    
 x86/x86_64.                                                                                                                                                                        
 .                                                                                                                                                                                  
 This is for sites that want the latest kernel headers.  Please read                                                                                                                
 /usr/share/doc/linux-headers-2.6.35-23/debian.README.gz for details.

---

