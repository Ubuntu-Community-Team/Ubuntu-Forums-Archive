---
title: "using vuze on maverick was going well but problems"
date: 2010-09-02
forum: General Help
---

### Post by shantiq on 2010-09-02
all was well at first but now it all says fine on the gui but nothing happens


can anyone stop possible reasons for that from terminal reading


```
shantiq@shantiq-desktop:~$ vuze
[COLOR="Red"][warning] /usr/bin/vuze: No java runtime was found
[warning] /usr/bin/vuze: No JAVA_CMD set for run_java, falling back to JAVA_CMD = java[/COLOR]
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.5.1.jar ; file:/home/shantiq/
DEBUG::Thu Sep 02 15:03:07 BST 2010::org.gudy.azureus2.core3.secur*******pl.SESecurityManagerImpl::initialise::177:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::214,ConfigurationManager::initialise::153,ConfigurationManager::getInstance::86,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,SystemProperties::getUserPath::234,LocalSocketHelper::<init>::40,LocalSocketHelper::connect::68,LocalSocketHelper::listen::94,StartServer::<init>::71,Main::<init>::64,Main::main::255,Method::invoke::-1,Main::directLaunch::229,Main::main::132,Method::invoke::-1,MainExecutor$1::run::37,Thread::run::-1
UIFunctions/ImageLoad took 50ms
new shell took 402ms
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=26 null
new shell setup took 389ms
skinlisteners init took 0ms
skin init took 408ms
MainMenu init took 376ms
createWindow init took 0ms
skin layout took 0ms
pre skin widgets init took 77ms
hooks init took 0ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@35e7c381
skin widgets (1/2) init took 729ms
skin widgets init took 402ms
pre SWTInstance init took 0ms
Init Core Columns took 339ms
SWTInstance init took 0ms
shell.layout took 49ms
---------SHOWN AT 1283436199234;3873ms
---------DONE DISPATCH AT 1283436201340;5954ms
---------READY AT 1283436201415;6029ms
shell.open took 2206ms
processStartupDMS took 0ms
vuzeactivities init took 0ms
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
Locale Initializing took 26ms
03945:    Core: 349ms for activity between 'Loading Plugin: azupnpav' and 'Loading Torrents'
04295:    Core: 352ms for activity between 'Initialising Global Torrent Manager' and 'Loading Plugin: azupdater'
04383:    Core: 37ms for activity between 'Loading Plugin: Start/Stop Rules' and 'Loading Plugin: Torrent Removal Rules'
04415:    Core: 12ms for activity between 'Loading Plugin: Torrent Removal Rules' and 'Loading Plugin: Share Hoster'
04447:    Core: 38ms for activity between 'Loading Plugin: Share Hoster' and 'Loading Plugin: Plugin Update Checker'
04524:    Core: 52ms for activity between 'Loading Plugin: UPnP' and 'Loading Plugin: DHT'
04573:    Core: 37ms for activity between 'Loading Plugin: DHT' and 'Loading Plugin: DHT Tracker'
04620:    Core: 26ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
04663:    Core: 24ms for activity between 'Loading Plugin: Magnet URI Handler' and 'Loading Plugin: Core Update Checker'
04670:    Core: 13ms for activity between 'Loading Plugin: Core Update Checker' and 'Loading Plugin: Core Patch Checker'
04673:    Core: 13ms for activity between 'Loading Plugin: Platform Checker' and 'Loading Plugin: External Seed'
04717:    Core: 13ms for activity between 'Loading Plugin: Network Status' and 'Loading Plugin: Buddy'
04794:    Core: 77ms for activity between 'Loading Plugin: Buddy' and 'Loading Plugin: RSS'
05454:    Core: 675ms for activity between 'Loading Plugin: RSS' and 'Initialising Plugin: UPnP Media Server'
05496:    Core: 26ms for activity between 'Initialising Plugin: UPnP Media Server' and 'Initialising Plugin: Azureus Update Support'
05603:    Core: 102ms for activity between 'Initialising Plugin: Start/Stop Rules' and 'Initialising Plugin: Download Remove Rules'
05755:    Core: 126ms for activity between 'Initialising Plugin: Share Hoster' and 'Initialising Plugin: PluginUpdate'
05825:    Core: 63ms for activity between 'Initialising Plugin: PluginUpdate' and 'Initialising Plugin: Universal Plug and Play (UPnP)'
05865:    Core: 25ms for activity between 'Initialising Plugin: Universal Plug and Play (UPnP)' and 'Initialising Plugin: Distributed DB'
05921:    Core: 63ms for activity between 'Initialising Plugin: Distributed DB' and 'Initialising Plugin: Distributed Tracker'
05953:    Core: 26ms for activity between 'Initialising Plugin: Magnet URI Handler' and 'Initialising Plugin: CorePatcher'
05962:    Core: 12ms for activity between 'Initialising Plugin: CorePatcher' and 'Initialising Plugin: azplatform2'
05991:    Core: 13ms for activity between 'Initialising Plugin: External Seed' and 'Initialising Plugin: CoreUpdater'
06053:    Core: 51ms for activity between 'Initialising Plugin: CoreUpdater' and 'Initialising Plugin: LAN Peer Finder'
06065:    Core: 25ms for activity between 'Initialising Plugin: LAN Peer Finder' and 'Initialising Plugin: Network Status'
06111:    Core: 51ms for activity between 'Initialising Plugin: Friends' and 'Initialising Plugin: azintrss'
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=28 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=28 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=28 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=60 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=46 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=46 null
Core Initializing took 4593ms
DEBUG::Thu Sep 02 15:03:26 BST 2010::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::837:
    ResourceDownloaderURLImpl$2::run::395,AEThread2$threadWrapper::run::287
java.lang.NoSuchMethodError: method java.net.URL.openConnection with signature (Ljava.net.Proxy;)Ljava.net.URLConnection; was not found.
   at com.aelitis.azureus.core.util.Java15Utils.openConnectionForceNoProxy(Java15Utils.java:86)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.openConnection(ResourceDownloaderURLImpl.java:986)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:527)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.run(ResourceDownloaderURLImpl.java:395)
   at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
DEBUG::Thu Sep 02 15:03:26 BST 2010::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::837:
    ResourceDownloaderURLImpl$2::run::395,AEThread2$threadWrapper::run::287
java.lang.NoSuchMethodError: method java.net.URL.openConnection with signature (Ljava.net.Proxy;)Ljava.net.URLConnection; was not found.
   at com.aelitis.azureus.core.util.Java15Utils.openConnectionForceNoProxy(Java15Utils.java:86)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.openConnection(ResourceDownloaderURLImpl.java:986)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:527)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.run(ResourceDownloaderURLImpl.java:395)
   at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
DEBUG::Thu Sep 02 15:03:26 BST 2010::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::837:
    ResourceDownloaderURLImpl$2::run::395,AEThread2$threadWrapper::run::287
java.lang.NoSuchMethodError: method java.net.URL.openConnection with signature (Ljava.net.Proxy;)Ljava.net.URLConnection; was not found.
   at com.aelitis.azureus.core.util.Java15Utils.openConnectionForceNoProxy(Java15Utils.java:86)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.openConnection(ResourceDownloaderURLImpl.java:986)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:527)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.run(ResourceDownloaderURLImpl.java:395)
   at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)

(Vuze:1857): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=30 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=32 null
double removal org.gudy.azureus2.core3.util.StringInterner$WeakStringEntry h=-1;s=46 null

```


the java runtime warning seems the 1st problem any idea how to fix that?


SOLUTION
==========


with much searching it transpired that the openjdk-6-source had become unhooked in the synaptic all i had to do was to tick it again      vuze runs almost entirely on java

---

