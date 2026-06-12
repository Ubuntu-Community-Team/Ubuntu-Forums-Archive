---
title: "Gnome Clock Applet shows time one second behind"
date: 2011-04-17
forum: General Help
---

### Post by ve3gtc on 2011-04-17
Good day all,

I recently noticed that the time displayed in the Gnome Clock applet is exactly (or nearly so) one second behind NTP time.

I have a NTP server on my small network to which I sync my other PCs. Some of the applications I run are critical of time and need sub second accuracy - I am also a bit of Time Nut as well.

My NTP server is OK. My PCs can sync to my NTP server OK. My applications which require precise time get the right time from NTP - BUT - the time displayed in the GNOME Clock applet is always behind one second!

I have spent much time searching for others with similar problems and their solutions but so far nothing - hence my asking here, why do I see this behaviour and what can I do about it?

cheers, Graham

---

### Post by dino99 on 2011-04-17
so you are on a real time system ? with real time kernel ?

fighting against 1 second diff is hazardous: which to blame ? ntp, isp, dns, kernel, your settings

good luck :(

---

### Post by ve3gtc on 2011-04-17
> **dino99 said:**
> so you are on a real time system ? with real time kernel ?

fighting against 1 second diff is hazardous: which to blame ? ntp, isp, dns, kernel, your settings

good luck :(

Real Time? no

Real Time kernel?  no - only on linux box which drive a CNC machine.

One second time difference - not really. It is the GNOME clock applet that seems to behind one second all the time. Other apps are getting time correctly as will running date from a terminal display the correct time.  it is just the GNOME clock applet that is out.

This is not that big a deal it is just disconcerting to see the desktop clock lag behind real time.

Is there some way to configure the Gnome Clock applet other than to have it one or off?

cheers, Graham

---

### Post by mightymouse2045 on 2012-06-09
> **ve3gtc said:**
> Real Time? no

Real Time kernel?  no - only on linux box which drive a CNC machine.

One second time difference - not really. It is the GNOME clock applet that seems to behind one second all the time. Other apps are getting time correctly as will running date from a terminal display the correct time.  it is just the GNOME clock applet that is out.

This is not that big a deal it is just disconcerting to see the desktop clock lag behind real time.

Is there some way to configure the Gnome Clock applet other than to have it one or off?

cheers, Graham


Did you resolve this because I am having the same issue. I am updating from my cisco router and when I do a show clock on the router it is always 1 second faster than my ubuntu system time

It's rather annoying

---

