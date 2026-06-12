---
title: "knetworkmanager crashes"
date: 2010-04-07
forum: General Help
---

### Post by evilnone on 2010-04-07
As the title says I keep having knetworkmanager crash on bootup and whenever I try to start it manually it does the same thing. Gives a segment fault.

Output from command line:
```
 evilnone@evilnone-linux:~$ knetworkmanager

knetworkmanager(1781)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_networkmanager07.so" 
does not offer a qt_plugin_instance function.

Connecting to deprecated signal 
QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)

KCrash: Application 'knetworkmanager' crashing...

sock_file=/home/evilnone/.kde/socket-evilnone-linux/kdeinit4__0
knetworkmanager(1780): Communication problem with  "knetworkmanager" , it probably crashed.
 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.knetworkmanager was not provided by any .service files" " 


```

The only thing that has changed is I installed some debug tools for amarok when prompted as it kept crashing while loading my library. I had to boot into windows to post this, is there anything I can do to fix this?

---

### Post by Chame_Wizard on 2010-04-07
What does the log file  and dmesg read?

Try
```
sudo aptitude install kdbg kdenetwork-dbg
```


For various debug symbols
```
sudo aptitude search dbg
```

---

### Post by evilnone on 2010-04-07
I have no internet connection on kubuntu since knetworkmanager crashes

---

### Post by Chame_Wizard on 2010-04-07
Post your```
ifconfig
```here

---

### Post by crocodile2u on 2010-05-11
**evilnone**, if your computer obtains IP address via DHCP, then, regardless of whether knetworkmanager crashes or not - you may open terminal and say

$ sudo dhclient

This was the case with me (knetworkmanager crashed with the same message). If you are not using DHCP - then you'll have to study ifconfig manual page (man ifconfig) and/or the format of /etc/network/interfaces in order to make your network connection work.

---

### Post by neanderslob on 2011-08-09
So I know it's been a while since this thread was active but I figured it out on mine. 

As context, mine broke while I was trying to connect to a new router and I must have done something funky to it.

The problem was in my home directory, specifically: ~/.kde/share/apps/networkmanagement.  All I had to do was change the name of the networkmanagement directory to something else (networkmanagement.bu), so that it wouldn't be referenced by the system.  Then I restarted my computer, knetworkmanager came up just fine.  

But of course, none of my network manager settings were saved.  So what I did was I connected to the internet, went into my ketworkmanager.bu directory and copied all, the text files EXCEPT THOSE CREATED ON THE DAY I STARTED HAVING PROBLEMS, under the sub-directory "connections/" back over to the knetworkmanager/connections directory that the system automatically created in its stead.  In order for the system to automatically create this directory, you must FIRST connect to the internet.   Bada-bing bada-boom no problems.

On a personal piece of advice: TRY THIS BEFORE you try re-installing your operating system.  If your problem was the same as mine, it won't go away if you re-install andkeep your home directory!!!!

:guitar:

---

