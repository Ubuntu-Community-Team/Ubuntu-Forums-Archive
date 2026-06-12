---
title: "Add directory on media to path"
date: 2010-02-13
forum: General Help
---

### Post by pushkar_k on 2010-02-13
I need to add a directory to path in ubuntu. The directory I want to add is on Windows drive .
If I try to add a directory , lets say "some directory" to path , then on adding I get following error. The directory resides on HD.
  --------------------------------------------------------------------------------------------------------------------------------------- 
 user@user-desktop:~$ PATH=$PATH:/media/New Volume/some directory/javacc-5.0/bin
bash: Volume/some: No such file or directory.
  ---------------------------------------------------------------------------------------------------------------------------------------

If I try it after adding quotes("") to directory name then it doesn't give any error but still it gives following error.

  ---------------------------------------------------------------------------------------------------------------------------------------
user@user-desktop:~$ javacc simple1.jj
dirname: extra operand `Volume/some'
Try `dirname --help' for more information.
Exception in thread "main" java.lang.NoClassDefFoundError: javacc
Caused by: java.lang.ClassNotFoundException: javacc
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: javacc.  Program will exit.

  ---------------------------------------------------------------------------------------------------------------------------------------

can someone help ?

---

### Post by Ulex on 2010-07-10
I think that the media would have to remain mounted, but as long as it does there's a guide here that describes how to add a directory to path. It looks pretty straightforward.

[http://blog.matthewashrafi.com/2010/06/14/add-a-directory-to-path-in-ubuntu-10-04/](http://blog.matthewashrafi.com/2010/06/14/add-a-directory-to-path-in-ubuntu-10-04/)

Hope that helps. :D

---

