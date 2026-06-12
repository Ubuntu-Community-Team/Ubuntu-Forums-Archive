---
title: "Sunbird 1.0b1"
date: 2011-03-08
forum: General Help
---

### Post by Bert Mariën on 2011-03-08
Dear Fellow Sunbird-users:

These are the .deb-files for Sunbird-1.0b1.
I know that many of you did miss these packages, because no longer in the Ubuntu repo's.

I have put these 2 installer packages together using "alien".

Both .deb's (the 64bit and 32bit) worked for me on:

- Ubuntu Gnome 10.10 - 64bit
- Mint Gnome 10 - 32bit

---++---

Download the package (19.4 mb) with both 32 and 64 bit debs at

[http://www.beebab.be/que/sunbird-1.0b1-deb.tar.gz]("http://www.beebab.be/que/sunbird-1.0b1-deb.tar.gz")

---++---

To get it working: unpack and choose the version you need (32bit or 64bit) and install as you normally would.

Now the installation is in /usr/share/sunbird

The file "sunbird.png" still needs to be copied to /usr/share/pixmaps

This can only be done as root!

---++---

Then the only thing left to do, is to create a launcher for Sunbird.

Go to

System > Preferences > Main Menu

and click on "Office".

Click the tab "New Item". A new window opens.

Fill in for "Name": Sunbird

Fill in for "Command": /usr/share/sunbird/sunbird

Click "OK"

---++---

And you're done.

Have fun.

Bert.
[email]marien.bert@telenet.be[/email]

---

### Post by Bert Mariën on 2011-03-08
I also uploaded the same sunbird 1.0b1 installation files for rpm.
So:

Deb
[http://www.beebab.be/que/readme-deb](http://www.beebab.be/que/readme-deb)
[http://www.beebab.be/que/sunbird-1.0b1-deb.tar.gz](http://www.beebab.be/que/sunbird-1.0b1-deb.tar.gz)

Rpm
[http://www.beebab.be/que/readme-rpm](http://www.beebab.be/que/readme-rpm)
[http://www.beebab.be/que/sunbird-1.0b1-rpm.tar.gz](http://www.beebab.be/que/sunbird-1.0b1-rpm.tar.gz)

Cheers.

---

### Post by Bert Mariën on 2011-03-08
Please give me some feed-back?

---

### Post by nifocmike on 2011-04-03
Worked for me!

It should be noted that if you wanted two way access to a Google Calendar you need to add-on "provider_for_google_calendar-0.6b1-sb+tb+sm.xpi" and not the current version.

---

### Post by techunit on 2011-04-03
Thank you. I was under the impression that Sunbird had been killed off, or shoved aside to work on Lightning the calendar extension for Thunderbird.

Is the lightning extension working yet? For 64bit that is.

---

### Post by Pikestaff on 2011-06-01
Worked for me perfectly in KDE; thank you.

In case any future Kubuntu users are curious, the way I added Sunbird to the menu was by right-clicking on the "K" start menu and going to Menu Editor.  You can do it all from there.

---

