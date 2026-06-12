---
title: "dbus-daemon 60%+ CPU usage, causes crashes - iPhone related?!"
date: 2011-03-08
forum: General Help
---

### Post by gdea73 on 2011-03-08
I am having a really bad problem with Ubuntu 10.10 amd64 Desktop. I use this computer as a Minecraft server 24/7, so as you may have guessed, I'm logged in for long periods of time between restarts--which do happen but are rare for the continuity of my server services. Now this has in the past few days only created a problem--my computer was running very high CPU usages and I was unsure why--checking gnome system manager brought up dbus-daemon as the highest usage 60% at one time, up to 95% at others... and it make my system very unresponsive and glitchy. If I end dbus-daemon, the computer crashes and I have to hard reset--though that is probably normal as dbus is a required component...

when I mouse over dbus-daemon it reads this: /bin/dbus-daemon --fork --print-pid 5 --print address 7 --session

Interestingly enough this happened *right* after I plugged in my iPhone and got the "invalid mount spec" error, of which I could find no solutions with Google searching _at all_... even after unplugging the iPhone the problem continued. Rebooting did not help, with the iPhone plugged in.

If I unplug the iPhone (which I was simply charging, not planning on using with the PC) and then shut down the computer, turn it back on without plugging in the iPhone -- THEN -- dbus-daemon is back to normal (same process, but 0 cpu % and 1.3 mib ram, used crazy amounts of RAM before and viewing files associated listed around 64).

Is this really related to plugging in an iPhone to charge?! I got like bus timed out error too when I plugged it in, so maybe it is .. .seems odd, I knew it wasn't to be compatible, but simply using my server as a charging station would be nice.

Any help/suggestions/confirmation?

I can replicate by starting my PC with my iPhone plugged in or plugging it in while it is running. Also dbus daemon makes system monitor unresponsive when on high cpu %, sometimes fourth core of four core processor *disappears* in resources, and computer becomes unresponsive altogether.

---

### Post by h0l0gramm on 2011-03-16
I can confirm your observation.

Plugin your iPhone4, confirm the dbus-error message, wait a bit and then *dbus-daemon* goes up to over 60%.

When you look at the *dbus-messages*  console: 
```
dbus-monitor --session
```you will see that there is a kind of a message loop. There is a huge message repeating over and over again. The message contains the mounted file systems.
```

string "iPhone"
string ". GThemedIcon phone-apple-iphone phone-apple phone"

string "Lenovo_Recovery"
string ". GThemedIcon drive-harddisk-ata drive-harddisk drive"

string "CD/DVD Drive"
string ". GThemedIcon drive-optical drive"

string "Generic Flash HS-COMBO"
string ". GThemedIcon drive-removable-media-usb drive-removable-media drive-removable drive"

string "Generic Flash HS-CF"
string ". GThemedIcon drive-removable-media-usb drive-removable-media drive-removable drive"

```When you unplug your iPhone, messages in dbus stops, cpu usage goes down to normal.
The process *gvfsd* is now consuming much more memory than before.

Is there a dbus-crack out there? I am glad to help by submiting my dbus-messages that go wild. 

Ubuntu 10.10 amd64

Cheers
Jan

---

### Post by guru369 on 2011-03-24
I can confirm this issue is related to iphone and dbus.
ubuntu 10.10 AMD64

Dekel

---

### Post by dirtabulous on 2011-04-07
Seems to happen to me as well.  If I disconnect and reconnect the iPhone it usually stops.

---

### Post by h0l0gramm on 2011-04-20
I found the solution [here]("http://ubuntuforums.org/showthread.php?t=1628529&page=2") .

Add ppa "pmcenery"
```
add-apt-repository ppa:pmcenery/ppa
```

Update repo index
```
aptitude update
```

Upgrade
```
aptitude safe-upgrade
```or use the System > Administration > Update Manager

Plug-in your iPhone. It should be mounted by now.
See Icon on your Desktop

---

