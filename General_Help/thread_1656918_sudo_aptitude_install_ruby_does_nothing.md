---
title: "sudo aptitude install ruby does nothing"
date: 2010-12-31
forum: General Help
---

### Post by ixxalnxxi on 2010-12-31
i installed ruby 1.8.6 using the guide here: [https://help.ubuntu.com/community/RubyOnRails#Alternative%20to%20manual%20installation](https://help.ubuntu.com/community/RubyOnRails#Alternative%20to%20manual%20installation)

worked great first time around.

then i installed ruby 1.9.2, cause i wanted the latest version. ended up being that there were some incompatibilities with a project i was doing, so i wanted 1.8.6 back (what the guide up top originally got me). i did "whereis ruby" and removed those directories.

now when i follow the stuff on the guide, i get this:

root@tipu_ubuntu:/usr/lib/ruby# sudo aptitude install ruby
sudo: cannot get working directory
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sh: getcwd() failed: No such file or directory
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

and "whereis ruby" returns nothing. any ideas?

---

### Post by nitro_n2o on 2010-12-31
the shell prompt shows that you are root already, you do not need sudo! 

try it out without the sudo

aptitude install ruby 


if that fails, search for the right name 
apt-cache search ruby 

then install the one that you think is right

---

### Post by ixxalnxxi on 2010-12-31
i did:


root@tipu_ubuntu:/usr/lib/ruby# apt-cache search ruby1.8-dev
ruby1.8 - Interpreter of object-oriented scripting language Ruby 1.8
ruby1.8-dev - Header files for compiling extension modules for the Ruby 1.8

then


root@tipu_ubuntu:/usr/lib/ruby# aptitude install ruby1.8
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sh: getcwd() failed: No such file or directory
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

root@tipu_ubuntu:/usr/lib/ruby#

(nothing happened).

---

