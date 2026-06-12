---
title: "Lost the menu"
date: 2009-12-09
forum: General Help
---

### Post by colonel_panic on 2009-12-09
Hello

I've been playing with Ubuntu Netbook Remix, after a long relationship with Puppy Linux.

I accidentally switched my computer off as it was updating, and now I've lost the menu.

I don't know my way around Ubuntu yet; what should I be looking for to get it all back?

---

### Post by akakingess on 2009-12-09
Which menu are you talking about, did you lose the whole top bar, or just what "menu" did you lose, and if it is just a menu, you should be able to right-click on the top bar and choose to "Add To Panel" and select whatever menu you lost through the list that is available. Hope this helps in some sort of way..

---

### Post by audiomick on 2009-12-09
_**possibly**_, you might need to de-install and then re-install the GUI.

---

### Post by radgalez on 2009-12-09
same problem.
after installing updates last night right after reboot all I have is plain desktop with bar on the top.
whole menu (favourites, internet, etc.) is gone and I have no idea how to restore it.
thanks for all sugestions

---

### Post by akakingess on 2009-12-09
Like I stated earlier, you "could" right-click and add everything one by one, but if you have lost everything, than audiomick's suggestion might be a better route, since it sounds like you lost everything..

---

### Post by colonel_panic on 2009-12-09
> **audiomick said:**
> _**possibly**_, you might need to de-install and then re-install the GUI.

That sounds like the easiest way forward.

How would I go about doing such a thing?

---

### Post by akakingess on 2009-12-09
I am definitely not the expert to answer that question, so hopefully audiomick will chime back in and let y'all know how best to do that whole uninstall/reinstall with the GUI, although I don't know, it could be as simple as trashing your xorg.conf (after backing up first of course by just renaming current one to name.back) and letting it reconfigure upon reboot. That is just a suggestion and probably should not be acted upon unless approved by someone with some more experience. It almost makes me wish I had had more problems with Ubuntu to answer these questions, but I have had a relatively smooth ride thus far (knock on wood)..

---

### Post by audiomick on 2009-12-09
hallo again.
Trashing the x-org is not likely to do the trick. With the standard ubuntu, there is a meta-package called ubuntu-desktop or something similat. I haven't had any experience at all with the netbook re-mix, so I have no idea what it is called there.
I am also more than a bit shaky on the commands to remove and re-install the desktop, so I don't want to suggest anything.
Hopefully someone with a bit more of an idea will answer.:-?

---

### Post by paradigm2 on 2009-12-09
> **audiomick said:**
> hallo again.
Trashing the x-org is not likely to do the trick. With the standard ubuntu, there is a meta-package called ubuntu-desktop or something similat. I haven't had any experience at all with the netbook re-mix, so I have no idea what it is called there.
I am also more than a bit shaky on the commands to remove and re-install the desktop, so I don't want to suggest anything.
Hopefully someone with a bit more of an idea will answer.:-?

I'm looking around now in my UNR install....  I see....

netbook-launcher

which might perhaps be what he needs to install in synaptic or using apt-get?

---

