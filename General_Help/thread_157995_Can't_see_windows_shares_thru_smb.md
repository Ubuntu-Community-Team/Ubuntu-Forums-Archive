---
title: "Can't see windows shares thru smb"
date: 2006-04-10
forum: General Help
---

### Post by djsroknrol on 2006-04-10
Hello everyone...

Well, everything was working fine until I installed the new router....I accidently rebooted and the boot failed on the networking...now the windows boxes see the Ubuntu box shares, but I can't access the windows shares..lookup in Nautilus (control + L, smb://XXX.XXX.XXX.XXX) is very long, but finally comes thru....could someone point me in the direction to look to fix this...it seems like everything is alright...I reassigned new IP's for all the computers as assigned by the router, the firewall on the router is disabled...internet access is great....I'm really at a loss on this one....

---

### Post by dcstar on 2006-04-10
[QUOTE=djsroknrol]Hello everyone...

Well, everything was working fine until I installed the new router....I accidently rebooted and the boot failed on the networking...now the windows boxes see the Ubuntu box shares, but I can't access the windows shares..lookup in Nautilus (control + L, smb://XXX.XXX.XXX.XXX) is very long, but finally comes thru....could someone point me in the direction to look to fix this...it seems like everything is alright...I reassigned new IP's for all the computers as assigned by the router, the firewall on the router is disabled...internet access is great....I'm really at a loss on this one....[/QUOTE]
Do a search for "IPv6 disable" and see if those solutions help.

---

### Post by djsroknrol on 2006-04-10
Hi David...

Thanks for comming to my rescue...IPv6 is already disabled..I reinstalled Samba after work today, along with winbind...checked the smb.conf and nsswitch.conf files...they're all normal...I can ping all of the M$ boxes, and ran a traceroute...all worked fine...the new router is working great...no firewall..it's all disabled in the router...port 139 is open on all the boxes...windows brosing into the Ubuntu box is fine...the other boxes just don't show up in places>network servers...what else can I try?...I had to play around, didn't I ](*,) ...I really needed that new router...it was bottlenecking my internet access, which is the best it's ever been...

---

### Post by djsroknrol on 2006-04-11
An add on question might help me find the problem....what program controls the visuals in places>network servers?...the other boxes on the intranet just don't show up at all...after a minute, the windows network icon shows up, but past that, there's nothing...not even the Ubuntu box....something has got to be broke big time....

---

### Post by djsroknrol on 2006-04-11
Sorry for the bump....someone must have an idea.....

---

### Post by djsroknrol on 2006-04-11
Ok...just as I was going to reinstall Breasy, I looked at:

System>Administration>Networking


I never really noticed that the location was greyed out...opening that pull down showed "server", and I figured what the heck...and guess what...the M$ boxes came back...just wanted to post this for anyone else who might need this...

Thanks to all for reading...

---

### Post by CronoDekar on 2006-04-12
I've been having what seems to be the exact same problem -- I can connect to Windows shares, but they aren't showing up in Network Servers, even though they have before.  Unfortunately though, I don't have such a location in the Networking option.  Also, the problem seemed to come up just spontaneously (I didn't get a new router or anything), and hasn't gone away.

It's not particularly problematic since I don't use the network much, but it is kinda a thorn in my side, so if anyone has any ideas it'd be appreciated.

---

