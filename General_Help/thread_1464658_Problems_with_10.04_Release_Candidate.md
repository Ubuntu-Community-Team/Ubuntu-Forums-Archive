---
title: "Problems with 10.04 Release Candidate"
date: 2010-04-28
forum: General Help
---

### Post by Wise Marmoset on 2010-04-28
I have installed on an Acer Aspire One netbook. The same problems with the Netbook Remix and Gnome.

(1) RESTART is hit and miss. It gets stuck and I have to do a hard shutdown (press the on/off switch for a few seconds)
(2) WIRELESS CONNECTION is hit and miss. The Connection Information goes missing. Have to shutdown & restart for it to work (restart never works)
(3) APPLICATIONS FREEZE all of a sudden. The mouse stops working and the keyboard stops working. I have to do a hard shutdown. Restart does not work.
(4) RHYTHMBOX launch is hit & miss. The little icon appears in the tray but I can do nothing - can't ask it to Show Rhythmbox and can't shut it down. Have to use System Monitor and kill the process there. IF MY MACHINE HAS NOT FROZEN DOWN COMPLETELY.
(4) GOOGLE CHROME and FIREFOX browsers run quickly when they start, and then, as time passes, run more and more slowly, until the freeze the whole computer.

The situation has gotten WORSE since I installed the RC. I have installed all the updates, but still getting worse.

Official Release is tomorrow. Can I expect better?

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Do not do hard shutdowns. In stead hold right-ctrl+right-alt+SysRq and type out REISUB. Have you monitored the logs to see why it's freezing? System>Administration>Log File Viewer

---

### Post by dino99 on 2010-04-28
> **Wise Marmoset said:**
> I have installed on an Acer Aspire One netbook. The same problems with the Netbook Remix and Gnome.

(1) RESTART is hit and miss. It gets stuck and I have to do a hard shutdown (press the on/off switch for a few seconds)
(2) WIRELESS CONNECTION is hit and miss. The Connection Information goes missing. Have to shutdown & restart for it to work (restart never works)
(3) APPLICATIONS FREEZE all of a sudden. The mouse stops working and the keyboard stops working. I have to do a hard shutdown. Restart does not work.
(4) RHYTHMBOX launch is hit & miss. The little icon appears in the tray but I can do nothing - can't ask it to Show Rhythmbox and can't shut it down. Have to use System Monitor and kill the process there. IF MY MACHINE HAS NOT FROZEN DOWN COMPLETELY.
(4) GOOGLE CHROME and FIREFOX browsers run quickly when they start, and then, as time passes, run more and more slowly, until the freeze the whole computer.

The situation has gotten WORSE since I installed the RC. I have installed all the updates, but still getting worse.

Official Release is tomorrow. Can I expect better?

did you dist-upgrade ? Your problems may have multiple reasons: hdd full, messy sources.list: be sure you only have official lucid repo, no ppa nor third party, and updating from main server; then you can run into console: sudo apt-get install -f && sudo dpkg --configure -a

---

