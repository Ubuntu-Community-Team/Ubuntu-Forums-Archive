---
title: "Odd icon behavior on removable drives in /media folder"
date: 2011-04-21
forum: General Help
---

### Post by einir on 2011-04-21
This is my first post here, so I hope I'm doing everything right.

Anyway, I'm somewhat of an icon fanatic, so I like my most frequently used folders to have unique and recognizable icons. The other day I plugged in some of my removable storage devices and put a unique icon for each one in the /media folder where they mount by default. As far as I can see the icons stick to their respective drives, even when I unplug them and replug them, which is good. 

Then it turns out that when I have a drive plugged in and plug in another one, the icon on the former drive resets to default so that only the latter drive shows its custom icon. If I unplug the latter drive, the former drive shows me its custom icon again.

I'm confused as to why exactly this happens. Whether or not it's a bug or an intentional thing I'm hoping someone knows how I can prevent this from happening, because it kind of bothers me.

Thanks! :)

---

### Post by coffeecat on 2011-04-21
Welcome to the forum.

I don't quite follow what you are doing because a dynamic mountpoint is created in /media when you plug in a USB device and is then deleted when you unmount it. I've never tried putting icons in /media itself so I don't know how that would work.

However, there is a way of getting a unique icon for each mountable device/partition. You simply need to put the icon in *.ico format in a folder called "autorun" in the root of the device filesystem, together with a simple script called autorun.inf. This works in Windows as well as Linux. As an example, I have an icon called gnome-dev-flashkey.ico - see attached image - in the autorun folder, and the file called autorun.inf which consists of:

```
[autorun] 
ICON=AUTORUN\gnome-dev-flashkey.ico
```By the way, you'll notice that I had to convert gnome-dev-flashkey.ico to gnome-dev-flashkey.png to be able to attach it - the forum software doesn't recognise the .ico format. Using a png icon and having "ICON=AUTORUN\gnome-dev-flashkey.png" in the autorun.inf file works just as well in Ubuntu.

---

### Post by einir on 2011-04-22
Thank you for your help, that answers my question perfectly.

---

### Post by coffeecat on 2011-04-22
Actually, 

> **coffeecat said:**
> This works in Windows as well as Linux.

Looking at the cavalier way the autorun folder has been capitalised in the autorun.inf file and the backslash rather than a forward slash in the path...

> **coffeecat said:**
> ```
[autorun] 
ICON=AUTORUN\gnome-dev-flashkey.ico
```... tells me that this is really a Windows trick that happens to work in gnome as well. Which is useful. I remember now that I bought a WD drive a year or so ago and noticed the individualised desktop icon when I plugged it in. A little investigation uncovered the  autorun stuff and I found I was able to adapt this with icons copied from icon themes.

I'm glad it's of use to you.

---

