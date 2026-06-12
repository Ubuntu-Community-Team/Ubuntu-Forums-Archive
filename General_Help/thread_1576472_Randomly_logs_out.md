---
title: "Randomly logs out"
date: 2010-09-17
forum: General Help
---

### Post by Karl1982 on 2010-09-17
Occasionally over the past few weeks (maybe twice a week considering light usage), my Ubuntu 10.04 laptop will randomly just log me out and drop me back at GDM like I had just booted.  I briefly see the Ubuntu loading screen, then very briefly see a full screen nVidia logo (I have an embedded nVidia graphics chipset), and then I'm back to the GDM login screen.

It always seems to happen when I'm typing, but not anything in particular or in any particular program.  Usually I have the problem in Firefox, but just this morning, it did it when I hit enter in tsclient to connect to a remote server.  I'd thought maybe I was accidentally hitting a hotkey combo or something until this... Enter was the only key I pressed in several seconds.  I haven't seen any discernable pattern to it, just that it always seems to be when I'm striking keys.

The only notable changes I've made was about a month ago, I rearranged my Gnome panels and replaced one with a Cairo dock.  Could it be crashing Gnome or X?  I have a backup of my Gnome config from before I made the changes, but I wish I could identify that as the problem before I go reverting everything.

Edit: It's normal for my installation to see a flash of the nVidia logo when logging out, so I don't think that's relevant.  It looks like a perfectly normal logout.  Just at very inopportune moments, and closes everything I had open...

---

### Post by mihamil on 2010-09-17
my laptop is doing the exact same thing.  Please check your /var/log/syslog.  Mine shows that is was unable to reconnect to the xserver right when this happens.  Seemed to be happening a LOT on realtor.com the other day.  Maybe we can give others a clue to help us.

MH

---

### Post by Karl1982 on 2010-09-23
Ok, I've been looking over the syslog over the last several incidents, and I'm seeing a general pattern.  I'm wondering if it might have something to do with intermittent hard drive failure in my case because I have a solid state in my laptop, which I've already replaced for a brand new drive under warranty twice since I bought it.  I won't post the whole thing because just the two minute span up to the point where it happens is quite long, but the following lines have caught my attention.  First it seems there's a problem with DHCP, like it has an error and then releases the IP and deactivates the interface.  Then I see stuff like this:

```
Sep 23 19:09:04 karl-dv6325u wpa_supplicant[1326]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 23 19:09:04 karl-dv6325u gdm-simple-slave[2235]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 19:09:04 karl-dv6325u pulseaudio[2232]: core-util.c: Failed to create secure directory: Permission denied
Sep 23 19:09:04 karl-dv6325u pulseaudio[2230]: main.c: Daemon startup failed.
Sep 23 19:09:04 karl-dv6325u pulseaudio[2230]: core-util.c: Failed to create secure directory: Permission denied
Sep 23 19:09:04 karl-dv6325u pulseaudio[2230]: lock-autospawn.c: Cannot access autospawn lock.
Sep 23 19:09:04 karl-dv6325u acpid: client 1039[0:0] has disconnected
Sep 23 19:09:04 karl-dv6325u acpid: client connected from 2237[0:0]
Sep 23 19:09:04 karl-dv6325u acpid: 1 client rule loaded
Sep 23 19:09:04 karl-dv6325u acpid: client connected from 2237[0:0]
Sep 23 19:09:04 karl-dv6325u acpid: 1 client rule loaded
Sep 23 19:09:05 karl-dv6325u pulseaudio[2240]: core-util.c: Failed to create secure directory: Permission denied
Sep 23 19:09:05 karl-dv6325u pulseaudio[2240]: lock-autospawn.c: Cannot access autospawn lock.
Sep 23 19:09:05 karl-dv6325u pulseaudio[2240]: main.c: Failed to acquire autospawn lock
```Those 3 lines about pulseaudio repeat in sequence for several pages.  I'll omit the rest.  Also worth noting, no sound was playing when this crash occurs, nor was I expecting any.

