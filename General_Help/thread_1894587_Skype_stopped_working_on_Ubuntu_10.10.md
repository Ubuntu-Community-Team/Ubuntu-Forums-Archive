---
title: "Skype stopped working on Ubuntu 10.10"
date: 2011-12-12
forum: General Help
---

### Post by xlearner on 2011-12-12
Hello,

I am running ubuntu 10.10. I observed that skype has suddenly stopped working. I am unable to figure out what update has caused it.

When I run:
$ /usr/bin/skype 
/usr/bin/skype: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN16QIODevicePrivate4peekEPcx

I found this error on ubuntu skype documentation: [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting). But the comments there do not help me.

On searching on the net, I found the following interesting command:
$ ldd -r /usr/lib/libQtNetwork.so.4
	linux-gate.so.1 =>  (0xb7830000)
	libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0xb74c4000)
	libpthread.so.0 => /lib/libpthread.so.0 (0xb74aa000)
	libz.so.1 => /lib/libz.so.1 (0xb7494000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb73a9000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb738d000)
	libc.so.6 => /lib/libc.so.6 (0xb7230000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb722b000)
	librt.so.1 => /lib/librt.so.1 (0xb7222000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0xb7152000)
	libdl.so.2 => /lib/libdl.so.2 (0xb714e000)
	libm.so.6 => /lib/libm.so.6 (0xb7128000)
	/lib/ld-linux.so.2 (0xb7831000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb70f3000)
undefined symbol: _ZN16QIODevicePrivate4peekEPcx	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN16QIODevicePrivate4peekEx	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z14qDecodeDataUrlRK4QUrl	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK13QElapsedTimer7elapsedEv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK7QString7indexOfERK13QLatin1StringiN2Qt15CaseSensitivityE	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK13QElapsedTimer10hasExpiredEx	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData14detach_helper2EPFvPNS_4NodeEPvEPFvS1_Eii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData7append2ERKS_	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData12allocateNodeEi	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData6detachEi	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QMapData10createDataEi	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN13QElapsedTimer5startEv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN24QNonContiguousByteDevice12disableResetEv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory6createEP9QIODevice	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory6createEP11QRingBuffer	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData4freeEPS_i	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN7QStringC1EiN2Qt14InitializationE	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z9qBadAllocv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QVariantC1EiPKvj	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN7QString7replaceERK13QLatin1StringS2_N2Qt15CaseSensitivityE	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QMapData11node_createEPPNS_4NodeEii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN10QByteArray7replaceEPKciS1_i	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData11free_helperEPFvPNS_4NodeEE	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN10QByteArray6appendEPKci	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData8allocateEii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z14qt_safe_selectiP6fd_setS0_S0_PK7timeval	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory4wrapEP24QNonContiguousByteDevice	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData11detach_growEPii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK10QByteArray7indexOfEPKci	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN15QtSharedPointer20ExternalRefCountData9getAndRefEPK7QObject	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData10reallocateEPS_iii	(/usr/lib/libQtNetwork.so.4)

Then, I also found this script:
sudo sed -i 's/^\(\/usr\/local\/lib\/beidqt\)/#\1/' /etc/ld.so.conf
sudo rm /etc/ld.so.cache
sudo ldconfig
sudo apt-get install libqtgui4

