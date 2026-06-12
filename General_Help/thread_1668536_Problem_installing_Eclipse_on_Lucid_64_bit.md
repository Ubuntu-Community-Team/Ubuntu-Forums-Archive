---
title: "Problem installing Eclipse on Lucid 64 bit"
date: 2011-01-16
forum: General Help
---

### Post by dayv2005 on 2011-01-16
I am running Ubuntu Lucid Lynx. I followed this tutorial to get java/tomcat/eclipse installed - [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html) 

I did everything exactly. I downloaded jdk-6u23-linux-x64.bin for the jdk. I downloaded apache-tomcat-6.0.30.tar.gz for tomcat. I downloaded wtp-all-in-one-sdk-1.0-linux-gtk.tar.gz for eclipse. I think this might be an issue towards 64 bit version but unsure. Could someone help me out with this? 

When I run sudo /opt/eclipse/eclipse -clean i get an error popping up and saying... 

```

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
^C
david@david-desktop:~$ /opt/eclipse/eclipse -clean
bash: /opt/eclipse/eclipse: Permission denied
david@david-desktop:~$ sudo /opt/eclipse/eclipse -clean
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```

---

### Post by GregBrannon on 2011-01-16
This is how I recommend you install Eclipse on any Linux platform:

Ensure the JDK is installed (it includes the JRE).  The internet is littered with How-Tos to accomplish this in Ubuntu. 

1.  Download the desired version of Eclipse from eclipse.org: the latest release (Helios), 64-bit, 32-bit, Java, JEE, whatever flavor needed,

2.  Extract the downloaded archive into a directory of your choosing; recommend you choose one off your home folder, and

3.  Build a Link to Application to the Eclipse executable in the folder you just created and extracted the Eclipse archive to, updating the icon to the one that is also in that directory.

And it should work without fail.

I don't know what all of that other stuff is you're trying to do, but I would start by getting Eclipse up and running and then adding capability as you need it.

Others will tell you to just install it from the Software Center, but I know there are reasons for doing it manually.  However, you shouldn't need to worry about compiling anything or satisfying dependencies.  You decide.

Good luck.

---

