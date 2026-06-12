---
title: "Terminal Issue... can't install anything"
date: 2009-12-05
forum: General Help
---

### Post by dynamic.flare on 2009-12-05
So I just downloaded ubuntu 9.10 today and already having problems - lots.  First off, it says my hard disc is failing and this is a brand new dell laptop.  I posted this question on a separate thread but thought I'd add it here in case it is relevent to my issue now.

Anything I'm trying to download following directions with the terminal isn't working.  Broadcom chipset driver for linux won't install, flash player won't install, and I can't find a messenger system that someone told me comes automatically with linux.

I'm such a noob here, be kind :)

---

### Post by QIII on 2009-12-05
First, I would (cautiously) set aside the message about your disk.  There was some bugginess at least up until the Beta with regard to this.  I don't remember if I saw it after I did a clean install of Karmic when the final release came out or if it persisted until I did an update.

Could you please post one of the commands you are trying to do and the result?

It could be that you can't install something because you do not have the source in your sources list.

---

### Post by fluffman86 on 2009-12-05
First, plug into an ethernet cable to get online.  Then go to System > Admin > Hardware and install your wireless driver.

Then go to System > Admin > Software Sources, and check the first 4 boxes.  Close the window and press reload when necessary.

Now, go to Applications > Ubuntu Software Center > View > All.  Search for "flash".  Double click Ubuntu Restricted Extras (the first entry?) and then press install, type your password, and wait.  Flash, microsoft fonts, Java, and more will install.

If you're looking for pidgin, Ubuntu made the decision to replace that with Applications > Internet > Empathy by default.  It works OK for me, but I found it kind of confusing.  Personally, I still prefer pidgin, which can also be installed with Application > Ubuntu Software Center.  When it installs, you can launch it with Applications > Internet > Pidgin.

---

### Post by dynamic.flare on 2009-12-05
so somehow I changed the command for the hardware devices and don't know what to change it back to.... eek......

---

