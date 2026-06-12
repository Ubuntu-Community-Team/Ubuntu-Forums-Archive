---
title: "Citrix not working on 9.1"
date: 2009-11-14
forum: General Help
---

### Post by TaiChiRabbit on 2009-11-14
Hi
I've upgraded from Ubuntu 9.04 to 9.1 and my Citrix is no longer working.  I've reinstall Citrix 11 Linux Client software and also installed the libmotif3.  The problem is when the launch.ica pop-up box appears, I tell Firefox (v3.5.5) to open with /usr/lib/ICAClient/wfica (and have also tried /usr/lib/ICAClient/wfica.sh), a 1.5kb file is downloaded but nothing else happens!

The frustrating thing is that under 9.04 it worked fine (maybe beginners luck that time ;)).  Any ideas how I can get it to work?


 guy@guy-desktop:/usr/lib/firefox-3.5.5/plugins$ ldd /usr/lib/ICAClient/wfcmgr 
    linux-gate.so.1 =>  (0x00e40000)
    libXm.so.4 => /usr/lib/libXm.so.4 (0x0031d000)
    libXp.so.6 => /usr/lib/libXp.so.6 (0x00ff5000)
    libXpm.so.4 => /usr/lib/libXpm.so.4 (0x00110000)
    libSM.so.6 => /usr/lib/libSM.so.6 (0x00a3a000)
    libICE.so.6 => /usr/lib/libICE.so.6 (0x00e8d000)
    libXmu.so.6 => /usr/lib/libXmu.so.6 (0x00122000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00a45000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x007c5000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00aef000)
    libXt.so.6 => /usr/lib/libXt.so.6 (0x00599000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x00611000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x0013b000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x00f5e000)
    libuuid.so.1 => /lib/libuuid.so.1 (0x0014b000)
    /lib/ld-linux.so.2 (0x00c60000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00150000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00f18000)

---

### Post by tars_ac on 2009-11-14
I just tried Citrix on my 9.10 installation (btw, 9.10 stands for year.month, so usually it's easier to understand if you include the full thing).

The desktop client doesn't appear to work anymore (missing one of the shared libraries), but the Firefox plugin (version 9.0.0) is working fine.

Not sure if I can help you out, but I thought I'd let you know that someone is having success at least...

---

### Post by derekweber on 2010-03-28
Not sure if you've solved your problem but this is exactly what I was playing with tonight.

Thanks to the Ubuntu Community, it's already documented and worked handsomely for me on 32-bit Ubuntu: [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

Winner!

---

