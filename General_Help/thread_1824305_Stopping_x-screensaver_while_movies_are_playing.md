---
title: "Stopping x-screensaver while movies are playing"
date: 2011-08-13
forum: General Help
---

### Post by whatthefunk on 2011-08-13
Hi all,
Is there anyway to get x-screensaver to stop running when MPlayer is running?  Its driving me crazy...

---

### Post by amjjawad on 2011-09-22
> **whatthefunk said:**
> Hi all,
Is there anyway to get x-screensaver to stop running when MPlayer is running?  Its driving me crazy...

I know what will you say but that's the easiest approach :P

I'm interested to find that option if there is any. I looked into VLC Options the other day but didn't find something related to that.

---

### Post by whatthefunk on 2011-09-22
I couldnt get it to work so just purged xscreensaver.  I adjusted my power management settings so that after ten minutes my screen will go blank.  Over all its better...faster boot times, less resources used, and no more screensavers in the middle of my movies!

---

### Post by amjjawad on 2011-09-22
> **whatthefunk said:**
> I couldnt get it to work so just purged xscreensaver.  I adjusted my power management settings so that after ten minutes my screen will go blank.  Over all its better...faster boot times, less resources used, and no more screensavers in the middle of my movies!

That's definitely another option to go for :D
If your laptop is old then yes, that will make a difference.

How old is your Laptop? RAM? CPU?

---

### Post by whatthefunk on 2011-09-22
Its an old Sony Vaio.  256 ram, Pentium III, 30 gb.  Im saving up for a new pc...hopefully Ill have one by early next year.

---

### Post by WorMzy on 2011-09-22
In ~/.mplayer/config simply add:
```
heartbeat-cmd="xscreensaver-command -deactivate > /dev/null"
```

Then restart mplayer. From then on, whenever mplayer is playing, xscreensaver won't kick in.

---

### Post by whatthefunk on 2011-09-22
I tried that and several variations.....didnt work.  Anyway, Ive decided that screensavers are pointless.

---

### Post by amjjawad on 2011-09-22
> **whatthefunk said:**
> Its an old Sony Vaio.  256 ram, Pentium III, 30 gb.  Im saving up for a new pc...hopefully Ill have one by early next year.

You know what? I'd LOVE to have something like your laptop but I can't find that old where I live :(
I had HP Omnibook 4150 (Made in France - I think 1999) with much worse hardware specifications than yours (P2 @366MHz - 64MB RAM - 4GB HDD - CD-Drive is dead - Laptop is broken now). I installed Linux Mint LXDE 9 in Nov, 2010 and it worked. 2.5mins from startup until a working desktop.

[IMG]http://ubuntuforums.org/picture.php?albumid=2136&pictureid=7114[/IMG]

I can't use it now ... it fell from a high distance and I didn't even tried to see if it's working or not?
It was a challenge for me to get that piece of antique work and I spent one month until I managed to do that. That was all what I wanted to prove to myself at that point.
Now, I do need an old machine, a bit better than the above one but I can't find.

Good luck with saving. I'm using a Desktop Computer (PC) which is 6 years old and I don't need any new machines at the moment.

---

