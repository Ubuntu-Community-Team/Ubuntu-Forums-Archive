---
title: "Malformed URL reported by konqueror when using bluetooth:/ and sdp:/ kio slaves"
date: 2006-04-04
forum: General Help
---

### Post by ZiZi on 2006-04-04
Hi,
I have only recently installed the kdebluetooth package and it actually surprised me that it JustWorksTM out-of-the-box!! :KS 

The only thing that makes me sad is konqueror claiming that bluetooth:/ and sdp:/ are "Malformed URL"s, even though through System Menu -> Remote Places -> Bluetooth the bluetooth devices are listed correctly (and the Location toolbar contains "bluetooth:/"!!). :confused: 

However, as soon as I click any of the devices or just try to reload the page, konqueror reports "Malformed URL" bluetooth:/, sdp:/ respectively... ](*,) 

Is there any solution how to override this error to allow acces to bluetooth:/ or sdp:/ devices?

---

### Post by Randomskk on 2006-04-04
as far as bluetooth goes..
type into the location bar:
remote:/bluetooth/

That loads the bluetooth screen for me :/

---

### Post by GeneralZod on 2006-04-04
I'm getting the same thing, but the weird thing is that it was working perfectly until a couple of days ago.  I'm using Dapper, by the way.

---

### Post by ZiZi on 2006-04-04
When I tried to access bluetooth:/, 
this message was printed to console:

```
kio_bluetooth: kio_bluetooth: get() was called! This is nonsense
```

Yes, I understand, that it propably IS a nonsense, but what should I do to avoid it?

---

### Post by Randomskk on 2006-04-04
My "bluetooth:/" doesn't work, same error message, but using "remote:/bluetooth" works fine - you can just type remote:/blu<tab> and it will auto-complete it for you.

---

### Post by ZiZi on 2006-04-04
[QUOTE=Randomskk]as far as bluetooth goes..
type into the location bar:
remote:/bluetooth/

That loads the bluetooth screen for me :/[/QUOTE]
Yes, this works, but the devices are still unaccessible as they are linked via sdp:/localhost or sdp:/[mac-address]/, which keeps reporting Malformed URL errors...

---

### Post by ZiZi on 2006-04-04
[QUOTE=GeneralZod]I'm getting the same thing, but the weird thing is that it was working perfectly until a couple of days ago.  I'm using Dapper, by the way.[/QUOTE]

Yes, it may even be a result of another bug's fix, I'm using latest Kubuntu packages of KDE and Konqueror  - 3.5.2 - since about two weeks ago.

A friend of mine, who uses KDE 3.4.?, got it working without problems :-k

Any ideas? Google doesn't help yet, I'll keep looking...

---

### Post by GeneralZod on 2006-04-04
I've just reported this as a bug, referencing this thread:

[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/38064](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/38064)

---

### Post by ZiZi on 2006-04-04
This is a result of entering sdp:/ into Konquerors location textbox:
```
kio_sdp: *** Starting kio_sdp
kio_sdp: SdpProtocol::SdpProtocol()
kio_sdp: Looking for ServiceHandlers
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1108 mimetype:bluetooth/headset-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1108
kio_sdp: ->0x00001108:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x111f mimetype:bluetooth/handsfree-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x111f
kio_sdp: ->0x0000111f:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1105 mimetype:bluetooth/obex-object-push-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1105
kio_sdp: ->0x00001105:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1104 mimetype:bluetooth/synchronization-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1104
kio_sdp: ->0x00001104:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1111 mimetype:bluetooth/fax-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1111
kio_sdp: ->0x00001111:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1101 mimetype:bluetooth/serial-port-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1101
kio_sdp: ->0x00001101:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1103 mimetype:bluetooth/dun-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1103
kio_sdp: ->0x00001103:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1106 mimetype:bluetooth/obex-ftp-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1106
kio_sdp: ->0x00001106:00001000:80000080:5f9b34fb
kio_sdp: done.
kio_sdp: kio_sdp::setHost()
kio_sdp: kio_bluetooth: get() was called! This is nonsense.
```

---

