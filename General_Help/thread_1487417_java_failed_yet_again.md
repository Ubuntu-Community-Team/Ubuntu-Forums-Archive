---
title: "java failed yet again"
date: 2010-05-19
forum: General Help
---

### Post by Twiztid Anthrax on 2010-05-19
Hey im using "Xubuntu" on a bit dell laptop, i have installed everything i see to do with java in the software center and in the synaptic package manager and no java sites work sill i have downloaded every pacage from adobe for linux and after extracting them to my desktop and clicking on them it dose nothing ive tryed a few lines in the terminal but always have a destination error

---

### Post by BslBryan on 2010-05-19
Is it flash that doesn't work, or java?

If it's java, it's a real pain. Here's how to do it. Download the java self-extracting binary for your architecture from [here.]("http://java.com/en/download/manual.jsp#Linux")  It will either be the second or third link, depending on whether you have 32 or 64 bit Ubuntu installed.  

To install the Linux (self-extracting) file
Follow these instructions:
Open up a terminal, and change the directory to where you installed your file.  So, if you installed it in /home/username/Downloads, you would type:
```
cd Downloads
```

Next, change the permission of the file you downloaded to be executable. Type:
```
chmod a+x jre-6u<version>-linux-i586.bin
```
Verify that you have permission to execute the file. Type:
```
ls -l
```
 
Change to the directory in which you want to install. Type:
```
cd <directory path name>
```
For example, to install the software in the /usr/java/ directory, Type:
```
cd /usr/java/
```

**Note about root access**: To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions, or use the sudo command.
Run the self-extracting binary. Type:
```
./jre-6u<version>-linux-i586.bin

```
The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.

Java is installed into its own directory. For example, /usr/java/jre1.6.0_<version>. When the installation has completed, you will see the word Done.
 

Verify that the jre1.6.0_<version> sub-directory is listed under the current directory. Type:
```
ls
```
 


**Enable and Configure**

Firefox or Mozilla
Create a symbolic link to the libjavaplugin.so file in the browser plugins directory.
Go to the plugins sub-directory under the Firefox installation directory.
```
cd <Firefox installation directory>/plugins

```
Create the symbolic link 
```
ln -s <Java installation directory>/plugin/i386/ns7/libjavaplugin_oji.so 
```

(You may see the path say ns7-gcc29, simply use that instead if you do.)

In Firefox, you can enable the Java Console menu item in the Tools menu. Change directories to the Firefox extensions directory, then unzip ffjcext.zip there.
```
 cd /usr/lib/firefox-1.4/extensions 
unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip
```
**Example**
If Firefox is installed at this directory:
**/usr/lib/firefox-1.4/**
And if the Java is installed at this directory:
**/usr/java/jre1.6.0**
Then type in the terminal window to go to the browser plug-in directory:
```
cd /usr/lib/firefox-1.4/plugins
```
Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
```
ln -s /usr/java/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so 
```

Start the Firefox browser, or restart it if it is already up. 

In Firefox, type ```
about:plugins
``` in the Location bar to confirm that the Java Plugin is loaded. If the version is Firefox 1.5 or later, click the Tools menu to confirm that Java Console is there.


Hope it helps.

---

### Post by Twiztid Anthrax on 2010-05-19
when trying to do the cd downloads line it says no such directiory so i tryed cd desktop and had the same problem, i tryed skipping the first step and moving to the second with the same error, and its java btw

---

### Post by BslBryan on 2010-05-19
Case *does* matter in Linux and Unix.  So, first, you need to know where you downloaded it, and second, you have to remind your self that "cd downloads" is not "cd Downloads". :)

---

### Post by Twiztid Anthrax on 2010-05-19
heres a screen shot of what it dose to "cd downloads" 

[http://tinypic.com/r/qox8i1/6](http://tinypic.com/r/qox8i1/6)

---

### Post by BslBryan on 2010-05-19
Type in ```
su (your user name)
```

Then type 
```
cd Downloads
```

---

### Post by Twiztid Anthrax on 2010-05-19
welp i tryed it and it said i dont have permission, heh if i dident shave my head id be pullin my hair out ive been working on this for a week and cant figure out why it wont work, i wish ubuntu had a team viewer that worked as easy as windows did xD

---

### Post by dcstar on 2010-05-19
> **Twiztid Anthrax said:**
> Hey im using "Xubuntu" on a bit dell laptop, i have installed everything i see to do with java in the software center and in the synaptic package manager and no java sites work sill i have downloaded every pacage from adobe for linux and after extracting them to my desktop and clicking on them it dose nothing ive tryed a few lines in the terminal but always have a destination error

Icedtea is the standard Java packages that is installed by default in Ubuntu, if you want you can install the other JRE packages.

If you want to use these in a browser then you also have to install the relevant plugins.

---

