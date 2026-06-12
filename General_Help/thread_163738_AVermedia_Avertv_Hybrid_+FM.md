---
title: "AVermedia Avertv Hybrid +FM"
date: 2006-04-21
forum: General Help
---

### Post by mpi on 2006-04-21
Hi,
I searched around the net, but since this card is not so plain old I did not find much information.
The problem is that I won't get it running with ubuntu dapper. The card uses Philips SAA7134 which is supported by the kernel 2.6.15, but unfortunately the card is not completely recognized (subsystem unknown).
Dmesg says saa7133[0]: subsystem: 1461:f436, board: UNKNOWN/GENERIC [card=0,autodetected]. It shouldn't be 7133, but the 7134-drivers are loaded so it's fine. Now there are quite a lot cards available and supported by this driver. Hence I tried the supported 82 cards (information from the kernel release) by loading the saa7134-module with card=1.. card=2 .. etc and so on, but /dev/dvb will never be created.

I'm quite upset now, because AVermedia provides drivers on their own, but they're outdated to 2.6.11 and 2.6.13. They obviously won't load with a 2.6.15, will they? :)

Now.. Has anyone got this card running in dapper? She's quite awesome as they quality is really good in Windows, so I'm hesitating to send it back.
Can anyone help? 
Thank you :)

---

### Post by donaldd on 2006-04-25
I'm in the same situation as yourself wondered if you have managed to resolve the problem getting tv card to work?

---

### Post by mpi on 2006-04-28
This card is actually not supported by the LinuxTV framework, which means we have to wait. Avermedia seems to be moving into the linux-direction as far as I read from the linux-dvb mailing list.

@Mods: Can you please relocate this thread to a more appropriate forum for Dapper?

---

### Post by tattrat on 2006-04-28
I also have one of these, and I have just noticed that AverMedia have released (on 12 April) Linux drivers for:

Mandriva Linux 2006
Fedora Core3
Fedora Core4
SUSE Linux 10.0 OSS

It might be worth canvassing them to find out if Ubuntu drivers are planned - I know from experience that they  do respond to emails.

---

### Post by PosTi85 on 2006-12-07
Hi all, I'm thinking on buying this card, NOW is this card running on ubuntu?? Someone have it or know something about it?

---

### Post by Enverex on 2007-01-11
Everyone needs to be careful with this. Their drivers are currently not very good (0.03 version and only work on select distros and select versions of those distros). You also need to state WHICH one. The PCI/Cardbus/USB versions all use different chipsets, layouts and drivers from each other so keep that in mind too. I posted to the DVB mailing list last week and haven't had a single reply yet :(

---

