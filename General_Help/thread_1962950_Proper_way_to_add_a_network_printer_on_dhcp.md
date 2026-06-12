---
title: "Proper way to add a network printer on dhcp?"
date: 2012-04-21
forum: General Help
---

### Post by Roasted on 2012-04-21
Just curious what you folks may think about this scenario. Let's say you have a wireless printer that doesn't allow you to give it a static IP. On top of that, the printer isn't found automagically when you go to add a new printer. Traditionally, I've just added the printer via LPD, but that binds it by the IP the printer is on.

In the event that the printer's IP changes, then that link is essentially broken. Is there another way to add the network printer that isn't bound to the IP? Is LPD not optimal in this casE?

---

### Post by papibe on 2012-04-21
Hi Roasted.

A couple of ideas:[LIST]
[*]Set a DHCP reservation for the printer on your DHCP server, or router (if supported).
[*]If the printer does not allow an static IP, may be it allows to set up a hostname. Then, it may be possible to access the printer by hostname (if your DNS is on your LAN, i.e., it resolves no-domain LAN hostnames).
[/LIST]
Regards.

---

### Post by Roasted on 2012-04-21
I tried the reservation but the printer gets the same address next time I power it on. I assume it's holding onto a lease but on my router (NetGear 3700) I can't seem to find out how to delete dhcp leases like I could on my linksys back in the day. That's why I was hoping there was an alternative way to set up the printer to bypass that need.

---

### Post by Roasted on 2012-04-22
Along with my above question I'm kind of curious about something else. I've heard a lot about IPP but I never knew how to set it up. I always just used LPD based connections since they typically worked. Only downside is, LPD is very IP based, so if the printer's IP changes, "printer offline". Ehh...

So anyway, would IPP be a better option? Would it by chance allow me to print without being bound to the IP. How would I even set it up?

---

### Post by hawthornso23 on 2012-04-22
It is possible to install a network printer by name so that it can be accessed even if its IP changes with DHCP. You need to install WINS (via samba) and add it to the hosts list in nsswitch.conf (order matters - be VERY careful). Then when installing the network printer, you replace the IP address (of the found network printer) with the WINS name. It will ponder for a second or so while it checks that a printer of that name can be found, and if you've done it all right it will then install. It was a while ago and I no longer have things set up that way. But it can be done - I know because I've done it.

---

### Post by Roasted on 2012-04-22
Hmm I see. It's frustrating because I finally got a decent all in one, but the lack of a Web GUI is pretty lol. A specific Mac and windows utility to manage it? Come on guys... What's even more frustrating is my router IP reservations isn't working, which of course would be such an easy work around.

EDIT - derp derp... seems as if I forgot the "apply" button when assigning reservations. Suddenly, it works. Imagine that?

Still a little disappointed there's not a proper web GUI for it, or even the ability to change the IP locally on the printer itself. It DOES have an LCD and setup menu after all. I'm sure as time passes, that'll be the way that all network based printers go. Having a dedicated Windows application and a dedicated Mac application just makes no sense these days.

At any rate, setting a DHCP reservation was easy enough, once I hit the proper button to apply the settings.

That said, if anybody else has any info pertaining to IPP, I'd love to hear it. I'm still just unsure as to what IPP does differently than LPD...

---

