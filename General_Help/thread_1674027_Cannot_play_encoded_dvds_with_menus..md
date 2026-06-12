---
title: "Cannot play encoded dvds with menus."
date: 2011-01-23
forum: General Help
---

### Post by alittlemorered on 2011-01-23
Hi There

I cannot play encoded dvds, or access the menu options of dvds with menus.

1. My dvd drive appears to work fine. It can play anything else i put in it.
2. I have enabled Restricted Formats and Medibuntu. Both are fine.
3. I have installed libdvdcss2 and libdvdread4. Both are fine.
4. I have installed VLC. It can see the tracks on the disk but cycles through them without playing anything.
5. I have Gnome MPlayer. It can see the tracks on the disk, but not open the menu screen. It can even play tracks on the disk, but only from 25 minutes into the track and onwards. (?!?) The image and audio work fine so it can obviously read the data, but it can't manage the menu and finding the first 25 minutes of each track.
6. Everything is up to date. Nothing appears broken.

I have been using Ubuntu for 3 years now and have challenged many Windows friends to change. Some have. But without a dvd player... That's going to be like selling a three-wheeled car.

Please assist with how to play dvds.

Kind regards,
J.

---

### Post by andymorton on 2011-01-23
Enter the following in to the terminal  - 

sudo /usr/share/doc/libdvdread4/install-css.sh

andy

---

### Post by alittlemorered on 2011-01-24
Hi Andy

Thanks for the reply.
I entered the line. Installed with no errors. No difference, i still can't play the dvd.

J.

---

