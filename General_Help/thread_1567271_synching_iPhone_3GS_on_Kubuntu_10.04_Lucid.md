---
title: "synching iPhone 3GS on Kubuntu 10.04 Lucid"
date: 2010-09-03
forum: General Help
---

### Post by xjgnsdof on 2010-09-03
I installed Kubuntu 10.04 fresh and can't get it to recognize my iPhone 3GS. This is a deal-breaker for me unless there's a workaround. Let me know if this is possible and, if so, how to do it.

---

### Post by jdsmofo on 2010-10-03
I have exactly the same problem.  Am I the only other person in the past month?

---

### Post by xircon on 2010-10-03
Works fine here.  Have you installed libimobiledevice?  I use GTKPod and ifuse to connect.

[http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/](http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/)

---

### Post by mr_luksom on 2010-10-03
+1 for libimobiledevice and gtkpod.

It can sync iDevices with software up to iOS4.1. I can vouch for that - I just got my 3GS with 4.1 working today.

You need the latest libimobiledevice - use the PPA from Paui McEnery ([https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa) - there are numerous tutorials on how to add this repository).

You need to mount your iPhone manually using ifuse. To set it all up:
1. Create a mount point (/media/iPhone).
2. Assign the correct permissions (i use chmod 777)
Now to mount the iPhone:
3. ifuse /media/iPhone
4. Start gtkpod. It should recognise the phone automatically. If not, go to Edit -> Repository Options and got through the options create a iPhone repository.
5. Make sure you unmount before unplug!! fusermount -u /media/iPhone

If you are feeling inclined, you can put steps 3-5 in a bash script, so you just press one button.

---

### Post by jdsmofo on 2010-10-03
Yeah, it took me awhile to install libimobiledevice.  I had installed rhythmbox, which installed some older version, and installing the newer one created some conflicts.  I had to uninstall rhythmbox (maybe other
things, too) first, then try to reinstall.  After ilibimobile device was installed, and usbmuxd, my machine finally recognized the iPhone, as shown by ideviceinfo.  After installing gpodlib, ifuse and gvfs, Amorok finally recognized the songs.  

I've just now installed gtkpod, and created the mount point (thanks for the tip!).  We'll let you know how that goes.

---

### Post by jdsmofo on 2010-10-03
gtkpod connects!  Now need to debug syncing calendar, contacts, etc.  Thanks!

---

### Post by xircon on 2010-10-03
> **jdsmofo said:**
> gtkpod connects!  Now need to debug syncing calendar, contacts, etc.  Thanks!

I use Gmail to sync, which client do you use?

---

### Post by jdsmofo on 2010-10-03
Yeah, I sync my calendar to Google Calendar.  But my contacts are all currently synced to Outlook and am trying to break free of windows.  I used to be able to sync my desktop to Google Calendar through GCalDaemon, but that broke with my last upgrade.  Any recommendations?

---

### Post by xircon on 2010-10-03
No, since I got the iPhone, I now use web-based Gmail for everything, uninstalled evolution and thunderbird as they were getting on my nerves.

---

### Post by xircon on 2010-10-03
This was the link I followed to sync my contacts:

