---
title: "Virtualbox + Windows XP + iphone update = iphone stuck in recovery mode! HELP!"
date: 2009-10-07
forum: General Help
---

### Post by artheus on 2009-10-07
Hey!

With my Windows XP in a VirtualBox, I started to download the software upgrade 3.1 for my iPhone, but when iTunes put my iPhone in recovery mode I got stuck there, because Ubuntu 9.04 + VirtualBox 3.0.8 won't make a USB Proxy for my iPhone in recovery mode!

What can I do!? Help!

//Artheus

---

### Post by khelben1979 on 2009-10-07
You can search [virtualbox.org forum]("http://forums.virtualbox.org/") for information or register there as well. 

I've never used VirtualBox myself, so can't help you out more than that. Hope you find the forum helpful. If you have the possibility to update the iphone from a genuine Windows system I would rather do that if I were you.

---

### Post by nowhere@cox.net on 2009-10-07
I had the same thing happen. I am not exactly sure the root cause BUT here is what happened to me
[LIST=1]
[*]Apple pushed the new iTunes 9.0 which I downloaded and installed.
[*]I connected my iPhone and iTunes said there was an update for my iPhone firmware
[*]I downloaded and installed it which got to the recovery and crashed
[*]Vbox saw the iPhone on the USB port but stayed grey and wouldn't let me connect.
[*]I read the release notes for the iPhone firmware patch and one item said to make it compatible with iTunes 9! Ummm? Hello Apple? Wrong order?
[*]You may or may not like this but I have learned before updating stuff to make a backup. I had a backup copy of the vbox machine so I deleted the updated one, and reverted back to old iTunes
[*]When I reconnected my iPhone, it connected fine and I was able to update iphone firmware
[*]I then tried the update to iTunes 9 and everything worked after that
[/LIST]
If you don't have a copy of your vbox, I would suggest you create a new vbox, then install iTunes 8 and try to recover your phone and install the firmware. Then move it to your current vbox with iTunes 9 and see if that fixes the problem. You should be able to restore a backup to get your phone back to your settings at that point.

It was quite frustrating for me too. This is one reason why I have half a dozen vboxes, each with one piece of Windows software that I can't replace in ubuntu yet...

Good luck!

---

### Post by z_kvn on 2009-11-14
I met same issue but was able to solve the problem following below two steps

1. Setup correct user group
[http://ubuntuforums.org/showthread.php?t=1318160](http://ubuntuforums.org/showthread.php?t=1318160)

2. Created a USB filter in VBOX, cleared all of the fields except for the "Vendor ID" field. 
[http://forums.virtualbox.org/viewtopic.php?f=2&t=18852](http://forums.virtualbox.org/viewtopic.php?f=2&t=18852)

;) good luck!

Btw, I still don't understand why iTune is able to connect to my iphone at first without any above settings. So weird when iphone is turned into recovery mode, VBOX suddenly greys all usb devices...

---

### Post by z_kvn on 2010-06-23
Hi some update on this.

I am now using Ubuntu 10.04 and went through a lot of forums and finally got Iphone upgrade work in virtualbox.

1. First I experienced difficulties finding USB at all. 

What I did is remove OSE and install the newest version downloaded from Virtualbox.org

cd /tmp
wget [http://download.virtualbox.org/virtualb](http://download.virtualbox.org/virtualb) ... e_vbox.asc
sudo apt-key add oracle_vbox.asc

# add the below to /etc/apt/sources.lis
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

# then update and install
aptitude update
aptitude install dkms virtualbox-3.2

2. Shutdown the virtual machine, go to settings --> usb filter --> create one with only key words Apple Inc. in the Manufacture field.

In the recovery mode, somehow usb device is not recognized. Doing above will solve the issue.

3. Done, works like in real windows XP

---

### Post by L815 on 2010-10-31
I got my Ipod touch to work which was stuck in the usb connect screen after a failed update.

The key thing is that Virtualbox needs to be run as root.
The reason you see the usb listed but greyed out is because the permissions are blocked for the normal user in the state it is in.

So once you start virtualbox as root and setup your VM, add a USB filter with 'Apple Inc.' in the manufacturer field (no quotes).

Once that's setup, boot the vm and you should notice that itunes and virtualbox automatically mount/detect the device. 


A bit late in the response, but I figured someone might stumble here with the same issue and the thread wasn't tagged as solved.

---

### Post by bruno.braga on 2010-11-23
> **L815 said:**
> 
The key thing is that Virtualbox needs to be run as root.


That was the trick I missed.... thanks!!! I was already getting crazy here, even thinking of installing Windows on a partition to be able to recover my device... :popcorn:

Everyone reading this thread, just pay attention to this part!!!

---

### Post by kacheng on 2011-06-05
Thanks!

Running 'sudo virtualbox' and setting up the 'Apple Inc.' filter did the trick for me too.

---

### Post by secros on 2011-12-15
BUMP the start as root advice.  solved my problem, too!

---

### Post by dsauxier on 2013-02-10
It's been a while since the original post, but I'm happy to report that the USB Filter workaround still works.  Thanks a LOT for this!!
> **z_kvn said:**
> 
2. Created a USB filter in VBOX, cleared all of the fields except for the "Vendor ID" field. 
[http://forums.virtualbox.org/viewtopic.php?f=2&t=18852](http://forums.virtualbox.org/viewtopic.php?f=2&t=18852)



---

### Post by wildmanne39 on 2013-02-10
Old thread closed.

---

