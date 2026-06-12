---
title: "Java version 6 update 29"
date: 2011-10-25
forum: General Help
---

### Post by mining3 on 2011-10-25
p { margin-bottom: 0.21cm;Java version 6 update 29 – Ubuntu 11.04 

 x@x-desktop:~$ chmod a+x jre-6u<version>-linux-i586.bin
 bash: version: No such file or directory
 x@x-desktop:~$  
 

 I am a beginner and the Oracle instructions don't seem to work I need for applets on Quote Media streamer. Radio buttons freeze when I go to full screen, their teckies say it is java. Can you add this to Synaptic Package Manger?


Where do I down load to? I click on down load or do I open with some thing ???

 

 To install the Linux (self-extracting) file
 Follow these instructions:
 

    1. Change the permission of the file you downloaded to be executable. Type:
       chmod a+x jre-6u<version>-linux-i586.bin
    2. Verify that you have permission to execute the file. Type:
       ls -l
 

 Make sure the installation file has executable permission
 

    3. Change to the directory in which you want to install. Type:
       cd <directory path name>
       For example, to install the software in the /usr/java/ directory, Type:
       cd /usr/java/
 

       Note about root access: To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions.
 

    4. Run the self-extracting binary Type:
       ./jre-6u<version>-linux-i586.bin
 

       The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.
 

    5. Java is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_<version> directory. When the installation has completed, you will see the word Done.
 

 The installation completes

---

### Post by oldtimer7777 on 2011-10-25
You don't need to install it from the web site, it is easier to install it from a PPA instead.

It is about 1/5th the way down this list:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **mining3 said:**
> p { margin-bottom: 0.21cm;Java version 6 update 29 – Ubuntu 11.04 

 x@x-desktop:~$ chmod a+x jre-6u<version>-linux-i586.bin
 bash: version: No such file or directory
 x@x-desktop:~$  
 

 I am a beginner and the Oracle instructions don't seem to work I need for applets on Quote Media streamer. Radio buttons freeze when I go to full screen, their teckies say it is java. Can you add this to Synaptic Package Manger?


Where do I down load to? I click on down load or do I open with some thing ???

 

 To install the Linux (self-extracting) file
 Follow these instructions:
 

    1. Change the permission of the file you downloaded to be executable. Type:
       chmod a+x jre-6u<version>-linux-i586.bin
    2. Verify that you have permission to execute the file. Type:
       ls -l
 

 Make sure the installation file has executable permission
 

    3. Change to the directory in which you want to install. Type:
       cd <directory path name>
       For example, to install the software in the /usr/java/ directory, Type:
       cd /usr/java/
 

       Note about root access: To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions.
 

    4. Run the self-extracting binary Type:
       ./jre-6u<version>-linux-i586.bin
 

       The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.
 

    5. Java is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_<version> directory. When the installation has completed, you will see the word Done.
 

 The installation completes

---

