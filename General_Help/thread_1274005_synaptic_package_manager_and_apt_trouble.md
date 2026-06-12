---
title: "synaptic package manager and apt trouble"
date: 2009-09-24
forum: General Help
---

### Post by arj97 on 2009-09-24
[SIZE=2]whenever i try to update this occurs:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
///////////////////////////////////////////////////////////////////////////////
and when i do as prompted the following appears:-
///////////////////////////////////////////////////////////////////////////////
Setting up sun-java6-doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] ^Cdpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 sun-java6-doc
[/SIZE]///////////////////////////////////////////////////////////////////////////////////////
[SIZE=4]please help!!!!!!!!!!!!!!!!!!!!!!!!![/SIZE]

---

### Post by mthalis on 2009-09-24
Try this
> sudo dpkg --configure -a

---

### Post by zeroseven0183 on 2009-09-24
To install Sun Java 6 Runtime,
 1. click **Add/Remove** in **Applications**.
 2. be sure to select **All available applications** instead of **Canonical-maintained applications** in the Show drop-down box
 3. Type **Java** in the search box
 4. click the corresponding check box
 5. click **Apply Changes**, then
 6. enter your root password in the prompt

I guess that's the simplest method I know to install the application.

---

### Post by arj97 on 2009-09-24
[SIZE=5]no success with this one[/SIZE][SIZE=4]!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/SIZE]
[SIZE=5]please read the entire problem..............

[/SIZE]

---

### Post by mthalis on 2009-09-24
According to my knowledge, to install **sun-java6-doc ** you have to download java doc from sun web site and put that into temp folder after that you can install sun-java-doc. That's how i normally do.
 
what is the result of sudo dpkg --configure -a ?

---

### Post by arj97 on 2009-09-24
[SIZE=5]when i do as u told ,the following appears:[/SIZE]
[SIZE=2]Setting up sun-java6-doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] ^Cdpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 sun-java6-doc
[/SIZE]///////////////////////////////////////////////////////////////////////////////////////
[SIZE=4]please help!!!!!!!!!!!!!!!!!!!!!!!!!

i also tried to install it from add remove progs but no success!!!!!!

[SIZE=6][COLOR=SeaGreen]i hav tried to download jdk from sun and save it in temp and install it ,,,but no success!!!!!!!!!!!!!!!!!!!!!!!!
please guide [/COLOR][/SIZE]
[/SIZE]

---

### Post by mthalis on 2009-09-24
I'm confused, Do you want to install java, java Doc?
or 
Any error display in you're synaptic package manager?

---

### Post by blackened on 2009-09-24
Go to [http://java.sun.com/javase/downloads/]("http://java.sun.com/javase/downloads/").

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129573&d=1253774699[/IMG]

then

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129574&d=1253774699[/IMG]

then

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129575&d=1253774699[/IMG]

Make sure you download the file to the desktop. Then

```
sudo chown root:root ~/Desktop/jdk-6u10-docs.zip
```
```
sudo cp ~/Desktop/jdk-6u10-docs.zip /tmp
```
```
sudo dpkg --configure -a
```

---

### Post by Soul-Sing on 2009-09-24
[SIZE="7"]Maybe the above howto will help!!!!!!!
succes![/SIZE]

---

### Post by zeroseven0183 on 2009-09-27
I hope the original poster was able read this. It's so CLEAR

---

### Post by arj97 on 2009-09-30
[SIZE=6][COLOR=Purple]solved finally!!!!!!!!!!!!thanx alot!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/COLOR][/SIZE]

---

### Post by pytheia on 2009-11-23
thank you so much ,problem solved
very helpfull post

---

