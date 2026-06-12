---
title: "Installing VirtualBox on Lucid Lynx offline"
date: 2010-09-15
forum: General Help
---

### Post by pro_cad on 2010-09-15
Hi,

This is my first post and I am somewhat of a new Ubuntu user.

How do I go about doing an offline installation of VirtualBox on Ubuntu Server 10.04, ie. By downloading the installation files and then installing while disconnected from the internet.

I downloaded the .deb file from the VirtualBox website but the installation failed...
Any help would be highly appreciated.

Thanx :)

---

### Post by blueridgedog on 2010-09-15
You may have some dependencies that need to be downloaded as well.  I suggest you try and install the .deb file from the command line so that you can see what error it reports.

```
sudo dpkg -i filename.deb
```

---

### Post by pro_cad on 2010-09-16
I did try downloading and installing manually butt getting dependency errors as you mentioned.

Package libcurl3 is not installed...

Package libgl1-mesa-glx is not installed...

.
.
.
A few more dependencies.

Processing triggers for ureadahead...
ureadahead will be reprofiled on next reboot

How do I install these dependencies manually?

---

### Post by blueridgedog on 2010-09-16
You must download the .deb files for the dependent packages and install them.  They in turn may have dependencies that have to be satisfied.  Installing packages offline can be a challenge.

---

### Post by pro_cad on 2010-09-17
OK I was able to install the .deb file offline after downloading the required dependencies which had to be done online as mentioned, using **apt-get -f install**.

---

