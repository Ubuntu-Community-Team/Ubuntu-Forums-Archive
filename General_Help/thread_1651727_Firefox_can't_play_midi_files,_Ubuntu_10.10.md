---
title: "Firefox can't play midi files, Ubuntu 10.10"
date: 2010-12-23
forum: General Help
---

### Post by Labhrain on 2010-12-23
I have a Webpage where I've embedded a midi file.  I cannot hear it in firefox.  I see the player controls exactly where I wrote them to show up, but no sound comes, even if I hit play (even though it's coded for autostart.)

I have installed all sorts of stuff through the repository.  I have installed gstreamer and everything under the sun that goes with it.  

I am at a loss at this point.  I've Googled this multiple times but come up with no adequate solution.  

NOTE:   I CAN play the midi file locally from my computer.  It's only when I have it embedded on the Web that I can't play it.  I've checked my coding and spelling.  This is not something I've never done before, just never tried to play back on Ubuntu before.

---

### Post by ajgreeny on 2010-12-23
Install **timidity, timidity-interfaces-extra**, and lastly **freepats** or a soundfont of some type.  You should then hear something.

---

### Post by Labhrain on 2010-12-23
> **ajgreeny said:**
> Install **timidity, timidity-interfaces-extra**, and lastly **freepats** or a soundfont of some type.  You should then hear something.

I already have timidity installed.  No success with it.  I don't find thectimitdity- interfaces-extra or the freepats in the repository.  Where do I get them?

---

### Post by coffeecat on 2010-12-23
> **Labhrain said:**
> I  I don't find thectimitdity- interfaces-extra or the freepats in the repository.  Where do I get them?

The packages freepats and timidity-interfaces-extra are in the Universe repository for both 10.04 and 10.10. Make sure you have the Universe repository enabled (which you will have done to be able to install timidity) and have another look.

Don't forget that a midi file is not a sound file. It is just a set of instructions and needs a soundfont for you to get even a squeak from it. If freepats is not up to scratch (have a look at the package description in Synaptic), then have a look here for a sound font:

[http://www.personalcopy.com/](http://www.personalcopy.com/)

---

### Post by Labhrain on 2010-12-23
> **coffeecat said:**
> The packages freepats and timidity-interfaces-extra are in the Universe repository for both 10.04 and 10.10. Make sure you have the Universe repository enabled (which you will have done to be able to install timidity) and have another look.

Don't forget that a midi file is not a sound file. It is just a set of instructions and needs a soundfont for you to get even a squeak from it. If freepats is not up to scratch (have a look at the package description in Synaptic), then have a look here for a sound font:

[http://www.personalcopy.com/](http://www.personalcopy.com/)


Ugg.  I clearly have no idea what I'm doing.  According to the Synaptic package manager, I already have timidity, timidity-interfaces-extra AND freepats installed.

Here's what's very confusing to me.  I CAN play and hear midi files from my hard drive.  It's only the embedded one in the Webpage that I cannot hear.  I get the player, but it plays nothing.  It DOES work on the Windows machine, however, using Quicktime plugin.  

So, why would it work from the local machine, but not from the Webpage?  That's what's making no sense for me.  My computer itself has no problem playing midi files.  It seems to be the browser issue.  Since I have all of the suggested installations, I have to think that there's something missing in the browser, but I don't know what I need.

Does that all make sense?

Thanks for your help and patience.

---

### Post by coffeecat on 2010-12-24
> **Labhrain said:**
> Does that all make sense?

Yes it does, but unfortunately I don't have the expertise to do what you are trying to do. This does sound like a browser issue to me. I should imagine the Quicktime plugin enables the browser in Windows to use the Windows sound font. From what I remember, Windows comes complete with a sound font (someone correct me if I'm wrong, please) which is proprietary. Ditto for MacOS. You'll see that freepats is quite incomplete which is why I posted that link.

What plugin you need for a Linux browser, I don't know. Sorry.

---

### Post by OpenMinded on 2011-02-22
> **coffeecat said:**
> Yes it does, but unfortunately I don't have the expertise to do what you are trying to do. This does sound like a browser issue to me. I should imagine the Quicktime plugin enables the browser in Windows to use the Windows sound font. From what I remember, Windows comes complete with a sound font (someone correct me if I'm wrong, please) which is proprietary. Ditto for MacOS. You'll see that freepats is quite incomplete which is why I posted that link.

What plugin you need for a Linux browser, I don't know. Sorry.

Do you also have issues with WAV files?
I have and I created a bug report.
Maybe you should do the same

---

### Post by coffeecat on 2011-02-22
> **OpenMinded said:**
> Do you also have issues with WAV files?

Who are you addressing, the OP or me? WAV files are a completely different issue since they don't need sound fonts the way midi files do.

---