### Post by debernardis on 2006-04-04
There is already a thread on this bug: [http://bugs.kde.org/show_bug.cgi?id=123607](http://bugs.kde.org/show_bug.cgi?id=123607)
Vote it on the kde.org site to subscribe to the thread and promote the search for a solution.

It all started when I upgraded to kde 3.5.2 - no problems with 3.5.1.

I use bluetooth on my kubuntu breezy laptop only for browsing the file system of my symbian phone. By serendipity I found a workaround to get it even if the bluetooth:/ kio_slave is broken.

```
obex://[00:0e:ed:ae:d7:3b]:11/
```
By entering the above code, Konqueror directly opens the file system of my phone, without involving the broken bluetooth:/ kio_slave. BTW, it is the address that Konqueror shows when I opened the obex protocol under the sdp://device/ window for my phone.
Presumably, a similar code is already included into the list of recently opened url's in your address bar, with the correct hexadecimal mac-address and port for your device, so try to write **obex://** and see if it is autocompleted with your own data... good luck! :cool:

---

### Post by ZiZi on 2006-04-04
Thanx, I have just voted for the bug, hope it will be fixed soon...
**obex:/[MAC]:11/** really works just fine!:KS , the MAC address can also be retrieved via System menu -> Remote Places -> Bluetooth, and the communication progress functions as expected with my Sony-Ericsson T630.

However, I won't stop complaining until the bug is fixed[-( ;) It would literally be a handful of mud on this otherwise perfectly clean and polished KDE Bluetooth Service 8)

---

### Post by debernardis on 2006-04-05
Another way to get the mac address of nearby devices is 
```
hcitool scan
```
in a terminal window. This will output a list of reachable devices with mac-address and name.

---

### Post by debernardis on 2006-04-07
A patch has been published in [http://bugs.kde.org/show_bug.cgi?id=123607](http://bugs.kde.org/show_bug.cgi?id=123607) by Pavel Troller. I was unable to fully apply it, though, because I cannot find the .cpp files which should be patched... I guess this is because the patch should be applied to the sources, and not to the binaries on my machine.
I don't feel I am able to find the right binaries and compile them, so I'd appreciate an help from the forum members.

---

### Post by GeneralZod on 2006-04-07
[QUOTE=debernardis]A patch has been published in [http://bugs.kde.org/show_bug.cgi?id=123607](http://bugs.kde.org/show_bug.cgi?id=123607) by Pavel Troller. I was unable to fully apply it, though, because I cannot find the .cpp files which should be patched... I guess this is because the patch should be applied to the sources, and not to the binaries on my machine.
I don't feel I am able to find the right binaries and compile them, so I'd appreciate an help from the forum members.[/QUOTE]

That's correct; the patch must be applied to the source, and then the source must be re-compiled into a binary and the new binary installed.  The procedure is pretty involved, though, so you might want to wait for the Kubuntu devs to apply the patch (assuming they do, of course!) and get an updated kdebluetooth through Adept/ Synaptic.

---

### Post by debernardis on 2006-04-08
Is it possible to downgrade only kbluetooth to the 3.5.1 version?
What happens if I remove kbluetooth by apt-get, edit sources.list to downgrade the repository to 3.5.1, then apt-get install kbluetooth again?
(of course you could tell me to try ;) but before I do I'd appreciate your opinions...)

---

### Post by ianni67 on 2006-04-23
There seems to be a patch in the kde bugs forum against this bug.
Is it possible for the kubuntu admins to prepare an upgrade which embeds this patch? This bug seems to me quite severe.

---

### Post by GeneralZod on 2006-05-02
This has now been fixed in Dapper - thanks, Kubuntu devs! \\:D/

---

### Post by maniaq on 2008-04-27
so... this got "unfixed" in Hardy? Konqueror appears to not support bluetooth:/ or obex:/ protocols and I have no idea how to apply that patch?

i've tried reinstalling kbluetooth from the sources but the configuration keeps complaining it can't find obexftp - even tho I have it installed and working just fine?

---

### Post by maniaq on 2008-04-28
Hi just a quick update - (finally) ditched KDE-4 and went back to KDE-3 and... it works!

no messy patching, no nothing... serves me right for going with a borderline stable wm

---

