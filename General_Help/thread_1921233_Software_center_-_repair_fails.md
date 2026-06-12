---
title: "Software center - repair fails"
date: 2012-02-06
forum: General Help
---

### Post by mikej_w on 2012-02-06
Hello! 
 I was performing a normal update (Ubuntu 10.10, 64 bit), and the software update failed. Software center throws the error "Items cannot be installed... Want to repair"? I press repair button, and then the error "Package operation failed". 

I looked around on the net and found a couple things to try:

----------

**sudo apt-get install -f**
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... Done
    The following packages will be REMOVED:
      icedtea6-plugin
    0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
    After this operation, 283kB disk space will be freed.
    Do you want to continue [Y/n]? **y**
    (Reading database ... 211397 files and directories currently installed.)
    Removing icedtea6-plugin ...
    update-alternatives: unknown argument `--quiet'
    
    Usage: update-alternatives --install <link> <name> <path> <priority>
           update-alternatives --remove <name> <path>
           update-alternatives --help
    <link> is the link pointing to the provided path (ie. /usr/bin/foo).
    <name> is the name in /usr/lib/opkg/alternatives/alternatives (ie. foo)
    <path> is the name referred to (ie. /usr/bin/foo-extra-spiffy)
    <priority> is an integer; options with higher numbers are chosen.
    dpkg: error processing icedtea6-plugin (--remove):
     subprocess installed pre-removal script returned error exit status 2
    No apport report written because MaxReports is reached already
                                                                  Errors were encountered while processing:
     icedtea6-plugin
    E: Sub-process /usr/bin/dpkg returned an error code (1)
**sudo dpkg --configure -a**
**sudo apt-get update && sudo apt-get upgrade**
    mikew-MBU:~ $ sudo apt-get update && sudo apt-get upgrade
    Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release.gpg
    Ign [http://www.scootersoftware.com/](http://www.scootersoftware.com/) stable/non-free Translation-en                                                          
    Ign [http://www.scootersoftware.com/](http://www.scootersoftware.com/) stable/non-free Translation-en_US                                                       
    Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release                                                                           
    Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free amd64 Packages                                                           
    Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free amd64 Packages                                            
    Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free amd64 Packages
    Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
    Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
    Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
    Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
    Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
    Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
    Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
    Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
    Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
    Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
    Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
    Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
    Reading package lists... Done
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    You might want to run 'apt-get -f install' to correct these.
    The following packages have unmet dependencies:
     icedtea6-plugin : Depends: openjdk-6-jre (= 6b20-1.9.10-0ubuntu1~10.10.2) but 6b20-1.9.10-0ubuntu1~10.10.3 is installed
    E: Unmet dependencies. Try using -f.
**sudo apt-get clean**
**sudo apt-get install -f**
    (same error as above)

[B]I can see that a dependency on openjdk is broken, but I'm not sure what to do next to actually fix the issue. I need to install other software on my machine, and this is holding me back.

Any ideas?

Mike[/B]

---

### Post by Krytarik on 2012-02-06
Try downloading the necessary update to the "icedtea6-plugin" package from here:

[http://packages.ubuntu.com/maverick-updates/amd64/icedtea6-plugin/download](http://packages.ubuntu.com/maverick-updates/amd64/icedtea6-plugin/download)

... and installing it manually:
```
sudo dpkg -i FILENAME
```If it doesn't fail to install the package due to the screwed up state of the currently installed package, this would solve the dependency issue and thus clear up the situation.

Hope that works.

---

