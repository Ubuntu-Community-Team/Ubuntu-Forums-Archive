---
title: "Installing Java"
date: 2012-07-30
forum: General Help
---

### Post by clm55 on 2012-07-30
Hello all. I'm new to Ubuntu and the forum. Long story short: I bricked an Android phone and found a fix but I need to use Linux. Java is required too and I have spent the last 2 days trying to figure out how to install it. I have used a handful of methods I found online and while a few of them have seemed successful, when I try to verify my Java status from the website, it can't find anything. (Java IS enabled in Firefox, though.) When I open the .jar file its supposed to execute the utility I'd use to unbrick my phone, but instead it opens in Archive Manager. (There's actually a Read Me file that states if you can read it, something wrong happened and the file should just be executable through Java. ) Anyway, this has been such a headache and I'm just at a loss now. Any help is greatly appreciated!

By the way, I've got Ubuntu 11.04 running through Parallels 7.

---

### Post by QIII on 2012-07-30
See the Java wiki link in my signature.

In the Oracle Java 7 section, look for the link "Using webupd8.org's strikingly simple method" and follow the instructions on their website.

Let me know what happens.

---

### Post by clm55 on 2012-07-30
Hello and thanks for the quick reply! This is actually one of the methods I tried before but I tried it again. I'm not sure if this tells you anything but here's the last few lines of what that ended up doing:

gpg: key EEA14886: "Launchpad VLC" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


When I check the version, I get this:

java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b06)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)


So it looks (to me, at least) like Java should be installed. But when I go to the Java Detector at java.com, I get the message, "Something is wrong. Java is not working." 

If it means anything, some of the methods I found referred to /usr/local/java and while I don't have a directory titled "Java" there is one for the current JRE. 

Any thoughts?

---

### Post by QIII on 2012-07-30
But ```
about:plugins 
```indicates that the plugin is present?

Odd, indeed.  I'll see if I can dig something up.

---

### Post by clm55 on 2012-07-30
I can't believe how ridiculously helpful you've been! I don't think this means anything, but I also have Windows XP installed as a VM on Parallels. Could this be interfering? 

Also, I did have an older build of Ubuntu installed first (I forget which) and I installed Java 6, which WAS recognized on java.com, but my .jar file still opened in Archive Utility.

Edit: Not sure if you wanted me to try that code, but it didn't work for me: 

about: plugins: command not found

---

### Post by The Cog on 2012-07-30
> Could this be interfering? I think not.
You enter this into the address bar of firefox (instead of entering a http type url. Then firefox tells you what plugins are installed. We are guessing that it won't mention a java plugin. 
```
about:plugins
```

I'm not clear if you actually need firefox to run this java app. 
The other way to run a java app in Linux is to open a command prompt (console) and use a command like:
```
java -jar filename.jar
```
using the right filename of course. You can type "java -jar " and then drag/drop the file from the file manager to the command prompt window to make sure the full path is correct.

---

### Post by QIII on 2012-07-30
```
java -jar filename.jar
```

Will run it.

Bah!  Cog!  You scooped me while I was waiting for my cellphone to reestablish a connection!  Curses!

---

### Post by clm55 on 2012-07-30
Well using the code java -jar code worked! It loaded my .jar file. Still confused about why it wasn't recognized online but no big deal. Turns out it didn't fix my phone though - probably because Ubuntu won't read the USB drive by default, Mac OSX will. Next step is to do an install of Ubuntu through Boot Camp. Anyway, thanks for the help folks. I really appreciate it.

---

