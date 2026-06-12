---
title: "Complicated problem with wine"
date: 2010-09-05
forum: General Help
---

### Post by Grglbrgl on 2010-09-05
Yesterday I installed Ubuntu and I earned a bit of the basics before attempting to install pinnacle studio 12 by cd-rom. I downloaded wine, fooled with it a bit, and I got studio 12 install wizard to open up. However, at that point I didn't have a serial key I needed- one which I have today recovered. Now, however, I don't know how the hell I got the wizard to open.

I know exactly what I did. I opened up the cd port, and I opened up terminal. I typed in ```
wine
``` then I dragged and dropped the welcome.exe into the terminal then I pressed enter and it magically worked. Now when I do that I get: (this is the part where I re-did exactly what I said and it worked after not working three different times only a half minute prior.)

Now, though, when I'm in the pinnacle studio 12 installer if I attempt to install studio 12 then it gives me a wizzard box that simply reads: "1158:" Is this a Linux problem, because it didn't happen last time?

---

### Post by davidmohammed on 2010-09-05
I surprised you've got that far with Pinnacle Studio and Wine.  Studio is a heavyweight windows application that perhaps should just be left in windows to run.  In the winehq.org database, this version of studio is marked as "garbage" i.e. it wont run.

I would recommend you look at OpenShot, kdenlive or pitivi (installed with lucid) for your video editing in ubuntu.

---

### Post by Grglbrgl on 2010-09-05
I worked it a bit further and installed studio 12, however, you're right- it won't work without microsoft visual 2.0, which is impossible to install (but I tried that too)

I've yet to try your first suggestion, but I know for fact that your second and third refuse to acknowledge my DVC 100 capture card, and thus I can not record xbox gameplay with them. I'll try out your first suggestion, however.

---

### Post by Grglbrgl on 2010-09-05
I'm having trouble with openshot- It wont connect to the video source, and it wont detect the dazzle. Anytime I try to connect with anything it says I need libxvid, which I either have or cant find.

---

### Post by davidmohammed on 2010-09-06
xvid is in libxvid4.  Have you installed ubuntu-restricted-extras?

Also - it is definitely worth adding the medibuntu repository and added w32codecs (or w64codecs if using 64bit).

These will add all sorts of codecs useful for video editing and decoding.

---

### Post by davidmohammed on 2010-09-06
> **Grglbrgl said:**
> 
I've yet to try your first suggestion, but I know for fact that your second and third refuse to acknowledge my DVC 100 capture card, and thus I can not record xbox gameplay with them. I'll try out your first suggestion, however.

It seems linux has issues over your dazzle - its not related to the video editors.  Its more like a kernel issue.

---

