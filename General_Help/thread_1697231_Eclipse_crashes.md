---
title: "Eclipse crashes"
date: 2011-02-28
forum: General Help
---

### Post by Zilioum on 2011-02-28
I hadn't used eclipse since my upgrade to 10.10. I opened it yesterday, and after a few seconds it just crashed. This happens over and over. I don't even have to click on anything once it's open. Here are the first few lines of the error report it puts in my home folder:
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f6d95fd8bd6, pid=11732, tid=140108302956288
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) 64-Bit Server VM (19.1-b02 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# j  org.eclipse.cdt.internal.core.dom.parser.cpp.CPPASTFunctionDeclarator.postAccept(Lorg/eclipse/cdt/core/dom/ast/ASTVisitor;)Z+14
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
``` 
It goes on for pages, but I think that this is the important part.

It happens on all three eclipse versions I'm using. Galileo, Helios and Helios Cpp. I downloaded eclipse from the official homepage and run it from my home directory. This was working well for more than one year. Any ideas? I'd say it has something to do with the JRE (elaborate guess :) )

---

### Post by louisgag on 2011-03-01
I have a very similar bug, in Eclipse, and it just started happening, here is the auto-generated report.

-Louis


```

System: Linux 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64
X Vendor: The X.Org Foundation
X Vendor Release: 10900000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Clearlooks
Icon Theme: ubuntu-mono-dark
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 1300054016 vsize: 1300054016 resident: 420892672 share: 23945216 rss: 420892672 rss_rlim: 18446744073709551615
CPU usage: start_time: 1298993737 rtime: 4352 utime: 4137 stime: 215 cutime:21 cstime: 1 timeout: 0 it_real_value: 0 frequency: 100



----------- .xsession-errors ---------------------
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2045): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/louis/9669: No such file or directory.
No stack.
--------------------------------------------------

