---
title: "Which java do I have? Oracle or the open one ?"
date: 2010-10-23
forum: General Help
---

### Post by user1001 on 2010-10-23
Hi how do I check which one I have and how do I install the latest one of the Oracle version ?
because java applets on my browser doesn't seem to run :S

thanks.

---

### Post by gvscherman on 2010-10-23
to find out which java you are using open terminal and type in   java -version. Do you have the correct plugin installed in your browser?

---

### Post by user1001 on 2010-10-24
> **gvscherman said:**
> to find out which java you are using open terminal and type in   java -version. Do you have the correct plugin installed in your browser?

I think beans means number of posts, so welcome to Ubuntuforums.org

it looks like I have 

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9) (6b20-1.9-0ubuntu1)
OpenJDK Client VM (build 17.0-b16, mixed mode, sharing)

although I uninstalled it yesterday :S

do you know a way to install the proper Java ??? and the plugin for chrome/ium or Firefox...

thanks.

---

### Post by howefield on 2010-10-24
> **user1001 said:**
> do you know a way to install the proper Java ??? and the plugin for chrome/ium or Firefox...

If you are using 10.4 or later, you need to enable the Partner repository and install sun-java6-plugin sun-java6-fonts and sun-java6-jre.

Have a read here..

```
https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun Java moved to the Partner repository
```

---

### Post by chilisastry on 2010-10-26
I'm having a problem with Java Web Start in Firefox 3.6.

I added the Canonical Partner repository in System > Administration > Software Sources.  Then installed Oracle/Sun Java JRE plugin using System > Administration > Synaptic Package Manager.  And finally, uninstalled IcedTea, which does not run Power E*Trade Pro.

Now when I try to run Power E*Trade Pro from a Firefox at a E*Trade.com web-page, I get a message stating there is no association for this application, to set one up in Preferences.

In Firefox, Edit > Preferences > Applications, there is an entry for Java Web Start application, and it is set at Use Sun Java 6 Web Start (default).  [Used to be use IcedTea before I uninstalled it.]  For some reason Firefox cannot find this plugin.  I changed the entry to Always Ask.

Now, as expected, Firefox asks me for the application to use with the E*Trade Pro Web Start application (.jnlp).  I choose Sun Java 6 Web Start from the drop-down box and continue.  Power E*Trade Pro starts running - perfect.

The question is: Why can't Firefox find Sun Java 6 Web Start automatically?

---

