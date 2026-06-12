---
title: "Sun Java 1.5 should run .jar files"
date: 2006-02-15
forum: General Help
---

### Post by Timokl on 2006-02-15
Hi everybody,

yesterday, I downloaded and installed Sun's Java 1.5. That went quite smoothly, also the integration into Firefox had been no problem.

But how do I set up Sun's Java to handle .jar files directly from the Desktop or any other location by double-clicking them?

There is a Java application I need to run -- Reload ([http://www.reload.ac.uk](http://www.reload.ac.uk)) which is an open source SCORM editor. There is a downloadable package on their website called *Manual Installer*. This installer is just the .jar files, etc. in one zip file. On my computer at the office (running Windows), I just double-click onto the main .jar file to run the application.

Right now, by double-clicking the file simply is unpacked.

I used to run Ubuntu 64 Bit with Blackdown's Java where it was no problem to start a Java app by simply double-clicking it. However, due to the huge array of troubles (and me being a Linux Newbie), I switched to the 32 Bit version of Ubuntu Breezy.

I googled and searched on this forum already, but I did not find a solution. So, how can I set up my Java to run .jar files?

Regards,
Timo

---

### Post by timbosa on 2006-02-15
*Right* click on the .jar file. Choose **Properties**, then **Open With**. I don't know if java will be in the list. If its not choose **Add** and if its not in that list click on **Use a custom command**. Then type
```
java -jar
```
click on **add** and then close the box. It should then open up properly when you double-click on it.

---

### Post by Timokl on 2006-02-16
well, it's so easy if you know how to do it. ;) 

It did not work at first, but within the properties dialog I remarked, that the jar file had not been set to be executable. :mrgreen: 

Anyway, it works now. \\:D/  Thanks a lot, dude!

Bye,
Timo

---

