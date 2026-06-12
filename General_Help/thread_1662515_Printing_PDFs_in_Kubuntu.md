---
title: "Printing PDFs in Kubuntu"
date: 2011-01-08
forum: General Help
---

### Post by Silveri on 2011-01-08
The system: 64bit Kubuntu 10.04 LTS
The printer: Canon PIXMA MP640 (attached via USB, but also LAN-enabled)

*Intro: Without going into too much specifics on the history of my following opinion (as it isn't exactly dependent only on the problem at hand), I'd like to point out first that CUPS is a ragtag piece of **** and if there's one good thing to say about Microsoft, its at least that they managed to implement a working (and supported) printing standard to Windows. Even with TurboPrint (an excellent software that I'll most likely buy after the trial period ends as it solved 90% of my printing problems - leave it to commercial firms to come up with something that actually works) it's still not up to the competition. Honestly, after nearly 4 years of having Ubuntu/Kubuntu as my primary OS (haven't booted to Win on the main machine in about 3 years now although its still there), I reconsidered moving back to Win because CUPS is so awful, before I remembered why I moved out from Win in the first place.*

What I want to do: Print PDFs, with matching colors (not ICC profiled, but approximately match what's on the screen) where the size of the printed image would match with the ones I print with the same printer under Win7 (ie an image that has a width of 6" would have width of 6" instead of 5 6/8"). As they are for papercrafting purposes, the exact scale is important.

What I can do: Print it in the right size in Adobe Acrobat reader, Okular prints the images slightly smaller despite the settings I put into it.

The problem: With Acrobat the problem is that the colors are entirely too dark although the scale is on the mark. The colors are ok in Okular though, but the scale is off the mark. What I COULD do (and have done thus far) is to print it via the laptop downstairs, but that's a Win7 Eee PC that is a bit too slow for my taste.

Any suggestions?

--

edit: Actually, worked around the problem with Evince Document viewer, which prints in right colors in the right scale.

---

### Post by efflandt on 2011-01-08
Evince is the default document viewer for PDF files, so if that prints properly, is there some reason you need Adobe Acroread or Okular (which I am not familiar with)?  That may also be a sign that it is NOT a cups specific problem, but maybe the program that sends data to cups.

---

### Post by Silveri on 2011-01-09
Granted, this time it was not CUPS but the program. After hours of banging my head with CUPS-related problems previously with this printer and my previous printer, my general opinion on the faults of CUPS is not changed (such as some programs printing and others not and programs that printed 5 min ago refused to print more for any sane reasons). But, problem solved for now.

---

