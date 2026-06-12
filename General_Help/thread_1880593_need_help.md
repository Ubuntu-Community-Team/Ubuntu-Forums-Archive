---
title: "need help"
date: 2011-11-14
forum: General Help
---

### Post by devarshi on 2011-11-14
hello ... friends... i have downloaded eclipse.tar.gz file from the website... but  i am not able to install it on my pc...m pretty new to ubuntu ..so try to be more  explanation..on how can i do it. i have the file on /home/devarshi 

from basic step just tell me how will i install it on my pc..

thanks again .

---

### Post by WorMzy on 2011-11-14
Hi.. rather.. than.. trying.. to.. install.. eclipse.. via.. tar.gz.. why.. not.. use.. the.. software.. centre.. or.. apt-get..?

```
sudo apt-get install eclipse
```

---

### Post by devarshi on 2011-11-14
hi there..

well i come from india... here the net conncection speed is pretty slow.... best option is i keep ..all the required files downloaded at once on my pc...so whenever i install Ubuntu i get all the softwares installed pretty fast

 here the eclipse is 210 mb ..it will take 2hours to download for me..

so i have downloaded .tar.gz file...if you could help me out with tar.gz ..it would be much better...besides ya i know its a compressed file..but how can i get this file installed on my pc..now??

---

### Post by elliotn on 2011-11-14
check the read me file inside the tar.gz and read the instructions....you make come up with dependency problems

---

### Post by guestolo on 2011-11-14
Why not just right click the file and choose "Extract Here"
After it extracts, open the newly created folder >> **eclipse**

Them run the Eclipse executable file from within the eclipse folder

---

### Post by devarshi on 2011-11-14
ohk ...thanks now..i got the solution exact ..one here...

[http://colinrrobinson.com/technology/install-eclipse-ubuntu/](http://colinrrobinson.com/technology/install-eclipse-ubuntu/)

i installed it..and it worked fine..but now..another problem exist..for me



Now another PROBLEM 

whenever i try to open eclipse here is the error that i get:

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/opt/eclipse/jre/bin/java
java in your current PATH   


now..i have Java.bin file downloaded on my pc ..and i have installed it on my pc as well ...

using : 
chmod +x java.bin 
 
./java.bin


it showed license agremennt...i accepted it..and i installed it on my pc...


when i try to test the " javac" on my terminal ..it shows following msg 

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>


now should i download all these pacakges on my pc again ?? :( help me...plz

---

