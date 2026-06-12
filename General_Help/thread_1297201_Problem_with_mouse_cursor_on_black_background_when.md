---
title: "Problem with mouse cursor on black background when connected to Windows via RDP"
date: 2009-10-21
forum: General Help
---

### Post by samalex on 2009-10-21
Hi,

This is a weird question and thus far I haven't found anyone else reporting this ... though with my setup others may not have noticed this problem.

Basically I run Windows XP at work and Ubuntu 9.04 at home.  When I VPN from home into work and use RDP to connect to my Win XP workstation it works great until I run a program with a dark colored background.  The mouse cursor never changes to white.

In both Windows and Linux the mouse cursor changes to either black when on a lighter colored background or white when on a darker colored background, but this isn't happening through the RDP connection.  So when I RDP into Work from Home and move the mouse cursor into a window with a black background it basically disappears due to it staying black.  

I've tried every RDP client out there (rdesktop, gnome-rdp, krdc, tsclient, etc) and every one has this problem so I'm wondering if it's Gnome.  Also no where can i find a setting in Gnome or in any of the RDP clients that changes this.

Has anyone ran into this?  Or does anyone know of a suggestion that'll work?  I'm a DBA so I spend most of my time in VS and SSMS, but for me it's easier to see the text when it's a lighter color (white or green) on a black background.  With the cursor staying black this makes it next to impossible to work with.

Also I recently moved from an older iBook back to Linux on my laptop (System76 Pangolin Performance) and I didn't see this on the Mac -- but I was using Microsoft's RDP client.  I did try to get the Microsoft RDP client working through Wine but doesn't work.  I also have Windows XP loaded through VirtualBox and even there the cursor is having the same problem which again makes me think it's something in Gnome.

Thanks for any suggestions or ideas ...

Sam

---

### Post by Johan Gambolputty on 2010-09-16
It's annoying this problem has been around for so long now without an update being arranged and sent down the standard updates.

Anyway, I have a quick and easy solution!

Remote desktop to your windows machine, go to the control panel, find your mouse settings, and choose a different mouse cursor set. Eg the normal aero one, if you're using windows 7.

I'm guessing the problem may be difficult to reproduce because the people having it have disabled all fancy windows effects on the windows machine ? I know I certainly have.

Anyway, i'm very happy now not to lose the cursor on black consoles, and to have a proper text icon over text boxes and text areas.

Hope it solves things for others.):P

---

