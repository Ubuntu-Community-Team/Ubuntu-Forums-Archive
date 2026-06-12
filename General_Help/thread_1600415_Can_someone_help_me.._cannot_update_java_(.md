---
title: "Can someone help me.. cannot update java :("
date: 2010-10-18
forum: General Help
---

### Post by pr0ph37 on 2010-10-18
sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate



can anyone help me or point me in the right direction...


well sorry i didn't explain what i was trying to do.. i'm trying to upload frostwire so i am able to download some music, but when i go to use the upload center, it says "Wrong architecture 'i386' " i've searched and keep coming up with updating the java... am i wrong or ????

---

### Post by Pollox on 2010-10-19
Are you getting the deb file for frostwire from [http://www.frostwire.com/download/?os=ubuntu&](http://www.frostwire.com/download/?os=ubuntu&) ? What is the "upload center"? By "upload frostwire" I assume you mean "install frostwire".

I do not think java is your problem, especially given the error message you provided.

---

### Post by pr0ph37 on 2010-10-19
> **Pollox said:**
> Are you getting the deb file for frostwire from [http://www.frostwire.com/download/?os=ubuntu&](http://www.frostwire.com/download/?os=ubuntu&) ? What is the "upload center"? By "upload frostwire" I assume you mean "install frostwire".

I do not think java is your problem, especially given the error message you provided.

yes..

the ubuntu software center.. sorry.


i provided a screen shot of what i was talking about.. any suggestions? i get a Wrong architecture 'i386' error in ubuntu software center

---

### Post by cottfcfan on 2010-10-19
I think you may need to enable "Canonical partners" and "community" repo in synaptic. Reload and the search for "sun-java6-plugin" and install it from synaptic.

---

### Post by nlneilson on 2010-10-19
[http://aroundtheweb.info/2010/10/install-sun-java-ubuntu-10-10-maverick-meerkat-official-partner-repository/](http://aroundtheweb.info/2010/10/install-sun-java-ubuntu-10-10-maverick-meerkat-official-partner-repository/)

---

### Post by pr0ph37 on 2010-10-19
/thread, i figured out how to do it, i ended up downloading limewire on my laptop... thanks guys :popcorn:

---

### Post by Soul-Sing on 2010-10-19
the noarch package of frostwire uses openjdk, which comes by default with the install of ubuntu afaik.so sun java isn't need at all. untar/unpack it and run the =runFrostwire.sh= file.

---

### Post by TBABill on 2010-10-19
Are you trying to install 32 bit Frostwire within 64 bit Ubuntu? If so there are extra "force architechture" steps you have to take. I have not done it but will look for the steps and post if I find them.

---

### Post by TBABill on 2010-10-19
[http://ubuntuforums.org/showthread.php?t=1599055&highlight=frostwire+64+bit](http://ubuntuforums.org/showthread.php?t=1599055&highlight=frostwire+64+bit)
 
Steps to get it installed from Getdeb.

---

### Post by pr0ph37 on 2010-10-19
> **TBABill said:**
> [http://ubuntuforums.org/showthread.php?t=1599055&highlight=frostwire+64+bit](http://ubuntuforums.org/showthread.php?t=1599055&highlight=frostwire+64+bit)
 
Steps to get it installed from Getdeb.


this is what i used, the getdeb, after i installed it, everything loaded up fine and i stopped getting the error... still new to using this program / os but i'm loving it thus far... don't know why it took me so long to switch to it even though i knew it existed from reading this certain book :P

---

