---
title: "Wierd Local Issue"
date: 2010-05-25
forum: General Help
---

### Post by PerfectReign on 2010-05-25
I have a fresh install of 9.1 on my laptop.

I noticed that the date format on my bottom panel is set to day - month - year. I wanted it month-day-year.  

I also noticed when I added the weather applet to the system tray, it came in with temperature in Celsius.  Being in Los Angeles, I would prefer it in Fahrenheit.  This started me wondering - in which country does the system think I am?

I ran the "locale" command and got back that I'm in Canada somehow:

> kai@kai-laptop:~$ locale
LANG=en_CA.UTF-8
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=


Looking at the Language selected, it says, "English (United States)" for al litems.

Not finding a method of changing this in the control center (spelled, centre) I looked here: [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale).  Ugh! command-line stuff.

In any case, I entered my /etc/environment file and see the following:

> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"

So, where is it saying I'm in Canada?

---

### Post by dino99 on 2010-05-25
goto synaptic and remove/purge all the languages packages you dont need or let localepurge package to do it in the background.

about the date in panel: right click on it to set your prefs, idem for temperatures

---

