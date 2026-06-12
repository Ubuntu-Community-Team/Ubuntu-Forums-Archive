---
title: "XP through VirtualBox"
date: 2009-07-21
forum: General Help
---

### Post by nmaster on 2009-07-21
I think I'm going to remove my Vista partition.  I rarely use it and it wastes disk space.  However, I will still need Windows for certain things.  I want to know the limitations of using XP though VirtualBox.  I know that OSE doesn't allow the use of USB, so just assume that I'll be using the closed-source edition.  

Will I be able to connect to a networked printer?  I'll be using my roommate's printer in the fall and I've heard that linux doesn't always have good driver support for certain brands.  If VirtualBox could solve this issue, then that would be perfect.  

Any other issues I could face?

Thanks for the info.

---

### Post by bacil on 2009-07-21
Vbox allow you to access network as separte computer with its own MAC and no limitations to port or protocols, so you can use your mates printer no problem. 

i dont think there are anyh major gotchas i am runing several XP machines as well as one win7 and coupl 2003 servers in vbox as my test environment in our lab. and never experienced problems there. Mind you i use virtual box on RHEL, but i dont see that as an issue

---

### Post by WIGGMPk on 2009-07-21
It only gets 'hairy' when you are trying to do specific things that might not apply to all users.

For instance, the only two situations I have ran into trouble with are as follows:

Upgrading Firmware on Logitech Harmony Remote; Windows XP Pro SP3 guest would 'lose' the connection to the remote during the update. This happened because during the upgrade, the remote 'rebooted' as part of its normal process and the guest lost the connection (despite having custom USB filters for the device). This problem seems to have been fixed with the release of Virtualbox 3.0 (proprietary version of course)

Upgrading Operating System on Verizon Blackberry Storm; Windows XP Pro SP3 guest would again 'lose' the connection to the remote during the update. I suspect this is a problem with the Desktop Manager needing hardware level access to the device during the upgrade. This still remains a problem for me (despite custom USB filters for the device) on Virtualbox 3.0

Other than those two specific problems.. Everything else (every day computing) on my guests have been fine. Windows 7 RC also works pretty well/quick in Virtualbox.

Now Virtualbox 3.0 (proprietary version) includes experimental drivers for 3D acceleration for graphics.

---

### Post by nmaster on 2009-07-21
sounds like i'm good to go.  if anyone else has had an experience worth sharing please feel free.  thanks for the responses.

---

### Post by irv on 2009-07-21
I have been running Virtualbox 3.0, and it supports USB devices. I have been using USB memory sticks a 1TB USB external Hard Drive, a USB keyboard, and USB Mouse with no problems. Here are a few Screen shots.
[ATTACH]121921[/ATTACH]

[ATTACH]121922[/ATTACH]

[ATTACH]121923[/ATTACH]

---

### Post by nmaster on 2009-07-21
> **irv said:**
> I have been running Virtualbox 3.0, and it supports USB devices. 


is that the one in the repos?  i'd rather use ose, but if the usb support is only in closed source then i'll go with that.

---

### Post by WIGGMPk on 2009-07-21
To be clear, USB support is NOT available in the Open Source Edition (OSE) and only available in the proprietary version.

---

### Post by irv on 2009-07-21
> **neal.m.master said:**
> is that the one in the repos?  i'd rather use ose, but if the usb support is only in closed source then i'll go with that.

Here is the download site: [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by nmaster on 2009-07-21
> **neal.m.master said:**
> I know that OSE doesn't allow the use of USB, so just assume that I'll be using the closed-source edition. 

sorry about that. given my initial post, i just wanted to be clear and i wasn't mistaken about ose.

---

