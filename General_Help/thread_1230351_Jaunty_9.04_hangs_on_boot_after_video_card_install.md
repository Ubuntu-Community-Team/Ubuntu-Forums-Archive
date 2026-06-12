---
title: "Jaunty 9.04 hangs on boot after video card install"
date: 2009-08-03
forum: General Help
---

### Post by chipfryer on 2009-08-03
Hi there folks. I have a problem booting after installing a different video card. All I get is about 20% of the loading bar after which the computer just sits there.

I've tried recovery but get:
clocksource tsc unstable (delta etc.) at which point it stalls there too.
I've not seen safe mode on that list either.

Is there anything I can do about this please or am I looking at wiping this drive, (hope not).

Many thanks.

---

### Post by wojox on 2009-08-03
I'd try booting into safe mode and:

```
sudo dpkg-reconfigure xserver-xorg
```

exit and reboot. Should reset xorg.conf. Then install your new drivers.

---

### Post by chipfryer on 2009-08-03
Hi Wojox thank you.

The trouble is when I hit escape I don't see the safe mode option. Is there a syntax I need to get into safe mode please?

Many thanks.

---

### Post by chipfryer on 2009-08-03
Ok I've tried a lot of stuff.
Here is what happened so far as I can remember it:

1. I installed an MSI Video Card after removing a Ati.
2. On boot I got several messages mainly to do with reconfig the Xconf, (There weren't many options) so I decided to do this.
3. Booting 3rd time I had no options for screen res so thought in my stupidity I could just replace the card that worked. 
4. Now neither will load in Grub and there are NO options for safe mode either.

Question.............
Can I repair the Xconf from a Live CD and if so how do I go about that please?

I love Linux/Ubuntu but the one failing I think is that the FREE forums are not busy enough.

Many thanks..

Again.

---

### Post by chipfryer on 2009-08-03
Cancel that.

Even the LIVE CD stalls at the same point in Grub. What I'll do is wipe and reinstall though this peeved me a heck of a lot. There must be a workaround for this problem because it seems generic to me at least. I know parts and manufacturers for the most part don't support driver software, given.

What I find hard to believe is that no one else has suffered this problem because I am sure that some have.

If I can get to 'Terminal/Synaptic' then I would have a chance of getting something sorted out even it it was just to collect data from the host drive.

Perhaps it is my machine? I will check this out too just to make sure.
though consistency tells me this is a driver/conf/setup flaw/.


Thanks anyway.

---

### Post by chipfryer on 2009-08-04
Ok I used yet another card, this time an older PCI and Grub fails at exactly the same loading point as before. I've checked the cards in another machines and all work just fine.

I've checked the HD and ran a memory test to try and be certain that it isn't something reall obvious, all is the same as before.

I think I'm looking at completely wiping the HD again which isn't any big deal but my advice to anyone reading this is that you backup links/favorites mail settings to an off machine location :-? 

It's more annoying that it is life threatening and although I love Ubuntu and have been using it now for some time, I'll start eating humble pie a little and back up regularly knowing that sometimes Linux just doesn't know how to deal with a swap of hardware.

In short Backup - backup - backup.
I'm off to wipe (Again).

Cheers.

---

### Post by chipfryer on 2009-08-04
UPDATE Because it might help other people too.
There was a problem with an Audio Card. Since this has been removed I can now again access Ubuntu - However I now get the following.....

Ubuntu is running in low graphics mode
(EE) unable to find valid framebuffer device
(EE) NV(0): Failed to open Frambuffer device, consider warnings and/or errors above for possible reasons.
(EE) Screen(s) found but none have usable configuration.

I click OK

I am asked what I would like to do?
1. Run ubuntu in low graphics mode
2, Reconfigure graphics
3. Troubleshoot error.
4. Login to console area.

*** I did notice on boot that it told me that Xserver was already running on '0' would I like to try another location which is of course what got me to this point.

Any ideas now please?
Many thanks.

---

### Post by chipfryer on 2009-08-04
This is now solved. I tried to edit the first message.

What I did.
Installed the Nvidia drivers from
Administration >> Drivers
rebooted and found that I had a 600 x 300 (something) resolution.
Took the card out that I was replacing the older card with and booted.

This time I didn't get the Xserver error message.
The screen however was still too small.
I uninstalled the Nvidia drivers and booted.

no problems at all in fact I now have a very good high resolution of 1150 x 864 which is fantastic.

I've no idea what I did right or wrong but I'm sure happy to have my distro up and running again.

Best regards.

---

### Post by warby1212 on 2009-08-05
Hi Chipfryer,

My sympathy. I have installed a new m/b with on board video (intel ? does that make it ATI?) Anyway it freezes at exactly the same spot. It does complete booting though after several minutes but has disrupted video. No complaints from system about restricted drivers missing only that the wireless card is not supported even though it works! Be nice if the OS gave me some polite message about what's wrong. I know if I had all the time in the world I could sort it out but I don't and in the mean time because my pc dual boots into windows, the windows is calling me back noooooooooooooooooooo

---

