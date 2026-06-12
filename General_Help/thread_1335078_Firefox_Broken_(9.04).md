---
title: "Firefox Broken (9.04)"
date: 2009-11-23
forum: General Help
---

### Post by guy3pwood on 2009-11-23
Hi, new user here, just crawling on the floor begging for some help :)
(So if I make any newbie mistakes please forgive me)

My problem is thus; Firefox does not work properly anymore, when I enter and address and hit enter (or click browse, or whatver), nothing happens.
When I try and use the search engine toolbar on the side, nothing happens.
When I click on a button or a link in an opened page (say the homepage, which is the only thing that loads), nothing happens.
The status bar on the bottom always insists "Done".
"The internet" does work, since I am posting from that ubuntu setup using another browser (midori), and since wget and the synaptic package manager both work properly (that's how I managed to install midori)

Leading up to it; I was unable to use hibernate (according to the internet, because I don't have a swap partition), so I was trying to see if I could get it to hibernate to a swap file using advice found through google. The last thing I found was [http://wiki.geteasypeasy.com/Fix:_hibernate](http://wiki.geteasypeasy.com/Fix:_hibernate), and after trying it out and reaching the "If you run sudo s2disk now, it should hibernate correctly." phase, it did not hibernate correctly, and after resetting my system I found that firefox doesn't work (as described previously).

My only guess is some other guide I found that says changing toolkit.networkmanager.disable in about:config to true will help because the problem might be that firefox wrongly gets information that there is no internet connection, but after changing that setting and restarting, the setting goes back to previous, and firefox still does'nt work.

Thank you and have a nice day :)

---

### Post by teadystring on 2009-11-23
Did you recently upgrade, e.g. to 1.0.3? If so, any installed extensions might be interfering with normal functioning. 

I had similar serious issues moving from 1.0.2 to 1.0.3 where the menus were extraordinarily slow to open and I could not browse any pages. Disabling them requires editing some config files, v. [http://kb.mozillazine.org/Upgrading_(firefox](http://kb.mozillazine.org/Upgrading_(firefox)) . 

In my case the main culprit turned out to be User Agent Switcher 0.6.5, so I have uninstalled it until the next version is released.
_________________________
[remortgage bad credit rating](http://www.adverse-mortgage-centre.co.uk/remortgage-bad-credit-rating.html)
[discount auto insurance](http://www.quotes-auto-insurance-review.com/2009/09/car-insurance-quotes.html)

---

### Post by guy3pwood on 2009-11-23
Thanks for your help, but unfortunately my problem is still unresolved :(
I did not recently upgrade, and I also tried:
1) Enabling/Disabling addons (I only have NoScript and the Ubuntu compatibility addon)
2) Reinstalling Firefox (including complete removal and then a "fresh" install)
3) Disabling/Enabling restricted wifi driver (even though the problem manifests whether I'm using a wireless or a wired connection)

---

### Post by wojox on 2009-11-23
This should fix you up [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by guy3pwood on 2009-11-23
I've tried the various solution supplied there that seemed appropriate, I even tried going further than just deleting the places.sqlite and uninstalled FF, deleted .mozilla and reinstalled and still no luck.
The one thing that is problematic is one of the suggestions of turning ipv6 off in about:config, but like the previous tweak of turning networkmanager off in about:config, it doesn't "stick" and the setting in about:config returns to the previous setting, so I couldn't try that one.

I'm really perplexed about this one, because the problem persists even after a complete reinstall of firefox.

---

