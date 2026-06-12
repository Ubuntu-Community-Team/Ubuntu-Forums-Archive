---
title: "cant run *.sh"
date: 2010-01-28
forum: General Help
---

### Post by mikulopm on 2010-01-28
hi

i have this problem:

i want to run COWStarter.sh but nothing happens

in error.log i have: 
```
/home/mikulopm/COW-Client/COWStarter-debug.sh: line 2: java: command not found
```

when i write: ```
java -version
``` i get this:
```
mikulopm@mikulopm-laptop:~$ java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
java: command not found

```

but i have installed both - openJDK and SUNjava (even in ubuntu software center its checked as installed)

and i tryed this:

```
mikulopm@mikulopm-laptop:~$ sudo update-alternatives --config java
[sudo] password for mikulopm: 
Existuje 2 možností alternatívy java (poskytujúcej /usr/bin/java).

  Výber       Cesta                                     Priorita   Stav
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      automatický režim
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manuálny režim
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manuálny režim

Stla&#269;ením klávesu Enter ponecháte predvolenú možnos&#357;
[*], inak zadajte &#269;íslo výberu: 2
update-alternatives: upozornenie: forcing reinstallation of alternative /usr/lib/jvm/java-6-sun/jre/bin/java because link group java is broken.
update-alternatives: upozornenie: nenahrádza sa /usr/bin/java odkazom.

```(well, some of it is in slovak)

any suggestion, how to make it work?

thanks in advance

btw, i use ubuntu 9.10, i am quite new in ubuntu, without any codeing-skills... i google (or search on ubuntuforums) what i can, but i dont understand everything very good, so i would appreciate any help :) thanks again

---

### Post by Leppie on 2010-01-28
could you post the output of the following command:
```
dpkg -l | grep java
```

---

### Post by john newbuntu on 2010-01-29
[FONT=Verdana]In your home directory (/home/mikulopm) , there is a file called .bashrc .  Add the following lines to the file (If the file does not exist, create one):

[/FONT]```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin

```[FONT=Verdana]
[/FONT]
Then close the terminal and open another one.  Then try your *.sh command.

---

### Post by mikulopm on 2010-01-30
> **Leppie said:**
> could you post the output of the following command:
```
dpkg -l | grep java
```


thanks for response :)

this is it:
```

mikulopm@mikulopm-laptop:~$ dpkg -l | grep java
ii  ca-certificates-java                 20090928                                   Common CA certificates (JKS keystore)
ii  java-common                          0.30ubuntu5                                Base of all Java packages
ii  java-wrappers                        0.1.15                                     wrappers for java executables
ii  libaccess-bridge-java                1.26.2-1ubuntu1                            Java Access Bridge for GNOME
ii  libaccess-bridge-java-jni            1.26.2-1ubuntu1                            Java Access Bridge for GNOME (jni bindings)
ii  libhiglayout-java                    1.0-4                                      An easy-to-use layout manager for Java
ii  libjline-java                        0.9.94-5~ubuntu1                           Java library for handling console input
ii  libwoodstox-java                     1:3.9.2.dfsg-1ubuntu1                      a high-performance XML processor
ii  sun-java6-bin                        6-15-1                                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jdk                        6-15-1                                     Sun Java(TM) Development Kit (JDK) 6
ii  sun-java6-jre                        6-15-1                                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-plugin                     6-15-1                                     The Java(TM) Plug-in, Java SE 6
ii  tzdata-java                          2009u-0ubuntu0.9.10                        time zone and daylight-saving time data for 
mikulopm@mikulopm-laptop:~$ 
```

---

### Post by mikulopm on 2010-01-30
> **john newbuntu said:**
> [FONT=Verdana]In your home directory (/home/mikulopm) , there is a file called .bashrc .  Add the following lines to the file (If the file does not exist, create one):

[/FONT]```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin

```[FONT=Verdana]
[/FONT]
Then close the terminal and open another one.  Then try your *.sh command.

well, i tryed it, but nothing changed...

btw, i opened it with gedit and a i added it in gedit... was that what you meant? (i am a linux beginer, so i ask to be sure ;-) )

thanks for reply btw :)

---

### Post by tom.swartz07 on 2010-01-30
> **mikulopm said:**
> well, i tryed it, but nothing changed...

btw, i opened it with gedit and a i added it in gedit... was that what you meant? (i am a linux beginer, so i ask to be sure ;-) )

thanks for reply btw :)

Personally, I found that the version of java from the repos is really out of date- hit the link in my signature to install it from the official Java site.