[http://www.google.com/support/mobile/bin/answer.py?answer=138740&topic=14252](http://www.google.com/support/mobile/bin/answer.py?answer=138740&topic=14252)

---

### Post by jdsmofo on 2010-10-03
I wanted to avoid becoming completely dependent on Google (the way that is possible with MS).  So, I would like to have my contacts and email stored on my own machine to do whatever I want with.  Right now it looks like I cannot access my contacts or calendar on the iPhone through gtkpod, dolphin, or whatever.  For the moment, I can sync my calendar and contacts with linux only through Google, but that is a dependence I am trying to break.

---

### Post by jdsmofo on 2010-10-03
The sync between Google calendar and contacts on the one hand, and linux on the other, is almost, but not quite there.  You can add a package "akonadi-kde-resource-googledata" that is a plugin for the akonadi server, and use this route to sync korganizer and kontact with Google.  However, the former does not sync repeating events, and the latter apparently has some trouble with all data (though I have not tried it).

---

### Post by lucasmocellin on 2010-10-12
hello guys,

did someone tried with iPod touch 4g??

I'm doing exactly the same and nothing happens.

some info:

root@kktua:/usr/lib# dpkg -l|grep libimob
ii  libimobiledevice-dev                  1.0.3-1ubuntu1~lucid1                           Library for communicating with iPhone and iP
ii  libimobiledevice-utils                1.0.3-1ubuntu1~lucid1                           Library for communicating with iPhone and iP
ri  libimobiledevice0                     0.9.7-1ubuntu1                                  Library for communicating with the iPhone an
ii  libimobiledevice1                     1.0.3-1ubuntu1~lucid1                           Library for communicating with the iPhone an
root@kktua:/usr/lib# 

there the 2 packages, but I think that's fine, looking at the libs:
root@kktua:/usr/lib# ls -l libimobi*
-rw-r--r-- 1 root root 114030 2010-10-05 06:48 libimobiledevice.a
lrwxrwxrwx 1 root root     25 2010-10-08 05:47 libimobiledevice.so -> libimobiledevice.so.1.0.3
lrwxrwxrwx 1 root root     25 2010-10-12 20:43 libimobiledevice.so.0 -> libimobiledevice.so.0.0.0
-rw-r--r-- 1 root root  75732 2010-02-10 19:28 libimobiledevice.so.0.0.0
lrwxrwxrwx 1 root root     25 2010-10-12 20:36 libimobiledevice.so.1 -> libimobiledevice.so.1.0.3
-rw-r--r-- 1 root root  83980 2010-10-05 06:48 libimobiledevice.so.1.0.3

1 - if I use banshee, it shows me the iPod, but when I transfer it gives me the error:
"the mp3 format is not supported by the device, and no converter was found to convert it" or for any format.
2 - in rhythmbox it doesn't show up.
3 - for banshee and rhythmbox when I open up the iPod does the "sound"(beep) of synchronizing.
4 - root@kktua:/usr/lib# ideviceinfo 
usbmuxd_get_device_list: error opening socket!
No device found, is it plugged in?

any other solutions?

thank you guys.

---

### Post by dwsdad on 2010-10-13
I've tried syncing music between Lynx and my iPhone 4 running IOS 4.1 on Banshee, Rythmbox, and gtkpod.  All of them recognize the iPhone in that it shows up in the browser, but....

Rythmbox gives me a connection error 1:177

Banshee APPEARS to be syncing - the iPhone displays syncing in progress, but it takes forever and nothing shows up in iPod on the phone.

gtkpod DOES move a track over, but it places it in the RingTone folder.

I haven't tried Amarok yet.

I have the phone mounted using ifuse.

What am I missing to get all these issues?

EDIT:  Well, ain't that interesting.  I click on the iPhone icon on the desktop and drill down into iTunes_Control/Music/F00 and I see libgpod293231.mp3 and it does play, but still nothing displays in iPod on the phone.

---

### Post by francois.e on 2010-11-13
Trying mr_luksom procedure for the ipod touch 4g we ge the following error message:

root@max:~# ifuse /media/iPhone
usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.
root@max:~# 

As we have used /media/iPhone for the ipod, might it be only a question of reassigning the device into iPod?


Edit:
Rereading thru the post and the hyperlink, I went a little further. I will come back to report.

---

### Post by xircon on 2010-11-14
What is the output of:
```
lsusb
```

---

### Post by chanfle on 2010-12-01
> **xircon said:**
> What is the output of:
```
lsusb
```

Hello all,
I have a issue with my ipod touch 4g, when I connect on Ubuntu 10.10 the OS it detect perfectly (only see the photo folder)
but on Rhythmbox appear but disaapear quicly and I can't transfer my music on my ipod..
Any help for fix this issue?

---

### Post by neonboy on 2011-02-23
> **mr_luksom said:**
> +1 for libimobiledevice and gtkpod.

It can sync iDevices with software up to iOS4.1. I can vouch for that - I just got my 3GS with 4.1 working today.

You need the latest libimobiledevice - use the PPA from Paui McEnery ([https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa") - there are numerous tutorials on how to add this repository).

You need to mount your iPhone manually using ifuse. To set it all up:
1. Create a mount point (/media/iPhone).
2. Assign the correct permissions (i use chmod 777)
Now to mount the iPhone:
3. ifuse /media/iPhone
4. Start gtkpod. It should recognise the phone automatically. If not, go to Edit -> Repository Options and got through the options create a iPhone repository.
5. Make sure you unmount before unplug!! fusermount -u /media/iPhone


Hi guys,

I don't have the proper knowledge to fully understand point 2. & 3. and 
how to get libimobiledevice.

Can i have more details about the operations?

I'm on Ubuntu 10.10 try to sync an iPod Touch with iOS 4.1

I'll really appreciate any help.

Thanks to you all :)

---

### Post by xircon on 2011-02-23
Read:

[http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/](http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/)

Easy to follow instructions.

---

### Post by sesnf86 on 2011-02-27
hi 
i am facing a problem with my ipod touch 4g on slackware 13.1. I have already created a thread 

[http://ubuntuforums.org/showthread.php?p=10501038#post10501038](http://ubuntuforums.org/showthread.php?p=10501038#post10501038)

Can anyone go through it and tell me what to do 

thanks

---

### Post by sesnf86 on 2011-03-02
I have managed to get it working now. For anyone facing the same problem try doing > usbmuxd as root before the ifuse command. It worked for me this way.

Now i am trying gtkpod to sync my music. When i add some new files to the ipod, gtkpod shows them but it is not shown in the ipod. 

Anyone who has tried gtkpod face the some problem ?

---

