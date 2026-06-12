---
title: "Celestia Add-on Confusion"
date: 2012-01-25
forum: General Help
---

### Post by zorbama on 2012-01-25
Greetings,
One of my favorite applications is Celestia, and recently I wanted to expand it with some add-ons from the Celestia motherlode ([http://www.celestiamotherlode.net/](http://www.celestiamotherlode.net/)). However, I'm having difficulties installing the add-ons, as many times it requires playing around in order to appear in Celestia at all, and even then there are missing textures and sometimes missing objects alltogether, and I'm not sure what to do. I tried putting the add-ons in the /usr/share/celestia/extras folder and a subfolder for each file, like they say is possible in some documentation I read, but it didn't work. I moved it up one folder and placed it directly on the extras folder, but even then it didn't always work, so I put them in the main celestia folder with the original celestia files, and not only did it still not work properly, but I also had a giant mess in those folders and I had to remove and re-install Celestia to set it straight.
Is there something I'm missing, or doing wrong, or are the add-ons just not Linux-compatible? Or maybe I completely misunderstood how add-ons work? I just don't know!
Here is a partial list of the add-ons I tried:
Alpha Omega System ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1442](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1442))
Beta Hydri v2 ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=708](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=708))
Black Hole 108 Nebula ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=589](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=589))
NGC 7293 - Helix Nebula ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=853](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=853))
Boomerang Nebula ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1007](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1007))
VY Canis Majoris and R136a1 ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1569](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1569))
Tatooine, Endor and Death Star ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=167](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=167))
Daemon System ([http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1314](http://www.celestiamotherlode.net/catalog/show_addon_details.php?addon_id=1314))

Haha, super nerdy, I know :D

I use Ubuntu 11.10 with Celestia 1.6.0, gpu nvidia 8500gt.
If there are any other details needed I'll gladly provide them.
I wanted to go to the celestia forum, but they are yet to allow me membership there, so I thought maybe asking Ubuntu users could help me be on the right direction.

Thanks in advance!

-Amir

EDIT: Solved! I don't know exactly how, but now all I do is place the add-on main directory in the extras folder (and sometimes tinker just a little bit with things like capital letters in files etc.) and the add-ons work. One thing I did was to change /usr/share/celestia's permissions so that I could work there without root powers. Hope this helps to anyone who might have a similar problem. :)

---

