---
title: "Syncing a Palm Pilot with Dapper"
date: 2006-06-18
forum: General Help
---

### Post by haroldinct on 2006-06-18
Hi,

Does anyone know how I can sync a Palm Pilot with Dapper?  I have a zire71 and would like a graphical interface like KPilot.  But anything would be better than nothing.  

I really want to be able to put books and other things on it and now only have the Dapper desktop.

Thanks for any help.:)

---

### Post by wastrel on 2006-06-20
USB sync with gpilotd is broken in dapper, so if you can sync via IR or network it would be easier.  

If you have to use USB, it's going to take some effort... I suggest reading up on the other palm/dapper threads here in the forums.

---

### Post by moffa on 2006-06-20
I have read good things about [Jpilot]("http://www.jpilot.org/") but have not tried it yet

---

### Post by pito on 2006-06-20
The same problem is with jpilot and pilot-xfer, so no worth to try right now.
I have been using the jpilot and pilot-xfer in Ubuntu 5.10 without any problems for a while.
After the upgrade to Ubuntu-6.06 I managed to get a contact with the palm only 3 times.

Is there any body who knows about a solution to that problem ?

There has been rumors that UDEV and some USB problems are in current kernel version. Probably there has been a success story with a home compiled 2.6.17  but not confirmed.

I will wait for a while for a fix if not arrived in a week or two I will go back to the Breeze Ubuntu 5.10.

Piotr

---

### Post by wastrel on 2006-06-20
I have had zero problems with jpilot in Dapper, it works every single time -- as long as I make sure jpilot is configured to connect to the correct USB port.

Because of udev creating the USB ports on-the-fly this may be different every time.

To make sure you're connecting to the correct serial port:

1.  Hit the hotsync button on your palm.
2.  tail /var/log/messages   The messages here will tell you which USB port(s) your palm has connected to.

Here's an example from mine:
```

Jun 20 17:59:13 localhost kernel: [17535854.068000] usb 2-1: Sony Clie 5.0 converter now attached to ttyUSB0
Jun 20 17:59:13 localhost kernel: [17535854.068000] usb 2-1: Sony Clie 5.0 converter now attached to ttyUSB1

```

3.  Make sure jpilot is connecting to the serial port listed in the /var/log/messages output.  This is configured in File > Preferences > Settings > Serial Port.  Mine is set to /dev/ttyUSB0 for the example output listed above.  
4.  Now click the hotsync button on jpilot.

This works for me every time.  I've had a lot of trouble connecting with gnome-pilot, even when I have the right port, but none at all with jpilot.

There is a way to configure udev rules to automatically set your /dev/pilot to point to the correct USB port - it's mentioned in a post somewhere in the forums.  This would allow you to set jpilot to point to /dev/pilot and not have to check which /dev/ttyUSB* to use each sync.  I haven't tried this yet so I don't know if it works reliably.

EDIT:

Just finished some testing - jpilot ONLY works if I choose /dev/ttyUSB0  -- it doesn't work if I choose /dev/ttyUSB1 even though the kernel is saying that it's connected to both.  I believe in Breezy either one would work.

---

### Post by Ken.Lank on 2006-06-21
[quote=wastrel]
Just finished some testing - jpilot ONLY works if I choose /dev/ttyUSB0  -- it doesn't work if I choose /dev/ttyUSB1 even though the kernel is saying that it's connected to both.
[/quote]

It also appears that if you configure gnome-pilot to use this port it will work too!

---

