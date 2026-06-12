---
title: "wizard fails when installing pcanywhere"
date: 2009-07-10
forum: General Help
---

### Post by keevill on 2009-07-10
am posting this help question once more since I have been unsuccessful installing pcanywhere 12.1 or 12.5 on Ubuntu 9.0.4
Bascially, I am getting an error message when  doing the install. Pls see below. As you can see, I have even tried logging in as root in case the permissions on the tmp files described below were foxing the installer. I have java ver 1.6 installed.
I need pcanywhere both as host and remote on my pc and if I cannot get it to work, then I have to stick with Windoze which is definitely not my desire !
The help file @ Symantec say that the cross platform install should work on Linux.
This error seems to be nothing experienced by others when I google it.
Hope some clever person can suggest something.
I am not a very experienced 'Nix person but learning fast.


root@ubuntu:~/Desktop# cd pcaw
root@ubuntu:~/Desktop/pcaw# ls
0x0404.ini  0x0412.ini  1041.mst      MacInstaller.app
0x0407.ini  1028.mst    1042.mst      media.inf
0x0409.ini  1031.mst    Autorun.inf   Setup.ini
0x040a.ini  1033.mst    Data1.cab     SetupLinuxMac.jar
0x040c.ini  1034.mst    instmsiw.exe  SetupWindows.exe
0x0410.ini  1036.mst    Linux.bin     Symantec pcAnywhere CrossPlatform.msi
0x0411.ini  1040.mst    Mac.command   WindowsInstaller-KB893803-x86.exe
root@ubuntu:~/Desktop/pcaw# java -jar SetupLinuxMac.jar
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
WARNING: could not delete temporary file /tmp/ismp001/567306
WARNING: could not delete temporary file /tmp/ismp001/3574935

---

### Post by Peter09 on 2009-07-10
Cannot help you with pcanywhere but there are several free applications in the repositories that do the same job.

Depending on what you need - 

ssh and sshserver
nxfree

are two good ones.

---

### Post by keevill on 2009-07-10
Unfortunately I have about 20 pcs running pcanywhere to support so another option would only help if it allowed connections from and to pcaw machines.

I have  got a bit further with the install of PcAnywhere 12.5 on Ubuntu 9.0.5.
Firstly  I navigate to the pcaw files directory which I  copied from the cd onto  the desktop on Ubuntu machine
"ls" shows the cross platforms we need.

Then I cd to that directory then perform "ls" and I can see the SetupLinuxMac.jar 

Next I go to the terminal console and try the following commands:

tried this ......
david@david-desktop:~/Desktop/pcaw/Symantec pcAnywhere CrossPlatform$ sudo /usr/lib/jvm/java-6-sun/jre/bin/java -jar SetupLinuxMac.jar -console

and this....

david@david-desktop:~/Desktop/pcaw/Symantec pcAnywhere CrossPlatform$ sudo /usr/lib/jvm/java-6-sun-1.6.3.13/bin/java -jar SetupLinuxMac.jar -console

both end up with JVM not found after about 50-75 % of the installation.

 I also checked "update-alternatives --config java"

quite normally . I get this.....but it does show me the correct path to the jvm .

"There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure."



This is the final failure showing JVM not found...

|-----------|-----------|-----------|------------|
0%         25%         50%         75%        100%
||||||||||||||||||||||||||||||||||||
-------------------------------------------------------------------------------
Symantec pcAnywhere CrossPlatform - InstallShield Wizard

Errors occurred during the installation.
  - JVM not found

Same thing happens if I use ..

sudo/usr/lib/jvm//java-6-sun-1.6.0.13/java -jar SetupLinuxMac.jar sudo /usr/lib/jvm/java-6-sun-1.6.0.13/java -jar SetupLinuxMac.jar

No matter whether I use the console command or the GUI install either way fails with same error JVM not found.

It appears the installer cannot see that JVM is installed.

---

### Post by davidlarg on 2009-07-20
I have installed pcAnywhere 12.1 using wine and had no problems with the install.  Some of the features do not work.  If connecting to more than one computer at a time it will lock it up.  Also clicking on properties will lock it up.  But accessing only one machine works fine.  I have read that pcAnywhere 11 works better with wine.  Maybe you can try an older version if you have it.

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

