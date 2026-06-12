---
title: "Ubuntu to windowsXP"
date: 2009-10-15
forum: General Help
---

### Post by aquarius79 on 2009-10-15
hello! i want to know how to uninstall Ubuntu and install Windows XP. No problem with Ubuntu just more familiar with Windows. Thx.

---

### Post by undecim on 2009-10-15
Just install XP like normal. Or, you can keep both by dual booting.

Just install Windows before you install Ubuntu. Windows doesn't play nice with other operating systems and will overwrite the MBR, making it so you can only boot windows. If you isntall Ubuntu second though, you will get to choose which one you want to use when you start your computer.

When installing Ubuntu, just make sure you install the two systems "Side by Side". Which is the default setting when installing.

Also, if you are familiar with windows and don't want to bother learning something completely different, check out the Ubuntu variant called Kubuntu. The only diffrence between the two is the desktop interface; Ubuntu uses GNOME, and Kubuntu uses KDE.

KDE looks and behaves more like Windows than GNOME does, so you may like it better than Ubuntu.

EDIT:

Or if you don't want to go to the trouble of reinstalling, you can go to a terminal and run this command: ```
sudo aptitude install kubuntu-desktop
```
That will install all the same packages that are in Kubuntu.

---

### Post by mick55 on 2009-10-15
Hey Aquarius79

If you keep using Ubuntu you will be more familiar with it.
It takes about 2 months to really start digging it.
You could install Windows xp in a Virtual Machine and use
them both.

[html]http://www.virtualbox.org/wiki/Downloads[/html]Windows XP runs faster in Ubuntu.Just make sure you install
the VBoxAdditions.

good luck
mick

---

### Post by QIII on 2009-10-15
You probably won't be able to just install XP over it.

Windows likes to believe it is the only game in town.  When it sees something as foreign as ext3 or ext4, it pukes, wets its pants and generally has a bad day.

If you really want to get rid of Ubuntu (You won't get any complaints from me.  It's your choice, and that is all you should worry about.), I suggest you use gparted from the LiveCD, delete any partitions you have and create one large NTFS partition.

That way XP will be fat, dumb and happy when it looks at the new home you are about to give it.

(Now, if you have an idea that you might want to keep Ubuntu... only use maybe half of your drive for that NTFS partition and install Ubuntu later on the other half.)

---

