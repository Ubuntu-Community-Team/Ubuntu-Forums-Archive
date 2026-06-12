---
title: "Dv4000 card reader"
date: 2006-03-21
forum: General Help
---

### Post by matthewinuk on 2006-03-21
I wondered whether anyone had any knowledge on how to get the built in card reader for my Hp Dv4000 laptop working. Ive already searched far and wide to no avail. Many thanks to the whole community for various other probs which I have been able to sort.  :)

---

### Post by rado_london on 2006-03-21
Well I have the same laptop and the card reader doenst work. I read somewhere that there are no modules for the kernel which means that this device is not supported.

---

### Post by matthewinuk on 2006-03-21
is there not some way one can install the drivers which come with the cd u get for recovery?

---

### Post by rado_london on 2006-03-22
Well they are windows drivers right?
So I think is too complicated and risky. I suggest you to keep dual booting.

---

### Post by Boatswain on 2006-04-30
I also have had no luck with getting the car reader working, which is a big bummer--it's pretty much the only thing I'm keeping Windows on the machine for.  I've also got the no-LEDs-for-wireless-or-mute thing, but that doesn't bother me too much.  You guys have any other issues with the machine?

Oh, and anyone know how to add music files to the hp quickplay playlists?  From what I can tell, it only looks in the My Music folder in XP for files, and won't look in shortcut folders.

---

### Post by watstein on 2007-04-21
Acutally there is a fix in Edgy and it also works in Fiesty for the wireless light.
Go to the terminal and type.

sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1

If that works then
sudo echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200

That is all, very easy fix.

Also does anyone have a problem getting quickplay to work with Ubuntu. I am running Feisty and Vista and XP and I made a 212mb partition for quickplay and I put in the cd but it will not alow me to install it. Any help would be appriciated.

---

### Post by rado_london on 2007-04-23
> **watstein said:**
> Acutally there is a fix in Edgy and it also works in Fiesty for the wireless light.
Go to the terminal and type.

sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1

If that works then
sudo echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200

That is all, very easy fix.

Also does anyone have a problem getting quickplay to work with Ubuntu. I am running Feisty and Vista and XP and I made a 212mb partition for quickplay and I put in the cd but it will not alow me to install it. Any help would be appriciated.

Works as a charm man!!! The button switches off the wireless. Coool finally:)

---

