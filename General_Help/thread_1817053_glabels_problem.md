---
title: "glabels problem"
date: 2011-08-02
forum: General Help
---

### Post by Steptoenson on 2011-08-02
Hi there,

I am running ubuntu 8.10 but occasionally I have to reinstall from scratch. When I last did this, I was unable to re-add glabels as a package. It is not there, and sudo apt-get install glabels at a terminal does not work either. I am happy with 8.10 and do not want to upgrade.
Please can someone, in simple terms, help me to get glabels back working with 8.10? I know glabels has been upgraded, but is there an old version I can download and install?

Thank you in anticipation of any help with this matter,

Regards,

Richard :(

---

### Post by Tamlynmac on 2011-08-03
You may wish to try some of the previous stable versions [here]("http://sourceforge.net/projects/glabels/files/glabels/") or [here]("http://glabels.sourceforge.net/download/").

Good Luck & hope this helps.

---

### Post by Steptoenson on 2011-08-03
Hi, 

Thank you for replying. I have downloaded glabels-2.2.3 but do not know how to add this as a package or install it. Please can you help with simple instructions?

Thanks,

Richard :)

---

### Post by Tamlynmac on 2011-08-03
I'll try. It's been awhile since using 8.10.

I believe it's a tar.gz file and can be unzipped (if you will ) with the Archive Manager.

Open the file in your archive manager and extract it to it's own folder located in your home directory (make one in your file browser).

****** After extracting in the archive manager, it might popup a window  and ask you if you wish to install glabels - if so select yes.******

If not:
Then use your file manager to view the files that have been uncompressed. If there's an install file double click on it in your file manager and follow the instructions. If there's no install file, find either "the bin folder and then double click on the executable file located in your bin folder" or "double click on the executable glabel file in the list of files somewhere in your created folder". I have no idea how it will unzip and what folders/files will be created. That should start glabels.

If it doesn't have an install file and you have to start it manually, you'll probably want to put it in the menu - right click on your menu and select edit menu. Select the desired menu on the left side and then hit the "New Item" button on the right. A popup box will open asking for the name "glabels" and location. Use the browser to find the executable in your home directory and select it. If no icon is present or you don't like the icon, left click on the icon and choose a different one. Close the popup and the edit menu window. The glabels app should now appear in your menu.

Good Luck & I hope this helps.

---

### Post by Steptoenson on 2011-08-04
Hi,

Thanks again for your continued help. I have tried your various suggestions. I have the folder that was downloaded in my ub-home folder. I couldn't get it to run or install with any of the files or folders. I managed to create a new menu option but again was not sure which file is the right executable one, as none I tried worked. The install text file listed some of the following information. Is this anything to do with it? Some of that stuff is a bit technical for me. Apologies for my lack of knowledge. I'm sure it's fairly straightforward for someone who knows what they are doing.


The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Thanks,

Richard :)

---

### Post by robert shearer on 2011-08-04
> **Steptoenson said:**
> Hi there,

I am running ubuntu 8.10 but occasionally I have to reinstall from scratch. When I last did this, I was unable to re-add glabels as a package. It is not there, and sudo apt-get install glabels at a terminal does not work either. I am happy with 8.10 and do not want to upgrade.
Please can someone, in simple terms, help me to get glabels back working with 8.10? I know glabels has been upgraded, but is there an old version I can download and install?

Thank you in anticipation of any help with this matter,

Regards,

