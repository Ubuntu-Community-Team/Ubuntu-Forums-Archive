---
title: "No video from Lucid Live CD"
date: 2010-05-08
forum: General Help
---

### Post by denzilla on 2010-05-08
I have no video at all booting to Lucid from Live CD. When the CD first boots, I see what appears to be Plymouth, then the monitor goes into standby. The booting process appears to continue, but without a screen to look at, its not much use.

Asus M2N-X MB
4GB RAM
Sapphire Radeon 3450 PCI-E 512MB
LG 19' LCD model L1933TR (Connected through DVI)

I want to boot to a Live session and then create a Bootable flash drive to carry my Ubuntu installation around.

Any ideas?

---

### Post by denzilla on 2010-05-09
Anyone?

---

### Post by dino99 on 2010-05-09
on the boot line, add video=vesa and remove "splash" in case

---

### Post by denzilla on 2010-05-09
How do I get it to go to command line during the CD boot? Do I need to edit the ISO?

---

### Post by bville09 on 2010-05-12
So, I assume you can get to the actual menu, right? (the purple coloured screen, with the ubuntu logo, and the two white icons), or does it go straight to plymouth?

Anyway, I'm just going to assume you get the menu. Press any key when you see that screen, it'll ask you to select your language, do that. Then press the F6 key, you'll be presented with a bunch of options (like noacpi, nolapci, etc.), anyway, you'll also see the command line (it looks like a bunch of random words, and it's right above the other F1 - F6 options at the bottom of the screen).

Add the "video=vesa" (no quotes) to the end of that, and delete the word that says "splash", then hit enter, should work, if not, hit CTRL and X and then it should work.

I had this exact same problem (still do), and the only thing that worked for me (for some strange reason) was to enable all the options in the F6 menu (except edd=on and Free software only), and it seemed to work. It also seemed to work flawlessly when I switched my display over to the intel integrated, but it failed epically when I attempted to install nvidia drivers.

Using an ancient XFX GeForce 6200, the type of video card you get as prizes in cereal boxes.

Another curious thing to add, is that I also had this problem in everything pre-RC Lucid (such as the first alpha, the second alpha and the first beta), and just decided that now wasn't the best time to test out the newest Ubuntu, however, I didn't have this problem at all using the RC. The problem seems to have magically returned in the final release. Odd.

---

### Post by denzilla on 2010-05-12
> (the purple coloured screen, with the ubuntu logo, and the two white icons)

Yea, this is where I get. I'm not too familiar with Linux (I try it with each new Ubuntu release) I'll try your suggestion and report back :)

---

### Post by denzilla on 2010-06-09
Unfortunately, nothing I've tried works. Always end up looking at a black screen.

---

