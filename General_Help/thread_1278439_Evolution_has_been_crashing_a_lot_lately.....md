---
title: "Evolution has been crashing a lot lately...."
date: 2009-09-29
forum: General Help
---

### Post by badperson on 2009-09-29
it's never done that before...maybe something in an update? Anyone else have that issue? I didn't change anything, it seems I need to forec quit a lot. 
bp

---

### Post by dcstar on 2009-09-30
> **badperson said:**
> it's never done that before...maybe something in an update? Anyone else have that issue? I didn't change anything, it seems I need to forec quit a lot. 
bp

Mine is still working ok.

---

### Post by badperson on 2009-10-10
Is there anyway to re-install evolution? I'm not sure what the problem is, but I have a macbook and a windows partition, and those email clients pick up the mail fine. 
bp

---

### Post by wojox on 2009-10-10
```
apt-get --reinstall install evolution
```

Or open synaptic and search for it and mark for reinstallation.

---

### Post by badperson on 2009-10-11
I installed Thunderbird and will use that...I use it on my windows partition and like it. 

How can I get the mail icon on teh upper title bar of Gnome to point to Thunderbird instead of Evolution?
jason

---

### Post by sgosnell on 2009-10-11
The crashes are more likely a result of corrupted data files.  Trying to read corrupt data can crash many programs.  Reinstalling won't help if this is the case, and will only help if the program file is corrupt.

---

### Post by badperson on 2009-10-11
like a corrupt email file? I have other email clients on my win partition and my macbook, and they have no problem. 
jason

---

### Post by sgosnell on 2009-10-11
Could be a corrupt email, or a calendar entry, or a contact entry, or anything.  What are you usually doing when it crashes?

---

### Post by alicemoon on 2009-11-09
> **sgosnell said:**
> Could be a corrupt email, or a calendar entry, or a contact entry, or anything.  What are you usually doing when it crashes?

I have been having similar crashes since installing 9.1 - usually when trying to open or save an attachment - on the odd occasion my whole system freezes following the evolution crash and I have to reboot. Usually it's just evolution and if I wait for a force quit prompt to come up it's ok i just restart evolution - if I use my force quit applet from the panel evolution will not restart and I have to reboot the system (at which point i get a message saying evolution is still running in the background.)
Should I take evolution out and reinstall it - or is this a problem connected to 9.1 - I don't want to go back to thunderbird as I like the evolution integration.

---

### Post by graphius on 2009-11-10
My Evolution is crashing a lot as well. it seems to lock up on startup. 
I don't believe it is a corrupt file, because it will work fine for one session, then next time I turn on the computer it locks up. I filed a bug, but withdrew it because I originally thought it was due to the hotspot at my local coffee shop, but it has crashed at home now a few times.
I don't really want to go to thunderbird if I can help it.

On further examination, it seems to be network related. I seem to get more crashes when switching wireless locations, or even switching from wireless to wired.

---

### Post by proxess on 2009-11-10
Delete your .evolution/  folder. You'll have to reconfigure your accounts, but it should be more stable later.

```
rm -R .evolution/
```

---

