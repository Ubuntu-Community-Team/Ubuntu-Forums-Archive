---
title: "I/O error with CanoScan N670U in XSANE"
date: 2006-03-31
forum: General Help
---

### Post by kwaanens on 2006-03-31
What the title says. It detects the scanner and makes a preview OK, but when I set it to scan there's a screeching sound, too loud to be normal for a loooong time. The main window says "getting gray data" for a while, then finally I get the error saying I have an I/O error. The annoying sound goes on and on and on, and doesn't shut down until I unplug the scanner.
I connected it using only the USB and not the external power supply (it's my brother's scanner so I don't have access to the the ext power supply chord), but if everything else works it should get enough power, right? It's connected to a standard USB on my Dell Inspiron 9300.
Any thoughts?

- Ketil

---

### Post by kwaanens on 2006-03-31
Update:
I tried with a different USB outlet and now it scans OK. Well, actually, more than OK. It's great!
I used the USB outlets in the back of my computer (there are 4 there), and changed to one of the two on the left side. Does anyone know the difference? The only thing connected in the back was/is my optical cabled mouse.

- Ketil

---

### Post by collier on 2006-04-07
Ketil,
I'm sad to hear that Dapper still has Xsane problems with CanoScan USB scanner.  Or doees it?  I have been trying to get my D660U to work under Breezy with very similar results to those you report.  I have also tried changing USB ports without success.  I have the supplied powerpack, so it's not a shortage of power.

Did your installation of Dapper find and run the scanner without you having to tweak anything?  other than the USB port I mean.

John

---

### Post by kwaanens on 2006-04-07
[QUOTE=collier]Did your installation of Dapper find and run the scanner without you having to tweak anything?  other than the USB port I mean.[/QUOTE]

I had no errors until I tried to actually *scan* stuff. Previewing too went fine. All was detected automagically. Changing the USB port made me able to scan the image too.
I'm going to scan a lot of stuff today, for the first time since my second post on this thread. I'll notify you of the results.

Edit: I didn't have the scanner plugged in when *installing* Dapper, and have never configured it at all in Ubuntu. I just started XSane, and it was detected.

- Ketil

---

### Post by kwaanens on 2006-04-07
Update: I managed to scan 13 images. I encountered a few problems along the way. I tried to switch USB-ports, but it looks like the hardware is actually crashing nonetheless. It happens ever so often, mostly when done scanning, I think. The scanner makes an infernal noise, but the bar with the light that actually does the scanning is not moving. XSane  does not respond when this happens. Forcing Xsane to quit and replugging the USB does the trick, and Xsane again starts up normally.
This happened 4 times in about 17 scans.

- Ketil

---

### Post by collier on 2006-04-09
Ketil,

Thanks for the update.
I haven't been able to scan anything.  I get to preview and then the stalled scanner lamp and screeching noise.
At least Dapper seems to be able to recover and actually scan something!

John.

---

### Post by kwaanens on 2006-04-13
I've used the scanner extensively so far this easter, and it's still working. However, I still have to replug the USB and XSane every once in a while.

- Ketil

---

### Post by eugenia on 2006-10-15
Is this really a problem with Dapper?

I have only recently upgraded from Breezy where my N670U worked perfectly. It will not work under Dapper. I just get the screeeeeeech and also have to force quit and unplug the scanner.

It still works perfectly if I reboot to Windows ME so it is unlikely that the USB port is the culprit.

As far as I can see Xsane is the same version as the one used in Breezy so the only thing that has changed is the version of Ubuntu.

Any thoughts??

---

### Post by stu on 2006-10-24
This is still a problem under Edgy unfortunately.

---

### Post by rpaco on 2007-08-23
> **stu said:**
> This is still a problem under Edgy unfortunately.
I found this solution, but it only works for one or 2 scans then it jamms the N670U again with horrible grinding noises.
[http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html#more-204](http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html#more-204)

---

