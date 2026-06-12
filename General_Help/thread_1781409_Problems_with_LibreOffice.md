---
title: "Problems with LibreOffice"
date: 2011-06-13
forum: General Help
---

### Post by bostjanv on 2011-06-13
Hello,
Some time after installing Ubuntu 11.04 I started getting the following message on LibreOffice startup:

LibreOffice 3.3 - Fatal Error
The application cannot be started. A general error occurred while accessing your
central configuration

This is actually occurring on multiple computers, and I have no idea what is causing it. Can someone help me?
Regards,
bostjanv

---

### Post by marl30 on 2011-06-13
You can try deleting .libreoffice folder from the home directory. This is a hidden file, so you'll have to enable show hidden folders first. This folder contains all the user configurations for Libreoffice. By deleting it will reset the configurations to default and possibly solve any issue you might have.

---

### Post by bostjanv on 2011-06-13
Hi,
Thanks for answering. As a matter of fact, I have done that; but the result is the same, i.e., I get the same message
Regards,
bostjanv

---

### Post by inkrypted on 2011-06-13
I had a similar problem and it stopped after installing sun-java6-bin and sun-java6.jre I think you have to have the Mediabuntu repository enabled first. Good luck.

---

### Post by bostjanv on 2011-06-14
Hi,
Thanks. Unfortunately, your advice didn't work. I was able to add the repository, and I was able to install the .jre file, but the sudo apt-get install sun-java6-bin command returned with the message that the package couldn't be located. I also tried uninstalling (purging) libreoffice and reinstalling it, but again, the result is the same (i.e. the above fatal error).
Regards,
bostjanv

---

### Post by marl30 on 2011-06-14
> **bostjanv said:**
> Hi,
Thanks. Unfortunately, your advice didn't work. I was able to add the repository, and I was able to install the .jre file, but the sudo apt-get install sun-java6-bin command returned with the message that the package couldn't be located. I also tried uninstalling (purging) libreoffice and reinstalling it, but again, the result is the same (i.e. the above fatal error).
Regards,
bostjanv

You could download and install the new Libreoffice 3.4 to see if you have any luck.

---

### Post by SoFl W on 2011-06-14
Do you get any additional information if you type "soffice" from the command line (terminal)?

also try "soffice -norestore"

---

### Post by bostjanv on 2011-06-28
Hi,
I don't have a solution to the problem yet, but I do have some new information, and perhaps someone can recognize what is going on. The problem might have something to do with gtk since (I think) libreoffice uses gtk. Namely, I use emacs as my editor, and I first installed the gtk version of emacs, which is when I noticed the libreoffice problem. After not being able to solve it, I reinstalled Ubuntu 10.04, and downloaded the lucid version of emacs and up to now libreoffice is behaving fine. On the other hand, I must say that after noticing the libreoffice problem (but before reinstalling Ubuntu) I did uninstall emacs; however, the problem persisted. So, that is a piece of evidence that speaks against gtk involvement.

I might note that I have encountered some other problems with the gtk version of emacs
Regards,
bostjanv

---

### Post by bostjanv on 2011-07-21
I still haven't found the solution to this problem, but I have the following additional information: It seems that the only thing wrong with the LibreOffice installation is that it can be activated only by root (sudo). If I try to use it as a normal user I get the message that I quoted above.
Regards,
bostjanv

---

