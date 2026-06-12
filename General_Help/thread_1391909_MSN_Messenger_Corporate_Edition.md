---
title: "MSN Messenger Corporate Edition"
date: 2010-01-27
forum: General Help
---

### Post by kbasarab on 2010-01-27
Hey guys.  I am loving my Ubuntu install and want to transition my office computers to it.  I can install it and run everything no problem but I am unable to connect to the corporate IM.  

It is running a Messenger corporate edition on Windows its version 5.  I remember on Mac you had to download an older version of Messenger for Mac for it to work as well as either our Exchange servers or one of our servers that powers it is really old. 

The connection settings on Mac were using a custom server name over TCP or TLS and a custom port plus mentioned it being a SIP Communications device.

Does anyone know of a way to run this older Messenger corporate edition on Ubuntu?  I've tried using aMSN, Empathy and Pidgin to no avail with connecting with those settings.  Not sure if I'm missing something or not.

---

### Post by t4thfavor on 2010-01-27
Set it up as an msn messenger account in empathy. If that doesn't work, look into what product is hosting the im's, and google for a setup tutorial for empathy. You probably will not get the file transfer, or talk part of it. But IM should work fine.



OOPS I forgot MSN has locked servers. I will take a quick look, and post back.


Guess theres work being done on Pidgin to support Windows Live Communcation Server. As of yet, I am not sure what the progress has been.

---

### Post by kbasarab on 2010-01-27
Just saw your update.  I did some more digging and we are using Exchange Server 2000 instant messaging so not the new Live Communications server.

I installed telepathy sofiasip for empathy but that didn't seem to do it.  

Seems like connecting to Live Server is easy but not the old Exchange 2000 one (I'm not really surprised).  Company doesn't want to upgrade quite yet to the "newer" stuff.

EDIT: I also tried installing Messenger 5 with Wine which installed without a problem but when I try to open it after install nothing actually happens.

---

### Post by running_rabbit07 on 2010-01-27
Have you tried AMSN?

---

### Post by t4thfavor on 2010-01-27
Try launching it from the Command line with wine /path/to/msn.exe and see what error it gives you.

---

### Post by kbasarab on 2010-01-28
I tried aMSN but to no avail.

Here is the error I get in Wine. 

wine /home/kbasarab/Desktop/Messenger/Msmsgs.exe
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Networking.RtcDll"
err:module:import_dll Library MSIMG32.dll (which is needed by L"Z:\\home\\kbasarab\\Desktop\\Messenger\\Msmsgs.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\kbasarab\\Desktop\\Messenger\\Msmsgs.exe" failed, status c0000135


Also doing some research yesterday on Wine it sounds like this has already been logged as a problem before.  Looks like I'm probably screwed until our corporation upgrades to Live server.

---

### Post by t4thfavor on 2010-01-28
MSIMG32.dll

Find that dll on your system, to verify it's actually there, then if it's not there find it on a windows install and copy it to your wine system32 folder. Can't hurt.

---

### Post by kbasarab on 2010-01-29
t4thfavor - Copying that DLL file actually got Messenger to load.  Though it never gave me the SIP Communications area.

With that bit though I started doing some more Googling and found SIPE.

This page:
[http://sipe.sourceforge.net/install](http://sipe.sourceforge.net/install)

From there I was able to follow those instructins and get it to work with Pidgin no problems!  So for anyone else out there looking to connect to an old Exchange/SIP Communications server in your enterprise LAN or corporate LAN with Messenger 5.1 this is the solution.  

Use Pidgin with SIPE.  Thanks for everyone's help on this.

---

