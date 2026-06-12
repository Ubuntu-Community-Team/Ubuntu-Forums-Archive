---
title: "Problem with GPS using 11.04"
date: 2011-05-22
forum: General Help
---

### Post by G4MJW on 2011-05-22
Hi, I've been using my little Asus Eee PC 900 with Ubuntu as a Marine Navigator for a few years.

My GPS (Evermore SA-320 USB Marine GPS) uses **[COLOR="Red"]GPSD[/COLOR]** driver installed through Synaptic package manager. My Navigation program is **[COLOR="Blue"]OpenCPN[/COLOR]** (Chart Plotter Navigator) downloaded and then installed using Ubuntu Software Centre.

It's worked fine using Ubuntu 8.XX, 9.XX and 10.4  I've upgraded to 11.04 and have problems with the GPS.

I boot up and then load OpenCPN, go into the navigator but no GPS present. I tried un-plugging it and then plugging it in again but that does not work. The only way I can make it start is that when I shut down the machine, then un-plug the GPS. After starting the machine on the next day or session, when it's fully booted, plug in the GPS. Then launch OpenCPN and the GPS is there.

With previous versions of Ubuntu, I left the GPS permanently connected and it always came up OK.

Any ideas?

Many thanks

Steve Carey

---

### Post by ajgreeny on 2011-05-22
It sounds as if you need to delay the start of OpenCPN to allow the full desktop environment to load completely.   OpenCPN is, I presume is in your startup applications list at the moment.  If this is the problem you can do it by starting OpenCPN with a compound command in the startup applications list of ```

```bash -c "sleep 20; *opencpn*"

I have no idea what the normal command is, but obviously, use whatever is normally used to start the application.  The sleep 20 will add a delay of 20 seconds before the start of opencpn, but you may need trial and error to get that time delay right.

---

### Post by G4MJW on 2011-05-22
No, I don't start OpenCPN immediately, but when I do, I click on the icon. Often I will have checked email and done a few other things and it maybe 10 mins or so before I launch the chartplotter, as I've always done.

I had thought of delaying GPSD driver but I can't see that would do anything.

It's always worked with the previous versions and yesterday I did go back to 10.10 and it worked perfectly!

Steve

---