```
Sep 23 19:09:05 karl-dv6325u gdm-session-worker[2330]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 19:09:06 karl-dv6325u rtkit-daemon[1641]: Sucessfully made thread 2339 of process 2339 (n/a) owned by '114' high priority at nice level -11.
Sep 23 19:09:06 karl-dv6325u rtkit-daemon[1641]: Supervising 1 threads of 1 processes of 2 users.
Sep 23 19:09:06 karl-dv6325u rtkit-daemon[1641]: Sucessfully made thread 2355 of process 2339 (n/a) owned by '114' RT at priority 5.
Sep 23 19:09:06 karl-dv6325u rtkit-daemon[1641]: Supervising 2 threads of 1 processes of 2 users.
Sep 23 19:09:06 karl-dv6325u gdm-simple-greeter[2324]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep 23 19:09:06 karl-dv6325u rtkit-daemon[1641]: Sucessfully made thread 2357 of process 2339 (n/a) owned by '114' RT at priority 5.
Sep 23 19:09:06 karl-dv6325u rtkit-daemon[1641]: Supervising 3 threads of 1 processes of 2 users.
Sep 23 19:09:09 karl-dv6325u bonobo-activation-server (karl-2365): could not associate with desktop session: Failed to connect to socket /tmp/dbus-GTR97LkUDJ: Connection refused
Sep 23 19:09:10 karl-dv6325u gdm-session-worker[2330]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

```After searching for rtkit-daemon, I'm seeing this is a known issue with 10.04, but I haven't found a solution yet. I suspect either the bonobo-activation-server or the rtkit-daemon will end up being a key factor.  I'll look through the log a big more and see if maybe I can figure out what process that is rtkit-daemon is messing with.

---

### Post by lkjoel on 2010-09-23
I'm having the same problem
Could anyone help?

---

### Post by nickflyer on 2010-09-26
im having this issue as well

---

### Post by davidvandoren on 2010-09-26
same thing here including random crashes.

Trying to figure it out for a week now.

systemlog
```
Sep 26 12:50:00 david-desktop gnome-session[1642]: WARNING: Detected that screensaver has left the bus
```

```
Sep 26 12:50:02 david-desktop gdm-session-worker[2693]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
```

```
pulseaudio[2697]: module-alsa-card.c: Failed to find a working profile.
Sep 26 12:50:02 david-desktop pulseaudio[2697]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep 26 12:50:02 david-desktop gdm-simple-greeter[2691]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep 26 12:50:02 david-desktop rtkit-daemon
```

---

### Post by Karl1982 on 2010-09-26
Those of you saying you have the same problem, please post any log entries you have that are the same as ours. We have to narrow this down. 

Also, I'm finding the line about /etc/gdm/custom.conf inaccessible to be very suspicious. As I understand it, gdm initiates X, making it a child process, and therefore a crash and restart of gdm might close the x server and drop you back to the freshly-reloaded gdm's login screen. Or maybe it's that X restarts when it's called again by gdm. Either way, both gdm and X end up restarted by what's going on. I could see gdm failing to access a necessary file causing it to crash. So in my mind, that's one plausible explanation. We need more logs.

Does everyone have that line in their syslog? Is everyone using gdm?

---

### Post by nickflyer on 2010-09-27
i was having this issue and it looks like the fix was just posted
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640127](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640127)

---

### Post by Karl1982 on 2010-09-30
> **nickflyer said:**
> i was having this issue and it looks like the fix was just posted
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640127](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640127)

I have all updates installed, and it's still happening.  I don't think the changes they made have been put in the repository yet.  This is very irritating because it keeps interrupting and destroying my work.  How do I install this update?

---

### Post by jwedekin on 2011-09-16
Same issue (except I am using the LinuxMint version based on Ubuntu 11).

I will attach all the logs that contain information around the time of the BSOD, which is 21:10.

---

### Post by OneidaLake on 2012-01-18
hmmm...Interesting.  I'm a newbie, so I'm wondering if a more advanced user could comment on this theory.

Not sure if this is related, but I no longer have this problem after I installed a semi-permanent bluetooth adapter.  This has been annoying me for several months now.  I'm on 11.04 and until last month, it randomly and abruptly logged me out every day.  Also, I was having this other problem where my computer would freeze for no apparent reason and I would have to do a "hard boot".

Now that I think about it, this problem occurred around the same time that I experimented with bluetooth by temporarily installing my wife's bluetooth adapter.  I was just testing out her adapter and I removed it within an hour.  Since that time...random logouts at least once a day.

Last month, I decided to buy an adapter of my own, so I purchased one of those "mini" usb bluetooth adapters, so I could keep it plugged in 24/7.  I'm really grasping at straws here, but since I've had it plugged in, I have not had a single random logout or screen freeze.

Thoughts?

---

### Post by forez84 on 2012-08-30
I have that problem too :(

---

