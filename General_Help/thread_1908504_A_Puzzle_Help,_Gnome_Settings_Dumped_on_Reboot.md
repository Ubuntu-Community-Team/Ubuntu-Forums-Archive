---
title: "A Puzzle: Help, Gnome Settings Dumped on Reboot"
date: 2012-01-13
forum: General Help
---

### Post by tehowe on 2012-01-13
Help! All my gnome desktop appearance and panel settings are just - **gone**.

**Not only the panels and AWN and these cosmetic things are gone, but wierd seemingly unrelated things too** - examples

[LIST]
[*]Calibre had to be shown where my ebooks are again
[*]Gwibber and Evolution need their configs redone
[*]Banshee no longer remembers where my music is
[*]VPN connections under network has forgotten my settings
[*]Byobu seems to have lost its config as all the status indicators are reset and my preset tabs are gone
[*]I had to add myself back to the MythTV group to get that working... etc!
[/LIST]

Other things (like Liferea) are unaffected

I had been working away on the system all night, but nothing you'd thikn would cause this - I was learning how to do a basic apache2 config for 3 folders under /var/www (succesfully), got acidbase working for snort, and installed Google's custom-built Google Earth deb. The very last thing I did before I restarted and lost all the settings was to reconfigure snort (in /etc/snort/snort.debian.conf) to use the external IP of my VPN, and to sniff on tun0 instead of eth0. Who knows, maybe that did it but correlation with my OpenVPN going down isn't necessarily causation.

**Thankfully I do have an rsync'd backup of /home/me** as of 3am last night on my other drive, so in theory all I have to do is copy over the pertinent folders to /home/me but which ones would store those settings? Is it gconf? But I don't want to just roll the entire backup in as then I'd lose the now-working acidbase and apache2 config!

Maybe you too know what it's like at 4am when you're thinking, awesome, I win, I can get a few hour's sleep now and then *boom* :O

I can post whatever logs might be useful, as I'm really into learning the ins and outs of the console right now. Thanks in advance!

**Ubuntu Studio 11.04, Gnome 2D Desktop**

---

