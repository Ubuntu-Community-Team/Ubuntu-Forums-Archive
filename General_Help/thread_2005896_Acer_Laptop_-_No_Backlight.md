---
title: "Acer Laptop - No Backlight"
date: 2012-06-18
forum: General Help
---

### Post by Kyle Maclean on 2012-06-18
Hi, Ubuntu is the first operating system that I've tried besides Windows XP, Vista and 7. I bought an Acer Aspire 5332 with a dual-core 1.9Ghz Celeron processor, 2GB of RAM and 220GB HDD. The other day I tried to install the latest version of Ubuntu (12.04)(I wrote the ISO to a 2GB flash drive) and I got a problem where I could see the purple boot manager but as soon as it started up the screen went blank. I couldn't see anything so I shut down my computer. After many different Linux ISO burners later and many hours browsing around these forums, I lost hope. I then went and installed Ubuntu 10.04 and the same thing happened. It finally worked when I installed 8.04 and everything is fine now. I found some other guys on these forums saying that they had the same problems with their Acer laptops and the only way they could solve it was by downgrading to 8.04. What I was wondering is when it's safe to upgrade and if anyone has a question about something I missed out here, if they could please post below. I forgot to mention that I was able to slightly see my screen just enough to see that when I use the built-in keys (Fn + Left/Right Arrow) to adjust brightness, it displays at max already.

---

### Post by eric703 on 2012-06-18
To me, what it sounds like is you need a new processor. I'm not sure if your 1.9 ghz is enough.

---

### Post by Kyle Maclean on 2012-06-18
Well it is dual-core and I know of someone with a 1.5Ghz dual-core PC who can run Ubuntu. Also, I know I can run it because I thought I could make out the installation screen for when you first boot Ubuntu. In other words, when I tilted the screen backwards, I could see the buttons for trying Ubuntu and Installing Ubuntu.

---

### Post by Kyle Maclean on 2012-06-18
I forgot to ask that if there isn't a solution; I could use 8.04 forever? I know that the server support ends in April 2013 and the desktop client was supposed to end on 12 May 2011

---

### Post by Redblade20XX on 2012-06-18
> **Kyle Maclean said:**
> I forgot to ask that if there isn't a solution; I could use 8.04 forever? I know that the server support ends in April 2013 and the desktop client was supposed to end on 12 May 2011

You tried pushing the "nomodeset" kernel parameter when grub starts?
Take a look here for some reference: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
It's a bit old but still gives you an idea.

-Red

---

