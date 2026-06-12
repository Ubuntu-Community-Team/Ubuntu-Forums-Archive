---
title: "&quot;Agreeing to EULA&quot; scrolling feature bug.."
date: 2009-11-14
forum: General Help
---

### Post by Xog on 2009-11-14
Hello,

I'm experiencing a problem with wine. I'm trying to install WoW, I've followed all the steps leading up to this part correctly, tried several times for the past week. I'm running 9.10, I have the latest version of Wine, and I downloaded the World of Warcraft installer from their website after logging in.

The problem I'm experiencing:
I get to the screen before the installation that states I have to agree to the EULA, but in order to do so I must scroll to the bottom. OK.

When I scroll to the bottom, it's still unavailable to click "Agree!"

Here's a link to the image (tried posting the actual image but it's pretty big, don't feel like resizing)
[http://img136.imageshack.us/img136/1238/wowwg.jpg](http://img136.imageshack.us/img136/1238/wowwg.jpg)

---

### Post by Wim Sturkenboom on 2009-11-14
Did you try to click in the Eula text?

---

### Post by Xog on 2009-11-14
Yes.. I've also tried highlighting everything. I've also held the down arrow from top to bottom, and the page up/down button from top to bottom.

---

### Post by howefield on 2009-11-14
> **Xog said:**
> When I scroll to the bottom, it's still unavailable to click "Agree!"


Seems to be a bug in wine, and is fixed in certain wine releases. You said you were running the latest wine, would that be 1.1.33

---

### Post by Xog on 2009-11-14
Yep. I tried the most recent stable release and the beta.

---

### Post by Xog on 2009-11-14
I've discovered this might be a Gecko related problem. Upon first entering the installation mode, it states the program is trying to display HTML content, so wine offers to download and install "Gecko" which if I recall correctly is the mozilla engine?

Well, wine downloads and installs gecko and then the EULA pops up (which I'm assuming is the HTML content).

Is there another way I can have wine use a different program to display the EULA?

---

### Post by howefield on 2009-11-14
> **Xog said:**
> Is there another way I can have wine use a different program to display the EULA?


Yes, use ies4linux.

Google for "can't agree WoW ies4linux" or something like that, you'll get a few hits describing what you need to do, eg,..

[http://aspectofthehare.blogspot.com/2008/09/linux-users-do-it-with-wine.html](http://aspectofthehare.blogspot.com/2008/09/linux-users-do-it-with-wine.html)

---

### Post by andrewjoy on 2009-11-14
I have not run wow under wine since 3.1 but this is a known problemm with the wrath install your best bet is to get a pc running windows and install wow then copy the folder over to your .wine directory and edit your config file in the wow directory to the correct setting ( resolution refresh rate ect).

I have used this method and have had the same install of wow for about 5 years running on 2k xp ubuntu and 7.

---

### Post by Xog on 2009-11-14
> **howefield said:**
> Yes, use ies4linux.

Google for "can't agree WoW ies4linux" or something like that, you'll get a few hits describing what you need to do, eg,..

[http://aspectofthehare.blogspot.com/2008/09/linux-users-do-it-with-wine.html](http://aspectofthehare.blogspot.com/2008/09/linux-users-do-it-with-wine.html)

Thanks! that worked

---

