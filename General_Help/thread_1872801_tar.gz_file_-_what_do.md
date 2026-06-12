---
title: "tar.gz file - what do"
date: 2011-10-31
forum: General Help
---

### Post by AlexThompsonn on 2011-10-31
Heyy i'm kinda new to Ubuntu, and i'm trying to download utorrent for it. It came in a tar.gz file and i'm not sure how to install it or what. Someone help? :)
Thanks

---

### Post by haqking on 2011-10-31
> **AlexThompsonn said:**
> Heyy i'm kinda new to Ubuntu, and i'm trying to download utorrent for it. It came in a tar.gz file and i'm not sure how to install it or what. Someone help? :)
Thanks

any reason for utorrent it only alpha version for Linux and is CLI as far as i know, there are plenty of others on offer which are in the software centre for easy install such as qbittorrent, deluge and transmission is already installed or should be depending on your version of Ubuntu.

**First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

You can also use Gdebi package installer or look at dpkg.

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set 

Have fun

Regards

haqking

---

### Post by AlexThompsonn on 2011-10-31
awesome thanks man, and i just prefer to use uTorrent because it's what im used to :) but i have had this problem with other things too so it was kinda not just for that. thanks!

---

### Post by haqking on 2011-10-31
> **AlexThompsonn said:**
> awesome thanks man, and i just prefer to use uTorrent because it's what im used to :) but i have had this problem with other things too so it was kinda not just for that. thanks!

no worries you are welcome, remember though that Utorrent for Linux is an alpha release still.

Good luck

---

