---
title: "putting Nautilus back to default state"
date: 2011-09-16
forum: General Help
---

### Post by rmcellig on 2011-09-16
I installed Nautilus Elementary and now Nautilus doesn't look quite the same as when I originally installed Ubuntu 11.04. How can I put Nautilus back to it's default state the way it was when I first installed Nautilus. I am running in Ubuntu Classic mode.

---

### Post by dcstar on 2011-09-17
> **rmcellig said:**
> I installed Nautilus Elementary and now Nautilus doesn't look quite the same as when I originally installed Ubuntu 11.04. How can I put Nautilus back to it's default state the way it was when I first installed Nautilus. I am running in Ubuntu Classic mode.

In your home folder there is a (hidden) config folder that contains all of this stuff AFAIK, you may want to rename it and it should be created from scratch when you next start Nautilus:

~.gconf/apps/nautilus

Let us know if it works.

---

### Post by rmcellig on 2011-09-17
I just wanted to make sure I am renaming the right file or folder. Which folder should I be renaming?

---

### Post by Krytarik on 2011-09-17
Forget about the previous suggestion. Sorry, dcstar!

Instead run these commands to revert Nautilus to the official version:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```Then restart Nautilus:
```
killall nautilus
```Greetings.

---

### Post by rmcellig on 2011-09-17
I ran the three commands and then restarted my laptop. It seems that there are still items missing from menus. Attached is an example. I don't see the option that allows you to split a window. How can I get that back and how can I tell that my nautilus is back to the default state?

Thanks so much!!!

---

### Post by Krytarik on 2011-09-17
> **rmcellig said:**
> How can I get that back and how can I tell that my nautilus is back to the default state?
Check the version number via "Help -> About".

[LIST]
[*]the official Nautilus of Natty would be: 2.32.2.1
[*]and Nautilus Elementary would be: 2.32.2.2
[/LIST]
And yes, there are indeed some menu items missing. Try resetting Nautilus' settings by running:
```
gconftool-2 --recursive-unset /apps/nautilus
```
This does basically the same as *dcstar* suggested earlier.

---

### Post by rmcellig on 2011-09-17
This is what I am running:

Nautilus 2.32.2.1

I will post back if I was successful after applying the command.

---

### Post by rmcellig on 2011-09-17
It didn't seem to work. I invoked the command and then restarted my laptop. View menu still looks the same.

---

### Post by Krytarik on 2011-09-17
> **rmcellig said:**
> It didn't seem to work. I invoked the command and then restarted my laptop. View menu still looks the same.
Not really surprising, actually. However, I'm not sure if the menu in Natty is the same as in Lucid, my system, with which I have compared your screenshot. Anyone else with Natty, please tell us how it looks by default!?

---

### Post by rmcellig on 2011-09-17
I have 11.04 running 11.04 as well and the menu looks different than 11.04 running on my other laptop. Screenshot to follow....

---

### Post by rmcellig on 2011-09-17
Here is the menu on my other laptop.

---

### Post by Krytarik on 2011-09-17
While I still can't say why there are apparently differences in the menus, I have two questions:

[LIST]
[*]Were both screenshots taken from the menu in a usual Nautilus window, like launched via the Places menu, for example?
[*]Why does the second screenshot look such strange? Meaning, the "View" menu item isn't highlighted while the menu is open, and the toolbar overlays the upper part of the menu. Looks like fabricated, actually.
[/LIST]

---

### Post by rmcellig on 2011-09-17
Yes. I opened the Home folder from places and because I do not know how to take a screen shot of a pull down menu. I took a screen shot of the open Home window with the menu down and then opened that picture up and then took a screenshot of the pull down menu zoomed in so that you could see it.

---

### Post by Krytarik on 2011-09-17
Meh, just try reinstalling "nautilus" and "nautilus-data", and also make sure the "ubuntu-desktop" meta-package is installed and not broken, maybe it helps:
```
sudo apt-get install --reinstall nautilus nautilus-data ubuntu-desktop
```

---

### Post by rmcellig on 2011-09-17
Thanks!!

Looks fine now. Actually it looks like I am running Ubuntu Elementary because now I see Embed Terminal and Clutterflow under the view menu of my home folder.

I jst want to take this time to thank all of you who have helped me out. I am a newbie and long time Mac user and I have to say that this forum continually blows me away with the wealth of knowledge regarding Linux. Thanks again!!

---

