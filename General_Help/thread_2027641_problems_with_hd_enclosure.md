---
title: "problems with hd enclosure"
date: 2012-07-16
forum: General Help
---

### Post by pooper on 2012-07-16
had some odd problems with an old hd and enclosure so I can use it via usb (SATA to USB) 

basically worked first time, had access to everything on there.

then gradually got worse, to a point I could no longer see any files/folders and was telling me a 60gb partition was 12gb...

anyway tried reformatting and so far have managed to wipe drive but now when I try to create partition table it tells me 'unrecognised disk label'

any ideas?

Basically what I wanted to do is re-use the hd in another laptop, but initially check what was on it then format it ready to go in..

---

### Post by sudodus on 2012-07-16
What enclosure is it? If the power is supplied only via USB, it may be failing because of poor power supply. You could try with another computer, or if you have a USB switch with external power supply. 

Some hdd enclosures have two USB connectors (the extra one is there to add current from a second USB port). Some enclosures have a separate power supply.

---

### Post by pooper on 2012-07-16
It's branded 'Dynamode' 
I've gone through xp now and reformatted through that and it works now. 
It is powered by USB and lead does have 3 usb connections, one for enclosure one for computer and I wondered what the third was for! I thought it may have been power but was to scared to plug it in.. However it worked in xp with just one plugged in?

---

### Post by pooper on 2012-07-16
hmmm, just tried with both cables plugged in for the extra power supply and still has problems..

---

### Post by sudodus on 2012-07-16
> **pooper said:**
> 
However it worked in xp with just one plugged in?

hmmm, just tried with both cables plugged in for the extra power supply and still has problems..

Is this the same computer (dual booted)? Or are you running Windows in another computer?

If it is the same computer, there is probably some other error or incompatibility with Ubuntu. I don't know that particular brand, but my experience is that this kind of equipment will work without problems with linux.

But different computers can have different power supply levels via USB.

---

### Post by pooper on 2012-07-19
Thanks for your help, it is the same computer dual booted.So weird it worked perfectly first time then all downhill after that :S

---

### Post by sudodus on 2012-07-20
> **pooper said:**
> Thanks for your help, it is the same computer dual booted.So weird it worked perfectly first time then all downhill after that :S
Could it be a failing drive? Can you see it well enough to get S.M.A.R.T. information (if the drive supports it)?

Try from Windows, if it works better!

If it is gradually failing, save your private files as soon as possible.

---

