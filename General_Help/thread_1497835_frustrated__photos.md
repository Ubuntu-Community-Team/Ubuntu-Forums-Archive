---
title: "frustrated  photos"
date: 2010-05-31
forum: General Help
---

### Post by kennethtb on 2010-05-31
I expected more from ubuntu 10.4 with regards to printing with exact size photos and with poor auto colour printing  but the situation remains unchanged!
for instance .. the photo size configurations for ubuntu/fspot/gimp and others are not compatible with my printers (HP and Brother) .. here in Europe a typical standard size photo (10x15inches or 150x100mm **are not even on the Ubuntu listing?** I have tried all listed possibilities including "custom" (which does not seem to ever work correctly?)and the result at best is photos with uneven boarders or at worse my printer goes a bit crazy with much wasted photo paper and expensive ink  ...even photos selected for "no boarders" still produces photos with the self same uneven boarders.
I have tried pretty much everything over time following advice in this forum and including using HPlip and updating drivers required for my Brother printer _but the root problem seemingly lies with the Ubunto photo size setup listing._
Working with Ubuntu over the years I have found that it can do pretty much everything that Windows can do except for this dam ongoing photo quality and configuration problem.

---

### Post by dino99 on 2010-05-31
have you installed icc-profiles & photoprint ?

---

### Post by kennethtb on 2010-05-31
Thanks for your reply .. and no I have not tried these two options (first time I have heard about these) but my experiance tells me no matter what photo configuration software one uses it always connects through the basic root Ubunu photo configuration and there lies the problem with uncompatible size listings                       ie system/preferences/printing

---

### Post by ajgreeny on 2010-05-31
Photoprint is great!

You can print several pictures on one A4 or Letter size page, the application arranges the pictures to give the best layout, or you can easily set custom image dimensions.

It's well worth a try.

---

### Post by kennethtb on 2010-05-31
Thanks for info I intend to try out this Photoprint but meanwhile can you confirm that it can (exactly) format standard European photo paper sizes eg 150x100mm and will that transfer through the Ubuntu root print options.

---

### Post by ajgreeny on 2010-05-31
> **kennethtb said:**
> Thanks for info I intend to try out this Photoprint but meanwhile can you confirm that it can (exactly) format standard European photo paper sizes eg 150x100mm and will that transfer through the Ubuntu root print options.
No, I'm afraid I can't, mainly because I don't really understand what you mean by the ubuntu root print options.

Why do you want to use root instead of a user to print something, or have I completely misunderstood your meaning?

---

### Post by kennethtb on 2010-05-31
Hi again  sorry for the confusion I only meant to say that the Ubuntu option - system/prefrences/print has (contained within)a photo size selection (which seems to contain only amercian photo sizes) and no matter what photo software one uses (such as F-spot for instance) this base Ubuntu size listing overrides any settings made in other 3rd party photo software. The ubuntu listing contains settings such as A4, A5, A6, Photo, Photo without borders plus a whole list of other strange sizes but non of which conforms to 150x100mm or 10x15 inches which is a standard size found in Europe.
The photos always come out incorrect no matter what I try.

---

### Post by coldraven on 2010-05-31
I cannot help you with your image settings but I can help with your ink costs.
Do a Google for "CISS" that stands for Continuous Ink Supply Systems.
I have been using a six colour one in my Epson for over three years, no problem!
It has six 100ml. tanks of ink, I can print a lot with that.
Ink costs about £15 a litre instead of £1000 a litre using printer cartridges.
(It would cost £1000 if you had a Canon printer!)
You just refill by pouring ink out of a bottle through a funnel into the ink tanks , it takes minutes.

P.S. I just looked at Gimp 2.6.7 and it has definable custom paper sizes but I've not tried them. Good luck :)

---

### Post by cogier on 2010-05-31
Firstly I am in Europe and so understand the paper size issues. I have had trouble getting my HP Photosmart to print correctly but have managed to get it to print photos A4 borderless using Gnome photo printer and HPLIP. If that is of interest let me know and I will list out what I have done it.

---

### Post by kennethtb on 2010-06-01
Thanks everyone for your ideas especially the ink refill comments as I was already planning to break open an empty HP three colour ink cartridge to see if one could modify for refilling. 
As for the unobtainable photo sizing (which I need you use in a semi professional capacity) I believe this is a basic flaw within the Ubuntu programming .. a point perhaps someone with higher computer skills and Ubunto knowledge could pick up upon otherwise one needs to revert to Windows in order to obtain a basic European standard photo size.

---

### Post by tiznom on 2010-06-21
I'm having this same problem. 

I just tried Photoprint and it did not correct the problem. Looks like a cool program, though. Just didn't fix what I needed. 

The fundamental problem seems to be that Ubuntu won't fill the photo paper when the source image has a different aspect ratio than the target paper size. If you manually crop the photo ahead of time with Gimp, for example, to the exact aspect ratio as your photo paper, you will get a borderless photo. 

I want Ubuntu to simply center the image and fill the paper, cropping some off the sides or top "automagicly" as needed to fill the print. An option to manually pan up/down and side to side during print options would be nice, but not essential. 

So far I've tried F-Spot, Picasa, digiKam, Photoprint, and just printing right from Nautilus. Tried these with hplip installed and an HP Photosmart printer, Ubuntu 10.04. Anyone figure this out? Surely someone in Europe has sorted this out. There are a lot of people here printing a lot of photos with metric-sized paper. Are they all coming out wrong with Ubuntu? I hope not. I used to do this no problem with Ubuntu 9.04 and a Canon MP830 and it worked fine. This is a new problem to me.

---

### Post by BarryM on 2010-09-04
I am glad that I am not the only frustrated user in Europe! I was getting brilliant prints on a custom size paper 100x150mm from fspot on my HP Photosmart C5180 before I upgraded from 9.10 to 10.04, much better than anything I could get using the HP printing package on Windows. I found that I had to explicitly tell Fspot to print full page and zoom on the image settings tab and also set paper type to photo on the advanced tab, otherwise I got borders and not such good quality.

Now, since upgrading yesterday, I find that my printer seems to start printing before the paper is in place, so I get ink in the works and the end 24mm or more blank!

I did, whilst upgrading, tell the system to retain all of the obsolete drivers: I wanted it to keep CUPS-PDF only, but got that wrong!

Has any one got any idea what to do to get the printer to print correctly on HP photo paper?

---

### Post by tiznom on 2010-09-04
Sadly, I still haven't figured this out. I have got everything but borderless photo printing sorted out. I had been carrying the wife's Windows tablet over to the printer and hooking it up via USB for photos, but now I have taken a different route. If you have a smartphone the "HP iPrint Photo" program works just fine. Symbian, Windows Mobile, Android and iPhone all supported. Still not a direct solution to our problem, but an acceptable workaround for now. Good luck.

---

### Post by BarryM on 2010-09-04
Unfortunately I don't have any other means of printing other than my PC, dual boot Ubuntu or Windoze: looks like I will have to resort to printing via the unmentionable OS for now!

Thanks for your comments.

By the way, I measured up a sheet of genuine HP 100mmx150mm paper, and it is actually 4"x6" exactly, so tried a print using the HPLIP 4x6 setting, slightly better, but still with the offset and ink getting into my printer's works.

Best wishes

---

### Post by jcolyn on 2010-09-04
Why not try the gutenprint plugin for Gimp?

Type gimp in synaptic and scroll down.

---

### Post by BarryM on 2010-09-05
If I install gimp-gutenprint will it upset normal (text) printing using HPLIP?

---

### Post by jimmers on 2010-09-05
You could always have a look at this :-
  	 	 	 	 	 	  **Open Source Photography Software**

 by Vivek Gite ·  
 [[IMG]http://c.cyberciti.biz/cbzcache/3rdparty/linux-logo.png[/IMG]]("http://www.cyberciti.biz/tips/category/linux")
 I recently brought Canon EOS 500D mid-range DSLR cameras with good promotional discounts. My photography interests date back to my school days but I did not take photography seriously until recently. Now, I'm researching for quality open source photo-software which may be available to photographers. This blog post gives a quick and dirty view of the different photo applications available for Linux operating systems:
 [INDENT]Photography on the free software desktop has come a long way in recent years. All of the major desktop environments support camera import and provide image management and editing applications, including the all-important raw file conversion. But the desktop defaults are really geared towards casual users, optimized for point-and-shoot cameras and sharing photos online. Don’t be fooled by that, though; open source can and does offer the tools to support professional photographers and high-end enthusiasts.[/INDENT] [INDENT]Rather than drop in a long, bulleted list of applications, though, let’s take a look at what the open source alternatives are, task-by-task, to get a better feel for how the pieces fit together into a normal photographic workflow.[/INDENT] Read more: [Photography with Open Source / Linux]("http://blog.worldlabel.com/2010/photography-with-open-source-linux.html")


Luck

---

### Post by jimmers on 2010-09-05
Even better why not suscribe to nixcraft.com, to receive E-mails for all things Linux.


Luck

---

### Post by BarryM on 2010-09-10
It works!!

I am not sure what I have done (if anything) but my printer now seems to be working correctly from Fspot. I have just managed to print a picture on borderless 6"x4" photo paper (what HP call 100x150mm in the UK: it is actually 101.6x152.4mm).

I set up page as "Photo or 4x6 inch index card", portrait for my printer (Photosmart C5100 series) in the Page Setup Dialogue, then, in the printer dialogue, set up Page Setup Tab page source Photo Tray, Image Settings Tab Full Page (no margins) and Zoom, Advanced Tab Printout Mode Photo (on photo paper), the print. One perfect print, no borders and excellent colour rendering.

I did clean the feed rollers in the printer, which may have helped with the feed problem, and I have had a couple of system updates since I last tried, so I do wonder if one of these may have done something to the printing?

---

