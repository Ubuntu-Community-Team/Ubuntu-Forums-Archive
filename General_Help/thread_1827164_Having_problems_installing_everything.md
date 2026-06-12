---
title: "Having problems installing everything"
date: 2011-08-17
forum: General Help
---

### Post by Vinilguy on 2011-08-17
I'm new to Ubuntu and basically every time I try to install anything using the Software Center displays me this: 'Package Operation Fail'

E:I wasn't able to locate a file for the libqtscript4-uitools package. This might mean you need to manually fix this package. (due to missing arch): Setting up liblastfm0 (0.4.0~git20090710-1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblastfm0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-runtime (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmysqlclient16 (5.1.41-3ubuntu12.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmysqlclient16 (--configure): 
 subprocess installed post-installation script returned error exit status 2

---

### Post by oldos2er on 2011-08-17
Try running this in a terminal, if there are any errors, please post the output here. ```
sudo apt-get clean && sudo apt-get update && sudo apt-get install libqtscript4-uitools
```

---

### Post by Vinilguy on 2011-08-17
I did it but got a few errors. I think the problem starts over here:

The following packages will be upgraded:
  libqtscript4-uitools
1 upgraded, 0 newly installed, 0 to remove and 438 not upgraded.
4 not fully installed or removed.
Need to get 284kB of archives.
After this operation, 852kB of additional disk space will be used.
Get:1 [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/main libqtscript4-uitools 0.1.0-3build1 [284kB]
Fetched 284kB in 1s (150kB/s)                
(Reading database ... 
dpkg: warning: files list file for package `libqtscript4-uitools' missing, assuming package has no files currently installed.
(Reading database ... 135871 files and directories currently installed.)
Preparing to replace libqtscript4-uitools 0.1.0-3build1 (using .../libqtscript4-uitools_0.1.0-3build1_i386.deb) ...
Unpacking replacement libqtscript4-uitools ...
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdebase-runtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up liblastfm0 (0.4.0~git20090710-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liblastfm0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmysqlclient16 (5.1.41-3ubuntu12.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmysqlclient16 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqtscript4-uitools (0.1.0-3build1) ...
Errors were encountered while processing:
 kdebase-runtime
 liblastfm0
 libmysqlclient16
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

