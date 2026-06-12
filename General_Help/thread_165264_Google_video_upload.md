---
title: "Google video upload"
date: 2006-04-24
forum: General Help
---

### Post by Oz_hack on 2006-04-24
i am wondering if anyone has any success in uploading to google video. 

They do make a uploader for linux in the form of a *.jar file ( java) but no intructions on how to work it. I have tried ./ to see if that works but no luck there i have java installed the latest version i will play more tonight on it see if i can find the answer 


My knowledge is ok but not the best on here, my sister has win virus so i can use that to upload but would prefer not !! 

thanks in advance for all the help

---

### Post by sefs on 2007-07-13
once you have the Jar file then ...

```

java -cp /path/to/jarfile/GoogleVideoUploader.jar com.google.uploader.Uploader * 

```

will launch it.

---

### Post by niceguy123 on 2008-01-06
> **sefs said:**
> once you have the Jar file then ...

```

java -cp /path/to/jarfile/GoogleVideoUploader.jar com.google.uploader.Uploader * 

```

will launch it.

Tried that and got...

```
niceguy@niceguy-desktop:~$ java -cp /home/niceguy/Desktop/downloads/GoogleVideoUploader.jar com.google.uploader.Uploader *
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.EventQueue.isDispatchThread(libgcj.so.70)
   at java.awt.EventQueue.invokeAndWait(libgcj.so.70)
   at javax.swing.SwingUtilities.invokeAndWait(libgcj.so.70)
   at com.google.uploader.Uploader.main(Uploader.java:19)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...4 more

```

I'm not sure if I have java installed, how would I check?

---

### Post by niceguy123 on 2008-01-06
I installed Java and then the google video uploader works as advised above.

Thanks,

Now how do I get the uploader into the applications menu?

---

### Post by staib on 2008-03-24
"Now how do I get the uploader into the applications menu?"

I would like to know this as well :)

Nick

---

### Post by stani on 2008-06-01
> **staib said:**
> "Now how do I get the uploader into the applications menu?"

I would like to know this as well :)

Nick

Right click on your applications menu and choose "Edit menus", go to "Audio & Video", click on new item and make sure you copy and paste the commandline there.

---

