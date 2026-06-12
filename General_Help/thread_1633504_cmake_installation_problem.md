---
title: "cmake installation problem"
date: 2010-11-29
forum: General Help
---

### Post by gnmeles on 2010-11-29
Hello
My name is George 

I have a problem installing cmake in ubuntu lucid lynx.
When i try sudo apt-get install cmake-qt-gui

i get this message in terminal
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cmake-qt-gui: Depends: cmake (= 2.8.1-4~lucid1) but 2.8.0-5ubuntu1 is to be installed
E: Broken packages

Any ideas?

thanks in advance.

---

### Post by mc4man on 2010-11-29
Go to software sources and under the 'other' tab make sure that lucid-backports is enabled. If having to enable then click close and reload.

If already checked then in a terminal run sudo apt-get update

Here's the required version of the package if you wish to see or manually dl and install
[http://packages.ubuntu.com/lucid-backports/cmake-qt-gui](http://packages.ubuntu.com/lucid-backports/cmake-qt-gui)

---

### Post by gnmeles on 2010-11-29
No luck with the update part.

I' ve seen the files and tried to install it manually but i get no result.
I' ve created a folder /opt/cmake/cmake-2.8.1 (the older version) and then ./bootstrap;make;make install.

It was my first attempt to manually install, so i must be missing something.

Is there any other solution?

---

### Post by mc4man on 2010-11-29
> Is there any other solution?
Not sure what you need a solution to.
you have basically 3 choices

use the lucid repo cmake and related packages - version 2.8.0-5ubuntu1
use the lucid-backports for cmake and related - version 2.8.1-4~lucid1 
(you cannot mix versions of cmake and cmake-*

Build your own, which you've now said you've done.
By default the files you built would have been installed to /usr/local, the binaries to /usr/local/bin
Also by default the gui would not of been built which was the point of this thread to begin with.

I can't see any advantage to using a self built cmake, the repo ones would suffice and possibly be better due to ubuntu/debian specific patches

In any event you should cd to your source folder and run a 
sudo make uninstall
Then either configure to build the gui or square away and use the repo packages, either lucid or lucid-updates

Edit: also see no reason to be building cmake in /opt, better to build in ~/

---

