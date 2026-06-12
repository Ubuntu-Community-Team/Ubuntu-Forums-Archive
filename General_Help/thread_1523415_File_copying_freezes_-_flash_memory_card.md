---
title: "File copying freezes - flash memory card"
date: 2010-07-03
forum: General Help
---

### Post by mje1708 on 2010-07-03
Hi

Using 10.04 Netbook version. I am finding on my Asus EEE 901 that sometimes file copy just seems to freeze - seems to happen usually when copying from the built-in SSD memory to the plug-in SDHC memory card. I have tried reformatting the card and using a different card. It is not just this computer since I found the same thing on my last Asus which was the 900 model.

I am told that there are issues with Nautilus. Is there anything which can be done to improve this or is there anything else which I can install besides Nautilus? I am assuming that there is some issue related to Ubuntu's handling of SDHC memory cards.

It is becoming annoying because it seems to work sometimes and then not. When it happens only option seems to be to turn the netbook off and on again. Even if the file copy is cancelled the card seems to be unaccesible until rebooted.

Also after a certain point it seems that when I try and copy new files to the card, they appear to copy ok but obviously are corrupt in some way - when you try to play videos for instance they are faulty.

Anyone any ideas?

Thanks

Mike

---

### Post by oldfred on 2010-07-03
Writing to flash drive is slow. On my system is says it writes the first 85% real quick (I am sure it lied) and then takes a very long time for the remaining 15%. I see it still working as my flash has a led that keeps flashing.

---

### Post by mje1708 on 2010-07-06
I have done a bit of research now and it appears that there is a problem with Asus EEE model pc.s and SDHC memory cards even though a slot is provided for them as standard. A lot of people are reporting having issues writing data (over a certain size - "small" files seem ok) to them both with Linux (various distros including Ubuntu) and Windows. Some people seem to have solved with a BIOS update (this did not work for me). So all in all it sounds like a hardware/ firmware issue.

I have ordered a cheap usb card reader as a work-around. If I can use this to write data to the card then at least I can read it using the Asus standard card slot. Not ideal but at least I can use the card to store movies which I can then watch on the asus using the standard sd slot - there seems to be no problem reading data when the card is in the slot - just writing.

Has anyone else encountered the same issues ?  Did you manage to solve in some way?

Thanks

Mike

---

### Post by mje1708 on 2010-07-21
On advice from somebody else with an EEE I purchased a Sandisk 16gb. This works perfectly with no problems.

I have come to the conclusion that some SDHC cards only show that they are actually faulty when asked to copy large files..... and maybe the EEE range is a little picky as to which cards you use.

I have subsequently tried another Sandisk (4gb) and this also works perfectly. So clearly, for whatever reason, Sandisk cards work fine with the Asus, Ubuntu etc

---

