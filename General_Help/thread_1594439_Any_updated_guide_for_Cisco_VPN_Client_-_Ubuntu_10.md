---
title: "Any updated guide for Cisco VPN Client - Ubuntu 10.10"
date: 2010-10-12
forum: General Help
---

### Post by altjx on 2010-10-12
Any updated guides anyone know of that works with Ubuntu 10.10 to get Cisco VPN Client (not Anyconnect) working with the latest version of Ubuntu?

---

### Post by dvannatter on 2010-10-14
The problem is caused by the renaming (relocating) the <linux/autoconf.h> file to <generated/autoconf.h>. There are 4 files that include this reference. linuxcnpi.c, frag.c IPSecDrvOS_linux.c and interceptor.c. Edit these files, change the filenames and rebuild it. 

Thats all I did to make it work.

---

### Post by brokenromeo on 2010-10-14
I just install vpnc and vpnc plugin from Software Center, it allows me to import the cisco profile and connect to my company network...

---

### Post by iaggrey on 2010-10-17
> **altjx said:**
> Any updated guides anyone know of that works with Ubuntu 10.10 to get Cisco VPN Client (not Anyconnect) working with the latest version of Ubuntu?

The patch/info provided by [tuxx-home]("http://projects.tuxx-home.at/?id=cisco_vpn_client") still work for me on a vanilla install of Ubuntu 10.10 64-bit. 

[L.A.M.N.K.]("http://http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/") provides an even easier way, but essentially just wraps everything mentioned at tuxx-home in a convenient patch.

**[COLOR="Red"]FYI:[/COLOR] Make sure you have [COLOR="Green"]ia32-libs[/COLOR] installed. No source except tuxx-home mentioned this...but it was at the bottom of their page. The "no file or directory" error I was getting because of that was driving me CRAZY.**

---

### Post by thelaw on 2010-10-27
I am attempting to install vpnclient-x86-4.8.02.0030-k9.tar.gz.  I am unable to run the 'patch' command successfully.  I have performed the following:

- download the client from Cisco
- download vpnclient-linux-2.6.24-final.diff
- change to vpnclient folder
- run: patch ../vpnclient-linux-2.6.24-final.diff

When running 'patch' my cursor drops to the next line and just hangs - no output, etc.

I do have a previously patched copy (version 8.0.1.0640) from my old hard drive (Hardy Heron) so I copied that over and the install seemed to work, however, running etc/init.d/vpnclient_init start fails with an error.

Additionally, I took the advise of modifying the 4 files (linux/autoconf.h > generated/autoconf.h) but that made no discernible difference. This was tried on both the 8.01 (patched) and 8.02 (unpatched)

Finally, I have verified the headers are installed and, indeed, re-installed (says they're already their).


Suggestions?

---

