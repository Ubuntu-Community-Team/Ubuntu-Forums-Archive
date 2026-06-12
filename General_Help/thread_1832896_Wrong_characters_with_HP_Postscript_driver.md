---
title: "Wrong characters with HP Postscript driver"
date: 2011-08-25
forum: General Help
---

### Post by leemid on 2011-08-25
Hi all,

I have a really tiny but annoying issue with printing when using the Postscript driver with my HP Color LaserJet 2840 MFP. Basically it will print random characters in a document as boxes. If I change to the Foomatic driver everything prints perfectly - but I lose the ability to change a lot of driver settings which I use often (paper type, weight etc.).

If anyone could point me in the right direction of a solution I'd be **really** grateful - only one other PC in the building has the same problem, the rest all print fine. BTW - The only font I use (for coroprate work) is URW Gothic L, which comes with Ubuntu... but I'm not sure that could be the problem as it displays perfectly on screen.

Once again, all help gratefully received, it's driving me mad!

---

### Post by leemid on 2011-09-02
Sorry to bump, but does anyone have any ideas?

---

### Post by cliddell on 2011-09-02
How much control over the HP driver do you have? If it is configurable like the Windows (sorry!) drivers, you could check whether there is an "embed all fonts" or similar option.

URW Gothic L is an equivalent of one of the Postscript standard font set, so the driver may be spotting that, and option not to include the font in the Postscript being sent to the printer. I've seen cases where the characters or encoding (ordering, effectively) do not match in the system's and the printer's font, and the wrong glyphs get printed.

Drivers also sometimes have a "convert fonts to bitmap" option, which will usually increase the size of the PS sent to the printer, but is another option to try for correct output.

Chris

---

### Post by LowSky on 2011-09-02
What application are you using to print the job with?

As a work around... could you print to PDF? Then print the PDF? As PDF's are seen as images and not documents it might work.

Also if you are using HP drivers are you using Version 5e or 6?  Not sure if the option is the same with the Linux drivers over the Windows version but using 5e always gave me better results in a windows environment. I have found that version 6 has some flaws printing some fonts.

---

### Post by cliddell on 2011-09-02
> **LowSky said:**
> What application are you using to print the job with?

As a work around... could you print to PDF? Then print the PDF? As PDF's are seen as images and not documents it might work.


What "sees" PDFs as images? Because it's wrong: it's not an "image".

> **LowSky said:**
> 
Also if you are using HP drivers are you using Version 5e or 6?  Not sure if the option is the same with the Linux drivers over the Windows version but using 5e always gave me better results in a windows environment. I have found that version 6 has some flaws printing some fonts.

The OP said they're using Postscript: 5e and 6 are PCL versions, not Postscipt.

Chris

---

### Post by leemid on 2011-09-03
**@[cliddell, @LowSky**

Yes, I can print to PDF and those files look perfect. However if I try to print said PDF normally using CUPS the same thing happens again. Therefore I have to use Adobe Reader to print it if I don't want the dodgy glyphs.
Also I couldn't find an 'embed text as image' in the driver settings but sounds similar to the 'text to path' function in Inkscape - and hey presto, that works fine when I print, even from Document Viewer.

I generally print from Firefox 6, Thunderbird, LibreOffice, Inkscape and Document Viewer/Evince. The dodgy glyphs appear in printouts from all of the above except LO - which I believe uses a different printing backend. Do correct me if I'm wrong!

Thanks for the help, both of you
Lee

---

### Post by cliddell on 2011-09-03
Given that the "text as path" option seems to work, it does sound to me like some kind of incompatibility between the system font and the printer font. It might be worth trying to find out if there is some setting or tweak that would force fonts to always be embedded.

Chris

---

### Post by mjc1 on 2011-09-09
I have the same problem on Fedora 15 with my HP Color Laserjet CP2025. It is really annoying. No solution yet, except to use the PCL driver (which has its own glitches).

- Mike

---

### Post by leemid on 2011-09-19
Thank you for your help and ideas everyone - I think I've cracked it.

It seems that there's a glitch somewhere between the Postscript font on the computer and how the printer interprets the page to be printed. I found a copy of the CUPS driver for my printer [here]("http://www.cups.org/ppd.php?L667+I0+T+Q2840") ([others can be found here]("http://www.cups.org/ppd.php")), and looked inside the .ppd file.

In the "Device Capabilities" section, I changed LanguageLevel to 2 (so that CUPS will send the page in an older version of Postscript), then went into System Settings -> Printing, and chose this driver (click "Change" next to "Make and Model").

So far, that's fixed my problem and everything I've tried to print looks great. I hope this helps others experiencing the same problem.

---

### Post by shakma on 2011-11-29
Thanks for pursuing this and posting your solution, leemid!  I had the same problem on an HP LaserJet 4100N at my work for YEARS!  I ended up printing to a networked copier just so I wouldn't have to deal with the seemingly random wrong or "boxed" characters.  (Sometimes a "B" would print as a "T".  But not always... even on the same page of a document.  Or, the letter "x" won't print??  Seriously?!)  Your link to the driver and editing solution worked beautifully.  Thanks again!

Peace.

---

### Post by leemid on 2011-12-04
Shaka, you're more than welcome. After an extended period of use, I've noticed that some driver settings are not available (automatic duplexing, paper weight etc.) but I never need to use these on my 4100, only the Color LaserJet. Interestingly after doing a fresh install of Oneiric, I only noticed after a few weeks that I didn't need to hack the driver as everything was printing normally again. Maybe this was a regression of something. Either way, I'm pleased I've managed to help someone going through the same hell as I was!

---

### Post by Eric106 on 2012-01-21
Another thanks for posting the solution to this.  I have a 4100 that had been doing the same thing forever and driving me crazy.  This took care of it.  

Interestingly, I'm running the Xubuntu version of Oneiric and was still experiencing the font problems.  If you say you do not have the issue any more with Oneiric (I'm assuming the standard distribution) then there must be something different in the printing between the two.

-Eric

---

### Post by leemid on 2012-01-22
> **Eric106 said:**
> Another thanks for posting the solution to this.  I have a 4100 that had been doing the same thing forever and driving me crazy.  This took care of it.  

Interestingly, I'm running the Xubuntu version of Oneiric and was still experiencing the font problems.  If you say you do not have the issue any more with Oneiric (I'm assuming the standard distribution) then there must be something different in the printing between the two.

-Eric

Glad it worked for you. I suppose your Xubuntu experience could depend on whether you did a clean install of Oneiric or an in-place upgrade. I had varying results with respect to the printing problem depending on which route I took to upgrade. My guess is that you've only got to make one change to your print settings for a load of configuration files to be protected against automatic replacement during an upgrade.

---

### Post by zeero_k on 2012-04-01
Thanks for the tip, leemid!

I was having the same problem with my HP Color Laserjet 2550. I just went to /etc/cups/ppd and manually changed LanguageLevel setting in the PPD file that was already there. The missing character issue was instantly fixed!

As a side note, there are laughably few settings available under System Settings --> Printers in Ubuntu 11.10 in Classic Gnome. Instead, you can point a web browser to [http://localhost:631](http://localhost:631) to access the CUPS Administration page and do much more.

   ~0K

---

