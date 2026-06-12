---
title: "Help installing Jabref (java program)"
date: 2006-03-01
forum: General Help
---

### Post by Zyzzyva100 on 2006-03-01
Can somebody possibly help me install Jabref? It is a java based bibtex gui frontend that can parse medline/pubmed (which is the key to why I need it), and it will import endnote files (another key to why I need it).

I would love to be able to get this program installed on my laptop so that I can use it to help in writing my thesis. I already have it installed and working on my desktop, which is running gentoo. Since there was an ebuild for gentoo, installing it wasn't a problem.

All there seems to be otherwise for linux, is a .jar file, which I can't get to do anything. The sparse installation instructions are here: [http://jabref.sourceforge.net/documentation.php](http://jabref.sourceforge.net/documentation.php).
When I follow those, however, all I get once I try to run java -jar jabref.jar is an error saying that the file cannot be accessed (even when I have made it executable in the permissions).

I have never managed to have any luck installing a java program from a jar file before (I have tried with nih's imagej, but failed). Any help would be much appreciated.

---

### Post by Zyzzyva100 on 2006-03-07
Anybody have any ideas on this one?

---

### Post by cwf on 2006-03-09
Hi,

Download JabRef-2.0.1.jar at:

[PHP]http://prdownloads.sourceforge.net/jabref/JabRef-2.0.1.jar?download[/PHP]

Then to run it:

[1]  You go to the directory to which you downloaded the file.
[2]   type:    java -jar JabRef-2.0.1.jar

Let me know if you were successful.

Siva

---

### Post by lioncoeur on 2006-03-09
Hi!

Sorry for hijacking this thread, I'm having the same problem, my .jar file doesn't do anything.

This is the message I get, after doing: java -jar JabRef-2.0.1.jar

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.                                                                                                                                 
awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.ImageIcon.ImageIcon(java.net.URL, java.lang.String) (/usr/lib/                                                                                                                                 
libgcj.so.6.0.0)
   at javax.swing.ImageIcon.ImageIcon(java.net.URL) (/usr/lib/libgcj.so.6.0.0)
   at net.sf.jabref.GUIGlobals.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at net.sf.jabref.JabRefPreferences.JabRefPreferences() (Unknown Source)
   at net.sf.jabref.JabRefPreferences.getInstance() (Unknown Source)
   at net.sf.jabref.JabRef.JabRef(java.lang.String[]) (Unknown Source)
   at net.sf.jabref.JabRef.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit no                                                                                                                                 
t found in gnu.gcj.runtime.SystemClassLoader{urls=[file:JabRef-2.0.1.jar,file:./                                                                                                                                 
], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.                                                                                                                                 
0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgc                                                                                                                                 
j.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.                                                                                                                                 
0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader)                                                                                                                                  
(/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...10 more


```

It's probably something I don't have installed, right?

Thanks in advance :)

---

### Post by Zyzzyva100 on 2006-03-10
I can't even get that far, I just get an error saying "invalid or corrupt jar file", and I have downloaded and redownloaded it a few times, so I really have no idea what the problem might be.

---

### Post by lioncoeur on 2006-03-11
Have you tried running it from the weblink on the JabRef site? For me, this works flawlessly. I can't explain this behaviour! It's not ideal at all, because sometimes I won't have an Internet connection. Does anyone know why it would work off the weblink and not through the downloaded *.jar (which IS essentially the same thing, since it downloads it and then runs it when you click on the weblink).

---

### Post by Zyzzyva100 on 2006-03-14
The web version doesn't even work for me.  I really can't figure out what the problem is, other than I'm sure its the fault of java.  This works flawlessly for me on gentoo, but I really don't feel like going through the time of installing gentoo on my laptop, when ubuntu has worked so nicely.

---

### Post by ipstone on 2006-03-24
- I encountered the same problem

jabref runs well on mac os x, suse linux 9.3 pro, debian,
but somehow doesn't work on my recent kubuntu - 

Here is the fatal code; I guess it's something to do with the java gdk package in kubuntu? 


(.:8005): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted

---

### Post by ekarni on 2006-03-24
Jabref 1.8.1 runs fine for me.  I agree, it sounds like everyone is getting java errors of some sort, rather than a problem with Jabref.  Here's a list of the Java-related packages I've got installed.  Maybe you need one of them (judging by the errors, I'd try java-common and sun-j2re1.5 first).

gij
j2re1.4
java-common
java-gcj-compat
libgcj6
libgnujaxp-java
libgnujaxp-jni
libjaxp1.2-java
sun-j2re1.5

and again the command is just *java -jar YourJarFile*

---

### Post by lioncoeur on 2006-03-27
I did some more fiddling around with this. It seems that the Blackdown version of Java works wonderfully with JabRef. I suggest you all use it :)

---

### Post by ipstone on 2006-03-28
Hi, 

actually the java in blackdown works well for ubuntu breezy, but somehow doesn't work for my other kubuntu install, but eventually just got it works in kubuntu breezy eventually  by a quick way:

get ImageJ for free at: [http://rsb.info.nih.gov/ij/download.html](http://rsb.info.nih.gov/ij/download.html)

get the linux version and extract it where you want

this package include the jre 1.5, and itself was run by ./jre/bin/java -mx256m -cp ij.jar ij.ImageJ

so what I did is using this java package included in imageJ to run jabref
by cd /directory where you put the jre folder
/jre/bin/java -jar JabRef-2.0.1.jar 

now jabref works very well.

---

### Post by orsula on 2006-08-28
Hi,
I am hijacking this thread as well for Jabref related problems. I tried to install everything I could think of that relates to Java. 
I currently have the following response:
 
~/bin$ java -jar JabRef-2.1.jar
Unable to create graphical interface.


I installed j2sdk1.4.2_12. How could I get the GUI to work. It seems the file itself is fine and the java installation is ok, but the graphics get stuck somewhere.

Thanks
Gideon

---

### Post by orsula on 2006-08-30
This thread is the simplest solution.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by civetta on 2006-10-03
just place the .jar file where you want it, then...
```

sudo apt-get install sun-java5-bin
```

Right click on the .jar and choose "open with Sun Java 5.0 Runtime"

This worked for me in both Dapper and Edgy Beta.

---

### Post by canard on 2006-10-13
An alternative to this if you like to use command line is the following:
Get the Jabref jar file from the website on sourceforge.
Create a directory Jabref in /opt/ and put the jar file in it (i assume it is the latest version Jabref-2.1.jar):
```
sudo mkdir /opt/Jabref 
sudo mv Jabref-2.1.jar /opt/Jabref/
```
Create as root a file name jabref in /usr/bin/ with the following line:
```
sudo touch /usr/bin/jabref
sudo echo "/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/./java -jar /opt/Jabref/JabRef-2.1.jar">/usr/bin/jabref
```
and you can launch it by typing jabref in a terminal or the quick launch applet.

Enjoy!:cool:

---

### Post by idole on 2006-11-01
There is a Debian unstable. 

Works fine here with 6.10

Read about it on [Sourceforge]("http://sourceforge.net/projects/jabref/") or download it [here]("http://packages.debian.org/unstable/tex/jabref").

---

### Post by venik212 on 2007-04-13
Does anyone know why JabRef had been removed from the Synaptic repositories?

---

### Post by webby35 on 2007-06-01
> **civetta said:**
> just place the .jar file where you want it, then...
```

sudo apt-get install sun-java5-bin
```

Right click on the .jar and choose "open with Sun Java 5.0 Runtime"

This worked for me in both Dapper and Edgy Beta.

Make sure you have Sun's version of Java (look at the FAQ on the JabRef website). Once that's ok, I got JabRef to work by right-clicking  the .jar and choosing "open with Sun Java 5.0 Runtime". I've now changed the properties of the .jar so that it automatically uses Sun JRE when I click on it. 

FYI, I'm using Feisty Fawn.

---

