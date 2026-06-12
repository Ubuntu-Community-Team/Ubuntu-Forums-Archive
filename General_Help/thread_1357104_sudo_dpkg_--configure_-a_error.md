---
title: "sudo dpkg --configure -a error"
date: 2009-12-16
forum: General Help
---

### Post by aklo on 2009-12-16
I installed java jre, jdk and netbeans for my project last night. I also install the chinese chess programs which is why i think it is also included in the error.

Anyway this morning i went to the synaptic package manager and it says something about dpkg error and asked me to type "sudo dpkg --configure -a"  
I did what it says and below is the output from the teminal.

I don't understand from the output what does it mean? seems like it is asking me to install my java again? I did not.

I tried my netbeans and it is working correctly, my chinese chess program is also working correctly and the error from synaptic package manager disappear mysteriously? 

I had searched the internet and there are not many with the exactly problem and although it offers solution, it seems in my case that i do no need it and for me, it just disappear after i type the sudo dpkg thing which i have no idea what it does.

> sudo dpkg --configure -a
[sudo] password for kelvin: 
Setting up gmchess (0.20.2-0ubuntu1) ...
Setting up sun-java6-doc (6-15-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

---

### Post by 3rdalbum on 2009-12-16
If there's no error now, then everything is fine.

---

