---
title: "Multiple problems, don't know what the root is?"
date: 2011-03-31
forum: General Help
---

### Post by evanseeds on 2011-03-31
I recently reinstalled Ubuntu and have had multiple problems with different programs since, and don't know if the problems are systemic or each program:

Google Chrome has been crashing (the Ah Snap! page, not a full crash) on certain websites (wikipedia, youtube, pitchfork.com, demonoid, to name a few), even with no extensions or plugins enabled, and Firefox does the same, on the same websites even. Other websites, such as this one, work fine.

In addition, Transmission has been giving "input/output" errors on multiple different torrents. Also, I'm not sure how helpful this is, but the system in general seems a little sluggish.

Thanks for any help.

---

### Post by cain071546 on 2011-03-31
try a older version of ubuntu or even a derivative like Mint


i loves my Linux Mint

---

### Post by Ocxic on 2011-03-31
Check your hard drive with disk utility.. your drives might be failing, and the smart status will show if there is anything wrong.

---

### Post by deathadder on 2011-03-31
> **evanseeds said:**
> Google Chrome has been crashing (the Ah Snap! page, not a full crash) on certain websites (wikipedia, youtube, pitchfork.com, demonoid, to name a few), even with no extensions or plugins enabled, and Firefox does the same, on the same websites even. Other websites, such as this one, work fine.
Flash sounds like the thing most of those sites have in common, do you have a flush plugin installed? If so disable it and see if the browser crashes. If it runs ok, try updating you flash plugin. If it doesn't then we need to look a little deeper.

> 
In addition, Transmission has been giving "input/output" errors on multiple different torrents. Also, I'm not sure how helpful this is, but the system in general seems a little sluggish.
A [quick Google]("http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=Transmission+i%2Fo+error&aq=f&aqi=g-v1&aql=&oq=") found a thread on [Transmission's]("https://forum.transmissionbt.com/viewtopic.php?f=4&t=4585&p=26627") site that may help,
> 
IOError means Input-Output Error, and that is a file system error, not a tracker one. It shows up when your client is for some reason unable to open the partially downloaded torrent files. The most common cause is two instances of the client to be running simultaneously: the last time the client was closed it somehow didn't really close but kept running in the background, and is therefore still locking the files, making it impossible for the new instance to open them.
Have you run fsck recently? It may be that you've got something wrong with the filesystem. Try forcing fsck to run on the next boot and see if that throws any errors. To do that you need to run the following command:
```
sudo touch /forcefsck
```
Finally, it may all be down to bad memory. You can use memtest to do that, have a look at the [faulty hardware]("https://help.ubuntu.com/community/FaultyHardware") how-to to start the process (it may take a while). It'll also give you other ideas on what to check.

---

