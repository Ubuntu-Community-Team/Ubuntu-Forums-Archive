---
title: "prevent overwrite of xorg.conf persistent usb install"
date: 2011-12-19
forum: General Help
---

### Post by maestrobwh1 on 2011-12-19
I have a quirky xorg.conf for a compiled via driver in ubuntu intrepid, persistent install.  I know:-P  It was a custom built iso for this machine at the time.  It is the only version that has everything working and it boots really fast.

I need to either disable the whatever init script that overwrites xorg.conf or add a script that inserts my custom one before x starts. Being that is is still booting as a live cd, I understand why this happens but since I have persistence, I should be able to work around this?

I have an OQO model 02 with the via graphics (driver works compiled from via source) and a custom xorg.conf with needed modelines for the 800x480 display.  

It keeps getting wiped out at the next boot ant it keeps trying to use the openchrome driver which does not work.  The person who modified the iso mentioned in the very old post that veas was the only driver that could work with iso (true if booted with no persistence file).

Currently I either boot with "xforcevesa" and just use vesa OR i run "single" and drop to root and manually cp the custom xorg, then reume normal boot.

I have added a command to /et/rc.local but the overwrite is happening after that.  I have also blacklisted the via_openchrome driver and added the via driver to /etc/modules.

---