### Post by pito on 2006-06-28
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds. 
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by newman on 2006-06-28
[http://www.ubuntuforums.org/showthread.php?t=202552]("http://www.ubuntuforums.org/showthread.php?t=202552")

---

### Post by palmdoc on 2006-07-01
[QUOTE=Ken.Lank]It also appears that if you configure gnome-pilot to use this port it will work too![/QUOTE]

tail /var/log/messages shows this
```

Jul  1 20:05:45 localhost kernel: [17180716.288000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jul  1 20:05:45 localhost kernel: [17180716.288000] visor 1-2.2:1.0: device disconnected
Jul  1 20:07:36 localhost kernel: [17180827.824000] usb 1-2.2: new full speed USB device using uhci_hcd and address 8
Jul  1 20:07:37 localhost kernel: [17180827.924000] visor 1-2.2:1.0: Handspring Visor / Palm OS converter detected
Jul  1 20:07:37 localhost kernel: [17180827.924000] usb 1-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jul  1 20:07:37 localhost kernel: [17180827.928000] usb 1-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Jul  1 20:08:07 localhost kernel: [17180858.336000] usb 1-2.2: USB disconnect, address 8
Jul  1 20:08:07 localhost kernel: [17180858.336000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jul  1 20:08:07 localhost kernel: [17180858.336000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jul  1 20:08:07 localhost kernel: [17180858.336000] visor 1-2.2:1.0: device disconnected
palmdoc@UbuntuDaddy:~$ tail /var/log/messages
Jul  1 20:08:07 localhost kernel: [17180858.336000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jul  1 20:08:07 localhost kernel: [17180858.336000] visor 1-2.2:1.0: device disconnected
Jul  1 20:08:44 localhost kernel: [17180895.520000] usb 1-2.2: new full speed USB device using uhci_hcd and address 9
Jul  1 20:08:44 localhost kernel: [17180895.624000] visor 1-2.2:1.0: Handspring Visor / Palm OS converter detected
Jul  1 20:08:44 localhost kernel: [17180895.624000] usb 1-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jul  1 20:08:44 localhost kernel: [17180895.624000] usb 1-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Jul  1 20:09:29 localhost kernel: [17180940.108000] usb 1-2.2: USB disconnect, address 9
Jul  1 20:09:29 localhost kernel: [17180940.108000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jul  1 20:09:29 localhost kernel: [17180940.108000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jul  1 20:09:29 localhost kernel: [17180940.108000] visor 1-2.2:1.0: device disconnected
```

Editing Gnome pilot to /dev/ttyUSB0 or /dev/ttyUSB1 still does not work for me
Sigh
:confused:

---

### Post by manfredj on 2006-09-14
I have/had the same problem with synching my Palm Pilit (actually Handspring Visor) to Ubuntu 6.x (Dapper). 

It turned out that I had to configure gpilotd-control-applet to use the cradle USB device
  /dev/ttyUSB1  
even though the messages in /var/log/messages indicated that both ttyUSB0 and ttyUSB1 would be connected.

The pre-configured /dev/pilot was not working.

---

### Post by haygoog on 2006-09-15
Got jpilot to sync!

Palm: Zire 72
System: ibook g3 900 // Dapper Xubuntu server install-update*9/13+ xdm, fluxbox, jpilot, etc.

1)No sync after initial jpilot install 
2)Installed pilot-link (MIA)- no sync ('no /dev/pilot')  
3)Tried scripts in rules folder - no sync ('too many symbolic links'). 
4)Removed pilot-links | installed coldsync - no sync ('symbolic links') 
5)Erased rules scripts above - communication but no sync due to 'null user id on palm' (previous hard reset)
6)Synced in Palm Desktop on mac to reset id - SYNC! Worked 5x with jpilot.

According to my experiment just replace pilot-link with coldsync and jpilot should work.  

(Somewhere along the line I set my serial port to /dev/ttyUSB1 in jpilot prefs and that tag still remains)

Hope this helps.

---

### Post by haygoog on 2006-09-15
Seems I need to activate sync from Palm prior to sync from jpilot (have heard this before?).  Sync fails if I try jpilot first.  Messaage reads: 
dip: ReadSysinfo error
Exiting with status SYNC_ERROR_PI_CONNECT

---

### Post by jktrigg on 2006-09-16
I've finally found the key.  Since *two* devices are created, the rule in 60-symlinks.rules is wrong -- it needs to specify KERNEL=="ttyUSB[13579]" rather than KERNEL=="ttyUSB*".  Far too often the default rule links /dev/pilot with the wrong device.

---

### Post by Kadin2048 on 2006-09-22
Has anyone had any success using an older serial-sync PalmPilot in Dapper?

I'm using Kubuntu and trying to use an old M100. I have it connected to my serial port and I can't get anything to work. I thought because it was serial and older it might be easier to get working than the newer USB ones.

Unfortunately I can't find any documentation, and everything refers to /dev/pilot, which I don't have, and I'm not sure if it's supposed to be automatically set up or what.

All I know is that KPilot doesn't autodetect it, even though I have it connected up and am pressing the HotSync button, and the Pilot says that it's trying to connect.

Very frustrating so far.

Any suggestions?

---

### Post by wastrel on 2006-10-09
> **Kadin2048 said:**
> Has anyone had any success using an older serial-sync PalmPilot in Dapper?

I'm using Kubuntu and trying to use an old M100. I have it connected to my serial port and I can't get anything to work. I thought because it was serial and older it might be easier to get working than the newer USB ones.

Unfortunately I can't find any documentation, and everything refers to /dev/pilot, which I don't have, and I'm not sure if it's supposed to be automatically set up or what.

All I know is that KPilot doesn't autodetect it, even though I have it connected up and am pressing the HotSync button, and the Pilot says that it's trying to connect.

Very frustrating so far.

Any suggestions?


