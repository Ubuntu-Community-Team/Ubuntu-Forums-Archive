---
title: "Locating Java directory"
date: 2010-04-08
forum: General Help
---

### Post by driebel on 2010-04-08
I need to locate my Java installation directory.  Specifically, I am trying to follow the following directions:

"If you decide to use a different Java Runtime Environment than is provided by our own installers, or are running on a platform other than our standard installations (this, e.g., applies to Linux 64-bit machines), then you should use this 'generic' installation: Spitzer-pride18_0_1-generic.sh. First, obtain (or locate) your own local Java 1.5.x installation.  Then, click on the link here and save the program to disk. To make the program executable, type: chmod +x Spitzer-pride_18_0_1-generic.sh. Finally, to install it, type: ./Spitzer-pride_18_0_1-generic.sh. The installation script will ask you for the explicit path to your Java directory"

I am running a 64-bit version of Hardy.  I began my search by running: which java
which pointed me to a symbolic link, which pointed to another symbolic link, which pointed to /usr/lib/jvm/java-6-openjdk/jre/bin/java which is an executable.

Which directory in that chain is my Java directory?

Is there a reason to expect disaster given that I seem to have Java 6, and this is mentioning Java 1.5.x?

Thanks!

---

### Post by scouser73 on 2010-04-08
> **driebel said:**
> I need to locate my Java installation directory.  Specifically, I am trying to follow the following directions:

"If you decide to use a different Java Runtime Environment than is provided by our own installers, or are running on a platform other than our standard installations (this, e.g., applies to Linux 64-bit machines), then you should use this 'generic' installation: Spitzer-pride18_0_1-generic.sh. First, obtain (or locate) your own local Java 1.5.x installation.  Then, click on the link here and save the program to disk. To make the program executable, type: chmod +x Spitzer-pride_18_0_1-generic.sh. Finally, to install it, type: ./Spitzer-pride_18_0_1-generic.sh. The installation script will ask you for the explicit path to your Java directory"

I am running a 64-bit version of Hardy.  I began my search by running: which java
which pointed me to a symbolic link, which pointed to another symbolic link, which pointed to /usr/lib/jvm/java-6-openjdk/jre/bin/java which is an executable.

Which directory in that chain is my Java directory?

Is there a reason to expect disaster given that I seem to have Java 6, and this is mentioning Java 1.5.x?

Thanks!

Go to the Terminal and enter > **locate java**

---

### Post by JoelOl75 on 2010-04-09
Also try:

update-alternatives --list java

You can also set the java you want with the update-alternatives command which is the proper way as many different java's can be installed at the same time and the one in use is symlinked.  Just changing the symlink is kinda  a kludge on the the right way to set it.

---

### Post by driebel on 2010-04-12
Hmmm.  I've executed both of these suggestions, but I'm not sure how to interpret the results.  According to its man page, "locate" finds files by name, and sure enough, it found every file on my system with "java" in the name.  A list which overflowed the terminal's buffer.

update-alternatives gives a more reasonable list:
driebel@:~: update-alternatives --list java
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/bin/cacao
/usr/bin/gij-4.2
/usr/lib/jvm/java-6-sun/jre/bin/java

But again, I'm not clear what in this list constitutes the java directory.  Could you clarify?  Thanks,
Dave

---

