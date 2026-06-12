---
title: "Help, what did i do ?"
date: 2010-05-29
forum: General Help
---

### Post by gpgp on 2010-05-29
I was trying to play an iso file in VLC player. somehow i seem to have changed some associations. now when i go to the "Places" tab and select any folder under it it tries to open the location with vlc player. and does a decent job of it but with a lot of errors!
 
If i open nautalis from terminal it uses the file browser correctly to display the same locations and opens things with the correct programs. 

Any help or hint in the right direction is most appreciated.

Thank you

gpgp

---

### Post by gpgp on 2010-05-29
[Edit by admin: Threads merged]

I was trying to play an iso file in VLC player. somehow i seem to have changed some associations.  now when i go to the "Places" tab and select any folder under it it tries to open the location with vlc player. any folder above "computer" and does a decent job of it but with a lot of errors!
Other locations, ( computer, network, external drives )open in nautalis
Also if i try to browse my wine "C" drive it opens with vlc player.

If i open nautalis from terminal it uses the file browser correctly to display the same locations and opens things with the correct programs. 

Any help or hint in the right direction is most appreciated.

This is ubuntu lucid.

Thank you

gpgp

---

### Post by dino99 on 2010-05-29
goto synaptic , search & select "vlc" package, right click on it to remove/purge it, then reinstall "vlc" package

sudo dpkg --configure -a

---

### Post by gpgp on 2010-05-29
Thank you

It had occurred to me to do that, i wasn't certain if the associations would be restored.

Well that worked quite easily.

Thank you very much 

gpgp

---

### Post by gpgp on 2010-05-29
okay after reinstalling vlc the problem has returned. I think i must need to remove some more like vlc-data or some other packages.

gpgp

---

### Post by gpgp on 2010-05-29
a complete removal of vlc still has the same problem after reinstallation. 
i think it is a gnome setting ?

gpgp

---

### Post by tomseivert on 2010-05-29
Please help!  I tried to update from 9.10 to 10.04 a few days ago.  Everything seemed to work fine.  When I got to the end of the process and was asked to reboot, the splash screen would display for only about a second and then the computer would hang with a grey screen and no further disk activity.  I rebooted multiple times with the same result.

I then downloaded the install to a CD and tried it from that.  Same result.  In desperation to retrieve my laptop from boat anchor status, I reinstalled 9.10 from a CD -- only to find to my horror that all files, email and Firefox bookmarks were gone.

I'd like to keep up to date on Ubuntu (lest support go away in time), but I'm now very leery to try reinstalling without more guidance.  At this point it appears I don't have much to lose, but if it is still possible to reacquire the pointers to all my files, etc. -- that would be great.

Any guidance?

Tom Seivert

---

### Post by Andrew_Grant on 2010-05-29
[http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/](http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/)
this link should help.

Andrew

---

### Post by gpgp on 2010-05-29
Maybe start your own thread for help ?
Sorry i cant help you, and this thread will probably not help you even if it is  solved.

gpgp

---

### Post by gpgp on 2010-05-29
Thanks for that link Andrew, but i am afraid it does not help. when you look at the properties of a folder there is no open with tab.

It is only from the "places" tab and browsing the wine "C" drive. If i open nautalis from a terminal the same locations open with nautalis. only if i select them from the menu "places" and select a place , like photos or music does it open with vlc player. removing vlc does fix but when i reinstall the problem returns. 

I think it is a gnome setting but i have no idea where. its kind of catch 22 i cant change the opens with from the places drop down and it behaves correctly in nautalis when opened from terminal.

thanks, any other ideas ??

gpgp

---

