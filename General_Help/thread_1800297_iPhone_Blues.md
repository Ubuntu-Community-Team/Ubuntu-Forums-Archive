---
title: "iPhone Blues"
date: 2011-07-08
forum: General Help
---

### Post by Akovia on 2011-07-08
For the love off all things ubuntu, would someone please help me?

Received an iphone 1,2 (3G) as a gift and have already wasted most of a week trying to get some basic functionality. Too many guides followed & tricks tried to mention. I've also posted to libimobiledevice, banshee, & gtkpod mailing-lists/tickets. (no responses) One thing that has never ever happened is my phone being auto-mounted with an icon on the desktop, as was reported to be the plug-n-play functionality of my OS.

[B]My details:
Xubuntu 10.04 (Lucid) 2.6.32-32-generic SMP i686
ppa:pmcenery/ppa
iOS 4.2.1 (still in jail)[/B]

**_Problems:_**
**banshee:**
banshee doesn't correctly identify my device but does find "Apple iPhone"
It did once show the correct name, "A's iPhone", but still wouldn't convert any songs. Failing with GNUTLS errors.

Right now before I try any transferring of music, here are some of the errors I see in the terminal.

```
AppleDeviceSource is ignoring unmounted volume A's iPhone
Device 0 (VID=05ac and PID=1292) is UNKNOWN.
LIBMTP PANIC: could not inspect object property descriptions!
[Warn  18:30:37.311] Unable to get battery level from MTP device - Mtp.LibMtpException: Could not retrieve battery stats (in `Mtp')
  at Mtp.MtpDevice.GetBatteryLevel (Mtp.MtpDeviceHandle handle, System.UInt16& maxLevel, System.UInt16& currentLevel) [0x00000] in <filename unknown>:0 
  at Mtp.MtpDevice.get_BatteryLevel () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
```

I'm thinking this has to do with gvfs not auto-mounting the phone. Upon further inspection I noticed that libgvfscommon0 is not installed. Trying to install it prompts that about 30 packages will be removed.

```
The following packages will be REMOVED:
  brasero firestarter gdm gnome-power-manager gnomebaker gvfs gvfs-backends gvfs-bin gvfs-fuse hipo libbonoboui2-0
  libgnome2-0 libgnome2-perl libgnome2.24-cil libgnomeui-0 libgoffice-0-6 libgoffice-gtk-0-6 libpanel-applet2-0
  python-gnome2 python-gnome2-desktop python-gnomeapplet sbackup seahorse-plugins soundconverter
  system-config-printer-gnome usb-creator usb-creator-gtk vinagre xfswitch-plugin xubuntu-desktop xubuntu-gdm-theme
The following NEW packages will be installed:
  libgvfscommon0
```

No idea what to do here....

**gtkpod:**
Mounting with ifuse I am able get gtkpod to find my phone but functionality is spotty. I've been able to *finally* get some music on it, but it throws many errors and I have to reboot the phone to get the tracks to show up.

```
GNUTLS ERROR: A TLS fatal alert has been received.
usbmuxd_send: Error -1 when sending: Broken pipe
Error: Could not establish lockdownd connection!

** (gtkpod:25677): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

[run_post_process_commands] ERROR: Could not connect to device's lockdownd!
** (gtkpod:25677): WARNING **: Trying to unlock an already unlocked device
```

Trying to get pictures on the device is yet another effort in futility. Everything looks as if it's working, but I end up with all my pictures at 166x125 on my phone. (smallest original was 1024x768)


I would like to start from scratch but not sure I am able to, unless someone has an idea on how to fix where I'm at now. I'm just at wits end and feel like I'm chasing my tail. It seems to me that something was fundamentally wrong from the get-go since my phone never would mount with a desktop icon from the start.

Happy to post any detailed information asked for and will jump through hoops if only someone with enough knowledge to troubleshoot this down would help.

---

### Post by lakerssuperman on 2011-07-08
I see you are running 10.04.  Have you tried it with anything newer.  Sometimes, no matter what PPA's you have or tricks you try, using a new version is your best bet.  Even running a livecd on your hardware and seeing if it detects your device might be something to try.

---

### Post by La_Lata on 2011-07-21
i am a new user to linux (1 week) so the terminal stuff is a mystery to me.

Yet no guide i find can help me resolve this same issue.

I have installed Banshee on my xubuntu 11.04 OS but my iPhone 32gb 3GS is not recognised nor is it even mounted withing the OS itself.

--------

I'm not so interested in the syncing of music, rather the backing up of the iPhone itself is important to me. I am preparing my notebook for an epic backpacking trip around South America and I really need this to be working.

I have also tried WINE and installing the latest iTunes, yet that does not work either.

Thx for your time.

---

