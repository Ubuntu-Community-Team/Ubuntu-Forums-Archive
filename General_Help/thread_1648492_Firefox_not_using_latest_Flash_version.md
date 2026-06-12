---
title: "Firefox not using latest Flash version?"
date: 2010-12-18
forum: General Help
---

### Post by ManyBeers on 2010-12-18
I run Ubuntu 8.04 on my Sony laptop and Firefox 3.6.13 and have installed 
via synaptic Flash 10.1.102.65-2 but Firefox uses Flash version 9.
How come? 

By the way this is on a fresh reinstall of both Firefox and Flash and 
a newly created profile.

---

### Post by BicyclerBoy on 2010-12-18
The synaptic flash package is just a downloader/installer script...

Did this actually complete successfully?
What does the browser "Tools - add-ons -  plugins" report?

Try "find updates" from that window..

---

### Post by ManyBeers on 2010-12-18
> **BicyclerBoy said:**
> The synaptic flash package is just a downloader/installer script...

Did this actually complete successfully?
What does the browser "Tools - add-ons -  plugins" report?

Try "find updates" from that window..
9.0.r289. 
So i need to upgrade through the Add-on interface correct?

---

### Post by BicyclerBoy on 2010-12-18
I would let the synaptic package manager install the flash updating script again.
You should click the "show details" & watch the terminal stdout info..
You need to read what it says its doing...

Are you sure your firefox is up to date ?
You didn't manually install it outside the package manager (synaptic) ? i.e. direct download from mozilla ??

---

### Post by ManyBeers on 2010-12-18
> **BicyclerBoy said:**
> I would let the synaptic package manager install the flash updating script again.
You should click the "show details" & watch the terminal stdout info..
You need to read what it says its doing...

Are you sure your firefox is up to date ?
You didn't manually install it outside the package manager (synaptic) ? i.e. direct download from mozilla ??

No. I installed through Synaptic(.Firefox ver. 3.6.13)
It says i already have Ver. 10 installed.

---

### Post by BicyclerBoy on 2010-12-19
Using the Firefox add ons dialogue : Manually remove the old flash plugin.
Maybe that is blocking the updated plugin.

Remove anything adobe or flash or shockwave.

Restart firefox & browse to a flash content website.

What happens ?

Should be no flash content just an f character as placeholder.

Then try the flash install again..the install may be invoked by clicking on flash content (in browser).
Out of ideas now..

---

### Post by colobix on 2010-12-19
Or you can install the AddOn called Flash AID.
This addon will do the whole work for you.

---

### Post by ManyBeers on 2010-12-19
> **BicyclerBoy said:**
> Using the Firefox add ons dialogue : Manually remove the old flash plugin.
Maybe that is blocking the updated plugin.

Remove anything adobe or flash or shockwave.

Restart firefox & browse to a flash content website.

What happens ?

Should be no flash content just an f character as placeholder.

Then try the flash install again..the install may be invoked by clicking on flash content (in browser).
Out of ideas now..

I moved libflashplayer.so(ver 10.1r102)...from /usr/lib/adobe-fashplugin..
to../usr/lib/flashplugin-nonfree...and now Firefox is using the latest
Flashplayer but it still won't work in fullscreen.

---

