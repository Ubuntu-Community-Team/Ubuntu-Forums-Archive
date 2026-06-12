---
title: "Ubuntu Software Center not listing any packages"
date: 2011-06-11
forum: General Help
---

### Post by airspoon on 2011-06-11
For some reason, the Ubuntu Software Center seems to not be working on my 11.04. It goes to the "get software" section and lists the various categories, however upon clicking those categories, it has the little pin-wheel as if its loading, though it stays on that pin-wheel indefinitely. The same thing for when I use the search box. It is also doing the same thing for the "installed software" section. In addition, it there is no sign of the additional repositories that I have added either?

I have a network connection, as I'm using this computer to post this. 

Is this something broken on my end and how can I go about fixing this? Thanks.

Edit to add: It is however showing the "History" section and if I click on one of the recommendations, it will show those, but that is about it.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **airspoon said:**
> For some reason, the Ubuntu Software Center seems to not be working on my 11.04. It goes to the "get software" section and lists the various categories, however upon clicking those categories, it has the little pin-wheel as if its loading, though it stays on that pin-wheel indefinitely. The same thing for when I use the search box. It is also doing the same thing for the "installed software" section. In addition, it there is no sign of the additional repositories that I have added either?

I have a network connection, as I'm using this computer to post this. 

Is this something broken on my end and how can I go about fixing this? Thanks.

Try using Synaptic Package Manager instead, that way you have a more transparent process to observe and report where it is hanging..

---

### Post by airspoon on 2011-06-11
I use Synaptic too, but I like using the Software Center to see the various reviews and different apps. Also, I'm worried as to why this is broken and to know if anything else is broken or affected.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **airspoon said:**
> I use Synaptic too, but I like using the Software Center to see the various reviews and different apps. Also, I'm worried as to why this is broken and to know if anything else is broken or affected.

Until you try it on Synaptic it could be anything until you report back the results because Synaptic will actually show you what is wrong.  Software Center is just a fancy GUI that does the same job without telling you what it is doing, or what is wrong.  :)

---

### Post by airspoon on 2011-06-11
Thanks, but how do I see what's wrong with the Software Center from Synaptic? Is there an option or something? Synaptic seems to be working fine.

The Ubuntu Software Center isn't showing anything now. It's just a blank window with a title-bar (that says "Ubuntu Software Center"), that's it.

---

### Post by airspoon on 2011-06-11
Okay, the "software center" in Synaptic, has an exclamation point, instead of a green radio-button and the "changelog" says:

```

software-center (4.0.3) natty-proposed; urgency=low

  [ Gary Lasker ]
  * softwarecenter/app.py:
    - expand the "Get Software" item in the viewswitcher by default
      so that its subitems are always visible and available
      (LP: #774590)
  * softwarecenter/view/availablepane.py,
    softwarecenter/view/catview_gtk.py:
    - jumpstart Featured and What's New carousel transitions
      on launch (LP: #786403) 

```

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **airspoon said:**
> Thanks, but how do I see what's wrong with the Software Center from Synaptic? Is there an option or something? Synaptic seems to be working fine.

The Ubuntu Software Center isn't showing anything now. It's just a blank window with a title-bar (that says "Ubuntu Software Center"), that's it.

So basically from what you are saying is that there is nothing wrong going on in Synaptic, however you having trouble using Software Center to download and install software. 

Try uninstalling the software center in Synaptic, by right clicking on it and "completely" uninstalling your software center.    Then clean out your system with good old bleachbit.

sudo apt-get install bleachbit
sudo bleachbit

Careful not to have it eat your bookmarks and passwords.. 

Then do a reboot when it is done cleaning out everything..

Then go back to Synaptic and reinstall your software center, and see if the problem persists.  That should do it. :)

---

### Post by airspoon on 2011-06-11
I'm not sure if you saw my second post, but this is what Synaptic says about the Software Center. Do you know what would break it? Does the Changelog give any valuable information? It surely couldn't break on its own, could it? If it's something I did or installed, I don't want to make the same mistake again. Thanks.

> **airspoon said:**
> Okay, the "software center" in Synaptic, has an exclamation point, instead of a green radio-button and the "changelog" says:

```

software-center (4.0.3) natty-proposed; urgency=low

  [ Gary Lasker ]
  * softwarecenter/app.py:
    - expand the "Get Software" item in the viewswitcher by default
      so that its subitems are always visible and available
      (LP: #774590)
  * softwarecenter/view/availablepane.py,
    softwarecenter/view/catview_gtk.py:
    - jumpstart Featured and What's New carousel transitions
      on launch (LP: #786403) 

```

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **airspoon said:**
> I'm not sure if you saw my second post, but this is what Synaptic says about the Software Center. Do you know what would break it? Does the Changelog give any valuable information? It surely couldn't break on its own, could it? If it's something I did or installed, I don't want to make the same mistake again. Thanks.

Regardless, uninstall software center with the instructions above.  Use bleachbit. Clean that out good.  Reboot.  Use synaptic to reinstall it.

It's just the order of operation to attempt a decent fix of this issue. 

Something is kinda funky about your system I think..  It's not just the software center. But that can wait for the moment.

---

### Post by airspoon on 2011-06-11
Bleachbit? What's that and how do I get it? Why would you think something is funky with my system? Other than the problem I'm having with the nvidia driver (which, I'm reading that a lot of other people are also having), this is the only thing that has "broken" on me. Lol, now I'm a little paranoid.

I'll try to reinstall the software center.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **airspoon said:**
> Bleachbit? What's that and how do I get it? Why would you think something is funky with my system? Other than the problem I'm having with the nvidia driver (which, I'm reading that a lot of other people are also having), this is the only thing that has "broken" on me. Lol, now I'm a little paranoid.

I'll try to reinstall the software center.

Don't reinstall software center until you have run bleachbit first. 

Bleachbit works like this:

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

To install it go to your terminal and type:
```

sudo apt-get install bleachbit

```To run it from terminal type:
```

sudo bleachbit

```I use it all the time.
Just be careful that it doesn't delete your bookmarks and your passwords.. Other than that you can select most of the other options without worry.
 :)

When done, go back to Synpatic, search for software center, and right click on it and select install.

Remember this method to fix future problems like this as well. Usually works too.

A computer is only as good as a clean system.

---

### Post by Andrew.Z on 2011-06-12
> **linuxinstalledfromhdd said:**
> 
Just be careful that it doesn't delete your bookmarks and your passwords.. Other than that you can select most of the other options without worry.


The bookmarks used to be erased by the option Firefox - Places (which also deleted URL history), but this feature was removed in BleachBit version 0.8.5.

Other than that, most users can avoid wiping free disk space and memory.

---

### Post by airspoon on 2011-06-12
Thanks. I installed "BleachBit", though just when I was about to use it, I rebooted and upon restart, "Software Center" seems to have fixed itself, as it is now working, with no change from me.

I'm wondering if it was just something wrong with the X-server and by rebooting, it fixed it?


Anyway, thanks.

---

### Post by VanR on 2011-06-12
If it's any consolation to you my Software Center has been acting up also.

---

### Post by madmax75 on 2011-07-30
Here too.

I'm on 10.10 and the Software Center gives me package categories, but all of these are empty, no entries whatsoever. The package suggestions have just a big grey question mark on them.

Synaptic works all right, though.

---

