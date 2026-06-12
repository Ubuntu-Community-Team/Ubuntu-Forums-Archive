---
title: "Fluxbuntu Restricted Drivers - Wireless"
date: 2009-08-22
forum: General Help
---

### Post by kazbear on 2009-08-22
In looking for a smaller, quicker linux distro, I decided to try Fluxbuntu.  Its seems pretty good so far.  I am running it on a Dell D600 laptop and trying to go all internet.  Not really caring for any apps so much other than a browser.

Of course you need something to get it all set up, and this has proven to be a challenge, especially with wireless.  I think when I had Ubuntu on the laptop, I was able to plug it in wired, go to the Restricted Drivers manager and install the drivers for the wireless card (Broadcom).  This does not appear to be an option for Fluxbuntu,

Though it implies that the Restricted Drivers Manager is installed, I am unable to run it.  There is no choice in the menu system for it, and the command "gksu jockey-gtk" does nothing.  Just returns me to the prompt.

The main point of this post is to ask for help setting up the wireless card in Fluxbuntu, but if there any other suggestions on a small footprint internet browser set up, I am ready to test it.

Thanks
kaz

---

### Post by snowpine on 2009-08-23
Hi Kazbear,

1st off, Fluxbuntu does not include jockey-gtk by default... it is not really the "Fluxbuntu way" to include a bulky GUI application for something that can be configured from the command line. If you want, use your wired connection to install jockey-gtk (sudo apt-get install jockey-gtk). As I'm sure you know, 7.10 has reached its "end of life" so you will need to edit your sources.list to point to old-releases before you can install anything from the repository.

Another way of course is to search for a Gutsy tutorial specific to your card, then use the command line. The terminal command lspci will tell you which chipset you have (mine is BCM4312, for example, and works best with the wl module). Broadcom makes a lot of cards, and they have different solutions... some need wl, others b43, and some are best with ndiswrapper. Sorry I can't be of more help, but I haven't used Gutsy in a long time.

Fluxbuntu is cool, but if you are looking for a non-obsolete lightweight distro, I highly recommend the current version (9.04) of Crunchbang. It includes jockey-gtk by default and recognized my Broadcom card out-of-the-box.

---

### Post by kazbear on 2009-08-24
Hey thanks!

Im going to look into Crunchbang.  Since I am just messing around anyway, I dont mind trying something new.  And if it just works...Even better!

-kaz

---

### Post by P4man on 2009-08-24
I briefly tried crunchbang after reading about it here. Kinda disappointed in it. Just reconfiguring my keyboard layout was harder than needed (though not exactly impossibly hard, but still, hey only 5% or so of the world types on US keyboard, one might as well ask? And why does it require a REBOOT?), I couldnt figure out how to change my default soundcard (I got 2), none of my multimedia keys worked, boot times wheren't any better as ubuntu afaict (though I admit, I installed it on a less than stellar fast USB stick). The interface seemed... basic  to put it mildly. But that at least I expected :)

To each his own, and I may not have given it a fair chance, but for an older machine, I prefer PClinuxOS. I do love the splash screen though :D

---

