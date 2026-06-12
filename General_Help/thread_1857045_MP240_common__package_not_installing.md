---
title: "MP240 common  package not installing"
date: 2011-10-09
forum: General Help
---

### Post by CBGMale on 2011-10-09
Hey there. I'm using Ubuntu 11.04, and I'm trying to get my Cannon MP240 scanner/printer to install, but I have run into a brick wall. When I try to install the cnijfilter-common_3.00-1_i386.deb package, this is what I get at the bottom of the details screen after it tells me it cannot complete the installation:

Unpacking cnijfilter-common (from .../cnijfilter-common_3.00-1_i386.deb) ... 
dpkg: dependency problems prevent configuration of cnijfilter-common: 
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however: 
  Package libcupsys2 is not installed. 
dpkg: error processing cnijfilter-common (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 cnijfilter-common

I have checked the Ubuntu Software program and I have libcups2 installed already. What am I doing wrong? Please help. I've tried some of the suggestions offered earlier in the thread to no avail. Thank you in advance for any help.

---

