---
title: "Newbie Help - Digikam tarball"
date: 2010-09-19
forum: General Help
---

### Post by Quarkrad on 2010-09-19
Help please.  I have downloaded the Digikam tarball (I would like to see the difference between this v1.4 and v1.2 in the repository).  For my 'linux education' I would like to try and install this - tarballs always cause me issues.  The downloaded file is called **digikam-1.4.0.tar.bz2** and I have it in a folder called digikam in my root directory.  I.e. along side Pictures, Downloads, Documents, etc.  The instructions to install is:
[B]
  Extract the tarball via tar -xvjf filename.bz2, enter the extracted directory and then you need to issue a set of commands. You need to specify an installation prefix. This will be the base path of the installation. To determine the correct path to your KDE installation, use `kde4-config --prefix` and provide it as a parameter for cmake, as shown in the example commands below:


mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=relwithdebinfo -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
su
make install[/B]

I'm afraid this is bit confusing to me - although I think I understand the logic. If somebody could substitute my parameters for me I will try and work out what I cannot understand.  Many thanks.  (Source - [http://www.digikam.org/drupal/download?q=download/tarball](http://www.digikam.org/drupal/download?q=download/tarball))

---

### Post by Quarkrad on 2010-09-19
bump

---

