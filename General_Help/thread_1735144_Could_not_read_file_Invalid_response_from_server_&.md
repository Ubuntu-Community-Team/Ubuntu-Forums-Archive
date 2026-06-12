---
title: "Could not read file Invalid response from server: &quot;. &quot;."
date: 2011-04-21
forum: General Help
---

### Post by dkolars on 2011-04-21
OK, so updated my desktop (Dell Vostro) from Ubuntu 9.10 to 10.04 (was expecting to see 10.10 as the next upgrade, but it wasn't there)...

Running K-Mail and now get the following error message regularly:
 
***Could not read file Invalid response from server: ".".***


Have spent a long time hunting on the web for hints about this, with no definitive answers to the problem appearing. 



Also get the following when attempting to start K-Mail from the terminal:


[I][B](<unknown>:4596): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(<unknown>:4596): atk-bridge-WARNING **: IOR not set.

(<unknown>:4596): atk-bridge-WARNING **: Could not locate registry
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/kmail(4596)" Error in thread 3078711168 : "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/kmail(4596)" Error in thread 3078711168 : "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/kmail(4596)" Error in thread 3078711168 : "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/kmail(4596)" Error in thread 3078711168 : "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/kmail(4596)" Error in thread 3078711168 : "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/kmail(4596)" Error in thread 3078711168 : "QLocalSocket::connectToServer: Connection refused"
kmail(4596)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kmail(4596)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dkolars@Desktop:~$ kmail(4596)/kio (KIOJob) KIO::TransferJob::slotData: mimetype() not emitted when sending first data!; job URL = KUrl("pop3://myid%40comcast.net@mail.comcast.net:110/index") data size = 8 
kmail(4596)/kio (KIOJob) KIO::TransferJob::slotData: mimetype() not emitted when sending first data!; job URL = KUrl("pop3://myid%40comcast.net@mail.comcast.net:110/uidl") data size = 39 
[/B][/I]


At boot up, I get a message that tells me to ***Continue to Wait, Press S to Skip mounting, Press M for Manual***


Have never seen that until 10.04.


I am able to reboot the modem and router and then I can connect to get my e-mail.  But, the "Could not read file... " message can seemingly occur at any time.


K-Mail also now takes up to 30 seconds to send a simple message, where before it used to send it in a split second. 



I have a laptop that I upgraded from 9.10 to 10.04 to 10.10 using CD's... would 10.10 fix these problems (and not trash all my "stuff" on the HDD)?  


So, any ideas on 1) what is causing this, & 2) how to fix this?


I'm actually leaving Fri. until May 3 and will be using the laptop, so won't be dealing with the desktop problem until next month, but sure would be nice to know the fix!!

---

### Post by mastablasta on 2011-04-21
you could just try to backup all your emails. uninstall & purge K-mail and then reinstall it again. then restore the messages. 
 
as for ther boot message were you automounting some others disks or partitions before?
 
Edit: DO you have Kubuntu or Ubuntu? Becuase 10.04 Kubuntu is not really good KDE edition as i know. Unless they ironed out the bugs.

---

### Post by dkolars on 2011-04-21
1)  I have Ubuntu... thought I had Kubuntu, but I was wrong!

2)  Yes, I had an external HDD die.  So, it's looking for that, eh?  Didn't realize that.  Thought it would just read what was there and assign the drive names if found...

I know that since the update, using Krusader (I've used a shell program since Norton Commander 1st came out), it's seeing the drives in a different way...  and that was before the HDD died... I had Ext1, Ext2, & Ext3 for names... it suddenly started seeing them AND Ext1_, Ext2_ & Ext3_ as the names, but showed both names...  the NEW name with the underscore after was the valid drive???

I will very likely be doing the redeux of KMail when I get back home next month...  I checked my mail this a.m., no problem... opened Facebook, read a few links, posted a couple of things, went to check my e-mail again and got the error message!

Grrr...

---

### Post by dino99 on 2011-04-21
your installation seems to be customized, as you get ext1_ meaning you use /media.
fstab only need both entries: your boot partition & the swap partition, nothing else as mountall do the job when needed

check also your sources.list, need a clean one

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by dkolars on 2011-05-07
I posted a long reply to this last night...  anybody see it?  It seems to not be here...

---

### Post by demilord on 2011-05-17
It happens on a clean updated kubuntu 11.04 install

I also have lots of crashes on shutdown with policykit..
and my .xsession-errors grows with megabytes a hour with this messages

---

