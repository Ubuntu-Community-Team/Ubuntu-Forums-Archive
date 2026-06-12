---
title: "Sound doesn't switch to headphones"
date: 2010-10-07
forum: General Help
---

### Post by deathanatos on 2010-10-07
I have a laptop computer running Ubuntu 10.04 LTS. When headphones are inserted into the headphones port, sound continues to come out the internal speakers, and not through the headphones.

This works fine in Windows 7, so the hardware appears to be good. This did work properly when we first installed Ubuntu - it spontaneously stopped working one night, so I'm not sure what we did to make it stop acting normally.

I have run "alsamixer" in the terminal, and toggled every mute and volume bar there is (there are only 4).
The laptop is a Toshiba Satellite T135D-S1324.

General information:
uname -a:
Linux ... 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

lspci:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

(the laptop has a normal pc mic/headphones and an HDMI port, so I suspect that's why there are two devices listed...)

Thanks!

---

### Post by drifter2502 on 2010-10-08
This worked for me on my laptop. Now internal speakers switch off when my headphones are plugged in. I am  also able to record from Line In stream now but not before this fix.....
[http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/](http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/)

---

