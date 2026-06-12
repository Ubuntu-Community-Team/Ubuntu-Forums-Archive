---
title: "Having trouble with second monitor."
date: 2012-08-09
forum: General Help
---

### Post by modersbach on 2012-08-09
For the most part, I am new to Linux and Ubuntu. So please go easy on me with your answers. 

I have a Toshiba Satellite A665D with a broken monitor. The monitor is completely busted with over 80% of the screen unreadable. I cannot afford to get this fixed so I have a second "external" monitor plugged into it and am just using it as a desktop.

This setup -completely unchanged- worked flawlessly in Windows 7. 

* Whenever I try to run a full screen application, the "external" monitor just turns off. Even when I manage to blind-click the application closed (Is there an alt+f4 for Ubuntu?) my external monitor will not turn back on, and I have to reboot my computer to get it back.

* This also seems to happen if I leave my computer alone for too long. (standby mode, maybe?) And again, the only solution I can find is to restart the system. 

Thank you.

---

### Post by gordintoronto on 2012-08-09
Welcome to the Forums!

"Whenever I try to run a full screen application, the "external" monitor just turns off." That seems odd. On my laptop, I can connect to my TV set, and by default the two screens display the same thing, with no problems.

The Alt-F4 for Ubuntu is: Alt-F4.

You might want to run System Settings and select: "Never" for "Turn screen off when inactive for.." in (maybe) power management or Brightness and Lock.

What is the video adapter in your laptop? (From the Dash, run Terminal and enter the command: lspci
One or two lines will contain "VGA", and that describes your video adapter(s).)

Can you be specific about what version of Ubuntu you are using? For example, 32-bit Ubuntu 12.04 Desktop.

---

