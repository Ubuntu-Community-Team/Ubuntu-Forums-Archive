---
title: "Is obex-data-server installed by default?"
date: 2009-11-06
forum: General Help
---

### Post by szim90 on 2009-11-06
Hello. I had a quick question about the obex-data-server package. Is it normally installed by default? I've been working on getting bluetooth file transfer working (without using the gnome-user-share package, as it depends on apache, which I don't want to install on my desktop), and now I'd like to revert my system to how it was before I began installing extra packages, and I can't remember if I installed obex-data-server manually, or if it was part of the system.

Thanks for any help in this matter.

-Sean

---

### Post by BQAggie2006 on 2009-11-06
I have a very basic install of 9.10 on a VM with very little modification (all I have done is replaced Empathy with Pidgin, Evolution with Thunderbird, and Tomboy with gnote), and obex shows as being installed in Synaptic, both server and client.

---

### Post by winotree on 2009-11-06
I believe that you've received your reply, but thought that the Karmic Manifest [http://cdimage.ubuntulinux.org/daily-live/current/karmic-desktop-i386.manifest](http://cdimage.ubuntulinux.org/daily-live/current/karmic-desktop-i386.manifest) may be useful or interesting.

Hmm -- re-reading my post I realize that the words *Karmic Manifest *seem unduly ominous.  :shock:  ;-)

---

### Post by fragos on 2009-11-07
obex-data-server isn't installed by default and isn't in the basic Ubuntu repositories any more. I installed blueman which replaces the Gnome Bluetooth Manager and does install that package. Bluetooth transfers now work in both directions.

---

### Post by winotree on 2009-11-07
Hmm -- would you take a look at that manifest **fragos** as obex-data-server 0.4.4-2build1 is listed -- I believed that it showed the default download, that's why I posted it.  If it's not then how are we to understand that?

---

### Post by fragos on 2009-11-07
Perhaps mine was replaced by a different version from the Blueman PPA because now it's the only one I can see. obex-data-server hasn't been installed by default in the past and it is required for Ubuntu to receive files over Bluetooth.

---