Serial devices should be easier than USB - try setting your pilot sync software to /dev/ttyS0 or /dev/ttyS1 (your first & second serial ports.)

---

### Post by jethro10 on 2006-10-10
I struggled for ages with this on several installs, and this now works totally reliably for me every time.

Use Jpilot and any dependencies it wants to install, there is some libraries "Pilot Link" i think it needs.
In its setup menu, the device is set to /dev/pilot  . This is actually a symlink to the ttyUSB port that the systems chooses. **Whatever the usb port chosen, the system correctly symlinks this to /dev/pilot every time**
On the serial port speed, set it to 9600, yes I know were using USB and it says this is not referenced... **This is the bit that totally screwed me every time.** I found it somewhere on a KDE info page (im using Gnome).

_NOW_
Press the button on the sync cradle first. This makes /dev/pilot come alive (creates the SymLink).
Then click the sync button in Jpilot on the screen. It can see the /dev/pilot SymLink now. These 2 steps allow them to see each other

Then Press the Cradle button again to sync.

Works every time for me.

J

---

### Post by Vin¢ on 2006-10-28
Guys, I'm really sorry to ask you dumb this down, but I'm a raging NuB, and can wrap my brain around only about half of this thread.

I'm trying to sync a T2 to a Compaq M2000 using an off-brand (Q-Stor / Edinsoft) USB/IRDA that worked well under Win. (Also worked well w/ my cell phone).

Have JPilot installed on Kubuntu 6.06.

Is new hardware indicated, or is what I have workable?

Thanks,
Vin¢

(I have otherwise been having a great ten months not genuflecting to Big Brother Bill!)

---

### Post by h3mlock on 2006-11-05
I never did get jpilot, evoloution, or kpilot to work with Dapper. I upgraded to Edgy and it now works fine.

---

### Post by jonrkc on 2007-01-20
> **jethro10 said:**
> 
_NOW_
Press the button on the sync cradle first. This makes /dev/pilot come alive (creates the SymLink).
Then click the sync button in Jpilot on the screen. It can see the /dev/pilot SymLink now. These 2 steps allow them to see each other

Then Press the Cradle button again to sync.

Works every time for me.

JI guess those of us who use a cable instead of a cradle (as far as I know the cable is the only USB way for a Tungsten E) are out of luck, as there is no button to push again.  Once the sync button on the Palm is pressed, then the sync button in JPilot, JPilot makes its connection (it says so), but then asks for the Palm button to be pushed again.  Well, now it doesn't exist: only a cancel button.  

And no cradle...

_Update:_ I just found out that repeated attempts to connect and sync will cause sync'ing to occur eventually.  It used to occur on the first go.  This is better than nothing, though.

---

### Post by trents on 2007-02-13
> **wastrel said:**
> I have had zero problems with jpilot in Dapper, it works every single time -- as long as I make sure jpilot is configured to connect to the correct USB port.

Because of udev creating the USB ports on-the-fly this may be different every time.

To make sure you're connecting to the correct serial port:

1.  Hit the hotsync button on your palm.
2.  tail /var/log/messages   The messages here will tell you which USB port(s) your palm has connected to.

Here's an example from mine:
```

Jun 20 17:59:13 localhost kernel: [17535854.068000] usb 2-1: Sony Clie 5.0 converter now attached to ttyUSB0
Jun 20 17:59:13 localhost kernel: [17535854.068000] usb 2-1: Sony Clie 5.0 converter now attached to ttyUSB1

```

3.  Make sure jpilot is connecting to the serial port listed in the /var/log/messages output.  This is configured in File > Preferences > Settings > Serial Port.  Mine is set to /dev/ttyUSB0 for the example output listed above.  
4.  Now click the hotsync button on jpilot.

This works for me every time.  I've had a lot of trouble connecting with gnome-pilot, even when I have the right port, but none at all with jpilot.

There is a way to configure udev rules to automatically set your /dev/pilot to point to the correct USB port - it's mentioned in a post somewhere in the forums.  This would allow you to set jpilot to point to /dev/pilot and not have to check which /dev/ttyUSB* to use each sync.  I haven't tried this yet so I don't know if it works reliably.

EDIT:

Just finished some testing - jpilot ONLY works if I choose /dev/ttyUSB0  -- it doesn't work if I choose /dev/ttyUSB1 even though the kernel is saying that it's connected to both.  I believe in Breezy either one would work.

Thanks, wastrel, this worked like a charm. Port ID stayed the same when I reobooted. Don't know if it would should I do something like add another usb device to the system or change to another physical port. Might have to reconfigure Jpilot port setting then. 

By the way, I'm really impressed with the quality and features of jpilot. Seems to be as good or better than the stuff Palm puts out.

Steve

---

