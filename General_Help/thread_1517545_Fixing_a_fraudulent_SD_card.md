---
title: "Fixing a fraudulent SD card?"
date: 2010-06-25
forum: General Help
---

### Post by Nick_Jinn on 2010-06-25
So I got one of the "32gb class 6 SD cards" from Ebay....Yeah, it was a scam. I should have known coming from China, though I equally suspected that things were just cheap from there.

Good news is I got it for free thanks to paypal policy. Bad news is its only 2gb.


So it should be good for SOMETHING. Reformatting it didnt help. How can I reset it to its true values? How can I discover its true class?

---

### Post by prshah on 2010-06-25
> **Nick_Jinn said:**
> Bad news is its only 2gb. So it should be good for SOMETHING. Reformatting it didnt help. How can I reset it to its true values? 

I dunno about SD cards, but the "fake" usb pendrives can be reset by using (freely available) programs. The programs are specific to each controller chipset; I suppose it should be the same with the sd card. 

I guess you might have to open up the SD card and study the chipset; a Google search from there might open up the possibilities.

At your own risk, please.

I wish I could be more specific, unfortunately, I lack the knowledge to do so; so I hope finger-pointing the direction to take may help.

---

### Post by dcstar on 2010-06-25
> **Nick_Jinn said:**
> So I got one of the "32gb class 6 SD cards" from Ebay....Yeah, it was a scam. I should have known coming from China, though I equally suspected that things were just cheap from there.

Good news is I got it for free thanks to paypal policy. Bad news is its only 2gb.


So it should be good for SOMETHING. Reformatting it didnt help. How can I reset it to its true values? How can I discover its true class?

Are you **sure** your card reader is compatible with that size card?

---

### Post by warfacegod on 2010-06-25
> Are you sure your card reader is compatible with that size card? 

He said he was able to reformat it. I think that implies compatibility but I could be wrong.

If all else fails, you can sharpen points onto it and use it as a miniature ninja throwing star.

---

### Post by Nick_Jinn on 2010-06-25
Its compatible because it worked "at first". It only has 2gb though when I ran a program to test it. Its a Windows program, though I wish I didnt have to log into windows to test the cards.

But hey, its a 2GB card I now have for free since paypal refunded me. 

I would like to be able to use it as a 2gb card. I need to rehack it though.


I dont want to take the card apart. I do want to erase the firmware or whatever is on there so that its accurate. Just reformatting to a different card type didnt work.

---

### Post by warfacegod on 2010-06-25
> **Nick_Jinn said:**
> Its compatible because it worked "at first". It only has 2gb though when I ran a program to test it. Its a Windows program, though I wish I didnt have to log into windows to test the cards.

But hey, its a 2GB card I now have for free since paypal refunded me. 

I would like to be able to use it as a 2gb card. I need to rehack it though.


I dont want to take the card apart. I do want to erase the firmware or whatever is on there so that its accurate. Just reformatting to a different card type didnt work.

Sounds like you'll need to flash the firmware. And no, whipping open your jacket for a second doesn't count. Google should be your friend here.

---

### Post by Nick_Jinn on 2010-06-25
My fiend? My little demon in a bottle.


Telling people to look it up is kind of a non answer. I did a google search and didnt find anything useful for Ubuntu, even when adding Ubuntu to the search....Im sure there is something in there somewhere but pointing people in the right direction and offering input or opinions on the software available is a lot more helpful.

---

### Post by steveneddy on 2010-06-25
Try this:

Mount the card in Ubuntu with whatever source you have available - putting it in the laptop - use a USB card reader - whatever....

Then go to 

System --> Administration --> Disk Utility

OK - see if you can see the SD card there - and I believe you should because it's like a little drive.

Now - Unmount the card with the Disk Utility - format the card with Disk Utility - then remount the card - it should have the file system you want on there and you should be able to see the true size of the card now also.

Good luck.

EDIT:

Before I posted I tried it on an old SD card here. Seems that fix should work well.

---

### Post by tgalati4 on 2010-06-25
Put it in a camera and reformat.

---

