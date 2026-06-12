---
title: "Breezy to Dapper migration tools"
date: 2006-05-13
forum: General Help
---

### Post by kadil on 2006-05-13
Is the Ubunut team going to release any migration tools to move from Breezy to Dapper. Please excuse my ignorance, but I understand one day Breezy will not be supported and I was wondering if every breezy user would back up thier files, settings, etc in their own way, or if there would be some systematic way to do it. Is there any documents that relate to these sorts of intentions?

Regards,
Kim

---

### Post by meng on 2006-05-13
Oh boy, deja vu all over again.
[http://www.ubuntuforums.org/showthread.php?t=175335]("http://www.ubuntuforums.org/showthread.php?t=175335")

---

### Post by skippy81 on 2006-05-13
All you need to do is burn your home directory onto a dvd or cd and then you are safe to upgrade.  I went from breezy to dapper using apt-get, took about 2 hours to download and install everything, and all my settings remained.

---

### Post by aysiu on 2006-05-13
I don't see why you would have to back up your settings for a migration any more than you would have to back up your settings for just... nothing.

An upgrade to Dapper doesn't destroy your data. It may, if it fails, conk out your xserver or locales, but your data and settings will remain intact.

The best thing to do is create a separate /home partition. That way, you can keep your settings and files separate from your installation and do a clean reinstall every time.

For upgrade instructions:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by dsokus on 2006-05-13
[QUOTE=kadil]Is the Ubunut team going to release any migration tools to move from Breezy to Dapper. Please excuse my ignorance, but I understand one day Breezy will not be supported and I was wondering if every breezy user would back up thier files, settings, etc in their own way, or if there would be some systematic way to do it. Is there any documents that relate to these sorts of intentions?

Regards,
Kim[/QUOTE]
I have just upgraded to Dapper and all my settings stayed as before! :D 

Unfortunately Dapper couldn't quite solve my screen resolution problem either though. :s

Zs.

---

### Post by kadil on 2006-05-14
In any transfer, there are a few risks including:
(1) The core system version numbers can change, so data in the home directory might be in an out of date format.
(2) Manual hardware configs may not be transferable ( like my wireless lan)
(3) if the update fails, I have to look through synaptic and reselect all the extra apps that were part of my system, and find the few that did not have repositories
(4)you cannot just use "dpkg --get-selections" as alternative packages may be used in the new system

I know there is a technical solution to these hazards, but Ubuntu is great for the uninitiated, it would be good to not have to learn the ins and outs of the system, incase things go wrong with the update.

Each time I switch distro's, I find it is good to have /home and /etc on other media. But it still takes days to get everything right, including non packaged apps, mail settings, lan settings, video card settings, etc.

I just though this may have been considered in the grand scheme Ubuntu. It is a bit more complex than:

   sudo gedit /etc/apt/sources.list
   change every "breezy" into "dapper"
   sudo apt-get update && sudo apt-get dist-upgrade

Kim

---

