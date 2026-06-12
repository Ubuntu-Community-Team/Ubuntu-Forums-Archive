---
title: "ARIA (Advanced Robotics Interface for Applications)"
date: 2009-08-03
forum: General Help
---

### Post by elperzon on 2009-08-03
I recently transfered to Ubuntu Jaunty (2 days ago) and needed Aria to work. I have compiled Aria and installed the Java wrappers as needed. Now running in eclipse I keep getting an error after running

            System.loadLibrary("AriaJava");

How do i go about editing the java.library.path to include the Aria jar files?

Thanks

---

### Post by elperzon on 2009-08-03
Finally found the answer! in eclipse set up the run configuration to include setting the var LD_LIBRARY_PATH to /usr/local/Aria/lib. However my wireless is still unable to connect to the AmigoBot. Any ideas?

---

