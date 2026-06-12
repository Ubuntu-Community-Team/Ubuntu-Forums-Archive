---
title: "What would cause packages to be uninstallable??"
date: 2011-08-27
forum: General Help
---

### Post by Atamisk on 2011-08-27
Good afternoon, 

I was trying to install a package named qgis. It installed on my ubuntu 11.04 desktop, but when i tried to install it on my 11.04 on my laptop, it complained about broken packages for libqt4. here's the aptitude output from the issue... note that i've basically done everything i can to force the program in through apt; it's just not going! =/

```

sudo apt-get install -y --ignore-hold  qgis 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qgis : Depends: libgdal1-1.6.0 but it is not going to be installed
        Depends: libpq5 (>= 8.4~0cvs20090328) but it is not installable
        Depends: libqgis1.4.0 but it is not going to be installed
        Depends: libqt4-network (>= 4:4.5.3) but it is not installable
        Depends: libqt4-sql (>= 4:4.5.3) but it is not installable
        Depends: libqt4-svg (>= 4:4.5.3) but it is not installable
        Depends: libqtwebkit4 but it is not installable
        Recommends: qgis-plugin-grass but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed
E: Broken packages

```Any Ideas?




EDIT: 
Solved it by referencing this bug. 

[https://bugs.launchpad.net/ubuntu/+s...11/+bug/829202]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/829202")

Just in case anyone else has this issue, adding the referenced lines in sources.list solved the problem. 

Thanks all!

---

### Post by dino99 on 2011-08-27
Do you really want/need a breakage ?
partial=incomplete

---

### Post by gmargo on 2011-08-27
This is almost always simply due to being out of date.  You just need a healthy dose of "apt-get update ; apt-get dist-upgrade" before you install anything new.

---

### Post by Atamisk on 2011-08-27
No Joy....

```

apt-get update && apt-get dist-upgrade && apt-get install qgis

<Removed ign hits for compactness!>

Fetched 2,005 B in 2s (811 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
***0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.***
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qgis : Depends: libgdal1-1.6.0 but it is not going to be installed
        Depends: libpq5 (>= 8.4~0cvs20090328) but it is not installable
        Depends: libqgis1.4.0 but it is not going to be installed
        Depends: libqt4-network (>= 4:4.5.3) but it is not installable
        Depends: libqt4-sql (>= 4:4.5.3) but it is not installable
        Depends: libqt4-svg (>= 4:4.5.3) but it is not installable
        Depends: libqtwebkit4 but it is not installable
        Recommends: qgis-plugin-grass but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed
E: Broken packages

```

---

### Post by snowpine on 2011-08-27
Can you post the output of 

```
sudo apt-get update
```

please?

9 out of 10 times this kind of thing is a problem with software sources. :)

You can also try

```
sudo apt-get -f install
```

---

### Post by Atamisk on 2011-08-27
as requested:

```

apt-get update && apt-get dist-upgrade && apt-get install qgis
Ign http://archive.ubuntu.com natty InRelease
Ign http://ppa.launchpad.net natty InRelease   
Ign http://ppa.launchpad.net natty InRelease   
Ign http://dl.google.com stable InRelease      
Hit http://archive.ubuntu.com natty Release.gpg
Hit http://ppa.launchpad.net natty Release.gpg 
Get:1 http://dl.google.com stable Release.gpg [198 B]
Hit http://archive.ubuntu.com natty Release                                    
Hit http://ppa.launchpad.net natty Release.gpg                        
Get:2 http://dl.google.com stable Release [1,338 B]
Hit http://archive.ubuntu.com natty/universe amd64 Packages               
Hit http://ppa.launchpad.net natty Release                              
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://ppa.launchpad.net natty Release                           
Get:3 http://dl.google.com stable/main amd64 Packages [469 B]         
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages               
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Ign http://dl.google.com stable/main TranslationIndex                
Hit http://ppa.launchpad.net natty/main Sources                      
Hit http://ppa.launchpad.net natty/main amd64 Packages               
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Ign http://archive.ubuntu.com natty/universe Translation-en_US       
Ign http://archive.ubuntu.com natty/universe Translation-en          
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Fetched 2,005 B in 2s (811 B/s)

```

---

### Post by snowpine on 2011-08-27
Personally I would get rid of all the launchpad PPAs and try again with only the Ubuntu repos (just my opinion).

```
sudo apt-get -f install
```

---

### Post by Atamisk on 2011-08-27
Removed all PPA Archives, but the issue persists. in synaptic, the package that seems to carry qt4 is the current version and called libqtcore4. qgis is asking for a so-called transitional package that is named libqt4-core... both provide the same libraries, and the related packages are likely related to the new 'core' release. 

any ideas on how to fix this aside from compiling the damn thing from source (which is my next step)?

---

### Post by snowpine on 2011-08-27
> **Atamisk said:**
> Removed all PPA Archives, but the issue persists. in synaptic, the package that seems to carry qt4 is the current version and called libqtcore4. qgis is asking for a so-called transitional package that is named libqt4-core... both provide the same libraries, and the related packages are likely related to the new 'core' release. 

any ideas on how to fix this aside from compiling the damn thing from source (which is my next step)?

Something is fishy because according to [http://packages.ubuntu.com/natty/qgis](http://packages.ubuntu.com/natty/qgis) the dependency is libqt4core (not libqt4-core). 

Silly question perhaps, but did you remember to "sudo apt-get update" after changing your software sources? :)

What about "sudo apt-get -f install"?

---

### Post by Atamisk on 2011-08-27
yes, i updated sources, and tried to install using the -f flag.....

---

### Post by gmargo on 2011-08-27
Did you remove any packages that have been installed from PPA archives?  Removing the PPA entries from the sources.list files(s) alone will not restore packages to a previous version.

Generally PPA packages have a "ppa" in the version. The command  "dpkg -l | grep ppa" should find them.

---

### Post by Atamisk on 2011-08-27
All ppa archives (edit: er--packages) have been removed. still no joy. this package literally worked yesterday!

---

### Post by Atamisk on 2011-08-30
Solved it by referencing this bug. 

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/829202](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/829202)

Just in case anyone else has this issue, adding the referenced lines in sources.list solved the problem. 

Thanks all!

---

