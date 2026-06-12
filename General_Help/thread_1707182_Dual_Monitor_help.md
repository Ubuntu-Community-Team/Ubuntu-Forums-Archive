---
title: "Dual Monitor help"
date: 2011-03-15
forum: General Help
---

### Post by loy66 on 2011-03-15
I have two display adapters (1)On board Nvidia Geforce 6150SE nForce430, (2) ePCI card GeForce 210 and was wanting to see one workspace on one screen and the second workspace on the second. I have a RCA 32" LCD flatscreen TV(720line) with  an PC inlet and a 17" LCD Dell monitor on the second. I finally got both screens to work (xorg.conf).  I can get the mouse curser to go off the right of one screen on to the left of the second screen. But this is not what I want. I want one display for workspace 1 and the second for workspace 2.  What do i need to do?

---

### Post by scouser73 on 2011-03-15
You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

---

### Post by loy66 on 2011-03-15
I was mistaken, I can get a different workspace on the second monitor.  The second monitor display does not have any icons in the desktop but GNOME icons are their and the background screen.  The only way I know of to get to the 2 nt display is moving the cuser out of the 1st display to the 2nd. Is there a way to xfer to the 2nd screen with a keyboard command? Where can I find doc on dual screen commands?

---

### Post by loy66 on 2011-03-16
Thanks for the reply. In terminal mode I entered "sudo gksudo vnidia-settings" an got a lot of errors messages. I entered "gksudo vnidia-settings" an got nvidia  X server settings. I selected X server Display Configuration.  I see two displays but there is no place  to check which will set the primary display  screen.  This settings window is the same one as I get when going to Perferences>Monitors  in Ubuntu 10.04LTS.;)

---

