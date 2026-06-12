---
title: "Thunderbird Mail Notification"
date: 2009-08-12
forum: General Help
---

### Post by t-vercetti on 2009-08-12
hey guys!

i've read many threads in this forum dealing with similar problems, but i couldn't get my problem solved so far.
first off, i'm using linux mint 7 (based on ubuntu 9.04).

problem:
thunderbird does not show the mail notification icon in the tray and plays no sound.

it does however show the spash screen indicating sender and subject which disappears after a couple seconds. after that though i'm left without the tray icon (mail symbol). so if i'm not looking at the screen the moment a new mail pops in then i won't be able to see this from the gnome panel (i have to maximize thunderbird and see for myself).

so far i tried different thunderbird addons but none of them gave me the tray icon:
mailbox_alert-0.13.1-tb.xpi
libnotify_popups-0.1.2-fx+tb-linux.xpi


this one does show an icon but disables the thunderbird mail notification splash screen:
mozTrayBiff-1.2.3-tb2.0.0.0.xpi


- i have libnotify-bin installed
- i have thunderbird-traybiff installed

- the settings in thunderbird are activated (mail notification and sound)
- i have the indicator applet and notification area added on the gnome panel
- preffered mail apllication is set to thunderbird


summary:
no sound at mail income and no tray icon after mail income
mail notification splash screen working


please help!


thanx,
vercetti.

---

### Post by longtom on 2009-08-12
Same problem here with 8.04 (sorry for latching on).  I am using 2 e-mail accounts - one in evolution (which notifies just fine), and one with thunderbird, which displays exactly the same behaviour as the one described by the OP.

---

### Post by t-vercetti on 2009-08-12
@ longtom:

at least got one thing solved: in thunderbird preferences, change the sound-file for notifcation.
for example: /usr/share/sounds/alsa/Noise.wav
this means that the default thunderbird sound does not work, but others will (maybe the default one works too if you browse for it and enter it manually just like the above method).

still no idea though how to make the notification icon appear...


greetz,
vercetti.

---

### Post by longtom on 2009-08-12
> **t-vercetti said:**
> @ longtom:

at least got one thing solved: in thunderbird preferences, change the sound-file for notifcation.
for example: /usr/share/sounds/alsa/Noise.wav
this means that the default thunderbird sound does not work, but others will (maybe the default one works too if you browse for it and enter it manually just like the above method).

still no idea though how to make the notification icon appear...


greetz,
vercetti.

Thank you.  Since my sound is switched off for most of the time, this is not too critical to me.  However, the notification would be.

Thanks for staying on it....

---

### Post by valadil on 2009-10-16
I use Mailbox_alert and New Mail Icon.  The first flashes a message and runs a script.  The second adds an icon to my tray.  In case you're interested, the script mutes my sound, beeps, and unmutes (since I can't hear the computer beep if I have my headphones on).

---

### Post by fab.head on 2009-10-17
I'm currently using Firetray which also works with Thunderbird 3/Shredder (New Mail Icon only works with Thunderbird 2).

[http://code.google.com/p/firetray/downloads/list]("http://code.google.com/p/firetray/downloads/list")

---

