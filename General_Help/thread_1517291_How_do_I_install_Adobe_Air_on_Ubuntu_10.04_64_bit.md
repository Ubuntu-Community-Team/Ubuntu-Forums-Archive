---
title: "How do I install Adobe Air on Ubuntu 10.04 64 bit?"
date: 2010-06-24
forum: General Help
---

### Post by lightningfox on 2010-06-24
Hi 

I want to install Adobe Air on Lucid Lynx 64 bit.

I read that Adobe Air only has a 32 bit version for Linux.

Since I have already installed some 32 bit apps on my system (Flash, WINE) I think I already have the required libraries/dependencies.

I downloaded Adobe Air's deb from its webpage [http://get.adobe.com/air/](http://get.adobe.com/air/) and then I
tried to install it with "sudo dpkg -i adobeair.deb"
but I got the error message 

```
dpkg: error processing adobeair.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 adobeair.deb
```


Please tell me how to install Adobe Air on Lucid Lynx 64 bit.

---

### Post by oldos2er on 2010-06-24
```
sudo dpkg -i --force-architecture adobeair.deb
```

---

### Post by dckirba on 2010-07-02
Here's a detailed list of all the dependencies you need : [http://www.omgubuntu.co.uk/2010/01/how-to-install-adobe-air-ubuntu-64bit.html]("http://www.omgubuntu.co.uk/2010/01/how-to-install-adobe-air-ubuntu-64bit.html")

---

### Post by lightningfox on 2010-07-02
Thank you. I'll try that.

---

### Post by mdbarton on 2010-07-28
> **oldos2er said:**
> ```
sudo dpkg -i --force-architecture adobeair.deb
```

That did the trick for me - thanks!

---

### Post by Bukoptimistas on 2010-09-28
for me didnt work well when i forced deb package with command ```
sudo dpkg -i --force-architecture adobeair.deb
``` It will install, but after air app installation something goes wrong with ubuntu package's. When you want to update or install diffrent program it says that you have broken packages. Running ```
sudo apt-get -f install
``` removes installed adobe air app. 

So what i did and worked:

```
sudo dpkg -i getlibs-all.deb
```
Got latest Adobe air **.bin** file from their page [http://get.adobe.com/air/](http://get.adobe.com/air/)
made it executable
```
 chmod +x AdobeAIRInstaller.bin 
```
Run it
```
./AdobeAIRInstaller.bin
```
When you first time run Adobe air installer it will update to 2.x version. And installed apps wont break packages Ubuntu's information.
Thats my story for running Adobe air v2 on Ubuntu 10.04 64bit.

---

### Post by Dakra on 2010-12-11
Thank you Bukoptimistas, your solution worked perfectly. I have installed GOG.com downloader and it works fine.

---

