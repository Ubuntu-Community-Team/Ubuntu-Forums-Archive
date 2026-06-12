---
title: "System Update doesn't get Firefox 3.5x ?"
date: 2009-07-23
forum: General Help
---

### Post by UranUtan on 2009-07-23
Hi,

After a run of System Update today. I saw a few Firefox updates. But Firefox version still remains at 3.0.12. Will the 3.5x version be available through System update?

---

### Post by jocko on 2009-07-23
No. Once an ubuntu version is released, new versions of programs are almost never added to the repos (but there is a firefox 3.5 package available, but it will not replace the existing firefox, just install alongside it as an optional package).

---

### Post by Zeikcied on 2009-07-23
You need to install the firefox-3.5 package.  It's separate from the firefox package.

---

### Post by UranUtan on 2009-07-23
> **Zeikcied said:**
> You need to install the firefox-3.5 package.  It's separate from the firefox package.

Does that mean I will have both Firefox 3.0x and 3.5x active? 

If I install Firefox v3.5 manually. How would System Update work at the next run? I guess it will ignore the new FF 3.5 and will skip the update. If so does that mean I will now have to maintain FF 3.5x manually?

---

### Post by Zeikcied on 2009-07-23
> **UranUtan said:**
> Does that mean I will have both Firefox 3.0x and 3.5x active? 

If I install Firefox v3.5 manually. How would System Update work at the next run? I guess it will ignore the new FF 3.5 and will skip the update. If so does that mean I will now have to maintain FF 3.5x manually?

If you install the firefox-3.5 package from Synaptic (or whatever program you use), then System Update will still grab the FF 3.5 updates.  But if you install it manually from the Firefox website, then System Update won't keep it updated.

But yes, if you install the firefox-3.5 package, you'll have both 3.0 and 3.5 on your system.  You're free to uninstall the 3.0 packages, though.

---

### Post by mcduck on 2009-07-23
> **Zeikcied said:**
> You're free to uninstall the 3.0 packages, though.This is not recommended, for the very reason why Firefox 3 And Firefox 3.5 are kept as separate packages; quite many programs depend on the FF3 for HTML rendering, uninstalling it would break all those programs.

---

### Post by UranUtan on 2009-07-23
Oh, forgot to mention that I use Ubuntu 9.04 x64. So if FF 3.0 and 3.5 both exist, if I click on the Firefox icon in the top panel, which one will start? In case it's the old 3.0, what should I do to tell these icon to launch the new FF 3.5?

Is there anyway to tell Ubuntu to replace 3.0 by 3.5 ?

---

### Post by mcduck on 2009-07-23
> **UranUtan said:**
> Oh, forgot to mention that I use Ubuntu 9.04 x64. So if FF 3.0 and 3.5 both exist, if I click on the Firefox icon in the top panel, which one will start? In case it's the old 3.0, what should I do to tell these icon to launch the new FF 3.5?

Is there anyway to tell Ubuntu to replace 3.0 by 3.5 ?

No, you can't replace FF3 with FF3.5. Like I just said, many of the programs depend on the 3.0 version so it must be installed.

If the icon you have in your panel starts FF3.0 now, it will do the same after installing FF3.5. Just remove the icon and add the launcher for FF3.5 to your panel instead (it's as easy as simply right-clicking the program in the menu and selecting "Add to panel").

---

### Post by Zeikcied on 2009-07-23
> **mcduck said:**
> This is not recommended, for the very reason why Firefox 3 And Firefox 3.5 are kept as separate packages; quite many programs depend on the FF3 for HTML rendering, uninstalling it would break all those programs.

Oh...  I didn't know that.

Even on Kubuntu?  KDE apps should be using Konqueror.  I don't use a lot of GTK apps, other than Evolution.

---

### Post by Trebaruna on 2009-07-23
If it's just that one icon you care about, go into its properties and change the command from firefox to firefox-3.5

Of course you could do this with every icon, but it gets a little tedious. Or, just replace the launcher with the firefox-3.5 one. They look different (3.5 has a blue globe thingy) so you should be okay.

---

### Post by mcduck on 2009-07-23
> **Zeikcied said:**
> Oh...  I didn't know that.

Even on Kubuntu?  KDE apps should be using Konqueror.  I don't use a lot of GTK apps, other than Evolution.

Should be safe in Kubuntu, although if you try it be sure to check the packages that are uninstalled with it to make sure they don't include anything important.

---

### Post by dcstar on 2009-07-23
> **mcduck said:**
> This is not recommended, for the very reason why Firefox 3 And Firefox 3.5 are kept as separate packages; quite many programs depend on the FF3 for HTML rendering, uninstalling it would break all those programs.

FF *used* to be tied tightly into Ubuntu for rendering, but after many issues with people wanting to remove it I thought that the developers had moved away from this undesirable situation.

I have both FF 3 & 3.5 installed, they seem to co-exist reasonably well.

---

### Post by UranUtan on 2009-07-24
Found an easy alternative FF 3.5 also exist in Ubuntu repository

[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

When done on Ubuntu 9.04 x64, It adds a new menu item "Minefield 3.5" in the Application / Internet menu.

---

