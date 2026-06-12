---
title: "opening dvd player on laptop"
date: 2012-07-03
forum: General Help
---

### Post by tobythedog on 2012-07-03
hi i have put vlc on my laptop running lubuntu, i cannot work out how to open the dvd player, have tried pressing the button but this only works when its booting up,cannot find eject on vlc , tried the disc utility when i click eject on this it comes up with error /dev/sr0 is mounted.any help on how to eject dvds would be very good.

---

### Post by matt_symes on 2012-07-03
Hi

> **tobythedog said:**
> hi i have put vlc on my laptop running lubuntu, i cannot work out how to open the dvd player, have tried pressing the button but this only works when its booting up,cannot find eject on vlc , tried the disc utility when i click eject on this it comes up with error /dev/sr0 is mounted.any help on how to eject dvds would be very good.

First try this.

Open a terminal and type

```
eject
```

Does that open the dvd drive ?

If that throws an error try

```
eject /dev/sr0
```

Post back on efficacy.

Kind regards

---

### Post by tobythedog on 2012-07-03
hi yes eject on terminal does open it.

---

### Post by matt_symes on 2012-07-03
Hi

> **tobythedog said:**
> hi yes eject on terminal does open it.

I'm not sure why it's not ejecting when you press the button but for a work around to start with, let's create a simple script to eject the dvd player.

From the terminal type this (or copy and paste into the terminal).

```
echo "eject /dev/sr0" > ~/Desktop/eject_dvd && chmod 755 ~/Desktop/eject_dvd
```

That should make a file on your desktop called eject_dvd. double clicking on it should eject the dvd.

Try it out. Does it work as expected ?

Kind regards

---

### Post by tobythedog on 2012-07-04
hi thank you for the help this does put icon on desktop and it works ,
i have noticed the button on the dvd drive will eject the dvd when is not one in the drive , it wont when one is in it ,i think the problem could be the discs are mounted once they are installed , i dont know how to unmount them before ejecting them.
also is there not some way of ejecting them from the vlc media player

---

### Post by matt_symes on 2012-07-06
Hi

> **tobythedog said:**
> hi thank you for the help this does put icon on desktop and it works ,
i have noticed the button on the dvd drive will eject the dvd when is not one in the drive , it wont when one is in it ,i think the problem could be the discs are mounted once they are installed , i dont know how to unmount them before ejecting them.

You do not say which version of *buntu you're using but assuming it's Ubuntu  you should be able to unmont them from Nautilus.

If you look in the left hand pane, you should see the DVD/CD entry with an arrow next to it. Click on the arrow to unmount it.

Another option, assuming you are using unity, is to create a launcher that calls that script to eject the CD/DVD.

From the command line you should be able to use

```
sudo umount /dev/sr0
```> also is there not some way of ejecting them from the vlc media playerNot that i'm aware of but i use mplayer. Others will correct me if i am wrong here.

Kind regards

---

