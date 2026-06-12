---
title: "PXE install"
date: 2012-01-20
forum: General Help
---

### Post by PunkLV on 2012-01-20
Greetings,

I'm trying to resurrect a Dell Latitude C600 and get winxp on it.
The thing is, DVDROM does not work, it does not support USB-stick booting, so the only viable option is PXE. I myself am running debian.

So far I've managed to setup tftpd-hda, udhcpd and samba (not entirely sure).
The PXE booting goes fine and well till the point of configuring Network. It prompts to select a driver to use for the NIC adapter but none of them work.

The /srv/tftp/i386 has the lan drivers packs inside and should work for almost any existing NIC. So as far as I can tell the only options for this to happen is misconfigured samba or missing/misplaced files in /srv/tftp

How to add/point to the correct drivers? Or lmhosts need to be edited in some way?

I've never dealt with PXE before so any insight would be appriciated.

---

