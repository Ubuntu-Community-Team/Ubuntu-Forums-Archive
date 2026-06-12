---
title: "Need help with Java"
date: 2011-02-05
forum: General Help
---

### Post by ImageJPEG on 2011-02-05
I'm currently running Ubuntu 10.10 64 bit. I'm trying to get the 32 bit Java JRE installed so I can get Frostwire working. For some reason I had Frostwire working on OpenJDK. It doesn't now though, so I downloaded the Java-JRE file from Java's website for 32 bit systems (because Frostwire is 32 bit). Anyway, I try to start it up again and it wont work still...so I try:

> sudo update-java-alternatives -lAnd this is what I get:

> java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdkThat's the only entry...there's nothing about Java's own closed source JRE in there.

Help would be greatly appreciated.

---

### Post by YesWeCan on 2011-02-05
try
'which java' and 'java -version'
That will tell you what your default java is and where it is. OpenJava may still be in your PATH.

You might consider uninstalling all the OpenJava stuff. That's what I do on every Ubuntu install and then I install the proper Oracle/Sun version. I had a bad experience with OpenJava and IcedTea when I first switched to Ubuntu 2 years ago.

Remember to add the new java path to PATH. Remember to look up how to add the Mozilla plugin for Firefox. This involves adding a symbolic link in the Mozilla plugins directory to a .so file in the jre directory.

---

### Post by ImageJPEG on 2011-02-06
Okay, so I uninstalled the OpenJRE and whatnot and added the PATH and still doesn't work. I even removed the java link files from /etc/alternatives and /usr/bin and replaced them with java links from Sun's own Java JRE. When I run the update-java-alternatives -l command I get the same thing...


Wait a minute...when I reinstalled Frostwire, it installed OpenJDK again...WTF???

---

### Post by Perfect Storm on 2011-02-06
Why not installing sun java from the repositories, just enable "Partners".

---

