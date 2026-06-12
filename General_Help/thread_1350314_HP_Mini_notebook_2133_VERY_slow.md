---
title: "HP Mini notebook 2133 VERY slow"
date: 2009-12-09
forum: General Help
---

### Post by digitaltoast on 2009-12-09
Bit of a newb here, but been loving ubuntu netbook remix 9.10 on my EEE PC 701 4gb.

Bought an HP mini 2133 refurb notebook. It came pre-loaded with SUSE Enterprise Desktop 10.1, which was blurgh, couldn't update, didn't like.

I quickly installed latest UNR, during install it said it had found a proprietary driver for my network card. It installed fine, I connected to network, went to finish install, and got dumped to a command line.

Restarted install, ignored driver, rebooted (connected via LAN cable). Not only is it incredibly slow (11 seconds to change folders or in fact do anything) but User Manager and Software Update were missing. I got them going fine from the command line, but even after full update, it's unworkably slow. Bear in mind this is installed from the same USB stick I installed my EEE701 from last week. I know the C7-M chip isn't known for speed, but it ran the gigantic bloated SUSE install just fine.

Is there something I should be doing? Or is UNR not compatible in some way with this HP? And how can I get my wifi driver back now?

---

### Post by darkksyde. on 2009-12-09
Does it have intel graphics?

---

### Post by digitaltoast on 2009-12-09
> **darkksyde. said:**
> Does it have intel graphics?
Here's a bit more about it:
[http://h40059.www4.hp.com/hp2133/](http://h40059.www4.hp.com/hp2133/)
[http://www.notebookreview.com/default.asp?newsID=4352](http://www.notebookreview.com/default.asp?newsID=4352)

According to that (and running the test) says:
VIA Technologies CN896/VN/896/p4M900 (Chrome 9 HC) (REV 01)
Driver in use: Openchrome

Also, the wireless is Broadcom BCM4312

Once an app is running, it's fine. The testing, shell, firefox etc runs speedy. It's the UNR GUI that runs like treacle.

---

### Post by digitaltoast on 2009-12-21
Don't know what to do - can anyone help at all? I need to know whether the notebook is faulty or what.

netbook-launcher seems to be eating 50-70% cpu, and I see lots of "poll_schedule_timeout" in column called "waiting channel"

---

### Post by digitaltoast on 2009-12-26
> **digitaltoast said:**
> Don't know what to do - can anyone help at all? I need to know whether the notebook is faulty or what.

netbook-launcher seems to be eating 50-70% cpu, and I see lots of "poll_schedule_timeout" in column called "waiting channel"

Found the answer in this thread:
[http://ubuntuforums.org/showthread.php?p=8544024#post8544024](http://ubuntuforums.org/showthread.php?p=8544024#post8544024)

Ubuntu Netbook Remix isn't so good on netbooks.... :(

---

