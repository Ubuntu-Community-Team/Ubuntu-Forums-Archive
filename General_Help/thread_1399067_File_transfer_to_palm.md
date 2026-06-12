---
title: "File transfer to palm"
date: 2010-02-05
forum: General Help
---

### Post by mollyj on 2010-02-05
I've searched other posts for information on how to do something that I think should be quite simple. Transfer a file from my webbook (Ubuntu Hardy) to my palm phone. I know that the gnome-pilot application is there and it appears to synch my contacts with evolution however, from the forums it should be possible to transfer files by dragging them to the synch icon but this doesn't appear to happen.

I tried to look it up in the manual from the terminal: man gnome-pilot
This help file is a four liner which directed me to usr/share/ but there aren't any entries there other than conduit configuration files and what looks like a glade gui layout. pilot-xfer just gives me a 'command not found' or equivalent message.

Any suggestions?

---

### Post by efflandt on 2010-02-05
MicroSD or SD depending upon what slot it has.  The simplest way to transfer files to/from any phone, pda, camera, etc. is removable flash memory.

I have a Palm TX, which is not a phone, but works with Garmin Mobile XT for Smartphones (Bluetooth GPS).  I was trying to connect it to Linux with Bluetooth, but so far the Ubuntu PalmOS Devices app seems unaware of it when connected that way, and I think I need to configure a ppp connection in Linux to network (which I did in Windows with mRouter on Bluetooth or USB cable).  I have not tried direct USB cable or WiFi connection with Linux (other than ssh in a tiny Palm screen many years ago).

---

### Post by joeknoodle on 2010-02-05
> **efflandt said:**
> MicroSD or SD depending upon what slot it has.  The simplest way to transfer files to/from any phone, pda, camera, etc. is removable flash memory.

I have a Palm TX, which is not a phone, but works with Garmin Mobile XT for Smartphones (Bluetooth GPS).  I was trying to connect it to Linux with Bluetooth, but so far the Ubuntu PalmOS Devices app seems unaware of it when connected that way, and I think I need to configure a ppp connection in Linux to network (which I did in Windows with mRouter on Bluetooth or USB cable).  I have not tried direct USB cable or WiFi connection with Linux (other than ssh in a tiny Palm screen many years ago).
I'll second the SD card method. I've got a TX and gnome-pilot, but can't get a very good sync (address book doesn't sync at all).

You may also try j-pilot, but I'm not sure about the functionality.

---

### Post by mollyj on 2010-02-11
Thanks for the replies.
I've tried the SD route...it works fine for some files but others seem to require a registration with the OS that they are on the card.... I've found plucker PDBs need this otherwise plucker doesn't see them. However I've never had any success transferring files through pilot. As I said in my original post I think that I may have something missing in my incarnation of pilot.

---

### Post by Dngrsone on 2010-02-16
For the wireless problem:

Under System/Preferences/Palm OS Devices you must add your handheld. Best way to do that is with a direct USB sync.  If you want to install to the PDA, then go to the Conduits tab and make sure hte conduit named File is enabled.

You'll need to have a USB cradle set up under the Devices tab for a USB sync (duh) and add a Network Device for Network syncing.

Set up your handheld to access your wireless network. If you are using a firewall like my Smoothwall Express 3.0 then there's some additional footwork:

I have PDA's and other not-so-secure wireless going through my PURPLE interface, which is firewalled away from my wired LAN computers on GREEN.

I assigned a fixed IP to my T|X based on its MAC and pinholing that IP to my laptop's fixed IP on the GREEN interface using TCP and accessing port 14238.

This is good for syncing to gnomepilot. I have yet to figure out how to get jpilot to sync over the network, but since most of the jpilot apps seem to interface with the gnomepilot databases, I can netsync.

For installing to the handheld, you can use the commandline option gpilot-install-file.  I understand that you can also add the gpilot trnasfer applet to your taskbar and drag files onto it to add them to the queue, but I haven't tried that yet.

---

