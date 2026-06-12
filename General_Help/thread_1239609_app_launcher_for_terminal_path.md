---
title: "app launcher for terminal path"
date: 2009-08-13
forum: General Help
---

### Post by trozombo on 2009-08-13
hi, 
cant figure out how to do this:

i have this path from terminal to run skyshare-manager,

roberto@roberto-laptop:~$ cd Skyshare\ Manager\ v1.4.3
roberto@roberto-laptop:~/Skyshare Manager v1.4.3$ java -jar skyshare-manager.jarUnable to access jarfile skyshare-manager.jar
roberto@roberto-laptop:~/Skyshare Manager v1.4.3$ dir
bin  doc  installation.log  lib  Licence.txt  Readme.txt  res  Uninstaller
roberto@roberto-laptop:~/Skyshare Manager v1.4.3$ cd bin
roberto@roberto-laptop:~/Skyshare Manager v1.4.3/bin$ java -jar skyshare-manager.jar

basically i just want to do a app launcher to simplify the process.
thanks for yo help!!!!!
Trozombo

---

### Post by DaithiF on 2009-08-13
Hi,
create an app launcher, and use this for the command:
java -jar "/home/roberto/Skyshare Manager v1.4.3/bin/skyshare-manager.jar"

---

### Post by trozombo on 2009-08-14
> Hi,
create an app launcher, and use this for the command:
java -jar "/home/roberto/Skyshare Manager v1.4.3/bin/skyshare-manager.jar" 	



Hi,
thanks for the answer, however it doesnt work. comes up an error:
  Faliled to start application 

this what it says on the terminal:

java.util.zip.ZipException: error in opening zip file
    at java.util.zip.ZipFile.open(Native Method)
    at java.util.zip.ZipFile.<init>(ZipFile.java:114)
    at java.util.jar.JarFile.<init>(JarFile.java:133)
    at java.util.jar.JarFile.<init>(JarFile.java:70)
    at com.skyline.utils.IOUtils.extractContentStream(IOUtils.java:75)
    at com.skyline.client.ConfigManager.getProperties(ConfigManager.java:142)
    at com.skyline.client.gui.main.MainFrame.<init>(MainFrame.java:173)
    at com.skyline.client.SkylineUIClient.initContext(SkylineUIClient.java:53)
    at com.skyline.client.SkylineUIClient.<init>(SkylineUIClient.java:42)
    at com.skyline.client.SkylineUIClient$4.run(SkylineUIClient.java:289)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)

any ideas????

---

### Post by KhurramM on 2009-08-14
It is my doubt that either you have permission issues?

If not see that the application runs via the cli. If so good.

Next see and use ln command to link to the application to run it from the Desktop.

Hope this helps.

---

### Post by DaithiF on 2009-08-14
my guess is that it expects to be started from the bin directory, because it requires some other jar files located there, or relative to there.  Since it works for you when you cd there, then you can could a simple wrapper script to cd to that directory first, then run the java process.  Create a file with these contents:
```
#!/bin/sh
cd /home/roberto/Skyshare Manager v1.4.3/bin
java -jar skyshare-manager.jar
```
save the file in your home directory, naming it something like skylauncher.sh
Now in your launcher, change the Command to be /home/roberto/skylauncher.sh

---

### Post by trozombo on 2009-08-14
> my guess is that it expects to be started from the bin directory, because it requires some other jar files located there, or relative to there. Since it works for you when you cd there, then you can could a simple wrapper script to cd to that directory first, then run the java process. Create a file with these contents:
 	Code:
 	#!/bin/sh
cd /home/roberto/Skyshare Manager v1.4.3/bin
java -jar skyshare-manager.jar 
save the file in your home directory, naming it something like skylauncher.sh
Now in your launcher, change the Command to be /home/roberto/skylauncher.sh 	

Done it,
now this is the error

Esecuzione del processo figlio "/home/roberto/Skylauncher.sh" non riuscita (Permesso negato)

******** is in italian....

it basically says (Access denied) at the end. 

Does it suppose to run the application if I click on the sh file that I created????

Tnx!!

---

### Post by trozombo on 2009-08-14
> **KhurramM said:**
> It is my doubt that either you have permission issues?

If not see that the application runs via the cli. If so good.

Next see and use ln command to link to the application to run it from the Desktop.

Hope this helps.

I appreciate you help but this little bit beyond my knowledge.
what you mean by "run via cli"???
thx

---

### Post by DaithiF on 2009-08-14
Hi, to fix the permission denied issue, do:
chmod 755 skylauncher.sh
in a terminal

---

### Post by trozombo on 2009-08-14
> **DaithiF said:**
> Hi, to fix the permission denied issue, do:
chmod 755 skylauncher.sh
in a terminal

GRR i thought i was close........
now it does nothing, not even an error.......
frustrating.........

havent got clue why does not work.........

---

### Post by DaithiF on 2009-08-14
run the script directly from the command line to see what errors it produces.
in a terminal:
```
./skylauncher.sh
```

---

### Post by trozombo on 2009-08-14
> **DaithiF said:**
> run the script directly from the command line to see what errors it produces.
in a terminal:
```
./skylauncher.sh
```

Solved!!!
yep thanks to your last reply i realised there was an error with the cd path.
thanks mate for your help... much appreciated im and even happier ubuntu user
Trozombo

---

