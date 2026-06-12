---
title: "Problem installing QT."
date: 2011-12-17
forum: General Help
---

### Post by IanBorn on 2011-12-17
[FONT=Arial]
I  just install Xubuntu and download QT sdk.
-rwxrwxrwx 1 1404556800 2011-12-15 06:33 Qt_SDK_Lin64_offline_v1_1_4_en.run

bash: ./Qt_SDK_Lin64_offline_v1_1_4_en.run: cannot execute binary file? the 
I can not run it from Launcher neither,

Please, tell me how to have this program execute?

Thanks.
[/FONT]

---

### Post by BC59 on 2011-12-17
Install it from Ubuntu Software Center.

---

### Post by IanBorn on 2011-12-17
sudo apt-get install qtsdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qtsdk
sudo apt-get install qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qt

---

### Post by scorchgeek on 2011-12-17
As BC59 said, if the package is available from the Software Center/package manager, it is much easier to get the package from there, so try that first.

If you read that and the package really isn't in there, which is unlikely, you might try this:

Try editing the file in your favorite text editor and making sure that the first line says
```
#!/bin/bash
```

It's also possible that you might need to run the script with sudo. Finally, it could simply be that the file is corrupted, so you might try downloading it again.

---

### Post by BC59 on 2011-12-17
But why you are not installing it from the Software Center?

---

### Post by scorchgeek on 2011-12-17
The package won't be called just "qt." Run the Synaptic Package Manager instead and do a search for qt.

---

### Post by IanBorn on 2011-12-17
How to find out if Xubuntu is a 32 or 64 bits OS?
I will try to download QT for 32 bits Linux to see if it work.
Thanks.

---

### Post by gandaran on 2011-12-17
```
sudo apt-get install qt-sdk
```
qt-sdk installs the complete Qt Software Development Kit

---

