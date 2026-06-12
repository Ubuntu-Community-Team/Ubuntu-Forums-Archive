---
title: "ISO to Big for CD?"
date: 2009-12-14
forum: General Help
---

### Post by lakelovers on 2009-12-14
Count me among those with multiple 9.10 upgrade problems. So, I'm going for a fresh install. I downloaded 9.10 via bittorrent but now I can't get it burned to a CD. I get the message that the "blank CD does not have enough free space." According to the properties on the iso, the size is 689.6 MB. Why won't that fit on a 700 MB cd? How do I get the iso on a CD?

I've been using the CD/DV Creator but would like to use k3b which hangs on boot. Is k3b buggy?

---

### Post by zeroandone on 2009-12-14
> **lakelovers said:**
> Count me among those with multiple 9.10 upgrade problems. So, I'm going for a fresh install. I downloaded 9.10 via bittorrent but now I can't get it burned to a CD. I get the message that the "blank CD does not have enough free space." According to the properties on the iso, the size is 689.6 MB. Why won't that fit on a 700 MB cd? How do I get the iso on a CD?

I've been using the CD/DV Creator but would like to use k3b which hangs on boot. Is k3b buggy?

How to burn ISO image on a CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I usually use the built-in CD/DVD burning software in Ubuntu, it is very stable. I never had good experience with k3b. However, the downloaded ISO should fit on a 700MB CD.

---

### Post by JC Cheloven on 2009-12-14
Way too strange. You downloaded via bittorrent, so there's no need to check the md5sum (it will not hurt to check anyway). And indeed the image fits in a 700 Mb CD. Also k3b is one of the best burners around, not a buggy piece of crap (I don't use it though). Anyway right-clicking on the .iso and selecting 'burn to cd' works flawlessly in every machine I've tried.

So, if you're doing right and don't get the disk burned, there is a problem. Possibilities are:
- A bad iso image
- Your toaster is faulty
- The blank cd is bad
- Your installation has gone misconfigured

Difficult to say from here, but you'll find out quickly trying different ISOs in different OSes :-)

---

### Post by lakelovers on 2009-12-15
Thanks for your suggestions. I'll keep poking around and perhaps download another iso.

---

### Post by Grenage on 2009-12-15
I've had that problem only once, it turned out to be a bad disc.

---

### Post by howefield on 2009-12-15
You can burn it to a dvd as well. It'll work fine.

---

### Post by lakelovers on 2009-12-15
> **howefield said:**
> You can burn it to a dvd as well. It'll work fine.
Well, I can't find a solution. I don't have a DVD drive. I have followed the instruction on zorandon's link > How to burn ISO image on a CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto). I've tried several blank CD's so I don't believe my problem is defective CD's. When I google my problem I find numerous references to the same problem but can't find a solution that works. I've burned CD's before but never had this problem. Hopefully there's and easy solution if I ever find it. Very frustations.

---

### Post by lakelovers on 2009-12-15
Apparently, this is a bug but I don't understand how the Ubuntu team could allow such a bug to exist, so I'm not sure my conclusion is correct. I've researched this until I'm blue in the face. I've downloaded the iso through bitturrent twice. Same conclusion both times. I could try it a third time but I'm thinking that would be a waist of time. I have been a Ubuntu fan since sometime around version 5.0. Now, I'm not so sure. I may try some other distro.

---

### Post by JC Cheloven on 2009-12-17
Hey, 9.10 isn't a marvel by now, true. But don't despair, there should be a logical reason for your trouble. Let's revise the checklist from the beginning:

- People out there, including me, can burn the iso 
----> have you any friend able to burn this iso for you? (checking purposes)

- You've downloaded several times, using torrent
----> did you try direct downloading? (just in case)

- You're burning from, say, ubuntu 8.04
----> do you can burn other iso_s from this?
----> have you tried to burn from windows, or from another live cd boot?

If these are done, it should be easy to derive wheter it's your toaster or the iso. Or some misconfiguration in your present ubuntu. The only think that can be discarded from what you did is a bad blank disk.
AFAI understand ...

---

### Post by lakelovers on 2009-12-17
Thanks, JC. . . Don't have a friend who can burn a CD. I did an "Upgrade" when 9.10 "stable" version was announced. I haven't tried a direct download. I have the slowest DSL service, and normal download takes a couple of days. I upgraded from 9.04. I do have a 8.04 cd which I have thought about installing. I have my files backed up on an external drive. I don't have a Windows program. My wife upgraded to 9.10 on her laptop and that worked good and is still working. Amazing that I didn't think of downloading the iso on her computer and burning a CD on her computer. I'll give that a try. Thanks again.

