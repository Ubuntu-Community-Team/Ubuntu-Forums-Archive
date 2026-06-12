---
title: "Evolution Calendars &amp; Palm Zire 31"
date: 2009-07-20
forum: General Help
---

### Post by Hatch3r on 2009-07-20
Hello all,
My evolution client is setup with multiple calendars (you know personal, business etc).
I've also just bought a Palm Zire31, which can have multiple calendars on it.
However, I cannot find a way to sync multiple calendars all in one go.

Does anyone know of a way to sync multiple calendars?

I could, change the calendar sync settings to a different calendar however this would mix the appointments up. So definately not an ideal solution.

Thanks

---

### Post by komputes on 2009-07-20
On the wiki, [ChristopheCharlot]("https://wiki.ubuntu.com/ChristopheCharlot") posted that Evolution has trouble handling multiple calendars with a palm device. 
[https://wiki.ubuntu.com/PDADeviceList](https://wiki.ubuntu.com/PDADeviceList)

I did not find a bug on launchpad.net but I did find this one on gnome.org, the upstream maintainer for evolution and gnome pilot. I would recommend that you comment on this bug to let developers know that you are affected.

[http://bugzilla.gnome.org/show_bug.cgi?id=266609](http://bugzilla.gnome.org/show_bug.cgi?id=266609)

---

### Post by Hatch3r on 2009-07-20
Thanks komputes, I'll post a note up there later.

In the Palm software in Windows (I've not tried it on Wine) you can set different categories for each calendar item and when you Hotsync I believe it remains intact.

I'm wondering if there is a way that this can be harnessed with Evolution.

---

### Post by komputes on 2009-07-20
> **Hatch3r said:**
> 
In the Palm software in Windows (I've not tried it on Wine) you can set different categories for each calendar item and when you Hotsync I believe it remains intact.

I'm wondering if there is a way that this can be harnessed with Evolution.

It would have to be written correctly to support multiple calendars.

I'm pretty sure that you can't run the Windows software in a VM and have it talk to evolution. If anything the VM could use some other mail program to sync the calendars with an online calendar service which then you can pull from using evolution. Wine itself is limited when it comes to USB devices and usually only emulates mouse and keyboard from what I've seen.

---

