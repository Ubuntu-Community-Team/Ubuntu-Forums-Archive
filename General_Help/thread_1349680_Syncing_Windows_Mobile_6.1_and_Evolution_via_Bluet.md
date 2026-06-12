---
title: "Syncing Windows Mobile 6.1 and Evolution via Bluetooth"
date: 2009-12-08
forum: General Help
---

### Post by johnathanamber on 2009-12-08
Hey everyone,

**What I've got:**
Ubuntu 9.10 (64bit)
USB and Bluetooth (gnome-bluetooth)
SynCE
MultiSync
Palm Treo 700wx with Windows Mobile 6.1 Professional

_I was using Windows XP, but about two months ago I've switched to Ubuntu._

I've tried to follow the wiki for SynCE:
[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)

But I can't seem to get my device to be seen via the USB.

That is OK really since I do not want to use the USB cable anyway, rather use Bluetooth.

I've been able to connect my device with bluetooth using gnome-bluetooth.

I can see my device.

I have gone through the wizard to setup my device with gnome-bluetooth with a passcode. So that part is done.

In the services with my phone I see:
Serial (checked)
DUN
Activesync (checked)

When i try to sync using Activesync 'Connect via Bluetooth'... it tries to open the port via bluetooth and then it gives me 'Attention required'.

**It tells me:**
"*Port not available: cannot communicate with the pc because the port is not available*"

Due to the above link, I have already installed **synce**, **OpenSync** and **multisync** as well as the **evolution plugins**.

I've gone through numberous tutorials to no avail. The above tutorial is the closest that I've been able to get.

How can I correct this and sync my WM6.1 phone with evolution via Bluetooth?

Thank you for your time and Merry Christmas!
Johnathan

---

### Post by johnathanamber on 2009-12-29
*bump*

Hey everyone, Any ideas?

BTW, I've found out today that my USB cable isn't working... so I have to sync via bluetooth.

---

### Post by johnathanamber on 2010-02-22
*Bump*

BTW, USB cable is fine!

So back to the original posting.

Anyone have any ideas?

Thank you,
Johnathan

---

### Post by HtmlGifted on 2010-03-09
my question is why i can't get my blue tooth to show up in multi sync

---

### Post by johnathanamber on 2010-04-14
Does anyone have any puck with syncing their Palm Treo 700wx via Bluetooth?

If so, are you use synce-hal or odccm?

Are you using the bluetooth manager that came preinstalled with Karmic?

Any help would be greatly appreciated.

Thank you and God bless,
Johnathan

---

### Post by graphius on 2010-05-29
I just set up a bluetooth USB dongle on my laptop to sync with my palm (older unit, purchased for a song)
I had to purge and reinstall bluez-utils, then, for some strange reason, two reboots to get the bluetooth to work.
I set up a connection using System --> Preferences --> Bluetooth and followed the wizard.
On my palm, I set up a bluetooth connection for a hotsync
Then, finally, I set up a conduit in Evolution using the Sychronization Preferences
it seems to work fine.

---

### Post by johnathanamber on 2010-06-02
@Graphius,

Thank you for the reply.

Only problem is that your Palm is using the Palm OS and not Windows Mobile. Which is what I am using. Palm Treo 700WX.

---

