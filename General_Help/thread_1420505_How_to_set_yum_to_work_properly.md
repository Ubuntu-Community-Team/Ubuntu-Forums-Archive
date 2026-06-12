---
title: "How to set yum to work properly"
date: 2010-03-03
forum: General Help
---

### Post by lonerunner on 2010-03-03
I have ubuntu 8.04 64bit edition, i'm trying to install popular kloxo web server, which require yum, i installed yum with sudo apt-get install yum, but problem is when i try to run anything with yum i get this error

> There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.5.2 (r252:60911, Jan 20 2010, 23:14:04) 
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)]

If you cannot solve this problem yourself, please send this
message to <yum@lists.linux.duke.edu>.

but when i go to Synaptic Package Manager and search i get python-elementtree and python-celementtree both installed.

How can i check if module is installed correctly or versions match.

---

### Post by ronnielsen1 on 2010-03-03
I don't believe kloxo is ported to debian or ubuntu. As far as yum  it is a software installation tool for Red hat linux and Fedora Linux. You might try webadmin instead.


[http://en.wikipedia.org/wiki/Webmin](http://en.wikipedia.org/wiki/Webmin)

---

### Post by lonerunner on 2010-03-04
i usually use xampp it's easy and fast installation, but now i bought vps server with centos and kloxo so i need to install kloxo on my pc for testing purposes. anyway i found some answers how yum can work properly but i dont know where to find older packages for python: this is quote from other post here on forum how some people made it work but links for packages are dead 

> The following code downgrades the cElementTree and elementTree packages and is supposedly a fix.  I haven't tried it though.

 	Code:
 	sudo dpkg -r --force-depends python-celementtree
sudo dpkg -r --force-depends python-elementtree
sudo dpkg -i (your directory)/python-elementtree_1.2.6-10ubuntu2_all.deb
sudo dpkg -i (your directory)/python-celementtree_1.0.5-8ubuntu2_i386.deb 
[http://archive.ubuntu.com/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-10ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-10ubuntu2_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/c/celementtree/python-celementtree_1.0.5-8ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/celementtree/python-celementtree_1.0.5-8ubuntu2_i386.deb)



---

