---
title: "Installing extra software to additional hard Drive"
date: 2010-08-29
forum: General Help
---

### Post by JoBangles on 2010-08-29
Hi, I have added a 1.0 Tb USB HDD and would like to install games, extra software, etc. on it when using apt-get or Synaptic but I can not find any info on doing so. Thanks in advance for any help.:confused:

---

### Post by carl4926 on 2010-08-29
I don't think you can

---

### Post by garvinrick4 on 2010-08-29
apt-get or synaptics will only work within file system to download or remove packages and their dependencies. Cannot choose another drive to download to. Maybe with a raid setup if you want to look into that. raid combines the 2 drives so it is looked at as 1 drive, I have read about but never tried. Any which way here is a good manual to keep handy and read in spare time.

[Ubuntu Manual - Home]("http://ubuntu-manual.org/")

---

### Post by sharathcshekhar on 2010-08-29
May be you can do this if you build your packages from hand. 
Mount your HDD in, say /additional, Download the source and run
```

./configure --prefix=/additional
make 
sudo make install

```
This will install your software on your HDD
Not sure how you can do this from .deb packages.

---

### Post by JoBangles on 2010-08-29
Thank you for your advice, I think I will wait till this is a built in option with Ubuntu as I am sure there will be a need for large & removable hard drives.

---

### Post by Mark Phelps on 2010-08-29
It's not as simple as you want to believe ...

Regardless of where the package downloads to, the apps are installed to directories already created in the filesystem, and in this case, those directories would NOT be on your removable drive because they are the same set of directories shared by the system apps.

If you moved, or redirected, your app directories to your removable drive, system apps already installed would no longer work.

Linux is NOT like MS Windows with an equivalent of the Program Files directory. So, if you're waiting for something like this, you're wasting your time.

As already said, the only way to do what you want is to build each app from source and force it to install in a different set of directories than the default ones.

---

