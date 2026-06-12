---
title: "E: initscripts: subprocess installed post-installation script returned error exit sta"
date: 2011-05-03
forum: General Help
---

### Post by smukherjee11 on 2011-05-03
I just installed Ubuntu 10.04.2 x64 on my laptop. Initially, everything was working fine. 

After I ran update manager, it downloaded about 116 MB of updates, and after installation, it showed the error: "**E: initscripts: subprocess installed post-installation script returned error exit status 1**", followed by "**Not all changes and updates succeeded**".

Upon clicking "Details", it showed the following:

[B]Setting up initscripts (2.87dsf-4ubuntu17.1) ...
update-rc.d: /etc/init.d/ondemand: file does not exist
dpkg: error processing initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initscripts
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B] 
During the update process, I had aborted it once. But after I tried to update some time later, it resumed successfully.

After seeing that error, even if I try to download packages using apt-get or aptitude, after downloading, the above message is shown in the terminal. The packages appear to run fine, though.

Please help on what is wrong here and how to fix it. Thanks in advance.

---