### Post by ImageJPEG on 2011-02-06
> josh@Sapphire:~$ frostwire
HOSTNAME IS Sapphire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_23]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: .:lw-azureus.jar:lw-collection.jar:lw-common.jar:lw-http.jar:lw-io.jar:lw-mojito.jar:lw-net.jar:lw-nio.jar:lw-resources.jar:lw-rudp.jar:lw-security.jar:lw-setting.jar:lw-statistic.jar:aopalliance.jar:asm-3.1.jar:cglib-nodep-2.2.jar:clink.jar:commons-codec-1.3.jar:commons-logging.jar:daap.jar:forms.jar:foxtrot.jar:FrostWire.jar:gettext-commons.jar:gson-1.4.jar:guice-1.0.jar:httpclient-4.0.jar:httpcore-4.0.1.jar:httpcore-nio-4.0.1.jar:icu4j.jar:jaudiotagger.jar:jcip-annotations.jar:jcraft.jar:jdic.jar:jflac.jar:jl.jar:jmdns.jar:junit.jar:jython.jar:log4j.jar:looks.jar:messages.jar:mp3spi.jar:netx.jar:onion-common.jar:onion-fec.jar:splash.jar:tritonus.jar:vorbisspi.jar
1: Main.main([Ljava.lang.String;@19821f)
java.io.IOException: Stream closed
Loading hostiles
ThemeFileHandler - unable to extract theme! *silent warning* frostwirePro_theme.fwtp
ThemeFileHandler - unable to extract theme! *silent warning* frostwirePro_theme.fwtp
LocalIPFilter.refreshHostsImpl() - BadHosts -> 159575
****STARTUP DEBUG: Is this a supported windows or Mac? false
**OverlayAd.image() - OVERLAY AD, im going to load:file:///home/josh/.frostwire4.20/overlays/beyond_the_game_overlay.jpg
LocalIPFilter.refreshHostsImpl() - BadHosts -> 557902
UpdateManager.scheduleUpdateCheckTask() - TimerTask.run()
UpdateManager.checkForUpdates() - Invoked
Reading update file from [http://update.frostwire.com](http://update.frostwire.com)
java.lang.ExceptionInInitializerError
    at com.limegroup.gnutella.gui.Initializer$6.run(Unknown Source)
    at java.awt.event.InvocationEvent.dispatch(Unknown Source)
    at java.awt.EventQueue.dispatchEvent(Unknown Source)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.run(Unknown Source)
Caused by: java.lang.UnsupportedOperationException: The system tray is not supported on the current platform.
    at java.awt.SystemTray.getSystemTray(Unknown Source)
    at com.limegroup.gnutella.gui.notify.TrayNotifier.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.notify.NotifyUserProxy.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.notify.NotifyUserProxy.<clinit>(Unknown Source)
    ... 9 more
HostileUpdaterWorker starting now.
UpdateManager.checkForUpdates() - We have overlays to update.
UpdateManager.updateOverlays() invoked.
OverlayImageManager.getCachedImagePath(): Image didn't change, using cached
OverlayImageManager.getCachedImagePath(): Image didn't change, using cached
UpdateManager.updateOverlays() - About to update secondary overlay - file:///home/josh/.frostwire4.20/overlays/brandon_hines_overlay.jpg
**OverlayAd.image() - OVERLAY AD, im going to load:file:///home/josh/.frostwire4.20/overlays/beyond_the_game_overlay.jpg
Smileys should be ACTIVE!
MD5: 1c76bb54b98cb010c443786047eca71a
HostilesUpdater.alreadyHaveValidHostilesTxt() - Done. We have a good hostiles.txt already
_date : 1296976454121
_md5 : 1C76BB54B98CB010C443786047ECA71A
_status : INITIATED
_torrentURL : [http://dl.frostwire.com/torrents/hostiles/hostiles.txt.19.zip.torrent](http://dl.frostwire.com/torrents/hostiles/hostiles.txt.19.zip.torrent)
_version : 19

HostilesUpdater.processMessage() HostilesUpdater.checkHostilesMetaData(): Something went wrong the last time
HostileUpdaterWorker ending now.


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_23"
Java(TM) SE Runtime Environment (build 1.6.0_23-b05)
Java HotSpot(TM) Client VM (build 19.0-b09, mixed mode, sharing)

Look up at top...it says: "Suitable java version found [java = 1.6.0_23]"

Which is the Java version I downloaded from Sun's website...gah...this is being a pain...I've never had issues like this before.

---

### Post by YesWeCan on 2011-02-06
> **Artificial Intelligence said:**
> Why not installing sun java from the repositories, just enable "Partners".
For one thing, if you do that and then visit [www.java.com](www.java.com) and click on "Do I Have Java?" it will tell you that your Java is out of date.
Why aren't the repositories kept up to date?

---

### Post by runeh76 on 2011-02-06
```
sudo add-apt-repository 'deb http://archive.canonical.com/ubuntu maverick partner'
sudo apt-get update 
sudo apt-get install sun-java6-plugin
sudo apt-get remove icedtea6-plugin openjdk-6-jre
```


edit: I did check that latest java version "1.6.0_23" and notice this i586 !
hmm.. are u sure this is correct one?

I also went that java.com to test my version AND got this:

---------------------------------------------------------------------------------------------
Verifying Java Version
Oops! You don't have the recommended Java installed.
Your Java version is Version 6 Update 22. Please click the button below to get the recommended Java for your computer.
NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.

Download Free Java Software
Version 6 Update 23
-------------------------------------------------------------------------------------------
Where i can get i386 version or does this matter (i have amd 64b prosessor, but im running 32b ubuntu and allways have used only 32b softwares?)

edit II: Could someone correct this? I did googling this i386 i586 i686 thing, and it seems that only thing what i need to know is processor bit, NOT Ubuntu??? So i386&i586 supports above.

"I pulled this off another site. Apparently, i386 is considered the safest. While others may work with your system architecture, the i386 is guaranteed to work.

i386 - Optimized for 386 and above processors (386, 486, 586 (Pentium), beyond).

i486 - You rarely see these if ever. Optimized for 486 and above processors (486, 586(Pentium), beyond).

i586 - Optimized for 586/Pentium processors (586 (pentium), beyond).

i686 - Optimized for that beyond category (Pentium Pro???, Pentium II, Pentium III, Penmtium IV, K6-x, Atholon, Duron, Celeron (later only???), "

---

