---
title: "Firefox 3.5 broken after system update"
date: 2009-08-01
forum: General Help
---

### Post by UranUtan on 2009-08-01
Using Ubuntu 9.04 x64. I ran a system update yesterday, there were 3 items, related to Firefox 3.5 and XUL ...

After update complete and restarting FF 3.5. Now whenever I open FF 3.5, there is only a task labelle "Firefox 3.5" in the taskbar. Clicking on it show a minuscule window. Resizing this window to bigger show a complete blank screen.

What is the problem?

NOTE: this post is created using the previous FF 3.0 which is still in the machine.

---

### Post by Soul-Sing on 2009-08-01
How did you install firefox 3.5 next to the "old" version?
Thats important to know imo.

---

### Post by UranUtan on 2009-08-01
Via Ubuntu repositories, following the advices in this blog:
[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

---

### Post by UranUtan on 2009-08-01
Issue solved, after rebooting the computer.

The Update Manager said FF 3.5 needs to be restarted. I re-ran auto update several times (ne new update), close / open FF 3.5. Always same issue. As the last measure I tried a reboot. The open FF 3.5, this time I saw the FF update progression screen and it is back to working order.

---

### Post by brianpatrick on 2009-08-07
Something malodorous hit the fan:
I do see FF 3.5.2, but it ~can't find it's previous context (complains, but finally finds it), didn't verify the signatures of FF 3.5 and 2 other packages, and has lost flash altogether. 

Gory details:
WARNING: The following packages cannot be authenticated!
  xulrunner-1.9.1 firefox-3.5-branding firefox-3.5
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.1+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb)
  404 Not Found
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/firefox-3.5/firefox-3.5-branding_3.5.1+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/firefox-3.5/firefox-3.5-branding_3.5.1+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb)
  404 Not Found
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/firefox-3.5/firefox-3.5_3.5.1+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/firefox-3.5/firefox-3.5_3.5.1+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb)
  404 Not Found
-----------------------------------------------------------------
[http://www.youtube.com/watch?v=K5JWAEs-ZDE&feature=PlayList&p=5JIU4Ei2RlA](http://www.youtube.com/watch?v=K5JWAEs-ZDE&feature=PlayList&p=5JIU4Ei2RlA)
Shark Week 2009 / Shark After Dark: Great White Attack
Season 22 Episode 4
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

FF -> edit_prefs -> apps(flash) -> SPL and SWF files -> details > 
/home/brianp/.mozilla/plugins/libflashplayer.so
brianp@trex:~$ ls -l /home/brianp/.mozilla/plugins/libflashplayer.so
-rwxr-xr-x 1 brianp users 9560488 2009-08-06 13:18 /home/brianp/.mozilla/plugins/libflashplayer.so

This is the latest player from the tar file from adobe labs:
-rw-r--r-- 1 brianp brianp 3.6M 2009-08-06 23:48 libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
-rwxr-xr-x 1 brianp brianp 9560488 2009-07-17 23:04 libflashplayer.so
This 3 week old date is the date of the file extracted from the zip. 

---------------------------------------------------------------
At startup, I get this error message:
Well, this is embarrassing.
Firefox is having trouble recovering your windows and tabs. This is usually caused by a recently opened web page.
You can try:
    *             Removing one or more tabs that you think may be causing the problem
    *             Starting an entirely new browsing session


Is anybody else seeing these problems? Anybody found a workaround?

Thank you,

    BrianP

---

### Post by brianpatrick on 2009-08-07
But Wait!

After another online_update, I find that in app -> internet I have MineField 3.5 web browser and firefox. MF takes me to a totally unconfigured Shiretoko, Mozilla firefox for Ubu, 3.5.3pre. It has zero bookmarks, no add-ons, and all default settings??? What the heck is this thing?

I backed up my bookmarks from the existing bookmark and restored them into MineField/Shiretoko. Looks good. I only have a few custom settings and half a dozen add-ons. No great loss. 

And, most importantly, the right people have apparently slept with the trolls at adobe and they let the Mozilla gang build the dreaded, buggy, pain in the neck flash viewer into the browser! It actually works. 

Still has a few rough edges, but it is a PRE and it has flash. 

I will give it 1.7 thumbs up!

    BrianP

---