### Post by Nick_Jinn on 2010-06-25
> **steveneddy said:**
> Try this:

Mount the card in Ubuntu with whatever source you have available - putting it in the laptop - use a USB card reader - whatever....

Then go to 

System --> Administration --> Disk Utility

OK - see if you can see the SD card there - and I believe you should because it's like a little drive.

Now - Unmount the card with the Disk Utility - format the card with Disk Utility - then remount the card - it should have the file system you want on there and you should be able to see the true size of the card now also.

Good luck.

EDIT:

Before I posted I tried it on an old SD card here. Seems that fix should work well.


It said there was an error when I tried to check file system. I lost the message, but it didnt work.

Reformatting it didnt help. It still says 32gb.

---

### Post by Nick_Jinn on 2010-06-25
I am going to try to reformat it in my Entourage edge. Thanks for the helpful suggestions, even if they didnt work.

I sincerely appreciate your effort.

---

### Post by warfacegod on 2010-06-25
Short of setting it on a powerful magnet for a few hours and then making a burnt offering to the binary gods that your system can still read and format it afterward, I'm out of ideas.

---

### Post by tgalati4 on 2010-06-25
You can probably salvage the card, but you must do it in DOS with the format command and the appropriate CHS count.

That's cylinders, heads, sectors.

---

### Post by psusi on 2010-06-25
> **tgalati4 said:**
> You can probably salvage the card, but you must do it in DOS with the format command and the appropriate CHS count.

That's cylinders, heads, sectors.

1) CHS doesn't actually exist anymore ( and hasn't for hard drives for at least 15 years ), they are just meaningless numbers still stored in boot sectors that are widely ignored.

2)  Good luck finding a DOS driver for sdcard readers :lolflag:

---

### Post by dcstar on 2010-06-25
> **warfacegod said:**
> He said he was able to reformat it. I think that implies compatibility but I could be wrong.


The Internet is full of people who have problems because their card reader hardware is not compatible with newer high capacity SD (or SDHC) cards.

Only a fool would assume that hardware designed with fixed limits will magically work with things that exceed those limits.

I have a front panel SD card reader on my system, it is useless for anything but basic low capacity SD cards, I have a cheap USB plug-in SD card reader designed for high capacity SD cards, and - would you believe - it actually works.

---

### Post by tgalati4 on 2010-06-25
If you format an SD card under Linux, it will normally apply a CHS count that is appropriate for hard drives, not SD cards.  If you use the DOS FORMAT command with the correct (i.e. magic) CHS numbers, you can normally revive the card.

Or just format it in a camera.

---

### Post by Nick_Jinn on 2010-06-26
I have an external multi-card reader and it works excellent. That isnt the problem. The problem isnt just reformatting it, but completely reflashing the firmware....I am not 100% sure that  am using the right terminology or that I totally understand how it works, but a simple reformat doesnt seem to be helping.


I am trying to format with a camera.

---

### Post by cryptotheslow on 2010-06-26
Seriously... put it in the bin and save yourself the time and headaches.

---

### Post by Nick_Jinn on 2010-06-26
Maybe I could trade it for drugs.


jk

---

### Post by Nick_Jinn on 2010-06-26
Somebody joined just to copy me?

---

### Post by prshah on 2010-06-27
> **Nick_Jinn said:**
> Reformatting it didnt help. It still says 32gb.

Try the official SD formatter from [http://www.sdcard.org/consumers/formatter/](http://www.sdcard.org/consumers/formatter/)

The manual (English) seems to indicate that memory issues will be fixed automatically. The [manual (PDF)]("http://www.sdcard.org/consumers/formatter/SD_Formatter_Manual_English.pdf") is worth a read first (Esp page 8).

The bad news: It's Windows-only.

---

### Post by Nick_Jinn on 2010-06-28
Thanks. I am trying it now.

---

### Post by pricetech on 2010-06-28
No, don't throw it away, even if it's not worth the trouble.  You'll learn something from all your efforts that will make them worthwhile.

---

### Post by Nick_Jinn on 2010-06-28
Quick format didnt work. I will try the long one while Im sleeping. it takes like 6 hours to work.

---