I tried it. But it did not help me :-(! Any suggestions to get this work? Your help is really appreciated. Thanks!

---

### Post by oldtimer7777 on 2011-12-12
I've had this happen.

Uinstall skype. Use synaptic package manager.

sudo apt-get install synaptic
gksu synaptic

Then search for skype, right click on it and select "mark for complete removal". 

Clean the skype configuration files with Ubuntu Tweak package/config cleaner..  Then use bleachbit to clean your OS.

sudo apt-get install bleachbit

And then use that to really give your system a good cleaning, make sure not not accidentally delete your passwords with it... 

Then reinstall skype. 

sudo apt-get install skype

For more information on cleaning your system:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

Most users don't know that it is a good idea from time to time either. 

> **xlearner said:**
> Hello,

I am running ubuntu 10.10. I observed that skype has suddenly stopped working. I am unable to figure out what update has caused it.

When I run:
$ /usr/bin/skype 
/usr/bin/skype: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN16QIODevicePrivate4peekEPcx

I found this error on ubuntu skype documentation: [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting). But the comments there do not help me.

On searching on the net, I found the following interesting command:
$ ldd -r /usr/lib/libQtNetwork.so.4
    linux-gate.so.1 =>  (0xb7830000)
    libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0xb74c4000)
    libpthread.so.0 => /lib/libpthread.so.0 (0xb74aa000)
    libz.so.1 => /lib/libz.so.1 (0xb7494000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb73a9000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb738d000)
    libc.so.6 => /lib/libc.so.6 (0xb7230000)
    libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb722b000)
    librt.so.1 => /lib/librt.so.1 (0xb7222000)
    libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0xb7152000)
    libdl.so.2 => /lib/libdl.so.2 (0xb714e000)
    libm.so.6 => /lib/libm.so.6 (0xb7128000)
    /lib/ld-linux.so.2 (0xb7831000)
    libpcre.so.3 => /lib/libpcre.so.3 (0xb70f3000)
undefined symbol: _ZN16QIODevicePrivate4peekEPcx    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN16QIODevicePrivate4peekEx    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z14qDecodeDataUrlRK4QUrl    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK13QElapsedTimer7elapsedEv    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK7QString7indexOfERK13QLatin1StringiN2Qt15CaseSensitivityE    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK13QElapsedTimer10hasExpiredEx    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData14detach_helper2EPFvPNS_4NodeEPvEPFvS1_Eii    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData7append2ERKS_    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData12allocateNodeEi    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData6detachEi    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QMapData10createDataEi    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN13QElapsedTimer5startEv    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN24QNonContiguousByteDevice12disableResetEv    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory6createEP9QIODevice    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory6createEP11QRingBuffer    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData4freeEPS_i    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN7QStringC1EiN2Qt14InitializationE    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z9qBadAllocv    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QVariantC1EiPKvj    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN7QString7replaceERK13QLatin1StringS2_N2Qt15CaseSensitivityE    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QMapData11node_createEPPNS_4NodeEii    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN10QByteArray7replaceEPKciS1_i    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData11free_helperEPFvPNS_4NodeEE    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN10QByteArray6appendEPKci    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData8allocateEii    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z14qt_safe_selectiP6fd_setS0_S0_PK7timeval    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory4wrapEP24QNonContiguousByteDevice    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData11detach_growEPii    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK10QByteArray7indexOfEPKci    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN15QtSharedPointer20ExternalRefCountData9getAndRefEPK7QObject    (/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData10reallocateEPS_iii    (/usr/lib/libQtNetwork.so.4)

Then, I also found this script:
sudo sed -i 's/^\(\/usr\/local\/lib\/beidqt\)/#\1/' /etc/ld.so.conf
sudo rm /etc/ld.so.cache
sudo ldconfig
sudo apt-get install libqtgui4

I tried it. But it did not help me :-(! Any suggestions to get this work? Your help is really appreciated. Thanks!

---

### Post by xlearner on 2011-12-13
Hello All,

Suddenly skype has stopped working on ubuntu 10.10. (Actually, earlier I posted this thread on main ubuntu general forum as well. But I think it was removed from there). 

When I run the command:
$ /usr/bin/skype 
/usr/bin/skype: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN16QIODevicePrivate4peekEPcx

So any suggestion as to how to get rid of this error? Thanks!

---

### Post by xlearner on 2011-12-13
Dear Oldtimer,

Thanks for the reply. I tried running bleachit. It executed partially. Then it got hung in between. I closed it manually. 

When I installed skype again and tried launching it was giving the same error. So I don't know what to do. Any other suggestions?

Thanks

---

### Post by squaregoldfish on 2011-12-13
Skype quite often gets out of sync with the library versions installed on Ubuntu. The best solution is to download the static version from the Skype website - this is completely self-contained and comes with all the libraries it needs for itself, so it should work on any system.

[http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/)

The Static version is the last entry in the list when you hover over the Download Now button.

Steve.

---

### Post by nothingspecial on 2011-12-13
One thread per issue please.

Closed.

---