That might clear up any problems

---

### Post by Leppie on 2010-01-30
i'm not sure, but the fact that you have the sun jre installed and yet the java command cannot be found sounds a bit like something in your java runtime environment setup isn't correct. maybe you could try re-installing it?

---

### Post by pbrane on 2010-01-30
having two java environments installed *should* be okay. You might need to run **update-alternatives --set** to set the one you want as default.

---

### Post by Leppie on 2010-01-30
> **pbrane said:**
> having two java environments installed *should* be okay. You might need to run **update-alternatives --set** to set the one you want as default.
not sure that would work, as the "java" command doesn't seem to be recognized...

independently from the version installed, "java -version" should get an output (i have openjdk installed and get an output with that command).

---

### Post by mikulopm on 2010-02-01
> **tom.swartz07 said:**
> Personally, I found that the version of java from the repos is really out of date- hit the link in my signature to install it from the official Java site.

That might clear up any problems

well, i reinstalled it using your list... i removed old version of sunjava, i removed openjdk, i downloaded newest sunjava, installed it...

but at 9. point of your list:
```

root@mikulopm-laptop:/opt/java/32# sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_18/bin/java" 1
update-alternatives: upozornenie: forcing reinstallation of alternative /opt/java/32/jre1.6.0_18/bin/java because link group java is broken.
update-alternatives: upozornenie: nenahrádza sa /usr/bin/java odkazom (translation: not replaced by new link /usr/bin/java). 
root@mikulopm-laptop:/opt/java/32# sudo update-alternatives --set java /opt/java/32/jre1.6.0_18/bin/java
update-alternatives: upozornenie: forcing reinstallation of alternative /opt/java/32/jre1.6.0_18/bin/java because link group java is broken.
update-alternatives: upozornenie: nenahrádza sa /usr/bin/java odkazom.
root@mikulopm-laptop:/opt/java/32# java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
 * kaffe
Try: apt-get install <selected package>
java: command not found
root@mikulopm-laptop:/opt/java/32# 
```

i dont know what else to do...

---

### Post by Leppie on 2010-02-01
what does this mean:
> nenahrádza sa /usr/bin/java odkazom

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> what does this mean:

translation: not replaced by new link /usr/bin/java

---

### Post by Leppie on 2010-02-01
you could try to complete remove all java packages with their configuration files altogether and then re-install the packages:
```
dpkg --get-selections | grep java | gawk '{ print $1 }' > ~/javapackages.txt
sudo apt-get purge $(cat ~/javapackages.txt)
sudo apt-get install $(cat ~/javapackages.txt)
```

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> you could try to complete remove all java packages with their configuration files altogether and then re-install the packages:
```
dpkg --get-selections | grep java | gawk '{ print $1 }' > ~/javapackages.txt
sudo apt-get purge $(cat ~/javapackages.txt)
sudo apt-get install $(cat ~/javapackages.txt)
```


well, i did it... i removed it, installed sunjava 1.6.0_15

then i installed latest 1.6.0_18 ( with help [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10) )

now:
```
mikulopm@mikulopm-laptop:~$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)
```

it doesnt detect the newest one as the primer one...

```
mikulopm@mikulopm-laptop:~$ sudo update-alternatives --config java
Existuje 2 možností alternatívy java (poskytujúcej /usr/bin/java).

  Výber       Cesta                                 Priorita   Stav
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-sun/jre/bin/java   63        automatický režim
* 1            /opt/java/32/jre1.6.0_18/bin/java      1         manuálny režim
  2            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manuálny režim

Stla&#269;ením klávesu Enter ponecháte predvolenú možnos&#357;
[*], inak zadajte &#269;íslo výberu: 1
update-alternatives: upozornenie: forcing reinstallation of alternative /opt/java/32/jre1.6.0_18/bin/java because link group java is broken.
update-alternatives: upozornenie: nenahrádza sa /usr/bin/java odkazom.

```

so still the same problem and my *.sh file still doesnt work

---

### Post by Leppie on 2010-02-01
> **mikulopm said:**
> well, i did it... i removed it, installed sunjava 1.6.0_15
what did you do exactly? did you only remove sunjava?
you obviously did not remove everything, as you still have 3 java versions installed (of which 2 are the same sun java install), so i bet the configuration files have not been deleted at all either. just removing the package does not remove its configuration files at the same time.

---

### Post by mikulopm on 2010-02-01
i used this code:

```
dpkg --get-selections | grep java | gawk '{ print $1 }' > ~/javapackages.txt
sudo apt-get purge $(cat ~/javapackages.txt)
sudo apt-get install $(cat ~/javapackages.txt)
```

then i istalled newest version... i dont know how to uninstall everything, i thought this code above will uninstall everything...

---

### Post by mikulopm on 2010-02-01
i removed everything again

```
dpkg --get-selections | grep java | gawk '{ print $1 }' > ~/javapackages.txt
sudo apt-get purge $(cat ~/javapackages.txt)
```then i installed again newest sunjava

now:

```
mikulopm@mikulopm-laptop:/opt/java/32$ sudo update-alternatives --config java
V skupine odkazov existuje iba jedna alternatíva java: /opt/java/32/jre1.6.0_18/bin/java
Niet &#269;o konfigurova&#357;.
update-alternatives: upozornenie: forcing reinstallation of alternative /opt/java/32/jre1.6.0_18/bin/java because link group java is broken.
update-alternatives: upozornenie: nenahrádza sa /usr/bin/java odkazom.
```
(translation: In th group of links ther is only one alternativ java: /opt/java/32/jre1.6.0_18/bin/java
There is nothing to configure.
update-alternatives: warning: forcing reinstallation of alternative /opt/java/32/jre1.6.0_18/bin/java because link group java is broken.
update-alternatives: warning: It will not be replaced by /usr/bin/java link.)

```
mikulopm@mikulopm-laptop:/opt/java/32$ java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
java: command not found
```

so there is installed only one version, but its not detecting it...

---

### Post by Leppie on 2010-02-01
> **mikulopm said:**
> then i installed again newest sunjava
did sun java install to opt by default? it wasn't a .deb package you installed?

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> did sun java install to opt by default? it wasn't a .deb package you installed?

i used this help [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

so it was installed manualy by my choice (actually by the choice in help manual)...
it was .bin file...

---

### Post by Leppie on 2010-02-01
> **mikulopm said:**
> i used this help [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

so it was installed manualy by my choice (actually by the choice in help manual)...
it was .bin file...
have you tried to install through the repos after completely removing it?

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> have you tried to install through the repos after completely removing it?

yes, thats the 1.6.0_15 :

[http://ubuntuforums.org/showpost.php?p=8757478&postcount=14](http://ubuntuforums.org/showpost.php?p=8757478&postcount=14)

---

### Post by Leppie on 2010-02-01
> **mikulopm said:**
> yes, thats the 1.6.0_15 :

[http://ubuntuforums.org/showpost.php?p=8757478&postcount=14](http://ubuntuforums.org/showpost.php?p=8757478&postcount=14)
well, that's not quite the same i'd say since you installed the latest build (which didn't come from the repos) immediately after that...

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> well, that's not quite the same i'd say since you installed the latest build (which didn't come from the repos) immediately after that...

of course i installed after removing everything first sunjava from repos, i tryed if its working, but i couldnt run *.sh, so after that i installed latest build and its still not working...

in err.log file i have this: 
/home/mikulopm/COW-Client/COWStarter-debug.sh: line 2: java: command not found

---

### Post by Leppie on 2010-02-01
could you post the script?

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> could you post the script?

```
#!/bin/bash
java -Dfile.encoding=Cp1252 -Xmx256m -cp . de.brettspielwelt.client.base.Starter >& /dev/null
```

---

### Post by Leppie on 2010-02-01
> **mikulopm said:**
> ```
#!/bin/bash
java -Dfile.encoding=Cp1252 -Xmx256m -cp . de.brettspielwelt.client.base.Starter >& /dev/null
```
try to point the java command to the exact location of the executable:
```
/usr/bin/java -Dfile.encoding=Cp1252 -Xmx256m -cp .  de.brettspielwelt.client.base.Starter >& /dev/null
```

---

### Post by mikulopm on 2010-02-01
nothing happend

---

### Post by Leppie on 2010-02-01
i'm sorry, i've never used this...
have you tried contacting the people from that site?

---

### Post by mikulopm on 2010-02-01
> **Leppie said:**
> i'm sorry, i've never used this...
have you tried contacting the people from that site?

not yet, but i certainly will :)

thank you very much for your time, i appreciate it...
if i will find out something i will post it here....

thanks again

---

### Post by Leppie on 2010-02-01
> **mikulopm said:**
> not yet, but i certainly will :)

thank you very much for your time, i appreciate it...
if i will find out something i will post it here....

thanks again
you're welcome and again, sorry i've not been able to help you solve this issue so far...
keep us posted ;)

---

