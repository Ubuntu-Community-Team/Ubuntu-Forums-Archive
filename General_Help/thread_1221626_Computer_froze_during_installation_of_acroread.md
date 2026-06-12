---
title: "Computer froze during installation of acroread"
date: 2009-07-24
forum: General Help
---

### Post by lethalfang on 2009-07-24
My computer froze when I was installing acroread, so I had to force it to restart. Now my package manager wouldn't install or remove acroread.
How do I fix and recover that?

Thanks!

sudo aptitude install acroread:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  acroread 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up acroread (9.1.2-3jaunty1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing acroread (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 acroread
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done



sudo aptitude purge acoread:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  acroread{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 152MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 181898 files and directories currently installed.)
Removing acroread ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing acroread (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 acroread
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


---

