---
title: "Broken package manager"
date: 2012-02-28
forum: General Help
---

### Post by bobman321123 on 2012-02-28
Hey all, my package manager is broken, I think. 
Every time I try to install something (or update something) it simply fails. 
Help?

---

### Post by wildmanne39 on 2012-02-28
Hi, please post the output of:
```
sudo apt-get update
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Gremlinzzz on 2012-02-28
try in terminal

sudo apt-get update

sudo apt-get upgrade

sudo apt-get -f install 

sudo dpkg --configure -a

sudo apt-get autoclean 

sudo apt-get autoremove

---

### Post by lordvader1982 on 2012-03-01
I'd like to chime in, in that I'm having the exact same problem with all my package management.

All of the apt commands hang at 100% indefinitely, freezing at the "Reading package lists... 0%" point, meaning i cannot do any of the commands listed below.

I've tried running apt-get -update in gdb, so I can see if it's stuck in some kind of loop, and here's the stacktraces :

```

(gdb) bt
#0  0x00007ffff7ba226a in debPackagesIndex::FindInCache(pkgCache&) const () from /usr/lib/libapt-pkg.so.4.11
#1  0x00007ffff7b46a7f in ?? () from /usr/lib/libapt-pkg.so.4.11
#2  0x00007ffff7b4bf70 in pkgCacheGenerator::MakeStatusCache(pkgSourceList&, OpProgress*, MMap**, bool) () from /usr/lib/libapt-pkg.so.4.11
#3  0x00007ffff7b3fe22 in pkgCacheFile::BuildCaches(OpProgress*, bool) () from /usr/lib/libapt-pkg.so.4.11
#4  0x000000000040a48d in ?? ()
#5  0x00007ffff7afe133 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) () from /usr/lib/libapt-pkg.so.4.11
#6  0x00000000004090d4 in ?? ()
#7  0x00007ffff722630d in __libc_start_main (main=0x408e60, argc=2, ubp_av=0x7fffffffe768, init=<optimised out>, fini=<optimised out>, 
    rtld_fini=<optimised out>, stack_end=0x7fffffffe758) at libc-start.c:226
#8  0x00000000004093f1 in ?? ()
#9  0x00007fffffffe758 in ?? ()
#10 0x000000000000001c in ?? ()
#11 0x0000000000000002 in ?? ()
#12 0x00007fffffffe974 in ?? ()
#13 0x00007fffffffe985 in ?? ()
#14 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
^C
Program received signal SIGINT, Interrupt.
0x00007ffff7b1e005 in pkgCache::PkgFileIterator::operator++() () from /usr/lib/libapt-pkg.so.4.11
(gdb) bt
#0  0x00007ffff7b1e005 in pkgCache::PkgFileIterator::operator++() () from /usr/lib/libapt-pkg.so.4.11
#1  0x00007ffff7ba225a in debPackagesIndex::FindInCache(pkgCache&) const () from /usr/lib/libapt-pkg.so.4.11
#2  0x00007ffff7b46a7f in ?? () from /usr/lib/libapt-pkg.so.4.11
#3  0x00007ffff7b4bf70 in pkgCacheGenerator::MakeStatusCache(pkgSourceList&, OpProgress*, MMap**, bool) () from /usr/lib/libapt-pkg.so.4.11
#4  0x00007ffff7b3fe22 in pkgCacheFile::BuildCaches(OpProgress*, bool) () from /usr/lib/libapt-pkg.so.4.11
#5  0x000000000040a48d in ?? ()
#6  0x00007ffff7afe133 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) () from /usr/lib/libapt-pkg.so.4.11
#7  0x00000000004090d4 in ?? ()
#8  0x00007ffff722630d in __libc_start_main (main=0x408e60, argc=2, ubp_av=0x7fffffffe768, init=<optimised out>, fini=<optimised out>, 
    rtld_fini=<optimised out>, stack_end=0x7fffffffe758) at libc-start.c:226
