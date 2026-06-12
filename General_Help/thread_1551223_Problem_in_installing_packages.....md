---
title: "Problem in installing packages...."
date: 2010-08-12
forum: General Help
---

### Post by siteregsam on 2010-08-12
when i tried installing euca2ools in Ubuntu 10.04 ultimate  edition, i got following erros


 [I]sam@sam-laptop:~$ sudo apt-get install euca2ools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  cloud-utils libyaml-0-2 python-boto python-m2crypto python-yaml
The following NEW packages will be installed:
  cloud-utils euca2ools libyaml-0-2 python-boto python-m2crypto  python-yaml
0 upgraded, 6 newly installed, 0 to remove and 343 not upgraded.
Need to get 628kB of archives.
After this operation, 3,703kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  python-m2crypto python-boto euca2ools libyaml-0-2 python-yaml  cloud-utils
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main python-m2crypto 0.20.1-1ubuntu2
  Could not connect to archive.ubuntu.com:80 (91.189.92.166). - connect  (110: Connection timed out) [IP: 91.189.92.166 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main python-boto 1.9b-1ubuntu3
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main euca2ools 1.2-0ubuntu10
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main libyaml-0-2 0.1.3-1
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main python-yaml 3.09-2build1
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main cloud-utils 0.11-0ubuntu1
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/m2crypto/python-m2crypto_0....]("http://archive.ubuntu.com/ubuntu/pool/main/m/m2crypto/python-m2crypto_0.20.1-1ubuntu2_i386.deb")   Could not connect to archive.ubuntu.com:80 (91.189.92.166). - connect  (110: Connection timed out) [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python-boto/python-boto_1.9...]("http://archive.ubuntu.com/ubuntu/pool/main/p/python-boto/python-boto_1.9b-1ubuntu3_all.deb")   Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/euca2ools/euca2ools_1.2-0ub...]("http://archive.ubuntu.com/ubuntu/pool/main/e/euca2ools/euca2ools_1.2-0ubuntu10_all.deb")   Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/liby/libyaml/libyaml-0-2_0.1....]("http://archive.ubuntu.com/ubuntu/pool/main/liby/libyaml/libyaml-0-2_0.1.3-1_i386.deb")   Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pyyaml/python-yaml_3.09-2bu...]("http://archive.ubuntu.com/ubuntu/pool/main/p/pyyaml/python-yaml_3.09-2build1_i386.deb")   Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cloud-utils/cloud-utils_0.1...]("http://archive.ubuntu.com/ubuntu/pool/main/c/cloud-utils/cloud-utils_0.11-0ubuntu1_all.deb")   Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with  --fix-missing?[/I]

 I am connected to internet thro proxy. Do i need a a direct ip?
Thanks in advance....

---

### Post by howefield on 2010-08-12
Have you tried entering the proxy information into Synaptic Package Manager > Settings > Preferences > Network ?

---

### Post by siteregsam on 2010-08-12
> **howefield said:**
> Have you tried entering the proxy information into Synaptic Package Manager > Settings > Preferences > Network ?


I added proxy info to  Synaptic Package Manager > Settings > Preferences > Network.
Still i am getting the same error....:(

---

