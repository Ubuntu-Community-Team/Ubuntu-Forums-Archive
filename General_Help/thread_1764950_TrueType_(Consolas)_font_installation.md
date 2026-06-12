---
title: "TrueType (Consolas) font installation"
date: 2011-05-22
forum: General Help
---

### Post by HumbleNoob on 2011-05-22
Dear Ubuntu users,

I am trying to install the MS true-type font "Consolas" in my Ubuntu system but can't get it working correctly.

Basically, when I choose that font in Eclipse or Gedit, every character is rendered with a rectangle :-k.

I followed the instructions listed here: [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) and installed the font in "~/.fonts/".
The installation process didn't report any error and I see the font listed in Eclipse or Gedit.

I am a bit lost here. From what I read on forums, truetype fonts imported from Windows should be working smoothly on Linux. Most probably, I made a mistake somewhere but can't find it.

Any help or suggestion is welcome!

Many thanks in advance!

---

### Post by satanselbow on 2011-05-22
Did you rebuild the font cache?

```
sudo fc-cache -f -v
```

---

### Post by HumbleNoob on 2011-05-22
Yes, I did. The command result was successful (I also tried logout/login).

I forgot to mention that I took the font from a Windows 7 with Visual C++ Express 2010 installation.

---

### Post by satanselbow on 2011-05-22
Can you preview the font in a font manager? May be as simple as a "corrupt" file copy :(

---

### Post by HumbleNoob on 2011-05-22
Ok, I really deserve the last part of my nickname!!

Someway, you pointed me to the right direction!

Basically, while trying to fix my problem, I copied the font files from my Windows 7 disk drive using a sudo-ed Nautilus to my home directory (~/.home).
I didn't pay attention immediately to the files permission as the command fc-cache was successful (but it was too executed as root).

Following your advice, I wished to double-check the files validity and I noticed that.. i didn't have access to them!

Hum... At that point, I should be very, very ashamed... :oops:

Once granted the right access, the fonts were available as normal (so stupid mistake)!

Many thanks for your kind and prompt help!! :)

---

### Post by satanselbow on 2011-05-22
> **HumbleNoob said:**
> 

Hum... At that point, I should be very, very ashamed... :oops:

Once granted the right access, the fonts were available as normal (so stupid mistake)!

Many thanks for your kind and prompt help!! :)

Not ashamed - No! 

You are now 1 step closer to Ubuntu Uber Geek-dom :popcorn:

Glad I could (kind of) help :D

---

