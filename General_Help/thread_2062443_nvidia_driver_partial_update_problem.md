---
title: "nvidia driver partial update problem"
date: 2012-09-24
forum: General Help
---

### Post by Paco62 on 2012-09-24
I  did a clean install of 12.04 on one of my  hard drives.  It worked okay and started adding programs and configuring it and  one of the things I did was to add an nvidia ppa to get the latest drivers.    Update prompted me to install new nvidia components, but apparently the upgrade  was only partial and one of the components is still of the old build and this  caused a conflict which means only the full screen command prompt mode is  available.  Here is a summary of the error message I get when entering the  command 'startx' to try and get the graphics mode back:
  
                                         x.org x server 1.11.3
                                          release date 2011-12-16
                                           x protocol version 11,  revision  0
                                          kernel command line :  BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae  root=UUID=bdd13cca-1769-4370-ba25-afb776679539 ro quiet splash  vt.handoff=7
                                           build date: 04 august 2012  01:51:24 am
                                            x-org server  2:1.11.4-0ubuntu10.7
                                            current version of pixman:  0.24.4
                                            before reporting problems, check  [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version.
                                             marker :  (==) default  setting
                                            (==) log file:  "/var/log/Xorg.0.log" 
                                             (==) using config file :  "/etc/X11.xorg.conf"
                                             (==) using system config  directory  "/usr/share/X11/xorg.conf.d" 
                                               error: API mismatch: the  NVIDIA kernel module has version 304.43, but this NVIDIA driver component has  version 2.95.49 .  please make sure  that the kernel module and all NVIDIA  driver components have the same version.
  
                                             Fatal server error: no screens  found
                                              Please also check the log file  at "/var/log/Xorg.0.log" for additional information
                                            
                                              ddxSigGiveUp:  closing  log
                                               server terminated with error  (1) .  Closing log file.
                                              xinit: giving up
                                               xinit: unable to connect to X  server: No such file or directory
                                               xinit: server error
  
  
 Any help is appreciated.

I followed Dan C.'s advice and did a clean install of 12.04 on one of my  hard drives.  It worked okay and started adding programs and configuring it and  one of the things I did was to add an nvidia ppa to get the latest drivers.    Update prompted me to install new nvidia components, but apparently the upgrade  was only partial and one of the components is still of the old build and this  caused a conflict which means only the full screen command prompt mode is  available.  Here is a summary of the error message I get when entering the  command 'startx' to try and get the graphics mode back:
  
                                         x.org x server 1.11.3
                                          release date 2011-12-16
                                           x protocol version 11,  revision  0
                                          kernel command line :  BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae  root=UUID=bdd13cca-1769-4370-ba25-afb776679539 ro quiet splash  vt.handoff=7
                                           build date: 04 august 2012  01:51:24 am
                                            x-org server  2:1.11.4-0ubuntu10.7
                                            current version of pixman:  0.24.4
                                            before reporting problems, check  [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version.
                                             marker :  (==) default  setting
                                            (==) log file:  "/var/log/Xorg.0.log" 
                                             (==) using config file :  "/etc/X11.xorg.conf"
                                             (==) using system config  directory  "/usr/share/X11/xorg.conf.d" 
                                               error: API mismatch: the  NVIDIA kernel module has version 304.43, but this NVIDIA driver component has  version 2.95.49 .  please make sure  that the kernel module and all NVIDIA  driver components have the same version.
  
                                             Fatal server error: no screens  found
                                              Please also check the log file  at "/var/log/Xorg.0.log" for additional information
                                            
                                              ddxSigGiveUp:  closing  log
                                               server terminated with error  (1) .  Closing log file.
                                              xinit: giving up
                                               xinit: unable to connect to X  server: No such file or directory
                                               xinit: server error
  
  
 Any help is appreciated.

---

### Post by Toz on 2012-09-24
Merging duplicate threads. 
Please don't create duplicate threads - it dilutes the community effort.

---

### Post by Paco62 on 2012-09-25
solved this by running command 'sudo apt-get purge nvidia-current-updates' and then rebooting

---

