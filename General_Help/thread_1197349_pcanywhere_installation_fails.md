---
title: "pcanywhere installation fails"
date: 2009-06-26
forum: General Help
---

### Post by keevill on 2009-06-26
I am trying to install pcanywhere ver 12.x . I have read the instructions 
from Symantec.

"# JAVA Virtual machine version 1.4.2 or later is required and needs to be in your global $PATH in order to run.
# Open a Terminal Window and change directory to the Symantec pcAnywhere CrossPlatform folder located on the CD
# Run the following command line:

    *  java -jar SetupLinuxMac.jar

# Follow installation wizard instructions 

 The {java -version} command brings up

java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)
 
However I get the following error. Has anyone got an answer for me?
I am reasonably new to Unix and am trying to migrate away from Win but I have to use Pcanywhere both as a host and a remote for my work.

___________________________
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
WARNING: could not delete temporary file /tmp/ismp001/4221021
WARNING: could not delete temporary file /tmp/ismp001/6749217
david@ubuntu:/media/cdrom0/Symantec pcAnywhere CrossPlatform$ 
david@ubuntu:/media/cdrom0/Symantec pcAnywhere CrossPlatform$

---

### Post by dynomite on 2009-08-14
You can try using sunjava6-jre instead of the open version that comes with ubuntu.

Just install it with the package manager.

Then go to the terminal

sudo update-alternatives --configure java

Pick the java you want your system to use.

Hope this helps someone.

---

### Post by keevill on 2009-08-14
Thanks but I gave up with PCAW and am using VNC .
Just as good for my purpose and a bit faster.

---

### Post by burebista on 2010-10-04
try this:
1. install j2sdk1.4.2_18 in /usr/lib/jvm/j2sdk1.4.2_18
2. run from console:
$sudo -s
$/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -jar SetupLinuxMac.jar
and use the gui installer, it works 100%.
3. run from console
$sudo gedit /usr/bin/pcAnywhere
4. replace this line:
java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
with
/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
5. save the file /usr/bin/pcAnywhere
6. run from Alt-F2 or from Terminal "pcAnywhere".

That's it.

---

