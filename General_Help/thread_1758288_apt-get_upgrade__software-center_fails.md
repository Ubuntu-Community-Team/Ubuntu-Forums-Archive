---
title: "apt-get upgrade / software-center fails"
date: 2011-05-14
forum: General Help
---

### Post by Jove on 2011-05-14
Weird error - can't find any other references online, so posting here. Assuming that the crux of the matter is:

  File "/usr/lib/python2.7/subprocess.py", line 432, in <module>
    import pickle
ValueError: bad marshal data (unknown type code)

Any suggestions very welcome!

Alan 

root@asf-home:/var/lib/dpkg/info# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up software-center (4.0.1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2327, in <module>
    main()
  File "/usr/bin/pycentral", line 2317, in main
    if action.check_args(global_options):
  File "/usr/bin/pycentral", line 1486, in check_args
    arch = self.get_arch()
  File "/usr/bin/pycentral", line 1381, in get_arch
    import subprocess
  File "/usr/lib/python2.7/subprocess.py", line 432, in <module>
    import pickle
ValueError: bad marshal data (unknown type code)
dpkg: error processing software-center (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