```

---

### Post by alberto1976 on 2011-03-02
Same here. It has been working for ages, but after the most recent update, I get
```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fef1c37cafb, pid=12002, tid=140664866617088
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) 64-Bit Server VM (19.1-b02 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# V  [libjvm.so+0x691afb]
#
# An error report file with more information is saved as:
# hs_err_pid12002.log
[thread 140664868722432 also had an error]
[thread 140664865564416 also had an error]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

```I tried re-installing everything (both Galileo and Helios) and I noticed the problem occurs only after installing the C/C++ plugin (or all the time for Helios C/C++).

---

### Post by Zilioum on 2011-03-03
Your error message looks a lot like the one I get, alberto. Problems also started occurring after I installed c++ helios.
Did you install it from a repository? I got it from the website.

---

### Post by alberto1976 on 2011-03-03
> **Zilioum said:**
> Your error message looks a lot like the one I get, alberto. Problems also started occurring after I installed c++ helios.
Did you install it from a repository? I got it from the website.

It does indeed look similar.
I was using Galileo with C/C++ plugin with everything from repository. When the crashes started happening, I tried downloading Helios (C/C++) from the website but I got exactly the same behaviour. I also tried starting it all from scratch: deleting the .eclipse directory and re-downloading all the plugins, but it didn't help.

I followed the suggestion in the error message and filed a bug report at the Sun website.

---

### Post by Zilioum on 2011-03-03
> **alberto1976 said:**
> 
I followed the suggestion in the error message and filed a bug report at the Sun website.
Thanks, good idea! Could you please send me the link to the report, so that I can weigh in?

Cheers

---

### Post by alberto1976 on 2011-03-03
> **Zilioum said:**
> Thanks, good idea! Could you please send me the link to the report, so that I can weigh in?
Cheers

No problem. I used this link:

[http://bugreport.sun.com/bugreport/crash.jsp](http://bugreport.sun.com/bugreport/crash.jsp)

I did not hear anything at all from them though, so I don't have any link to the specific report I filed. Not even an auto-generated email with "thanks for submitting a bug report" or something like that.

---

### Post by Zilioum on 2011-03-03
Ah, thanks anyway for the link. I thought that it worked like launchpad, where you can say that a bug affects you as well. I'll take a deeper look at our problem this weekend, maybe using a different jre might solve the problem. On my notebook I don't have this problem, will check what the difference is.

Cheers

---

### Post by JKT7 on 2011-03-03
Same crash here. Just started happening after an apt-get update.

Version: Helios Service Release 2
Build id: 20110301-1815

vm_info: Java HotSpot(TM) 64-Bit Server VM (19.1-b02) for linux-amd64 JRE (1.6.0_24-b07), built on Feb  2 2011 16:55:54 by "java_re" with gcc 3.2.2 (SuSE Linux)

Crash report attached.

---

### Post by Zilioum on 2011-03-04
Your report looks very similar to the one alberto and I posted. Anyone got an idea which package changed?

Cheers

---

### Post by rname on 2011-03-04
I'm also seeing something similar.  Eclipse crashes after startup even if I'm not doing anything.
Could it be the same as this Launchpad bug?
[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/699859](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/699859)

Ubuntu 10.04 64-bit
I was running Eclipse Galileo (w/CDT) for months with no problems.
I recently decided to give Helios a try but since it's not available in the package manager for 10.04 I downloaded it & installed from the Eclipse site directly.  After installing Helios, it was crashing on startup, so I decided to uninstall and go back to Galileo.  Now Galileo also crashes shortly after startup.

!SESSION 2011-03-04 09:03:28.230 -----------------------------------------------
eclipse.buildId=M20100211-1343
java.version=1.6.0_24
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64 -consoleLog

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f299af07afb, pid=2071, tid=139816588687104
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) 64-Bit Server VM (19.1-b02 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# V  [libjvm.so+0x691afb]
#
# An error report file with more information is saved as:
# hs_err_pid2071.log
[thread 139816589739776 also had an error]
[thread 139816587634432 also had an error]
[thread 139816590792448 also had an error]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

---

### Post by rname on 2011-03-04
Try disabling C++ indexing quickly at startup.
If you click on the indexer in progress (lower right) and stop it, then Eclipse doesn't seem to crash.
It seems to be related to C++ indexing.

---

### Post by JKT7 on 2011-03-04
> **rname said:**
> Try disabling C++ indexing quickly at startup.
If you click on the indexer in progress (lower right) and stop it, then Eclipse doesn't seem to crash.
It seems to be related to C++ indexing.

I noticed this too, so I disabled indexing and project building completely. It crashes less often, but it's still crashing for me.

It only seems to crash when I have a C++ project open though. If I work only on one of my PyDev projects, it doesn't crash.

---

### Post by eotakos on 2011-03-06
Yeap! - The crash we all have is caused by some changes made in java during the last update... I was using eclipse for a long time without any issues before that.
are we all running 64bit OSs?

If someone tracks a workaround please post.

Thanks

---

### Post by alberto1976 on 2011-03-06
> **JKT7 said:**
>  It only seems to crash when I have a C++ project open though. If I work only on one of my PyDev projects, it doesn't crash.

I have experienced the same. It works fine unless a C/C++ project is open (even the built-in "Hello World" one).

> **eotakos said:**
>  are we all running 64bit OSs? 

Yes, 64bits here.

---

### Post by alberto1976 on 2011-03-07
Some updates:


[LIST]
[*]I managed to disable the C++ indexer (and you need to be fast) and the problem seemed fixed. I did experience few random crashes though even without the indexer.
[*]I found a possible solution at [https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227](https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227) where somebody suggested to add ```
-XX:-UseCompressedOops
``` to the file /usr/lib/eclipse.ini. I have done that and managed to re-activate indexing without seeing any crash.
[/LIST]

---

### Post by ThePineappler on 2011-03-07
Same here, Eclipse crashes with a similar error. :S
Also on 64-bit, if it helps.

---

### Post by janiskr on 2011-03-07
if that helps, these where the updates I installed:
```
Aptitude 0.6.3: log report                                                                                                           
O*, feb 22 2011 08:11:44 +0200                                                                                                       
                                                                                                                                     
IMPORTANT: this log only lists intended actions; actions which fail due to                                                           
dpkg problems may not be completed.                                                                                                  
                                                                                                                                     
Will install 6 packages, and remove 7 packages.                                                                                      
30,8MB of disk space will be freed                                                                                                   
===============================================================================                                                      
[REMOVE, NOT USED] javahelp2                                                                                                         
[REMOVE, NOT USED] libfelix-framework-java                                                                                           
[REMOVE, NOT USED] libfelix-main-java                                                                                                
[REMOVE, NOT USED] libjna-java                                                                                                       
[REMOVE, NOT USED] libnb-platform12-java                                                                                             
[REMOVE, NOT USED] libswing-layout-java                                                                                              
[REMOVE, NOT USED] visualvm                                                                                                          
[UPGRADE] sun-java6-bin 6.22-0ubuntu1~10.10 -> 6.24-1build0.10.10.1                                                                  
[UPGRADE] sun-java6-fonts 6.22-0ubuntu1~10.10 -> 6.24-1build0.10.10.1                                                                
[UPGRADE] sun-java6-jdk 6.22-0ubuntu1~10.10 -> 6.24-1build0.10.10.1                                                                  
[UPGRADE] sun-java6-jre 6.22-0ubuntu1~10.10 -> 6.24-1build0.10.10.1                                                                  
[UPGRADE] sun-java6-plugin 6.22-0ubuntu1~10.10 -> 6.24-1build0.10.10.1                                                               
[UPGRADE] sun-java6-source 6.22-0ubuntu1~10.10 -> 6.24-1build0.10.10.1                                                               
===============================================================================                                                      
                                                                                                                                     
Log complete.
```        
after what eclipse indexer started to crash in CDT. Before that Galileo and Helios worked normally.

---

### Post by rymurr on 2011-03-07
This is not terribly relevant but switching to openJDK 'fixed' the problem for me. Since I have no time to bug hunt and openjdk does what I want it is a good solution for now.

---

### Post by rname on 2011-03-07
Thank you alberto1976.  Adding -XX:-UseCompressedOops to eclipse.ini appears to have worked.
At least it finished indexing and hasn't crashed so far.

---

### Post by nemediano on 2011-03-09
Same here.

[LIST]
[*]Ubuntu 10.10 on 64bits
[*]Eclipse Elios SR1 (downloaded from the website)
[*]Sun java 6
[*]Using CDT
[/LIST]
I don't now what the problem is, it worked for me for tree days, and then it started crashed and crashed again.

I't crashed at the indexing and with the
-XX:-UseCompressedOops

At the eclipse.ini is working now. But i think we should use it as a temporary fix.

---

### Post by everweb on 2011-03-09
Use openJDK.

Open galternatives and set all of your java programs to openJDK instead of the Sun Java alternative.

---

### Post by Zilioum on 2011-03-10
> **everweb said:**
> Use openJDK.

Open galternatives and set all of your java programs to openJDK instead of the Sun Java alternative.

I can confirm this. On my notebook I have exactly the same setup as on my desktop, except that I use OpenJDK. No crashes on my notebook yet. Both are 64-bit as well.

---

### Post by axel_m on 2011-03-10
> **alberto1976 said:**
> Some updates:


[LIST]
[*]I managed to disable the C++ indexer (and you need to be fast) and the problem seemed fixed. I did experience few random crashes though even without the indexer.
[*]I found a possible solution at [https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227](https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227) where somebody suggested to add ```
-XX:-UseCompressedOops
``` to the file /usr/lib/eclipse.ini. I have done that and managed to re-activate indexing without seeing any crash.
[/LIST]

That's a bug in the 64Bit version of the Sun JDK/JRE. You should either add the above quoted line to your eclipse.ini or use OpenJDK.

---

### Post by eotakos on 2011-03-13
funny thing... I switched to the repository version and it worked. Not that running away from the problem actually solves the problem, but...

---

### Post by Olostan on 2011-03-14
Today eclipse with C++ starts crashing, but yesterday worked like a charm (nothing was updated, same cpp project and files).

'-XX:-UseCompressedOops' solved problem. 

Is there any explanation somewhere? Interesting when I can remove this switch (and should I?)

---

### Post by mchibani on 2011-03-15
Hi,
Got same crash ! I found this workaround :
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227](https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227)
it worked for me

Hope it helps

---

### Post by djtarki on 2011-03-24
> **alberto1976 said:**
> Some updates:


[LIST]
[*]I managed to disable the C++ indexer (and you need to be fast) and the problem seemed fixed. I did experience few random crashes though even without the indexer.
[*]I found a possible solution at [https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227](https://bugs.eclipse.org/bugs/show_bug.cgi?id=333227) where somebody suggested to add ```
-XX:-UseCompressedOops
``` to the file /usr/lib/eclipse.ini. I have done that and managed to re-activate indexing without seeing any crash.
[/LIST]


That worked like a charm! Thanks!

---

### Post by axylone on 2011-04-05
Fix seems to work for me too.  Thanks!

---

### Post by davidgutu on 2011-05-23
unfortunately fix doesn't seem to work for me.
Here is a copy of my log file:

!SESSION Mon May 23 18:51:54 EDT 2011 ------------------------------------------
!ENTRY org.eclipse.equinox.launcher 4 0 2011-05-23 18:51:54.131
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ClassNotFoundException: org.eclipse.core.runtime.adaptor.EclipseStarte
r
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:556)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1287)

---

