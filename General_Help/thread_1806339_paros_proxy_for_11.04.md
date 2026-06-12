---
title: "paros proxy for 11.04"
date: 2011-07-17
forum: General Help
---

### Post by letitworknow on 2011-07-17
I'm not sure if this is in the right categories but anyway...
i am trying to get paros proxy running for a security class that i am taking.  the problem that i am having is getting paros to open.  when i click the .jar file nothing happens.  i extracted the program, mozembedlinux-gtk2 and once again nothing happens.  i can find the program in the terminal 

hris@chris-System-Product-Name:~/paros$ ls
autoupd.bat                  license                paros_logo.ico
db                           log                    plugin
filter                       META-INF               release.txt
IeEmbed.exe                  MozEmbed.exe           resource
jdic.dll                     mozembed-linux-gtk1.2  session
libjdic.so                   mozembed-linux-gtk2    startserver.bat
libmozembed-linux-gtk1.2.so  org                    startserver.sh
libmozembed-linux-gtk2.so    paros                  tray.dll
libtray.so                   paros.jar              xml


this is where i'm stuck.  google seems to be failing me with this any help would be great thanks. i am running 64-bit ubuntu 11.04

---

### Post by letitworknow on 2011-07-17
this is what i get when i try to work with the program in the terminal

---

### Post by gmargo on 2011-07-17
If you want to use the 'paros' that you downloaded, you should start it by running the **startserver.sh** shell script, which basically just does "java -jar paros.jar".

I use a slightly modified startserver script that contains "java -Xmx96m -jar paros.jar -nouseragent".  The -nouseragent option means that paros will not replace the User-Agent string with it's own.

It appears that there is no **paros** package for 11.04 Natty; just Lucid and Maverick.

---

### Post by letitworknow on 2011-07-17
thanks alot man.  the startserver.sh command didn't work for me but java -jar paros.jar did.  thanks again

---

