---
title: "Cannot open 'Places/Network' from Main Menu"
date: 2011-10-13
forum: General Help
---

### Post by huggs on 2011-10-13
So, I have had my Ubuntu machine connected to my Windows WORKGROUP for some time now, and have always been able to go to Main Menu/Places/Network/  and from there the normal window would appear with my windows network and all the connected computers in it.

Today, when I went to Main Menu/Places/Network, instead of the window appearing as usual, I got an error message that says 'Could not display "network:///". Nautilus cannot handle "network" locations.'

To the besta of my knowledge I have not changed any settings or anything within Nautilus or my network settings or anything like that. Why all of a sudden am I having this problem, and how do I fix it? I have searched, but have only found issues where people have tried to create desktop launchers to specific network locations, etc. not anything like my proble.

Thanks for reading, and for any help given;)

---

### Post by Morbius1 on 2011-10-13
According to my notes ( I keep notes because I'm getting old and feeble minded ;) ) you will get that error is you have a package missing.

Try this and see if it fixes things:
```
sudo apt-get install gvfs-backends
```

---

### Post by huggs on 2011-10-13
That solved it. Turns out that removing all my bluetooth stuff (I don't use blutooth on my computer, thought I'd free up some space) removed something that Nautilus needed to handle my network places.

Thanks for your help:D:D

---

