---
title: "Unable to Find Application in Universe Repositories (Natty 11.04)"
date: 2011-08-16
forum: General Help
---

### Post by chiques on 2011-08-16
I'm trying to install an application named "piclab" but its not showing in my package manager. 

[https://launchpad.net/ubuntu/natty/+source/piklab/0.15.7-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/piklab/0.15.7-1ubuntu1)


Any suggestions?

---

### Post by oldos2er on 2011-08-16
Open a terminal and run ```
sudo apt-get update && sudo apt-get install piclab
``` If there are any errors along the way, please copy and paste the full terminal output here.

---

### Post by chiques on 2011-08-16
> **oldos2er said:**
> Open a terminal and run ```
sudo apt-get update && sudo apt-get install piclab
``` If there are any errors along the way, please copy and paste the full terminal output here.

I'm still getting an error:
[COLOR="Red"][SIZE="3"]**E: Unable to locate package piclab**[/SIZE][/COLOR]


```

root@V6133CL:/home/user# sudo apt-get update && sudo apt-get install piclab
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://apt.paulnovo.org natty InRelease                                    E: Unable to locate package piclab
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://apt.paulnovo.org natty/main i386 Packages                           
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com natty-backports InRelease                     
Ign http://archive.canonical.com lucid InRelease                               
Ign http://archive.canonical.com natty InRelease                               
Ign http://apt.paulnovo.org natty/main TranslationIndex                        
Hit http://extras.ubuntu.com natty Release.gpg                                 
Get:3 http://dl.google.com stable/main i386 Packages [773 B]                   
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Ign http://us.archive.ubuntu.com natty-proposed InRelease                      
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://archive.canonical.com lucid Release.gpg                             
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://extras.ubuntu.com natty Release                                     
Hit http://security.ubuntu.com natty-security Release                          
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com natty-backports Release.gpg                   
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://us.archive.ubuntu.com natty-proposed Release.gpg                    
Hit http://us.archive.ubuntu.com natty Release                                 
Ign http://apt.paulnovo.org natty/main Translation-en_US                       
Ign http://apt.paulnovo.org natty/main Translation-en                          
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://archive.canonical.com lucid Release                                 
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://us.archive.ubuntu.com natty-backports Release                       
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com natty-proposed Release                        
Hit http://security.ubuntu.com natty-security/main Sources                     
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.canonical.com natty Release                                 
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://archive.canonical.com lucid/partner i386 Packages                   
Ign http://archive.canonical.com lucid/partner TranslationIndex                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://us.archive.ubuntu.com natty-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com natty-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com natty-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty-backports/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty-backports/universe TranslationIndex     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com natty-proposed/restricted i386 Packages       
Hit http://us.archive.ubuntu.com natty-proposed/main i386 Packages             
Hit http://us.archive.ubuntu.com natty-proposed/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com natty-proposed/universe i386 Packages         
Ign http://us.archive.ubuntu.com natty-proposed/main TranslationIndex          
Ign http://us.archive.ubuntu.com natty-proposed/multiverse TranslationIndex    
Ign http://us.archive.ubuntu.com natty-proposed/restricted TranslationIndex    
Ign http://us.archive.ubuntu.com natty-proposed/universe TranslationIndex      
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://archive.canonical.com lucid/partner Translation-en_US               
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://archive.canonical.com lucid/partner Translation-en                  
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.canonical.com natty/partner Translation-en        
Ign http://us.archive.ubuntu.com natty/main Translation-en_US        
Ign http://us.archive.ubuntu.com natty/main Translation-en           
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en           
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en     
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en     
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en       
Ign http://us.archive.ubuntu.com natty-proposed/main Translation-en_US         
Ign http://us.archive.ubuntu.com natty-proposed/main Translation-en            
Ign http://us.archive.ubuntu.com natty-proposed/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com natty-proposed/multiverse Translation-en      
Ign http://us.archive.ubuntu.com natty-proposed/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com natty-proposed/restricted Translation-en      
Ign http://us.archive.ubuntu.com natty-proposed/universe Translation-en_US     
Ign http://us.archive.ubuntu.com natty-proposed/universe Translation-en        
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en
Ign http://orange.biolab.si squeeze InRelease
Ign http://orange.biolab.si squeeze Release.gpg
Hit http://orange.biolab.si squeeze Release
Ign http://orange.biolab.si squeeze/main i386 Packages/DiffIndex
Ign http://orange.biolab.si squeeze/main TranslationIndex
Hit http://orange.biolab.si squeeze/main i386 Packages
Ign http://orange.biolab.si squeeze/main Translation-en_US
Ign http://orange.biolab.si squeeze/main Translation-en
Fetched 2,318 B in 1min 58s (19 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package piclab
root@V6133CL:/home/user# 

```

Are the "Hit" and "Ign" an issue?

Thanks

---

### Post by Vaphell on 2011-08-16
```
apt-cache search pi[COLOR="Blue"]k[/COLOR]lab
piklab - IDE for PIC-microcontroller development
piklab-dbg - IDE for PIC-microcontroller development - debug
```

---

### Post by chiques on 2011-08-16
> **Vaphell said:**
> ```
apt-cache search pi[COLOR="Blue"]k[/COLOR]lab
piklab - IDE for PIC-microcontroller development
piklab-dbg - IDE for PIC-microcontroller development - debug
```

I think there is something wrong with my repositories?

> 
user@V6133CL:~$ sudo su
[sudo] password for user: 
root@V6133CL:/home/user# apt-cache search piklab
root@V6133CL:/home/user# 
**[COLOR="Red"][B]--BLANK--**[/COLOR][/B]


---

### Post by phuongdt3 on 2011-08-17
hello,i'm a newbie,i'm having semilar problem of these,thanks for sharing

---

### Post by realzippy on 2011-08-17
No,your sources are correct.
Piklab is deleted from universe repo:
[http://www.ubuntuupdates.org/packages/show/287985](http://www.ubuntuupdates.org/packages/show/287985)

You can get the sourcecode and amd 64 .deb here:
[https://launchpad.net/ubuntu/natty/amd64/piklab/0.15.7-1ubuntu1](https://launchpad.net/ubuntu/natty/amd64/piklab/0.15.7-1ubuntu1)

---

### Post by chiques on 2011-08-20
> **realzippy said:**
> No,your sources are correct.
Piklab is deleted from universe repo:
[http://www.ubuntuupdates.org/packages/show/287985](http://www.ubuntuupdates.org/packages/show/287985)

You can get the sourcecode and amd 64 .deb here:
[https://launchpad.net/ubuntu/natty/amd64/piklab/0.15.7-1ubuntu1](https://launchpad.net/ubuntu/natty/amd64/piklab/0.15.7-1ubuntu1)

**I fear installing stuff on ubuntu outside of the Package Manager- why??** because it rarely works. Here is a perfect example. I downloaded and extracted piklab_0.15.7.orig.tar.gz (2.4 MiB) on [https://launchpad.net/ubuntu/lucid/+source/piklab/0.15.7-1ubuntu1](https://launchpad.net/ubuntu/lucid/+source/piklab/0.15.7-1ubuntu1)

To no surprise to me, I get this error that has me tangenting in Google for hours- sucks!

[COLOR="Red"][SIZE="2"][B]configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.
[/B][/SIZE][/COLOR]
```

*********************
COMPILATION:
 - "make -f Makefile.cvs" (usually not needed for distributed tarballs)
 - "./configure --enable-debug=full" (check ./configure --help for other options)
 - "make"

INSTALLATION:
 - "make install" (as root)

*********************


root@V6133CL:/home/user/Downloads/piklab-0.15.7# ./configure --enable-debug=fullchecking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

root@V6133CL:/home/user/Downloads/piklab-0.15.7# make install
make: *** No rule to make target `install'.  Stop.
root@V6133CL:/home/user/Downloads/piklab-0.15.7# make
make: *** No targets specified and no makefile found.  Stop.
root@V6133CL:/home/user/Downloads/piklab-0.15.7# ls
acinclude.m4  configure.files   Makefile.am           piklab.xpm
aclocal.m4    configure.in      Makefile.am.in        po
admin         configure.in.in   Makefile.cvs          qt_config.h
all.pro       configure.in.mid  Makefile.in           README
app.pro       COPYING           man                   src
Changelog     doc               piklab.kdevelop       stamp-h.in
config.h.in   Doxyfile          piklab-prog.pro       subdirs
config.log    INSTALL           piklab-prog-qt4.spec  test
configure     lib.pro           piklab.spec           TODO
root@V6133CL:/home/user/Downloads/piklab-0.15.7# 

```

Any suggestions?

---

### Post by gandaran on 2011-08-20
> **chiques said:**
> **I fear installing stuff on ubuntu outside of the Package Manager- why??** because it rarely works. Here is a perfect example. I downloaded and extracted piklab_0.15.7.orig.tar.gz (2.4 MiB) on [https://launchpad.net/ubuntu/lucid/+source/piklab/0.15.7-1ubuntu1](https://launchpad.net/ubuntu/lucid/+source/piklab/0.15.7-1ubuntu1)

To no surprise to me, I get this error that has me tangenting in Google for hours- sucks!

[COLOR="Red"][SIZE="2"][B]configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.
[/B][/SIZE][/COLOR]
```

*********************
COMPILATION:
 - "make -f Makefile.cvs" (usually not needed for distributed tarballs)
 - "./configure --enable-debug=full" (check ./configure --help for other options)
 - "make"

INSTALLATION:
 - "make install" (as root)

*********************


root@V6133CL:/home/user/Downloads/piklab-0.15.7# ./configure --enable-debug=fullchecking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

root@V6133CL:/home/user/Downloads/piklab-0.15.7# make install
make: *** No rule to make target `install'.  Stop.
root@V6133CL:/home/user/Downloads/piklab-0.15.7# make
make: *** No targets specified and no makefile found.  Stop.
root@V6133CL:/home/user/Downloads/piklab-0.15.7# ls
acinclude.m4  configure.files   Makefile.am           piklab.xpm
aclocal.m4    configure.in      Makefile.am.in        po
admin         configure.in.in   Makefile.cvs          qt_config.h
all.pro       configure.in.mid  Makefile.in           README
app.pro       COPYING           man                   src
Changelog     doc               piklab.kdevelop       stamp-h.in
config.h.in   Doxyfile          piklab-prog.pro       subdirs
config.log    INSTALL           piklab-prog-qt4.spec  test
configure     lib.pro           piklab.spec           TODO
root@V6133CL:/home/user/Downloads/piklab-0.15.7# 

```

Any suggestions?
download the .deb package ( not the tar.gz) from the same website
installing the .deb package (for your ubuntu release) will pull and install all the necessary KDE dependencies from package manager, it'll save you a lot of work, compiling applications is always the last resort!
if any problem installing the .deb with ubuntu software center install gdebi from package manager then right click .deb and choose open with gdebi

---

### Post by realzippy on 2011-08-20
> **chiques said:**
> **I fear installing stuff on ubuntu outside of the Package Manager- why??** because it rarely works....

It *never* works when not installing the build dependencies 
for the program you are going to compile.

Anyway,+1 for using the [.deb file]("http://launchpadlibrarian.net/37875388/piklab_0.15.7-1ubuntu1_amd64.deb") ...

---

