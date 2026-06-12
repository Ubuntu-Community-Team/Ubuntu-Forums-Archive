---
title: "Install ia32-libs without internet connection"
date: 2010-06-05
forum: General Help
---

### Post by dhirajsuvarna on 2010-06-05
I am using Ubuntu 9.10 and i currently installed Ubuntu 10.4.

I am using internet connection of a provider named 24 Online Client, it requires me to login to the net using a executable named "crclient", now this executable is a 32 bit executable, but, i am using 64 bit Ubuntu 10.4, due to this i am unable to login to the internet and hence cannot use the same.

Now to run this executable i must install ia32-libs, and i dont have an internet connection to install it.

It would be great help, if someone suggested me a work around for this problem.

P.S: I tried to download the deb files from [http://package.ubuntu.com](http://package.ubuntu.com) but it failed to install since mine Ubuntu 10.4 is so crude that it doesn't even contain build-essentials, and i cannot download it because i cannot login to my internet connection

---

### Post by Andreas1 on 2010-06-05
i think if i remember correctly synaptic has a function to "generate script for downloading marked packages" or something. so mark ia32libs for install, then do that, and execute the script on the other system. that way you should have all dependencies covered. no need for build-essentials, you don't compile anything, the way i understand it.

---

### Post by Irony on 2010-06-05
Go to synaptic, tick the packages you require for install then go to File and to Generate Package Script. Select where to create the script, I suggest your desktop (make sure it is your desktop rather than the root desktop) hit okay.

On your desktop is a bash file - if you open it up in gedit you will see a link or links to the files you need to download, this can be done on a computer with an internet connection.

---

### Post by dhirajsuvarna on 2010-06-05
thank you guys for your valuable suggestions.

but when i view in synaptic and search for ia32-libs i am not able to find it and hence am not able to generate the script.

---

