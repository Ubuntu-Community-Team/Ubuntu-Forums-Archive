---
title: "router question"
date: 2010-08-30
forum: General Help
---

### Post by DouglasAdams on 2010-08-30
when i first joined O2 broadband the router they sent me had not arrived so i guessed at the settings i would need and when the transfer took place i connected without problem. my networked printer, Xerox-Phasor-6280N, worked perfectly. that was on 6 july 2010.

on 20 august 2010 bt phone me about a complaint i had made before i joined O2 and very shortly after they hung up i lost my ADSL2plus connection. a router reboot managed to re-establish the connection but it soon dropped again. after a few router reboots i rang O2 support.

O2 support where nice but the could not help me as i was not using the O2 router. so i switched and the connection became stable again.

however, i have never been able to access my printer since then.

the router can clearly see a device, identified as: "XRX0000AAAC292D", which i have set to being a printer but i still can't print.

O2 cannot provide printer support - especially as i'm using Linux.

---

### Post by mazzizo on 2010-08-30
If the router can see the printer and it's still not printing, make sure that the printer has the WEP/WPA or whatever type of encryption key in it. Try power cycling it and seeing if that helps as well. Stupid, I know, but you never know. Also the printer may be there and may have issues with the type of encryption you are using. And to be completely honest, if you cannot get it to work and your ISP is not going to provide support, contact Xerox for further support.

Oh and as for your signal dropping after they hung up, make sure your lines are filtered properly as DSL requires you to have that done. Unless you have a POTS filter on your DMARC. If you do, and the signal still drops when you've used the phone, give your ISP a call back, have them run line tests to see if there is any line errors and to get them fixed. 

Sorry was a Rep for Bell Canada :P Just tryin to help with that as well.

---

### Post by howefield on 2010-08-30
> **DouglasAdams said:**
> i was not using the O2 router. so i switched, however, i have never been able to access my printer since then.

If I have managed to get through the extraneous fluff, you had a network printer which worked, and now doesn't because you are using a different router ?

Have you tried setting it up again via System > Administration > Printing > Add new printer.

---

### Post by DouglasAdams on 2010-08-30
> **howefield said:**
> Have you tried setting it up again via System > Administration > Printing > Add new printer.
i certainly have - a couple of times.
everything looked as if it went ok but at the end of the installation the test print didn't print and, when completed, the icon showed a tick and an exclamation mark.

---

### Post by DouglasAdams on 2010-08-30
> **mazzizo said:**
> WEP/WPA or whatever type of encryption key in it

Try power cycling it

Also the printer may be there and may have issues with the type of encryption you are using

contact Xerox for further support.

Oh and as for your signal dropping after they hung up, make sure your lines are filtered properly as DSL requires you to have that done. Unless you have a POTS filter on your DMARC.

give your ISP a call back

have them run line tests to see if there is any line errors and to get them fixed. 

Rep for Bell Canada

wep/wpa:
tried both settings.
also, my wireless is disabled (i prefer wires).

issues with type of encryption:
encryption was set (did this for both), settings saved then wireless disabled and settings saved again?

signal dropping after they hung up:
my line and bb are with O2. my line had previously been with BT. i have received and made lots of calls but never had any other problems. it was just this once (well, 3 or 4 drops shortly after and for a few hours after just that one call) that my bb dropped out. also, new filter fitted with new router.

ISP:
i spoke to my isp before i posted. they tweaked my "ports" (i guess that means settings) and managed to up both my up and download speeds. they are calling me back tomorrow to check stability, etc.

line tests:
they have. that's the only reason i'm still using the isp provided router as my netgear allowed me to backup my router config, block sites, all sorts of nice features.

Ma Bell:
we have a company called BT but their staff never seem as helpfull as you are. are you sure it was a telco you worked for?  :D

power (moved to the end):
sorry, after pushing the big red button the test page sent to printer showed "printer warming" - for a the entire time i was writing this post, chatting to my daughter, watching a little tv, making coffee ... etc.
just before i submitted this post my printer went into sleep mode. i deleted the test page i had sent earlier and then queued another one. guess what? it printed!

problem solved. seems like the big red button won again.
when all else fails, try the haemorrhaging obvious!
many, many thanks.

---

