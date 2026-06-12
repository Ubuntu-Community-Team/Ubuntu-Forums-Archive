---
title: "downloading a &quot;jar&quot; file"
date: 2009-10-06
forum: General Help
---

### Post by craig10x on 2009-10-06
I have only been involved with Ubuntu and Linux for about 6 months, and have only used programs available on the Add/Remove programs or the Package Manager.....

There is a program that is available for Linux that i would like to download, but would require that i download a "jar" file....

How does this work?  What's the easiest and best way to handle that? (i don't want to mess up...lol).....

Also once the program is installed...if i need to remove it, how would i do that? (since it wouldn't be on my add/remove list)........

Thanks in advance for your help.....I hope it won't involve using the "terminal" i have used that once or twice but prefer not to whenever possible,,,, :)

---

### Post by Giblet5 on 2009-10-06
If a package is not wrapped for your linux distribution (eg, Debian .deb packages), then the terminal is what you must use.

It's surprisingly easy to install stuff -- even from source code -- once you get over termiphobia.

Uninstalling unpackaged software requires a deeper knowledge of the software package itself because you'll have to manually remove its files and undo any configuration changes the install process may have made.

Good news: disk is C.H.E.A.P. A 1TB drive is less than $100. Why bother uninstalling anything? :)

---

### Post by oldos2er on 2009-10-06
A .jar file must be run with Java. If you have Java installed, then in a terminal run java -jar /path/to/file.jar

---

### Post by macdhuibh on 2009-10-06
craig10x-
If you download the Java Run-time Environment (Similar to what is needed in other OS.) You can then save the file and do a right hand click on it, then pick  **Open with "Sun Java (version) Runtime".**

To install the Java run time, I am sorry to say terminal will be used.  
Java has published a good set of instructions on how to do it. 

First link is the download of the file, second is the instructions. Good luck.

[http://javadl.sun.com/webapps/download/AutoDL?BundleId=33880](http://javadl.sun.com/webapps/download/AutoDL?BundleId=33880)

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

---

### Post by craig10x on 2009-10-06
Thanks for the feedback so far :)

Well, i do have the Java 6 Runtime installed from the add/remove applications on Ubuntu...is this what  is needed to run the jar file?

If so...please give me an outline of what i need to do...starting from when i click on the jar download at the application's website....

---

### Post by ZaHACKieL on 2009-10-06
> **craig10x said:**
> 
Well, i do have the Java 6 Runtime installed from the add/remove applications on Ubuntu...is this what  is needed to run the jar file?

If so...please give me an outline of what i need to do...starting from when i click on the jar download at the application's website....

OK, so you have your .jar file, lets call it myfile.jar and suppose we saved the file in the desktop.

So, you have to first open the Terminal ( Applications > Accesories > Terminal )  and navigate to the Desktop directory (the directory where we saved the file). To change a directory via the Terminal you have to use the command "cd" , so, if you open the Terminal and you have a default configuration, you should only need to type: cd Desktop ,  and then press enter to go to the Desktop directory.

Just as a tip, if you want to see the files in that directory just type the command "ls".

So, now that we are located in the file's directory you only have to type the following command to run the .jar file:

java -jar myfile.jar

and that's it, that's how you run a .jar file.

I hope that helps, let us know if you still have trouble

ZL

---

### Post by craig10x on 2009-10-07
Thanks...that was very helpful...i will give it a try....:)

---

