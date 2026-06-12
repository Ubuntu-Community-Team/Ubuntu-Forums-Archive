---
title: "Opera Java not successful"
date: 2009-07-04
forum: General Help
---

### Post by Bill- on 2009-07-04
I am using an ISP that requires me to log in and, using java, then opens a separate window which must remain open for as long as I want internet access.

I have successfully configured Firefox to work with Java, but want also configure Opera to be able to open up Internet access (for example if Firefox gets upgraded or dies and needs to access the internet to recover - which it can't do without this Java window open...)

I have checked that Opera should work with Java (and other java website seem to be ok)

Tools -> Quick Preferences has Java and Javascript and plugins all enabled
Tools-> Preferences - 'Advanced' tab, and the 'Content' item off this tab, has 'Enable Java' box checked
'Java Options' button shows the path  /usr/lib/jvm/java-6-sun/jre/lib/i386
'Validate Java path' button is successful 

I opened the opera Java console and no errors were displayed. 
Below is the capture of the Firefox Java Console, so you can see what a successful activity looks like. 
[INDENT][INDENT]Java Plug-in 1.6.0_13
Using JRE version 1.6.0_13 Java HotSpot(TM) Client VM
User home directory = /home/xbxbxb

----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

basic: Added progress listener: sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@13bad12
basic: Loading Java Applet ...
network: No certificate info for unsigned JAR file: [http://192.168.2.1:65535/applet.jar](http://192.168.2.1:65535/applet.jar)
network: Cache entry found [url: http://192.168.2.1:65535/applet.jar, version: null]
network: Connecting http://192.168.2.1:65535/applet.jar with proxy=DIRECT
network: Connecting http://192.168.2.1:65535/ with proxy=DIRECT
network: Connecting http://192.168.2.1:65535/applet.jar with cookie "JSESSIONID=elfmp9eud2"
network: ResponseCode for http://192.168.2.1:65535/applet.jar : 304
network: Encoding for http://192.168.2.1:65535/applet.jar : null
network: Disconnect connection to http://192.168.2.1:65535/applet.jar
basic: Applet loaded.
basic: Applet resized and added to parent container
basic: PERF: AppletExecutionRunnable - applet.init() BEGIN ; jvmLaunch dt 97951 us, pluginInit dt 614061 us, TotalTime: 712012 us
basic: Applet initialized
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@13bad12
basic: Applet made visible
basic: Starting applet
basic: Applet started
basic: Told clients applet is started
network: Connecting http://192.168.2.1:8088/ with proxy=DIRECT
[/INDENT][/INDENT]
This may be an Opera security issue or some other non java problem too.  Any ideas please on : 
1. What may be going wrong
2. What other info would be helpful to capture or try to help isolate the problem (and how to do it, as I'm a Ubuntu newbie).

The "error" I get is the pre-requisite window opens, but is empty and doesn't actually establish an internet connection. When I do it in Forefox, the window opens, shows connected etc and internet access is fine.

I am using Ubuntu 9.04
Firefox 3.0.11

Opera :
Version information
Version
9.64
Build
2480
Platform
Linux
System
i686, 2.6.28-13-generic
Qt library
3.3.5
Java
Java Runtime Environment installed
Browser identification

Opera/9.64 (X11; Linux i686; U; en) Presto/2.1.1

Thanks in advance for your help.

---

