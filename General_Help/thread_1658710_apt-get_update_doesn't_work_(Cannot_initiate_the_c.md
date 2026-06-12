---
title: "apt-get update doesn't work (Cannot initiate the connection to  connect )"
date: 2011-01-03
forum: General Help
---

### Post by jpksampath on 2011-01-03
Hi expertises,
I am working on ubuntu (Xubuntos) using VMware virtual machine. when I enter apt-get update it gives following error;
```
xubuntos@xubuntos-tinyos:~$ sudo apt-get update
``````
 Err http://tinyos.stanford.edu edgy Release.gpg
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://tinyos.stanford.edu edgy/main Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Ign http://tinyos.stanford.edu edgy Release
Ign http://tinyos.stanford.edu edgy/main Packages
Err http://tinyos.stanford.edu edgy/main Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty Release.gpg
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/main Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/restricted Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/universe Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/multiverse Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates Release.gpg
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/main Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/universe Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security Release.gpg
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/main Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/restricted Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/universe Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Ign http://archive.ubuntu.com feisty Release
Ign http://archive.ubuntu.com feisty-updates Release
Ign http://archive.ubuntu.com feisty-security Release
Ign http://archive.ubuntu.com feisty/main Packages
Ign http://archive.ubuntu.com feisty/restricted Packages
Ign http://archive.ubuntu.com feisty/main Sources
Ign http://archive.ubuntu.com feisty/restricted Sources
Ign http://archive.ubuntu.com feisty/universe Packages
Ign http://archive.ubuntu.com feisty/universe Sources
Ign http://archive.ubuntu.com feisty/multiverse Packages
Ign http://archive.ubuntu.com feisty/multiverse Sources
Ign http://archive.ubuntu.com feisty-updates/main Packages
Ign http://archive.ubuntu.com feisty-updates/restricted Packages
Ign http://archive.ubuntu.com feisty-updates/main Sources
Ign http://archive.ubuntu.com feisty-updates/restricted Sources
Ign http://archive.ubuntu.com feisty-updates/universe Packages
Ign http://archive.ubuntu.com feisty-security/main Packages
Ign http://archive.ubuntu.com feisty-security/restricted Packages
Ign http://archive.ubuntu.com feisty-security/main Sources
Ign http://archive.ubuntu.com feisty-security/restricted Sources
Ign http://archive.ubuntu.com feisty-security/universe Packages
Ign http://archive.ubuntu.com feisty-security/universe Sources
Ign http://archive.ubuntu.com feisty-security/multiverse Packages
Ign http://archive.ubuntu.com feisty-security/multiverse Sources
Err http://archive.ubuntu.com feisty/main Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/restricted Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/main Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/restricted Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/universe Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/universe Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/multiverse Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty/multiverse Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/main Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/restricted Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/main Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/restricted Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-updates/universe Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/main Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/restricted Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/main Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/restricted Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/universe Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/universe Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/multiverse Packages
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Err http://archive.ubuntu.com feisty-security/multiverse Sources
  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/edgy/Release.gpg  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  Cannot initiate the connection to 3127:80 (0.0.12.55). - connect (22 Invalid argument)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
``` ,

My network is quite ok and I can connect internet using firefox. I have a proxy and I set my proxy this way;
```
xubuntos@xubuntos-tinyos:~$ gksu mousepad ~/.bashrc

``` ,
and append,
```

http_proxy=http://x.x.x.x:<PORT>
export http_proxy
``` ,
Even after read a lot about this I couldn't able to fix this.
I referred suggestions in following links

 ([http://www.linuxquestions.org/questions/linux-software-2/ubuntu-gcc-error-599025/#post2956189](http://www.linuxquestions.org/questions/linux-software-2/ubuntu-gcc-error-599025/#post2956189)
[http://ubuntuforums.org/showthread.php?t=248765](http://ubuntuforums.org/showthread.php?t=248765)
[http://ubuntuforums.org/showthread.php?t=924855](http://ubuntuforums.org/showthread.php?t=924855)
[http://art.ubuntuforums.org/showthread.php?t=561138](http://art.ubuntuforums.org/showthread.php?t=561138)
[http://ubuntuforums.org/showthread.php?t=152031](http://ubuntuforums.org/showthread.php?t=152031))

Can anyone please suggest me how to proceed?
Thanks in advance
BR
SAMPATH

---

### Post by Joe of loath on 2011-01-03
When did you install this VM? you seem to have a mixture of edgy/feisty repositories, which are unsupported and therefore probably offline.

---

### Post by cavalier911 on 2011-01-03
After a release has expired the url changes to the old-releases address.
Open the /etc/apt/sources.list as root in a text editor.
Replace archive or security with old-releases so it says:
[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

I would suggest removing the stanford address's which are wrong. If they mirror fiesty repo it's at a different url.

---

