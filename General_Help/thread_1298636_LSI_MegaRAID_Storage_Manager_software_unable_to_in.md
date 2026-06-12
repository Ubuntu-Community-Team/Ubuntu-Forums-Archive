---
title: "LSI MegaRAID Storage Manager software unable to initialize"
date: 2009-10-23
forum: General Help
---

### Post by Allan Tung on 2009-10-23
Hi, i am Ubuntu newbie. I wish to set a RAID 1 configuration in my pc with LSI MegaRAID 8480 HBA card and two Western Digital 500GB drives.
 
Note that this LSI HBA card does not suppot web BIOS settings which allow me to set the RAID configuration before the Ubuntu OS boot up. Therefore, i have no choice and try to install the MegaRAID Storage Manager software where it can download directly from the LSI official website. 
 
I already convert the MegaRAID Storage Manager software from RPM file into debian package via alien. Next, i install the MegaRAID Storage Manager software and it looks smooth in the entire installation process. 
 
The problem occurs when i try to open the software in Terminal. The Terminal shows the following message:
 
ftc@FTC-0000:~$ cd /usr/local/MegaRAIDStorageManager
ftc@FTC-0000:/usr/local/MegaRAIDStorageManager$ ./startupui.shSocket connection to 172.22.30.254 failed once..try again
Socket connection to 172.22.30.254 failed on retry
Fatal Error : Can not create SASKernel object !
java.net.ConnectException: Connection refused
at java.net.PlainSocketImpl.socketConnect(Native Method)
at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
at java.net.Socket.connect(Socket.java:525)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.connect(SSLSocketImpl.java:550)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.<init>(SSLSocketImpl.java:353)
at com.sun.net.ssl.internal.ssl.SSLSocketFactoryImpl.createSocket(SSLSocketFactoryImpl.java:71)
at Framework.Network.CachedSSLSocketFactory.createSocket(Unknown Source)
at KernelNetwork.RAIDSocket.processCommand(Unknown Source)
at SASKernel.SASKernel.registerWithFramework(Unknown Source)
at SASKernel.SASKernel.<init>(Unknown Source)
at SASKernel.SASKernel.getInstance(Unknown Source)
at GUI.VivaldiStartupDialog.discoverHosts(Unknown Source)
at GUI.VivaldiStartupDialog.<init>(Unknown Source)
at GUI.VivaldiStartupDialog.main(Unknown Source)
Terminating ....
Oct 21, 2009 12:39:24 PM java.util.prefs.FileSystemPreferences syncWorld
WARNING: Couldn't flush system prefs: java.util.prefs.BackingStoreException: /etc/.java/.systemPrefs/com create failed.
 
Based on my observation, the software unable to initialize due to 172.22.30.254 was not found. 
 
Anyone can help me to solve this? Thank you.

---