#9  0x00000000004093f1 in ?? ()
#10 0x00007fffffffe758 in ?? ()
#11 0x000000000000001c in ?? ()
#12 0x0000000000000002 in ?? ()
#13 0x00007fffffffe974 in ?? ()
#14 0x00007fffffffe985 in ?? ()
#15 0x0000000000000000 in ?? ()
(gdb) c
Continuing.                                                                                                                                 
^C                                                                                                                                          
Program received signal SIGINT, Interrupt.                                                                                                  
0x00007ffff785ce2d in std::string::compare(char const*) const () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6                              
(gdb)bt                                                                                                                                    
#0  0x00007ffff785ce2d in std::string::compare(char const*) const () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#1  0x00007ffff7ba2249 in debPackagesIndex::FindInCache(pkgCache&) const () from /usr/lib/libapt-pkg.so.4.11
#2  0x00007ffff7b46a7f in ?? () from /usr/lib/libapt-pkg.so.4.11
#3  0x00007ffff7b4bf70 in pkgCacheGenerator::MakeStatusCache(pkgSourceList&, OpProgress*, MMap**, bool) () from /usr/lib/libapt-pkg.so.4.11
#4  0x00007ffff7b3fe22 in pkgCacheFile::BuildCaches(OpProgress*, bool) () from /usr/lib/libapt-pkg.so.4.11
#5  0x000000000040a48d in ?? ()
#6  0x00007ffff7afe133 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) () from /usr/lib/libapt-pkg.so.4.11
#7  0x00000000004090d4 in ?? ()
#8  0x00007ffff722630d in __libc_start_main (main=0x408e60, argc=2, ubp_av=0x7fffffffe768, init=<optimised out>, fini=<optimised out>, 
    rtld_fini=<optimised out>, stack_end=0x7fffffffe758) at libc-start.c:226
#9  0x00000000004093f1 in ?? ()
#10 0x00007fffffffe758 in ?? ()
#11 0x000000000000001c in ?? ()
#12 0x0000000000000002 in ?? ()
#13 0x00007fffffffe974 in ?? ()
#14 0x00007fffffffe985 in ?? ()
#15 0x0000000000000000 in ?? ()


```The culprit seems to be that unkown method here:
 0x00007ffff7b46a7f in ?? () from /usr/lib/libapt-pkg.so.4.11

Don't know how useful any of this stuff is, but anything that uses apt, is currently borked (including the graphical frontends, such as muon)

---

### Post by flurospar on 2012-03-01
Try this:

```
sudo dpkg-reconfigure *apt*
```

---

### Post by lordvader1982 on 2012-03-01
Thanks, though, I'll never know if it worked.

Out of desperation, I deleted everything in the /var/cache/apt folder (as **apt-get clean **didn't clear anything, and **apt-get autoclean** would hand).

Manually deleting the cache seemed to fix my problem :)

---

### Post by bobman321123 on 2012-03-05
@wildmanne39 The output is: 

```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:3 http://dl.google.com stable/main amd64 Packages [772 B]                  
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:4 http://dl.google.com stable/main i386 Packages [759 B]                   
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://us.archive.ubuntu.com oneiric-backports Release           
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources      
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en 
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en 
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en 
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en 
Ign http://ppa.launchpad.net oneiric/main Translation-en                   
Fetched 3,076 B in 3s (780 B/s)                      
Reading package lists... Done
```

@Gremlinzzz: when I ran ```
sudo apt-get upgrade
``` it returned ```
josh@caesar:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up composite-2012 (2012.0-2503) ...
python: can't open file '/usr/autodesk/Composite_2012/etc/configure.py': [Errno 2] No such file or directory
dpkg: error processing composite-2012 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 composite-2012
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bobman321123 on 2012-03-17
Problem was solved by manually adding the offending folder (Composite_2012) in my file system (/usr/autodesk/Composite_2012), with the code ```
sudo mkdir /usr/autodesk/Composite_2012
``` then removing it with ```
sudo apt-get remove
``` from there

Thanks to raja.genupula for a solution

---

