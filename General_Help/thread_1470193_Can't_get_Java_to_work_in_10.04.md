---
title: "Can't get Java to work in 10.04"
date: 2010-05-02
forum: General Help
---

### Post by koekjestrommel on 2010-05-02
I tried

"
**sudo aptitude install gsfonts gsfonts-x11 flashplugin-nonfree**
"

and "
[B]Get Java Installation Help Now   	

Note: The instructions below are for installing Java 6. If you're-installing another version, make sure you change the version number appropriately when you type the commands at the terminal.
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

   6. Verify that the jre1.6.0_<version> sub-directory is listed under the current directory. Type:
      ls


   1. Create a symbolic link to the libjavaplugin.so file in the browser plugins directory
          * Go to the plugins sub-directory under the Firefox installation directory
            cd <Firefox installation directory>/plugins

          * Create the symbolic link
            ln -s <Java installation directory>/plugin/i386/
            ns7/libjavaplugin_oji.so [/B]

And I installed openJDK, but it still doesn't seem to work, and I also restarted my browser. It also doesn't show any java stuff in the plugin menu in firefox :S

help please :(

---

### Post by darolu on 2010-05-02
```
$ sudo apt-get install ubuntu-restricted-extras
```
This package install (among other things like flashplugin) java.

---

### Post by koekjestrommel on 2010-05-02
Downloading now, will keep you updated.

In the mean time I tried this one

**sudo apt-get install openjdk-6-jre icedtea6-plugin**
Atleast it didn't show that i didn't have Java installed, but it didn't work either ;s

---

### Post by Autodave on 2010-05-02
> **darolu said:**
> ```
$ sudo apt-get install ubuntu-restricted-extras
```This package install (among other things like flashplugin) java.


Thank you!  I just did the same thing as the other user with the same results. :-(  So, I figured I would search the forums like I should have done to start with!

---

### Post by koekjestrommel on 2010-05-02
Worked here too, don't know wheter it was the update or iced thea though :P


But thanks a lot!

---

### Post by Autodave on 2010-05-02
> **darolu said:**
> ```
$ sudo apt-get install ubuntu-restricted-extras
```This package install (among other things like flashplugin) java.

Hmmmm.....did that and all kinds of stuff scrolled by, but my Java still isn't working......

---

### Post by Autodave on 2010-05-02
Sigh....must be getting old.  I rebooted and it works fine now.  Thanks!

---

### Post by koekjestrommel on 2010-05-02
I think this is it, i'm not sure though

sudo aptitude install gsfonts gsfonts-x11 flashplugin-nonfree
sudo apt-get install openjdk-6-jre icedtea6-plugin
sudo apt-get install ubuntu-restricted-extras

---

### Post by darolu on 2010-05-02
> Hmmmm.....did that and all kinds of stuff scrolled by, but my Java still isn't working......
That's all I had to install to get java working (I think); the problem with the instructions posted in the first post of the thread is they are for a different distro that works different than Ubuntu, we use .deb packages while SuSE uses .rpm's even when you can use tools like "Alien" to transform a rpm to deb, it's not recommended, specially when we have the same packages ready in our own repositories.

The easiest and safer way to install what you need is using Synaptic, "System - Administration - Synaptic package manager"; search for Java there, I'm sure you'll find what you need there. I'm attaching an image with the packages I have installed under the name "java", everything works fine for me (you won't be needing all of them of course, it is just an example).

[IMG]http://i42.tinypic.com/34rfxw2.png[/IMG]

---

### Post by scouser73 on 2010-05-02
To install the latest version of Java, please follow the instructions on this website: [[COLOR="Red"]**Easy Linux Tips Project: Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by darolu on 2010-05-02
> **Autodave said:**
> Sigh....must be getting old.  I rebooted and it works fine now.  Thanks!

I'm glad it worked for you, would you mind changing the tag of your thread to [SOLVED]? so other users can use it as reference when having the same issue.

---

### Post by koekjestrommel on 2010-05-02
Done :)

---

### Post by Autodave on 2010-05-02
> **darolu said:**
> I'm glad it worked for you, would you mind changing the tag of your thread to [SOLVED]? so other users can use it as reference when having the same issue.


Hmmm....I didn't start the thread, so I don't believe that I can do that.  If I am in error, tell me how to do it and I will. :-)

---