Edit: The iso download and cd burn were successful (I think). However, I cannot boot from the CD. I have the BIOS set to boot from the CD, but it doesn't see the CD, continuing to boot from the HD. The properties on the CD suggest it's blank. That's weird because my wife's computer went through the burn and said it was complete. I don't know what I'm doing wrong but this is ridiculous. I guess I'll try another CD burn.

The first CD I burned the image file. The second CD I burned the contents. The second CD boots okay but when I start the installation I get an "Compression Error." So, I don't know where I go from here.

---

### Post by JC Cheloven on 2009-12-17
Well, there is some progress: at least you have burnt the iso image :rolleyes:

Sorry if I can't offer a true technical advice (It's doubtfully possible in the distance with this kind of problem). What I have to offer is barely some company, and perhaps some obvious ideas. For example:

You have a second pc at hand (your wife's one), thats great. Also, it seems that everything you tried on her pc has succeded, while it has failed on yours. This suggests a problem with your pc (hardware). Let's be sure:

---> does the iso images (be the 8.04 or any of the 9.10) boot on your wife's pc and not in yours? Is there a different behaviour of the same toasted cd in both pcs? 

If there are differences, together with the fact that you tell the bios to boot from cd but it ignores that, I'd suspect from your bios battery.
It is that small battery wich feeds the small cmos memory used by your bios. It last for years, but  with enough time, it may get eventually worn out. If your pc is quite aged, this could be the problem. It's cheap to replace, but you have to open your box.

Hope this gives you some useful hint.

EDIT: I'm having some problems myself. Karmic does not see the network card, and doesn't sounds, in a pc in which jaunty worked flawlessly. Even though I always do fresh installs :-(

---

### Post by lakelovers on 2009-12-17
Thanks for all your suggestions. I'll replace the battery. I've been in the box many times replacing HD's, increasing memory, etc., so that's not a problem. My problem with 9.10 started with random freezing. Sometimes I have to reboot several times just to get up and running. Then it will freeze at anytime as when I'm writing this response. There seems to be a lot of stability problems with 9.10. I don't have sound, either, and I can't load videos.

I have an 8.04 CD, that's good, so I'm still thinking about putting that one on my computer, then going to 9.04 and staying there until and if Karmac gets fixed or waiting for the 10.4 release. Though I have my files backedup I may lose some stuff, but I don't have anything that's do-or-die critical. My photos are all on CD's, and I don't have any music files. So, I can take the lumps by going back. I'm very disappointed with 9.10. It just seems to be a mess. I'm thankful though that my wife's 9.10 works, otherwise she would be driving me more nuts than I am.

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
I do have to say that I have the same problem with Karmic. brasero reports the free space on a black CD-r as 530-600 Mb (it varies), I had to boot to my Jaunty install to burn the .isos I downloaded.

---

### Post by lakelovers on 2009-12-19
For anybody who's interested, I have reinstalled 8.04, and now in the process of updating 346 applications which is going at a snail's pace. Life goes on. . .

---

### Post by joes7 on 2009-12-19
Are you using "ISOBurner"? If you aren't, download it.

---

### Post by 3rdalbum on 2009-12-19
Right-click the ISO and choose "Write to Disc". Trust me on this.

It sounds like you were trying to burn it as a single ISO file sitting on a data disc, which will give this message and will prevent you from being able to boot from the disc anyway.

---

### Post by lakelovers on 2009-12-21
I'm using Transmission Bit Torrent which seems to work fine but thanks for the info. I didn't see a gdeb installer for ISO Burner and it isn't listed in synaptic. It's always a challenge for me to install apps via tar or whatever.

I'm running 8.04 and will stick here until another LTS comes along (10.4?).

---

### Post by Hakume on 2009-12-21
I have the same problem as lakelovers has. The ISO says it's 706.532 MB, and when I check the properties, it says it's 723.489 MB. I downloaded it from both directly on the site and from the torrent, and the same problem exists.

---

### Post by Slim Odds on 2009-12-21
I downloaded using Transmission shortly after it was released and mine is 690MB. 

What did you do wrong?

---

### Post by Hakume on 2009-12-21
I just simply initiated the download, and let it go on its own. I am on Windows Vista Home Premium +SP2 on an Acer Aspire 4520 with the 4 GB max ram if that helps at all... >_>

---

### Post by Slim Odds on 2009-12-21
> **Hakume said:**
> I just simply initiated the download, and let it go on its own. I am on Windows Vista Home Premium +SP2 on an Acer Aspire 4520 with the 4 GB max ram if that helps at all... >_>

What program are you using to download?

I'd have to think that is the culprit.

---

