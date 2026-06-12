---
title: "Do not want wpa_supplicant enabled by default"
date: 2009-11-27
forum: General Help
---

### Post by computx on 2009-11-27
I have a fairly recent install of karmic on a desktop PC. It seems to me there is a lot of unneccesary things enabled by default. For example wpa_supplicant is running and I don't even have a wifi card in this desktop. Can anyone tell me how to disable this as I see no /etc/default/wpa_supplicant to edit.

Also why on earth is this enabled by default on a wifi-less PC? 
277 processes running seems a bit insane to me.

---

### Post by dcstar on 2009-11-27
> **computx said:**
> I have a fairly recent install of karmic on a desktop PC. It seems to me there is a lot of unneccesary things enabled by default. For example wpa_supplicant is running and I don't even have a wifi card in this desktop. Can anyone tell me how to disable this as I see no /etc/default/wpa_supplicant to edit.

Also why on earth is this enabled by default on a wifi-less PC? 
277 processes running seems a bit insane to me.

You are complaining about a process that takes 2MiB of RAM and is essentially dormant (which means it will be moved to swap if required)?

I would imagine that it exists because it **might** be required, and because the resources it takes are so trivial, it is easier to leave it there.

---

### Post by computx on 2009-11-28
> **dcstar said:**
> You are complaining about a process that takes 2MiB of RAM and is essentially dormant (which means it will be moved to swap if required)?

I would imagine that it exists because it **might** be required, and because the resources it takes are so trivial, it is easier to leave it there.
Yes I am complaining. By itself I agree that is a trivial amount of ram and most likely no problem. but 277 different processes ruunning multiplies that number to something I feel is non trivial. If it was a laptop or even a desktop with a wifi card then yes I agree it might be needed and would be ok to load at startup. But on a desktop with no wifi card installed it seems a bit excessive. I guess I expect a linux distro to be making better choices about non trivial usage of my resources than Windows would.

---

### Post by falconindy on 2009-11-28
If you think this is troublesome, wait till you try and remove Firefox because you're more interested in using Chrome, or Uzbl, or Epiphany...

---

### Post by dcstar on 2009-11-29
> **computx said:**
> Yes I am complaining. By itself I agree that is a trivial amount of ram and most likely no problem. but 277 different processes ruunning multiplies that number to something I feel is non trivial. If it was a laptop or even a desktop with a wifi card then yes I agree it might be needed and would be ok to load at startup. But on a desktop with no wifi card installed it seems a bit excessive. I guess I expect a linux distro to be making better choices about non trivial usage of my resources than Windows would.

Your specific complaint **is** trivial, if you want to come up with examples of any other "unnecessary" processes then they will be examined on their merits.

---

### Post by mediaexpert on 2010-07-27
> **computx said:**
>  It seems to me there is a lot of unneccesary things enabled by default. For example wpa_supplicant is running and I don't even have a wifi card in this desktop.

Same problem &, please, stop saying it's a trivial problem!

---

