---
title: "Advertisements stick to me"
date: 2011-05-01
forum: General Help
---

### Post by sparker1 on 2011-05-01
I am cursed to be dragging around advertisements to every website I visit and even some ubuntu 10.10 program pages (eg Freecell). In this case the advertisement is for Amazon "deal of the day" - I am just lucky that it is not some porno add. I can kill them with a re-boot but if I visit a website that has advertisements or a video (for instance the video on this site stuck [http://www.automotivetouchup.com/](http://www.automotivetouchup.com/)) then one of them will stick! If i close firefox (3.6.17) and open chrome then the same add will infest chrome without visiting any website. It would make a great virus but is getting me down. Is there any cure? I will try anything! I have added some screenshots for the doubters. By the way when I visited the website with the video it replaced the Amazon add with the video picture. keep the laughter down, please.

---

### Post by cymbaline42 on 2011-05-01
Sorry, I don't see any advertisements or anything untoward in your screenshots.  

Here are a bunch of Firefox add-ons and Chrome extensions that will help your browsing relatively ad-free and safe.

Firefox:

Adblock Plus ([https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/))
Web Of Trust ([https://addons.mozilla.org/en-US/firefox/addon/wot-safe-browsing-tool/](https://addons.mozilla.org/en-US/firefox/addon/wot-safe-browsing-tool/))
HTTPS Everywhere ([https://www.eff.org/https-everywhere/](https://www.eff.org/https-everywhere/))

Chromium:

Adblock ([https://chrome.google.com/webstore/detail/gighmmpiobklfepjocnamgkkbiglidom](https://chrome.google.com/webstore/detail/gighmmpiobklfepjocnamgkkbiglidom))
Web of Trust ([https://chrome.google.com/webstore/detail/bhmmomiinigofkjcapegjjndpbikblnp](https://chrome.google.com/webstore/detail/bhmmomiinigofkjcapegjjndpbikblnp))

Hope this helped.  Cheers.

---

### Post by sparker1 on 2011-05-02
Yes, you're right. The damn thing is transparent when I take a screen shot. I don't think this is an intentional attack but something in my settings with the video card or gnome but I don't have the knowledge to fix it. here are some photo's I took with a camera-sorry about the flash. The image is part of the video shown on this site 
[http://www.automotivetouchup.com/](http://www.automotivetouchup.com/)

[[IMG]http://img94.imageshack.us/img94/6520/imgp0675c.th.jpg[/IMG]]("http://img94.imageshack.us/i/imgp0675c.jpg/")
[[IMG]http://img862.imageshack.us/img862/1645/imgp0674j.th.jpg[/IMG]]("http://img862.imageshack.us/i/imgp0674j.jpg/")
[[IMG]http://img852.imageshack.us/img852/7469/imgp0673.th.jpg[/IMG]]("http://img852.imageshack.us/i/imgp0673.jpg/")

---

### Post by sparker1 on 2011-05-02
I think it was the video drivers. I have removed them and then reinstalled them and I seem good to go. I tested it on one of the sites that caused the proble and this time it did not cause one. However, with regards to the video driver - they still say "This driver is activated but not in use".

---

### Post by Rubi1200 on 2011-05-02
Install NoScript for Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

Clear the cache and cookies and restart the browser to see if it persists.

---

### Post by cymbaline42 on 2011-05-02
Ah, I see what you mean now.  It is a difficult problem to explain.

This seems to be an issue with Flash on Firefox.  There is a bug report and a solution mentioned here: [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/163361](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/163361)

To kill the application npviewer.bin, open System Monitor from System - Administration - System Monitor, click on the "Processes" tab, right click on it and kill the process.  It should go away now.

Also, if you haven't already done so, update Firefox and Flash player to the latest versions.

Hope this helped.  Cheers.

---

### Post by sparker1 on 2011-05-02
Thanks. I have installed No script and will have a look at that site on launchpad. I'll also update flash.

---

### Post by Rubi1200 on 2011-05-02
There is a great addon for Firefox that keeps Flash updated:
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

courtesy of forum member lovinglinux.

Hope this helps.

---

### Post by sparker1 on 2011-05-02
> **cymbaline42 said:**
> Ah, I see what you mean now.  It is a difficult problem to explain.

This seems to be an issue with Flash on Firefox.  There is a bug report and a solution mentioned here: [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/163361](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/163361)

To kill the application npviewer.bin, open System Monitor from System - Administration - System Monitor, click on the "Processes" tab, right click on it and kill the process.  It should go away now.

Also, if you haven't already done so, update Firefox and Flash player to the latest versions.

Hope this helped.  Cheers.

Thank you. I had a look at the bug. It relates to the 64 bit version - I am 32 bit; I tried the solution offered but there was no such process.

---

### Post by kaldor on 2011-05-02
> **sparker1 said:**
> Thank you. I had a look at the bug. It relates to the 64 bit version - I am 32 bit; I tried the solution offered but there was no such process.

I had this issue on Firefox only back a few weeks ago and it was quite annoying. Within a few days of it happening, I updated Flash and it was fixed. Make sure you don't have any updates you haven't applied. Also, you could try using a different browser if you can't get away from it since it seems to only affect Firefox.

---

### Post by sparker1 on 2011-05-06
Thanks kaldor and Rubi I have done both but Kaldor, it also affecetd Chrome.

---

