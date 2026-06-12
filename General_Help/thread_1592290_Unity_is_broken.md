---
title: "Unity is broken"
date: 2010-10-10
forum: General Help
---

### Post by Locke2053 on 2010-10-10
I have Netbook Edition. I just upgraded with do-release-upgrade, hoping to see the new Unity window manager. After the upgrade, my desktop has reverted to the default gnome window manager. When I select "Netbook Edition" under System / Administration / Login Screen, it STILL uses the default window manager.

How can I enable unity? Or is this just a bug and I have to wait for an update?

The system is 10.10 Maverick Meerkat 32b running under VirtualBox. It was upgraded from 10.04 Netbook Edition.

---

### Post by rapiertg on 2010-10-10
As far as i know unity needs some graphic acceleration on composite enabled. If it doesnt detect it it go back to login screen. Check if 3d is enabled in your VBox.

---

### Post by Locke2053 on 2010-10-10
The only way I was able to get any progress was to log out and select the 2D Netbook option from the login menu. The 2D Netbook version should be the failover.

---

### Post by kerry_s on 2010-10-10
> **Locke2053 said:**
> The only way I was able to get any progress was to log out and select the 2D Netbook option from the login menu. The 2D Netbook version should be the failover.

there is no 2d in the new netbook.

---

### Post by Locke2053 on 2010-10-11
Well, I upgraded, so it seems I still have the 2D option installed, and that's the only one that works for me.

---

### Post by gear.h34d.2012 on 2010-10-11
I'm having the same issue. I'm trying to load 10.10 Netbook on my laptop (trying to use Unity and try it out) and  my install defaults to standard Gnome because I can't load my Nvidia drivers until I load into the session. With no 2D fallback, this is becoming extremely bothersome. Anyone know what I can do?

---

### Post by scratman on 2010-10-11
I can use the 2d fallback, I just selected the 2d option at the bottom of the initial login screen. The 3d option does also work, but Mutter takes up a lot of my system resources (30+ MB on a system with only half a gig) so by the time I have a few apps going the system becomes slow, unresponsive, and eventually needs to be turned off and back on.  I'm hoping there will be some updates that will resolve this issue, otherwise I will simply keep using the 2d fallback.  Either that, or revert to 10.04 as that was extremely stable, and I'd much rather do that than spend time and money upgrading the memory in my Acer Aspire One ZG5, given that it seems to be quite time consuming.

---

### Post by emanuel79 on 2010-10-11
I'have the oposite issue. All my sessions ends up with unity so i'm stuck with it.

---

### Post by DrJohn999 on 2010-10-12
I created a new VirtualBox instance of Netbook 10.10 on my 10.04 LTS desktop system over the weekend. GuestAdditions 3.2.8 installed but only a normal Gnome session would load (but no mouse pointer, display, etc. from the additions). The Netbook session failed with the same "driver required" message.

Today VirtualBox 3.2.10 r66523 appeared in the mainstream so I upgraded it on the Lucid desktop and then correspondingly upgraded the guest additions in the Netbook 10.10 VM. With 3D acceleration (2D only works in Windows hosts) enabled I get only a blank screen and completely nonfunctional system when logging into the Netbook desktop; only functionality is it responds to ACPI shutdown from VirtualBox. Regular Gnome is fine. With 3D disabled I again get the "need a graphics driver" dialog when logging into Unity.

The VirtualBox graphics driver does not offer any enhanced / extended capabilities in Preferences, Appearance, Visual Effects -- all items are disabled there.

Thus -- Netbook 10.10 + Unity still broken in VirtualBox. Will try it  on my Samsung NC-10 netbook in the near future (fresh install, not upgrade)...

---

