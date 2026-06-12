---
title: "Firefox questions..."
date: 2010-02-25
forum: General Help
---

### Post by Gotaro on 2010-02-25
1.  When I added the ubuntu-mozilla-daily repo and updated to FF 3.6, it now says "Namoroka" instead of "Firefox," and the icon broke.  [COLOR="Blue"]How do I get the icon back?[/COLOR]  Did I get the latest version of FF?  Or [COLOR="Blue"]did I go beyond the latest release, since this one says 3.6.2**pre**?[/COLOR]

2.  FF and Thunderbird are both kind of sluggish to open, and both show me a busy spinner cursor for a good 5-10 seconds after opening.  [COLOR="Blue"]Is that normal?[/COLOR]  I would like both to open instantly.  [COLOR="Blue"]Is it possible to keep them pre-loaded in memory?[/COLOR]  I have 4GB of RAM and would like to utilize it :).  [Also, the busy spinner cursor doesn't go away for ~5 seconds even if I close FF/Thunderbird immediately after opening!  What is it doing?!]

Thanks! :D

---

### Post by Ozymandias_117 on 2010-02-25
The new name is Mozilla's codename for that release, you are using basically the "beta" edition instead of the "stable". No, you can't fix the icon.

 Not sure on your other questions, but I would say it isn't normal (At least, mine doesn't do it :P)

---

### Post by wojox on 2010-02-25
If you want you can uninstall the daily builds and install the stable from the ppa's (see my link below) 

As far as speed both TB2 and FF3 do the same as yours. Are you running it on a 64 bit build?

---

### Post by Gotaro on 2010-02-25
> **wojox said:**
> If you want you can uninstall the daily builds and install the stable from the ppa's (see my link below) 

As far as speed both TB2 and FF3 do the same as yours. Are you running it on a 64 bit build?
Yes, I'm on the 64-bit 9.10.  I'd like to try the stable 3.6, but..  I don't really know what I'm doing lol.  So I go to Synaptic and just uncheck FF, apply, remove the daily repo, add the stable one, then re-check FF and apply?

---

### Post by wojox on 2010-02-25
You can do it through Synaptic. You'll need to edit your Sofware Sources to remove the ppa's for it and then run:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox-3.6
```

That'll give you 3.6 Stable for Karmic 64 bit

---

### Post by Gotaro on 2010-02-25
> **wojox said:**
> You can do it through Synaptic. You'll need to edit your Sofware Sources to remove the ppa's for it and then run:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox-3.6
```

That'll give you 3.6 Stable for Karmic 64 bit
Thanks a bunch!  :)  That solved my icon problem, too!  I still get the loading cursor well after the browser has loaded and is ready to use, though.  Do you know if I can keep FF/Thunderbird pre-loaded in memory?

---

### Post by wojox on 2010-02-25
No idea about memory pre-load. I think it takes a little longer to invoke because of gnome support? Glad you got it worked out.

---

### Post by PoHandle on 2010-02-25
I had trouble with Firefox's loading speed too, and most advice I saw was to switch to Swiftfox or Swiftweasel.  I really didn't see this as a solution, but here I am using Swiftweasel. haha

---

