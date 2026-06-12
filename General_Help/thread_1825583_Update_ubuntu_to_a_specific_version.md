---
title: "Update ubuntu to a specific version"
date: 2011-08-15
forum: General Help
---

### Post by miivers on 2011-08-15
Hello Ubuntu forum.

Windows user here taking a daring step into the world of linux. 
I am trying to install openni for ros if anyone is familiar with it. That however is not what this post is all about. I am unable to continue the installation of openni because of OS version mismatch. Below is what I get in the console:

```

The following packages have unmet dependencies.
  ros-diamondback-openni-kinect: Depends: ros-diamondback-common (= 1.4.3-s1309998310~lucid) but 1.4.3-s1312425121~lucid is to be installed
                                 Depends: ros-diamondback-common-msgs (= 1.4.0-s1309998220~lucid) but 1.4.0-s1312425024~lucid is to be installed
                                 Depends: ros-diamondback-driver-common (= 1.2.3-s1309998784~lucid) but 1.2.3-s1312425643~lucid is to be installed
                                 Depends: ros-diamondback-geometry (= 1.4.2-s1309998487~lucid) but 1.4.2-s1312425340~lucid is to be installed
                                 Depends: ros-diamondback-image-common (= 1.4.1-s1309998868~lucid) but 1.4.1-s1312425732~lucid is to be installed
                                 Depends: ros-diamondback-perception-pcl (= 0.10.0-s1310000126~lucid) but 0.10.0-s1312427031~lucid is to be installed
                                 Depends: ros-diamondback-ros (= 1.4.8-s1306606948~lucid) but 1.4.9-s1312417699~lucid is to be installed
                                 Depends: ros-diamondback-ros-comm (= 1.4.7-s1309983292~lucid) but 1.4.7-s1312424690~lucid is to be installed
                                 Depends: ros-diamondback-vision-opencv (= 1.4.3-s1309998991~lucid) but 1.4.3-s1312425855~lucid is to be installed
E: Broken packages

```So my question here is. will any version newer than the required Ubuntu version do? If no. How can I update my version of Ubuntu to match the required OS version required? :confused:

Any help would be great.
Michael

---

### Post by mendhak on 2011-08-15
I think your best bet is to install VirtualBox.  In there, create a new virtual machine and install Ubuntu 11.04.  Then try installing your software and playing around with package versions.  Then you can safely know which version of Ubuntu your software can work comfortably with.

---

### Post by miivers on 2011-08-16
Thanks for the tip. setting up a VM to test it confirmed what Ubuntu version I should update to.

Michael

---

