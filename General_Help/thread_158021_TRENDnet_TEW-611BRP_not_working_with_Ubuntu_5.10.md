---
title: "TRENDnet TEW-611BRP not working with Ubuntu 5.10"
date: 2006-04-10
forum: General Help
---

### Post by scb147 on 2006-04-10
I just bought a new TRENDnet TEW-611BRP wireless router and I hooked it up with a wired connection to my Dell notebook.  I am running Ubuntu 5.10 on it using Network Manager.  It won't work! The notebook just keeps saying "Aquiring network address".  I then took the same notebook, booted into WinXP, and it connected right up.  So I took the opportunity to upgrade the firmware from 1.00 to 1.04.  Did that, rebooted the router, and rebooted back into Ubuntu.  Same problem, "Aquiring network address".  Still in Ubuntu, I then take my network cable and plug it into my old D-Link router that I am upgrading from.  Connects right up and gets an IP.  I have no idea what the problem is since the TRENDnet works with WinXP on my notebook and my old D-Link works with Ubuntu on the same notebook.

I have also tried the wireless connection the same way as above and it does the same thing.

I am thinking of disabling Network Manager in Ubuntu and using the regular networking properties in Ubuntu to see if Network Manager is the problem.

If anyone has any ideas on what could be the problem, please let me know. If this TRENDnet doesn't work nicely with my Ubuntu notebook, then I will have to look into another router.

Thanks!

---

### Post by PapaWiskas on 2006-04-10
Maybe try using a static address instead of relying on the router to send you one via DHCP.  I had a similar problem once, I also went as far as putting in DNS entries as well.

---

### Post by scb147 on 2006-04-10
Forgot to mention that I tried setting a static DHCP address.  It acted the same way as using a dynamic DHCP address.

I also don't have the WAN connected to anything yet.  I wanted to get the router setup before I plugged it into the cable modem.

---

### Post by scb147 on 2006-04-11
I was able to get Ubuntu to connect with the router using DHCP, but only after I disabled Network Manager.

With Network Manager running, it keeps trying to renew the IP address.  It does this every few seconds.  My log is full of entries when I have Network Manager running.  DHCP using Network Manager works with my old D-Link router no problem.  It just doesn't want to work with my new TRENDnet router.

Are there any settings for Network Manager somewhere that I can tweak that might allow me to get this working?

P.S. - I am running Network Manager 0.4.1

---

