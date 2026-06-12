---
title: "How to install nvidia drivers for bumblebee from the nvidia run script"
date: 2011-07-05
forum: General Help
---

### Post by rockorequin on 2011-07-05
If you have nvidia Optimus graphics and use bumblebee ([https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)) to get nvidia 3d acceleration, it installs the nvidia-current package.

If you want to build a more recent version of the nvidia driver to work with bumblebee, you can download the .run script that installs the drivers from nvidia's ftp site [ftp://download.nvidia.com/XFree86/Linux-x86_64](ftp://download.nvidia.com/XFree86/Linux-x86_64) (that URL is for 64-bit drivers), and use the attached script to install it.

```

# Remove the nvidia-current deb package
sudo apt-get remove nvidia-current
# Install the nvidia driver in the latest .run file
bash ./bumblebee-nvidia-install.sh
```

You can optionally specify the driver version, eg

```
bash ./bumblebee-nvidia-install.sh 280.04
```

The script is adapted from the Fedora install script in bumblebee with some extra logic to look for the latest version of the run file. It installs the module as nvidia-current in dkms so that it will rebuild if you upgrade the kernel.

Note: if you re-run the bumblebee installer, it will reinstall the nvidia-current deb package so you will probably have to run this again.

---

