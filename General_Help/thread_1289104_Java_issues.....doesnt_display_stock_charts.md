---
title: "Java issues.....doesnt display stock charts"
date: 2009-10-12
forum: General Help
---

### Post by mak_20789 on 2009-10-12
Hello,
I am using Hardy and I installed java some time back and was trying to see stock charts. Giving the link here:

[http://charting.bseindia.com/charting/index.asp?SYMBOL=590052](http://charting.bseindia.com/charting/index.asp?SYMBOL=590052)

There are 2 sections here: one small rectangle on left where some options are displayed and bigger one on right where chart is displayed.
Until now, i used to see chrt on right, but everything on left was not accessible, so I couldnt make any changes or see different chart of same stock.
Today, I searched and did following 2 things:
First I gave this command:

sudo apt-get install openjdk-6-jre

It took some time to download, but even then I faced the same problem.
Again, I looked up this site and gave following command:

sudo aptitude install sun-java6-jre sun-java6-plugin 

Now, when I try to see the chart, the panel on left is accessible, but I dont see any chart on right.
I get an error.Its says:

There was an error while executing the application.

When I click on details, I get:


Java Plug-in 1.6.0_16
Using JRE version 1.6.0_16-b01 Java HotSpot(TM) Client VM
User home directory = /home/mahesh
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


Reading certificates from 11 [http://charting.bseindia.com/charting/equis/metastock/ms4javav2.jar](http://charting.bseindia.com/charting/equis/metastock/ms4javav2.jar) | /home/mahesh/.java/deployment/cache/6.0/53/20ef9b75-4adbc550.idx
MetaStock Online
Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
Version 2.5.4
Mar 27 2000 12:00 MST
MS4Java --> Feature level at version 2.0.0
MS4Java --> In CheckClientKey()
MS4Java --> This client key (#8FB-700-0631) will expire on 3/2010.
MS4Java --> Client key (8FB-700-0631) is valid
MS4Java --> Language URL: 'http://charting.bseindia.com/charting/equis/metastock/english.lang'
BColor : e6eef1, FColor : 0089CF
MS4Java --> Parameters:
MS4Java -->   AdsURL                 = [http://charting.bseindia.com/charting/equis/metastock/ads](http://charting.bseindia.com/charting/equis/metastock/ads)
MS4Java -->   Applet Name Font Size  = 12
MS4Java -->   Applet Name Position   = west
MS4Java -->   AutoPriceStyleChanges  = true
MS4Java -->   Copyright notice       = Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
MS4Java -->   DateFormat             = MM/DD/YY
MS4Java -->   EODDataURL             = [http://charting.bseindia.com/charting/history.asp](http://charting.bseindia.com/charting/history.asp)
MS4Java -->   ForceUpperParam        = true
MS4Java -->   HelpURL                = [http://charting.bseindia.com/charting/help/index.asp](http://charting.bseindia.com/charting/help/index.asp)
MS4Java -->   HumanLanguage          = ENGLISH
MS4Java -->   IntradayDataURL        = [http://charting.bseindia.com/charting/intraday.asp](http://charting.bseindia.com/charting/intraday.asp)
MS4Java -->   MS4JVersion            = 2.0.0
MS4Java -->   NewsURL                = [http://www.bseindia.com/charting/news.asp?SYMBOL=](http://www.bseindia.com/charting/news.asp?SYMBOL=)
MS4Java -->   RelativeStrengthSymbol = BSE303
MS4Java -->   Removed Indicators     = NONE
MS4Java -->   SearchDialogHeight     = 0
MS4Java -->   SetDefaultIndicator    = Moving Average (value1=15, value2=15)
MS4Java -->   ShowAdPanel            = false
MS4Java -->   ShowData               = true
MS4Java -->   ShowDataErrorMessages  = true
MS4Java -->   ShowDebugMessages      = true
MS4Java -->   ShowDocumentHelpFrame  = _self
MS4Java -->   ShowDocumentNewsFrame  = _new
MS4Java -->   ShowHelpButton         = true
MS4Java -->   ShowIntradayVolume     = true
MS4Java -->   ShowNewsButton         = true
MS4Java -->   ShowPeriodicityControl = false
MS4Java -->   ShowPriceStyleControl  = false
MS4Java -->   ShowSymbolControl      = false
MS4Java -->   YAxisWidth             = 50
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1720)
	at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
[http://charting.bseindia.com/charting/indices.asp](http://charting.bseindia.com/charting/indices.asp)
Exception in thread "Thread-12" java.lang.NullPointerException
	at equis.metastock.MS4Java.run([DashoPro-V1.2-120198])
	at java.lang.Thread.run(Thread.java:619)
url =http://charting.bseindia.com/charting/G_sec_choice.asp
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://charting.bseindia.com/charting/G_sec_choice.asp](http://charting.bseindia.com/charting/G_sec_choice.asp)
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313))
	at java.net.URL.openStream(URL.java:1010)
	at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
	at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
result url  for checking BSE303 
Exception in SetSymbol()
java.lang.NullPointerException
	at equis.metastock.TestMS4Java.SetSymbol(TestMS4Java.java:420)
	at equis.metastock.TestMS4Java.action(TestMS4Java.java:545)
	at java.awt.Component.handleEvent(Component.java:6509)
	at equis.metastock.TestMS4Java.handleEvent(TestMS4Java.java:1140)
	at java.awt.Component.postEvent(Component.java:4922)
	at java.awt.Component.postEvent(Component.java:4932)
	at java.awt.Component.dispatchEventImpl(Component.java:4646)
	at java.awt.Component.dispatchEvent(Component.java:4460)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
BColor : e6eef1, FColor : 0089CF
[http://charting.bseindia.com/charting/indices.asp](http://charting.bseindia.com/charting/indices.asp)
SENSEX
Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
Version 2.5.4
Mar 27 2000 12:00 MST
MS4Java --> Feature level at version 2.0.0
MS4Java --> In CheckClientKey()
MS4Java --> This client key (#8FB-700-0631) will expire on 3/2010.
MS4Java --> Client key (8FB-700-0631) is valid
MS4Java --> Language URL: 'http://charting.bseindia.com/charting/equis/metastock/english.lang'
MS4Java --> Parameters:
MS4Java -->   AdsURL                 = [http://charting.bseindia.com/charting/equis/metastock/ads](http://charting.bseindia.com/charting/equis/metastock/ads)
MS4Java -->   Applet Name Font Size  = 12
MS4Java -->   Applet Name Position   = west
MS4Java -->   AutoPriceStyleChanges  = true
MS4Java -->   Copyright notice       = Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
MS4Java -->   DateFormat             = MM/DD/YY
MS4Java -->   EODDataURL             = [http://charting.bseindia.com/charting/history.asp](http://charting.bseindia.com/charting/history.asp)
MS4Java -->   ForceUpperParam        = true
MS4Java -->   HelpURL                = [http://charting.bseindia.com/charting/help/index.asp](http://charting.bseindia.com/charting/help/index.asp)
MS4Java -->   HumanLanguage          = ENGLISH
MS4Java -->   IntradayDataURL        = [http://charting.bseindia.com/charting/intraday.asp](http://charting.bseindia.com/charting/intraday.asp)
MS4Java -->   MS4JVersion            = 2.0.0
MS4Java -->   NewsURL                = [http://www.bseindia.com/charting/news.asp?SYMBOL=](http://www.bseindia.com/charting/news.asp?SYMBOL=)
MS4Java -->   RelativeStrengthSymbol = BSE303
MS4Java -->   Removed Indicators     = NONE
MS4Java -->   SearchDialogHeight     = 0
MS4Java -->   SetDefaultIndicator    = Moving Average (value1=15, value2=15)
MS4Java -->   ShowAdPanel            = false
MS4Java -->   ShowData               = true
MS4Java -->   ShowDataErrorMessages  = true
MS4Java -->   ShowDebugMessages      = true
MS4Java -->   ShowDocumentHelpFrame  = _self
MS4Java -->   ShowDocumentNewsFrame  = _new
MS4Java -->   ShowHelpButton         = true
MS4Java -->   ShowIntradayVolume     = true
MS4Java -->   ShowNewsButton         = true
MS4Java -->   ShowPeriodicityControl = false
MS4Java -->   ShowPriceStyleControl  = false
MS4Java -->   ShowSymbolControl      = false
MS4Java -->   YAxisWidth             = 50
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1720)
	at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
url =http://charting.bseindia.com/charting/G_sec_choice.asp
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://charting.bseindia.com/charting/G_sec_choice.asp](http://charting.bseindia.com/charting/G_sec_choice.asp)
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313))
	at java.net.URL.openStream(URL.java:1010)
	at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
	at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
BColor : e6eef1, FColor : 0089CF
[http://charting.bseindia.com/charting/indices.asp](http://charting.bseindia.com/charting/indices.asp)
SENSEX
Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
Version 2.5.4
Mar 27 2000 12:00 MST
MS4Java --> Feature level at version 2.0.0
MS4Java --> In CheckClientKey()
MS4Java --> This client key (#8FB-700-0631) will expire on 3/2010.
MS4Java --> Client key (8FB-700-0631) is valid
MS4Java --> Language URL: 'http://charting.bseindia.com/charting/equis/metastock/english.lang'
MS4Java --> Parameters:
MS4Java -->   AdsURL                 = [http://charting.bseindia.com/charting/equis/metastock/ads](http://charting.bseindia.com/charting/equis/metastock/ads)
MS4Java -->   Applet Name Font Size  = 12
MS4Java -->   Applet Name Position   = west
MS4Java -->   AutoPriceStyleChanges  = true
MS4Java -->   Copyright notice       = Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
MS4Java -->   DateFormat             = MM/DD/YY
MS4Java -->   EODDataURL             = [http://charting.bseindia.com/charting/history.asp](http://charting.bseindia.com/charting/history.asp)
MS4Java -->   ForceUpperParam        = true
MS4Java -->   HelpURL                = [http://charting.bseindia.com/charting/help/index.asp](http://charting.bseindia.com/charting/help/index.asp)
MS4Java -->   HumanLanguage          = ENGLISH
MS4Java -->   IntradayDataURL        = [http://charting.bseindia.com/charting/intraday.asp](http://charting.bseindia.com/charting/intraday.asp)
MS4Java -->   MS4JVersion            = 2.0.0
MS4Java -->   NewsURL                = [http://www.bseindia.com/charting/news.asp?SYMBOL=](http://www.bseindia.com/charting/news.asp?SYMBOL=)
MS4Java -->   RelativeStrengthSymbol = BSE303
MS4Java -->   Removed Indicators     = NONE
MS4Java -->   SearchDialogHeight     = 0
MS4Java -->   SetDefaultIndicator    = Moving Average (value1=15, value2=15)
MS4Java -->   ShowAdPanel            = false
MS4Java -->   ShowData               = true
MS4Java -->   ShowDataErrorMessages  = true
MS4Java -->   ShowDebugMessages      = true
MS4Java -->   ShowDocumentHelpFrame  = _self
MS4Java -->   ShowDocumentNewsFrame  = _new
MS4Java -->   ShowHelpButton         = true
MS4Java -->   ShowIntradayVolume     = true
MS4Java -->   ShowNewsButton         = true
MS4Java -->   ShowPeriodicityControl = false
MS4Java -->   ShowPriceStyleControl  = false
MS4Java -->   ShowSymbolControl      = false
MS4Java -->   YAxisWidth             = 50
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1720)
	at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
url =http://charting.bseindia.com/charting/G_sec_choice.asp
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://charting.bseindia.com/charting/G_sec_choice.asp](http://charting.bseindia.com/charting/G_sec_choice.asp)
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313))
	at java.net.URL.openStream(URL.java:1010)
	at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
	at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
BColor : e6eef1, FColor : 0089CF
[http://charting.bseindia.com/charting/indices.asp](http://charting.bseindia.com/charting/indices.asp)
SENSEX
Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
Version 2.5.4
Mar 27 2000 12:00 MST
MS4Java --> Feature level at version 2.0.0
MS4Java --> In CheckClientKey()
MS4Java --> This client key (#8FB-700-0631) will expire on 3/2010.
MS4Java --> Client key (8FB-700-0631) is valid
MS4Java --> Language URL: 'http://charting.bseindia.com/charting/equis/metastock/english.lang'
MS4Java --> Parameters:
MS4Java -->   AdsURL                 = [http://charting.bseindia.com/charting/equis/metastock/ads](http://charting.bseindia.com/charting/equis/metastock/ads)
MS4Java -->   Applet Name Font Size  = 12
MS4Java -->   Applet Name Position   = west
MS4Java -->   AutoPriceStyleChanges  = true
MS4Java -->   Copyright notice       = Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
MS4Java -->   DateFormat             = MM/DD/YY
MS4Java -->   EODDataURL             = [http://charting.bseindia.com/charting/history.asp](http://charting.bseindia.com/charting/history.asp)
MS4Java -->   ForceUpperParam        = true
MS4Java -->   HelpURL                = [http://charting.bseindia.com/charting/help/index.asp](http://charting.bseindia.com/charting/help/index.asp)
MS4Java -->   HumanLanguage          = ENGLISH
MS4Java -->   IntradayDataURL        = [http://charting.bseindia.com/charting/intraday.asp](http://charting.bseindia.com/charting/intraday.asp)
MS4Java -->   MS4JVersion            = 2.0.0
MS4Java -->   NewsURL                = [http://www.bseindia.com/charting/news.asp?SYMBOL=](http://www.bseindia.com/charting/news.asp?SYMBOL=)
MS4Java -->   RelativeStrengthSymbol = BSE303
MS4Java -->   Removed Indicators     = NONE
MS4Java -->   SearchDialogHeight     = 0
MS4Java -->   SetDefaultIndicator    = Moving Average (value1=15, value2=15)
MS4Java -->   ShowAdPanel            = false
MS4Java -->   ShowData               = true
MS4Java -->   ShowDataErrorMessages  = true
MS4Java -->   ShowDebugMessages      = true
MS4Java -->   ShowDocumentHelpFrame  = _self
MS4Java -->   ShowDocumentNewsFrame  = _new
MS4Java -->   ShowHelpButton         = true
MS4Java -->   ShowIntradayVolume     = true
MS4Java -->   ShowNewsButton         = true
MS4Java -->   ShowPeriodicityControl = false
MS4Java -->   ShowPriceStyleControl  = false
MS4Java -->   ShowSymbolControl      = false
MS4Java -->   YAxisWidth             = 50
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1720)
	at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
url =http://charting.bseindia.com/charting/G_sec_choice.asp
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://charting.bseindia.com/charting/G_sec_choice.asp](http://charting.bseindia.com/charting/G_sec_choice.asp)
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1313))
	at java.net.URL.openStream(URL.java:1010)
	at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
	at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1530)
	at java.lang.Thread.run(Thread.java:619)



Can someone please help me?


Thank you.

---

### Post by Mighty_Joe on 2009-10-12
I see the same thing.  It works fine for me in Windows XP(Java version is Version 6 Update 13), but loading it in Crunchbang gets an error (Version 6 Update 16).  
Searching says you aren't the [only one]("http://ubuntuforums.org/archive/index.php/t-1220028.html"). 
Looking at the [vendor site]("http://www.equis.com/") it doesn't look like they're aware of any problems.

---

