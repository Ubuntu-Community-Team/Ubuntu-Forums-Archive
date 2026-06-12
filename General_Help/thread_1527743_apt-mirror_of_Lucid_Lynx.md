---
title: "apt-mirror of Lucid Lynx"
date: 2010-07-09
forum: General Help
---

### Post by mhlavac on 2010-07-09
I have established a mirror of Lucid Lynx using the following in the mirrors.list file:

deb-amd64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-amd64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb-amd64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-amd64  [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid main main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-amd64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb-amd64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-amd64  [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid main main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer

When trying to upgrade from Karmic to Lucid using the mirror I get the following errors:

Failed to fetch [http://mgmt/ubuntu/pool/main/libg/libgnome-keyring/libgnome-keyring0_2.30.1-0ubuntu1_amd64.deb](http://mgmt/ubuntu/pool/main/libg/libgnome-keyring/libgnome-keyring0_2.30.1-0ubuntu1_amd64.deb) 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-glx-185_195.36.24-0ubuntu1~10.04_amd64.deb]("http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-glx-185_195.36.24-0ubuntu1%7E10.04_amd64.deb") 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.24-0ubuntu1~10.04_amd64.deb]("http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.24-0ubuntu1%7E10.04_amd64.deb") 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-185-kernel-source_195.36.24-0ubuntu1~10.04_amd64.deb]("http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-185-kernel-source_195.36.24-0ubuntu1%7E10.04_amd64.deb") 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-185-libvdpau_195.36.24-0ubuntu1~10.04_amd64.deb]("http://mgmt/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-185-libvdpau_195.36.24-0ubuntu1%7E10.04_amd64.deb") 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current-modaliases_195.36.24-0ubuntu1~10.04_amd64.deb]("http://mgmt/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current-modaliases_195.36.24-0ubuntu1%7E10.04_amd64.deb") 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-185-modaliases_195.36.24-0ubuntu1~10.04_amd64.deb]("http://mgmt/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-185-modaliases_195.36.24-0ubuntu1%7E10.04_amd64.deb") 404  Not Found
Failed to fetch [http://mgmt/ubuntu/pool/main/s/simple-scan/simple-scan_1.0.3-0ubuntu1_amd64.deb](http://mgmt/ubuntu/pool/main/s/simple-scan/simple-scan_1.0.3-0ubuntu1_amd64.deb) 404  Not Found

Those particular files do not exist on my local mirror.  They seem to have a newer timestamp (May) on the ubuntu.com mirrors, so that makes me think that they are updates.  If I am not getting updates, why?  I have a line above for lucid-updates...

Any help would be appreciated!

---

