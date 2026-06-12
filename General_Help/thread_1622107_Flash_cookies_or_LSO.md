---
title: "Flash cookies or LSO"
date: 2010-11-15
forum: General Help
---

### Post by NikoC on 2010-11-15
I wasn't really sure where to put this, but as most of you are probably aware Adobe Flash Player stores cookies on you machine which are quite hard to remove. You can do so via [their website]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html"), but I don't really like the idea of accessing local data via an online service.

Apparently these cookies are stored in your home folder in the .macromedia directory and I 've made an alias in my .bashrc to remove the folders where the cookies are being saved and this is how it works:
- edit .bashrc with your favorite text editor e.g. gedit .bashrc and add the following line to the bottom of the file:
alias cookieclean='rm -rf ~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys && rm -rf ~/.macromedia/Flash_Player/#SharedObjects'
- save and close
- to update your bash type in a terminal: source .bashrc
- use the command 'cookieclean' in a terminal to remove stored cookies

This seems to be working on Ubuntu 10.10 with both Chromium and Firefox (I assume they must be using the same directory to store those LSOs). I verified this by opening the webpage above and after 'cookieclean' all stored websites were removed.

Cheers,

NikoC

---

### Post by bouncingwilf on 2010-11-15
Interesting article on the subject here [LinuxPlanet - Tutorials - Getting Rid of Nasty Adobe Flash Cookies the Cool Linux Way - Preventing Flash Cookies]("http://www.linuxplanet.com/linuxplanet/tutorials/6709/3/")



Bouncingwilf

---

### Post by gmargo on 2010-11-15
I've used this Firefox add-on to delete LSOs: "BetterPrivacy"
[https://addons.mozilla.org/en-US/firefox/addon/6623/?src=api](https://addons.mozilla.org/en-US/firefox/addon/6623/?src=api)

---

### Post by endotherm on 2010-11-15
> **gmargo said:**
> i've used this firefox add-on to delete lsos: "betterprivacy"
[https://addons.mozilla.org/en-us/firefox/addon/6623/?src=api](https://addons.mozilla.org/en-us/firefox/addon/6623/?src=api)
+1

---

### Post by mister_playboy on 2010-11-15
If you don't want the cookies to ever be on your computer in the first place, you can set the ~/.macromedia folder to read-only.  Some sites refuse to work when they can't cookie you, however. :P

---

### Post by Rubi1200 on 2010-11-15
> **endotherm said:**
> +1
+2

BetterPrivacy is a great addon and highly recommended as an additional layer of security/privacy for your browser.

---

### Post by pqwoerituytrueiwoq on 2010-11-15
> **rubi1200 said:**
> +2

betterprivacy is a great addon and highly recommended as an additional layer of security/privacy for your browser.
+3

---

### Post by NikoC on 2010-11-16
> **gmargo said:**
> I've used this Firefox add-on to delete LSOs: "BetterPrivacy"
[https://addons.mozilla.org/en-US/firefox/addon/6623/?src=api](https://addons.mozilla.org/en-US/firefox/addon/6623/?src=api)

I'm currently using Chromium as my default browser and such an add-on is not available, yet. But thanks for the tip, I'll look into it!

---