Richard :(

When you sudo apt-get install glabels at a terminal what error message do you get ??

You say you have reinstalled from scratch.... have you enabled all repositories via synaptic  ??  then done a ..
```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```

**Then** tried to  ```
sudo apt-get install glabels 
```


failing that there is a glabels deb package for Intrepid here...

 "Downloadable files" ( glabels_2.2.3-0ubuntu1_i386.deb (332.8 KiB)   )   on this page ....[https://launchpad.net/ubuntu/intrepid/i386/glabels/2.2.3-0ubuntu1](https://launchpad.net/ubuntu/intrepid/i386/glabels/2.2.3-0ubuntu1)

download it then double click on it and it will install **or** give you a message about dependencies  (which you could copy and paste here if you need help )

---

### Post by Steptoenson on 2011-08-04
Hi,

Downloaded : [glabels_2.2.3-0ubuntu1_i386.deb]("http://launchpadlibrarian.net/17938759/glabels_2.2.3-0ubuntu1_i386.deb")                   (332.8 KiB)

Error: Dependency is not satisfiable: glabels-data, so could not install glabels.

I have tried to download [glabels-data_2.2.3-0ubuntu1_all.deb]("http://launchpadlibrarian.net/17938758/glabels-data_2.2.3-0ubuntu1_all.deb")                   (729.9 KiB) but it states

Error: A later version is already installed.

I cannot see a way to uninstall current version and replace with this one. I also do not know whether that will work regards installing glabels.[U]I have enables all repositories I think, but when I reload it states the following[U]

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


[/U]sudo apt-get update produces; sorry it's a long list and I can't stop it underlining.

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports Release.gpg      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports Release          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed Release           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources            
  404 Not Found [IP: 91.189.92.170 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/universe Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-proposed/universe Packages
  404 Not Found
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
[U]

ub@ub-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


ub@ub-laptop:~$ sudo apt-get install glabels
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package glabels is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  glabels-data
E: Package glabels has no installation candidate


A lot of error messages. Please can you help with this in as simple terms as possible. I would just like to install glabels as I used to have it.

Thank you for all help so far.

Regards,

Richard :) 
[/U][/U]

---

### Post by robert shearer on 2011-08-05
Intrepid 8.10 reached end of life in april 2010 and no longer receives security updates.(and no-one is coding for 2008 :( )

If you have enough space then re-sizing and installing an up-to-date version alongside 8.10 as dual boot might solve  the glabels problems and get you out of the last decade too. :)
(try 10.04 LTS for a stable supported version)

However, try opening Synaptic and searching for glabels-data, then right click it and select 'completely remove'.
 Apply and then retry installing the glabels-data package you downloaded.

You are really fighting an uphill battle trying to maintain an obsolete version of Ubuntu.
Perhaps if you could explain why  then we could suggest alternatives that would improve your experience without sacrificing whatever you perceive to be the advantages of not upgrading.  :)

all the best,
Bob.

---

### Post by Steptoenson on 2011-08-05
Hi Bob,

And there we have it! ... managed to completely remove glabels-data and install right version instead. Was then able to install glabels ... and we are off and running!!

Thank you very much to yourself and my friend in Colorado for helping me solve this problem.

With regards to trying to keep an old thing going ... that pretty much sums me up! My dad salvaged my laptop via his brother from a skip ... he was going to wipe it clean and install windows, but his brother thought I'd like Ubuntu. He was right. I've got used to the older versions, only upgrading a couple of times I think. The laptop has quirks and I know these older versions can too. I've looked at the newer versions and I sometimes feel that newer, more up-to-date and advanced versions of anything, sometimes can become too complicated, which in itself can lead to problems ... my car parked outside is a reflection of just that ... no power steering, no electric windows, no heated seats ... it does have a radio though & cassette player! I know CD's have been invented alongwith MP3's IPOD's, etc... it does have 4 wheels and an engine though, starts first time and gets me from a to b. I could waffle on, but will try not to.

I spent a long time designing the literature for my decking & fencing business, which was my introduction to glabels. I have tried to keep the old 8.10 & 2.2.3 glabels going on my laptop since!

Thanks again for all your help.

Best regards,

Richard :P

---

### Post by robert shearer on 2011-08-06
Richard, 
  Great to hear that glabels is working.:) !

 I enjoy it for making business cards and small handouts for shows where I demonstrate bodging and gate-hurdle making. :D

Although I am 6th generation Kiwi my forebears came from Cumbria and Yorkshire.
The first here in New Zealand was, amongst other occupations, a smith's striker and I have recently enlarged my workshop to accommodate a 212 kg anvil so I can forge tools to use in my Green wood-working and coppicing hobby endeavours.

All this in a round about way is to say I understand and support your desire to continue with an Ubuntu version that suits your needs and pace of life....:D:)

all the best,
Bob.

---

