---
title: "Cannot run batch script [newbie]"
date: 2009-12-12
forum: General Help
---

### Post by jon80 on 2009-12-12
See command log below, Any ideas?  Is this some bug?

administrator@elsueno:~/Desktop$ /java_ee_sdk-5_08-jdk-6u17-linux.bin
bash: /java_ee_sdk-5_08-jdk-6u17-linux.bin: No such file or directory
administrator@elsueno:~/Desktop$ ls -latr
total 164236
-rw-r--r--  1 administrator administrator      5453 2009-12-10 06:11 trash.desktop
-rw-r--r--  1 administrator administrator       156 2009-12-10 06:11 Home.desktop
-rw-r--r--  1 administrator administrator       113 2009-12-10 06:11 .directory
drwxr-xr-x 17 administrator administrator      4096 2009-12-12 07:42 ..
**-rwxr-xr-x**  1 administrator administrator 167978968 2009-12-12 11:55 **java_ee_sdk-5_08-jdk-6u17-linux.bin**
drwxr-xr-x  2 administrator administrator      4096 2009-12-12 11:55 .
administrator@elsueno:~/Desktop$ .java_ee_sdk-5_08-jdk-6u17-linux.bin
bash: .java_ee_sdk-5_08-jdk-6u17-linux.bin: command not found
administrator@elsueno:~/Desktop$ java_ee_sdk-5_08-jdk-6u17-linux.bin
bash: java_ee_sdk-5_08-jdk-6u17-linux.bin: command not found
administrator@elsueno:~/Desktop$

....

drwxr-xr-x 4 root root 4096 2009-12-12 13:44 ..
**-rwxr-xr-x 1 root root    0 2009-12-12 13:44 java_ee_sdk-5_08-jdk-6u17-linux-ml.bin**
drwxr-xr-x 2 root root 4096 2009-12-12 13:44 .
administrator@elsueno:/home/setups$** ./java_ee_sdk-5_08-jdk-6u17-linux-ml.bin**
administrator@elsueno:/home/setups$ java_ee_sdk-5_08-jdk-6u17-linux-ml.bin
bash: java_ee_sdk-5_08-jdk-6u17-linux-ml.bin: command not found
administrator@elsueno:/home/setups$ .java_ee_sdk-5_08-jdk-6u17-linux-ml.bin
bash: .java_ee_sdk-5_08-jdk-6u17-linux-ml.bin: command not found
administrator@elsueno:/home/setups$

-rwxr-xr-x  1 root   root           0 2009-12-12 13:49 java_ee_sdk-5_08-jdk-6u17-linux-ml.bin
drwxr-xr-x  2 root   root       36864 2009-12-12 13:49 .
administrator@elsueno:/usr/bin$ ./java_ee_sdk-5_08-jdk-6u17-linux-ml.bin
administrator@elsueno:/usr/bin$ ./java_ee_sdk-5_08-jdk-6u17-linux-ml.bin
administrator@elsueno:/usr/bin$ ./java_ee_sdk-5_08-jdk-6u17-linux-ml.bin
administrator@elsueno:/usr/bin$ echo $PATH
**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games**
administrator@elsueno:/usr/bin$ PWD
bash: PWD: command not found
administrator@elsueno:/usr/bin$




Download location: [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter)

Related links (attempted resolutions)
1. Command not found error ([http://www.cyberciti.biz/faq/linux-unix-command-not-found-error-and-how-to-get-rid-of-it/](http://www.cyberciti.biz/faq/linux-unix-command-not-found-error-and-how-to-get-rid-of-it/)) -

---

### Post by slakkie on 2009-12-12
try running bash ./the-java-thing

---

### Post by nuras on 2010-01-03
When i run 
./java_ee_sdk-5_08-jdk-6u17-linux.bin 

i get this error message -

./java_ee_sdk-5_08-jdk-6u17-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
I am a newbie to Linux as such - any help is greatly appreciated.

---

### Post by john newbuntu on 2010-01-03
The install appears to be looking for a specific standard C++ library that is probably not on your machine.  Open Synaptic package manager and search for something like "libstd" and see if you can find a package that you can install.  Then re-run your command.

---

### Post by nuras on 2010-01-03
Thanks John for your prompt reply. I did a quick check through synaptic and saw that i haev libstdc++6-4.4-dev and libstdc++6 already installed. I dont see anything with version 5 in it. Do i have to uninstall this  and if so which version should i install ? version 5 ? Would this mess up any of my other applications ? If you could you please advise me on th ebest steps to do this ?

Sorry i should haev given a pic of my system before letting you know of the issue -
I haev a Dual boot Vista / Karmic on a 32 bit Intell Chip with 4 GB RAM

---

### Post by john newbuntu on 2010-01-03
Since they have specifically linked it with the .so.5 version of the STL, I would recommend downloading the same and using it.  So, go ahead and download libstd 5.

---

