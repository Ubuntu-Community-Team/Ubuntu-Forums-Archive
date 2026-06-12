---
title: "ATI Raedon HD 4670 Drivers/Blu-Ray/Bluetooth with ubuntu systems"
date: 2009-07-14
forum: General Help
---

### Post by Odd_sam on 2009-07-14
Does anyone have the ATI Raedon HD 4670 Drivers working properly in Ubuntu? or at least enough to use compiz? I am looking into getting a Dell studio xps 16 and I was also wondering if it would be worth 200 bucks or so to get the Blu-Ray burner/reader if I plan to use ubuntu only on my laptop?

Also does the Dell Wireless 370 Bluetooth Module work in ubuntu? I saw some stuff on google that might suggest it's been blacklisted.

---

### Post by Odd_sam on 2009-07-27
Turns out the Dell Studio XPS works great in ubuntu! On first boots if you switch from ctrl alt f7 to f1 and back to your graphic terminal you will get trippy graphics and need to restart gdm before they will work properly again. I installed the closed source drivers and all the graphical issues vanished. Hibernation and standby will execute successfully before installing ATI's drivers, but you get the trippy graphics again so you need to restart gdm in order to get it to work properly again. After installing the closed source drivers hibernating and suspending hangs when trying to restart the ati drivers.

I haven't messed with the blu-ray player yet so I dunno anything there. And the bluetooth module works fine in ubuntu. As well as the special keys and the lit-back keyboard. With the exception of the eject key. I followed this guide to get it to work properly. [http://www.fmhq.com.ar/2009/07/dell-notebook-eject-cd-key-not-working.html](http://www.fmhq.com.ar/2009/07/dell-notebook-eject-cd-key-not-working.html)
Some issue's I've found can be annoying. Ubuntu's track pad drivers are such that lightly tapping the touch pad with the side of your thumb will cause the cursor to fly somewhere and click causing your text to go where ever the mouse randomly clicked. Also the touch pad thinks you have really small fingers, and can jump the cursor around the screen if you give it too much ;). 
Any questions I'll happily respond to.

---

### Post by sagen on 2009-08-23
Hi!

Thanks so much for sharing this! Very helpful as I'm considering buying the studio xps 16. 

May I ask what kernel you were running? There seem to be some problems with GLX for 2.6.29, as stated here: [http://www.linlap.com/wiki/dell+studio+xps+16](http://www.linlap.com/wiki/dell+studio+xps+16)

---

### Post by Odd_sam on 2009-10-23
> **sagen said:**
> Hi!

Thanks so much for sharing this! Very helpful as I'm considering buying the studio xps 16. 

May I ask what kernel you were running? There seem to be some problems with GLX for 2.6.29, as stated here: [http://www.linlap.com/wiki/dell+studio+xps+16](http://www.linlap.com/wiki/dell+studio+xps+16)

Hopefully you have gotten settled by now with your laptop. But I was using 9.04 at the time and I have now switched to the 9.10 Release Candidate and have found that if you use the envy-ng drivers for the video card suspend works with compiz without any issues but I have yet to get hibernation to work. There was some script work around that I found later and used but it never worked consistently. At the moment ubuntu has successfully suspended every time I've asked it to on the new 2.6.31-14 kernel.

---

### Post by shrndegruv on 2009-10-28
> **Odd_sam said:**
> Hopefully you have gotten settled by now with your laptop. But I was using 9.04 at the time and I have now switched to the 9.10 Release Candidate and have found that if you use the envy-ng drivers for the video card suspend works with compiz without any issues but I have yet to get hibernation to work. There was some script work around that I found later and used but it never worked consistently. At the moment ubuntu has successfully suspended every time I've asked it to on the new 2.6.31-14 kernel.


I have the karmic beta too, with the fglrx drivers, and hibernate works but suspend will not resume.  Is there a way around this? (xps studo 16 with the hd 3000 series card)

---

### Post by Odd_sam on 2009-11-11
I'm not sure I'm using a different card than you. in 9.10 final it works with the envy-ng drivers. (google envy-ng for help)

---

### Post by shrndegruv on 2009-11-11
> **Odd_sam said:**
> I'm not sure I'm using a different card than you. in 9.10 final it works with the envy-ng drivers. (google envy-ng for help)

what xorg.conf did envy-ng spit out?  Since i have the 9.10 catalyst i think its probably a matter of configuration.  

Are there issues with envy-ng where a new kernel api is installed by apt-get and all of a sudden X stops working?

---

### Post by shrndegruv on 2009-11-11
damn doesn't work for me...

---

