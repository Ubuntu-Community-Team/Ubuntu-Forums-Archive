---
title: "Error in terminal window when installing Ndiswrapper"
date: 2009-06-29
forum: General Help
---

### Post by g35celicaz on 2009-06-29
I am currently running ubuntu 8.10 on my laptop and I am trying to get wireless internet on it. I was able to get wireless internet on my laptop when Windows was the operating system, but now that it is ubuntu im having trouble getting the wireless internet. I have internet right now but its wired. 

I have been told that i have to use Windows Wireless Drivers and ndiswrapper


So i am using this guide to install ndiswrapper and Windows Wireless Drivers:


[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)



Every thing was going fine in this guide but when i put in this command in the terminal it gave me an error: 


sudo dpkg -i ndiswrapper-utils_*.deb


I put this in the terminal window and it game this:

g35celicaz@g35celicaz-laptop:~$ sudo dpkg -i ndiswrapper-utils_*.deb
[sudo] password for g35celicaz: 
dpkg: error processing ndiswrapper-utils_*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
ndiswrapper-utils_*.deb


What can i do?

Pleas help

- Thanks

---

### Post by ~sHyLoCk~ on 2009-06-29
Hmm, can you just use ```
sudo dpkg -i *.deb
``` and see if it works? [Provided you don't have any other deb packages in the same folder. If you do, copy it in a separate folder and try.]

---

### Post by g35celicaz on 2009-06-29
I put in this command in the terminal window:

sudo dpkg -i *.deb


And it gave me this:


g35celicaz@g35celicaz-laptop:~$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
g35celicaz@g35celicaz-laptop:~$ 


What should I do?

 - Thanks

---

### Post by synapsys on 2009-06-29
I think you mis-understood the guide. You currently have internet access so all you need to do is enable the correct repositories and install a package called ndisgtk.

> **2.1. Installing Packages (With Internet access on the Ubuntu computer)**

 If you already have Internet access via some other method while logged into Ubuntu: 
1. Ensure the multiverse and universe repositories are enabled; see [AddingRepositoriesHowto]("https://help.ubuntu.com/community/AddingRepositoriesHowto") 
2. Install the *ndisgtk* package from the Ubuntu repositories.  
```
sudo apt-get install ndisgtk
```If you don't know how to install applications then you can [read this guide]("http://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html"). Then skip to step 3 to configure.

(look at the table of contents on the right side of the page, it will make more sense)

---

