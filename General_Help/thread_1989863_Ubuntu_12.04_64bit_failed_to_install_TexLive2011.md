---
title: "Ubuntu 12.04 64bit failed to install TexLive2011"
date: 2012-05-28
forum: General Help
---

### Post by Heyayun on 2012-05-28
This is my first time to install tex. My installation steps are as follows:
sudo apt-get install perl-tk
wget [http://oss.ustc.edu.cn/CTAN/systems/texlive/tlnet/install-tl-unx.tar.gz](http://oss.ustc.edu.cn/CTAN/systems/texlive/tlnet/install-tl-unx.tar.gz)
tar -zxvf install-tl-unx.tar.gz 
cd install-tl-20120511/
sudo ./install-tl --gui -location [http://oss.ustc.edu.cn/CTAN/systems/texlive/tlnet](http://oss.ustc.edu.cn/CTAN/systems/texlive/tlnet)

In the setting gui, I change the directory as /home/hyy/texlive, and choose to make a sign link.

Here is the error information:
Installing [0001/2163, time/total: ??:??/??:??]: 12many [376k]
......
Installing [0455/2163, time/total: 01:07/04:24]: csvsimple [568k]
tar: tex/latex/csvsimple/csvsimple.sty: Cannot open: Input/output error
tar: Exiting with failure status due to previous errors
untar: untarring /home/hyy/texlive/2011/temp/csvsimple.tar failed (in /home/hyy/texlive/2011/texmf-dist)
untarring /home/hyy/texlive/2011/temp/csvsimple.tar failed, stopping install.
Installation failed.
Rerunning the installer will try to restart the installation.
Or you can restart by running the installer with:
  install-tl --profile installation.profile [EXTRA-ARGS]
Writing install-tl.log in current working directory.

Anyone helps?

---

