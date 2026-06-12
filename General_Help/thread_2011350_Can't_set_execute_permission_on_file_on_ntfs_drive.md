---
title: "Can't set execute permission on file on ntfs drive"
date: 2012-06-27
forum: General Help
---

### Post by ubnewbie2 on 2012-06-27
I have installed 12.04 in a partition alongside Windows 7.  When I access the Windows 7 NTFS partition in the file manager, and go right-click>properties>permissions on a java .jar file, it won't let me tick it as executable.  The tick appears, then disappears straight away.

---

### Post by David Andersson on 2012-06-27
> **ubnewbie2 said:**
> When I access the Windows 7 NTFS partition in the file manager, and go right-click>properties>permissions on a java .jar file, it won't let me tick it as executable.

That is reasonable. NTFS does not have the "executable" permission bit. However, all files should be interpredet as if they were executable, so scripts and such could be run. (Unless the file system is mounted with noexec.)

---

### Post by ubnewbie2 on 2012-06-27
> **David Andersson said:**
> That is reasonable. NTFS does not have the "executable" permission bit. However, all files should be interpredet as if they were executable, so scripts and such could be run. (Unless the file system is mounted with noexec.)

The file manager does not show them as executable, and I could not open the .jar file and run it with java.

---

### Post by Morbius1 on 2012-06-27
A *.jar file is not an executable entity so it doesn't have to have it's execute bit set.

There's 2 ways to fix this:

** Open a terminal and run:
```
java -jar /path/to/jar/file
```** Or, for a more permanent fix:
Run nautilus as root and go to the following folder:
```
gksu nautilus /usr/share/applications
```Right Click "OpenJDK Java 6 Runtime" and choose Properties.

In the Command line you will see something like this - It may be different on your system:
> [COLOR=Blue]**cautious-launcher %f**[/COLOR] /usr/bin/java -jarRemove the "cautious-launcher %f" part so that it looks like this:
> /usr/bin/java -jar
It's cautious-launcher that checks to see if something is executable - it's not a requirement of java and both methods above circumvent it's use.

[COLOR=Blue]* There are other ways around this dilemma:*[/COLOR]

** Mount the Win partition in fstab and make all files executable.
** Install the file manager Thunar, right click any jar file, select Open With, Open With Other Application, Use a Custom Command, and enter:
```
java -jar
```[COLOR=Blue]**EDIT**[/COLOR]: Just to be clear. Creating a custom command in Thunar doesn't mean you then need Thunar to run it. It will run in Nautilus.[I]

Note: Some of you old timers will probably remember the "use a custom command" from the olden tymes of Gnome2. Gnome3 removed that function because it was deemed a feature and thus classified as a bug.
[/I]

---

### Post by nipunshakya on 2012-06-27
Copy the jar file to your /home partition and try to set it as executable... might work out coz files NTFS cannot be set to be executed as a program...

---

### Post by ubnewbie2 on 2012-06-27
> **Morbius1 said:**
> 

Run nautilus as root and go to the following folder:
```
gksu nautilus /usr/share/applications
```Right Click "OpenJDK Java 6 Runtime" and choose Properties.

In the Command line you will see something like this - It may be different on your system:
Remove the "cautious-launcher %f" part so that it looks like this:
It's cautious-launcher that checks to see if something is executable - it's not a requirement of java and both methods above circumvent it's use.


Thanks, this fixed the problem. =D>

---

