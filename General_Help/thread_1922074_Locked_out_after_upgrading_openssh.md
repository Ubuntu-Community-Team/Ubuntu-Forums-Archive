---
title: "Locked out after upgrading openssh"
date: 2012-02-08
forum: General Help
---

### Post by mertoz on 2012-02-08
I would really appreciate your help. My goal was to upgrade openssh to version 5.9, and because with apt I could not get it I try to install it with a debian package. Installation was done with dpkg but afterwards it stopped with the following error:

"The following packages have unmet dependencies: openssh-client : Depends: libssl1.0.0 (>1.0.0) but it is not installable"

Mentioned library is not located in the system however every trial to fix the dependency chain with "apt-get -f install"  fails with the above error. Is any way how to reinstall openssh and remove that dependency?

And yes.. I was locked out probably because of removing openssh-server which was obligatory for ssh_askpass_gnome?

---

### Post by EbnorEqvine on 2012-02-08
I recently encountered this problem. The solution was running 'aptitude build-depends'. It cleared up the problem by downgrading the broken package (libnih1 & libnih-dbus1) and configuring the partially installed packages -- partially installed because their installation was halted by the broken dependency issue. So try 'aptitude build-depends'. It was an instant solution to my problem.

---

### Post by mertoz on 2012-02-08
Unfortunately I cannot install aptitude too because other dependencies and dependency from libssl1.0.0 is missing..  On the pc there is installed and a working version of openssl 9.8 however when I tried to install openssh-client with dpkg this dependency popped out.. What else can I do?

---

### Post by mertoz on 2012-02-08
I was able to solve the problem with following steps:

a) remove the package that caused the problem 
"dpkg --remove --force-all openssh-client"

b) fix dependencies, which triggered a downloaded of a previous openssh-client that was crushed with a new install

"apt-get install -f "

c) apt-get opennssh-server
reinstall the ssh server

---

