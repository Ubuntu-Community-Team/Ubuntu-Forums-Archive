---
title: "&quot;Set your JAVA_HOME, ANT_HOME and PATH&quot;; jdk is installed but not in /usr/local"
date: 2009-12-06
forum: General Help
---

### Post by johnyjj2 on 2009-12-06
Hello!

I've got still the problem ([http://ubuntuforums.org/showthread.php?t=1341005](http://ubuntuforums.org/showthread.php?t=1341005)). **I'd like to "Set your JAVA_HOME, ANT_HOME and PATH environment variables" as explained here [http://cmusphinx.sourceforge.net/sphinx4/#how_build](http://cmusphinx.sourceforge.net/sphinx4/#how_build) .**

In the directory /usr/local I've got directory ant but there is no directory jdk. It should be present because:

lib$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
mainaccount@mainaccount-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/lib$ sudo apt-get install ant
Reading package lists... Done
Building dependency tree
Reading state information... Done
ant is already the newest version.
The following packages were automatically installed and are no longer required:
linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
mainaccount@mainaccount-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/lib$

I cannot give the proper names here (below there are examplary values, I don't know what to choose exactly because I don't have any jdk in /usr/local):

export JAVA_HOME=/usr/local/jdk1.5.0_07
export ANT_HOME=/usr/local/ant
export PATH=$PATH:${JAVA_HOME}/bin:${ANT_HOME}/bin

because I cannot find this jdk directory in /usr/local.

The other command:

mainaccount@mainaccount-laptop:~$ echo -e "java=$JAVA_HOME \nant=$ANT_HOME \npath=$PATH"
java=
ant=
path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Greetings!

PS I thought it may be due to manually installing jdk. I thought installing jdk manually and from sudo apt-get install is the same but it looks like manual installation also requires setting paths. So can I do it in such a way that I would uninstall jdk and then use sudo apt-get install sun-java6-jdk so that it can set up the proper paths without need to set those manually? How to uninstall this jdk?

---

