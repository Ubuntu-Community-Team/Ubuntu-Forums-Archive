---
title: "Wierd box keeps showing up in corner of screen"
date: 2010-01-26
forum: General Help
---

### Post by _blink_ on 2010-01-26
Hello,
 I recently installed xubuntu on my computer everything was going fine but every once and awhile this happens to my computer
 [URL="http://i982.photobucket.com/albums/ae308/blink1337/Screenshot-1.png"][IMG]http://i982.photobucket.com/albums/ae308/blink1337/Screenshot-1.png[/IMG]
[/URL]
 When that little box shows there is no way to take it off. It just randomly shows up and disappears. It is very annoying and is pissing me off. Does anyone know what this is and how to make it stop showing up?
 Thanks!

---

### Post by t4thfavor on 2010-01-26
Stop the notify-osd service on your PC, and tell me if it goes away. This looks like your graphics setup has trouble with the transparency.

---

### Post by _blink_ on 2010-01-26
Yeah that made it go away. Is there a permanent fix for this?

---

### Post by t4thfavor on 2010-01-26
I am sure there is, but it's not in the system preferences startup applications, so I guess someone else who knows how to shut off the notify-osd will have to answer.

Im not sure what removing it would do. but if your feeling brave
sudo apt-get remove notify-osd

Or you could see if there are settings that will enable it to work with your hardware. I know it has a bunch of transparency stuff that could not work correctly on underpowered/old/very new hardware.

there are instructions for disabling it here:
[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

---

### Post by efflandt on 2010-01-26
I imagine you may have the same trouble trying to view System Monitor (since I did on an old PC with that symptom).  I wish I knew what to search for to find the post where someone gave a possible solution (it might have been something about disabling direct rendering due to insufficient video RAM 32 MB or less).

Since it was an old ATI card, I think I resolved it by installing xorg-driver-fglrx.  I put Qimo for kids on it (Ubuntu 8.10 based) and gave it to my niece for her twin boys.

---

