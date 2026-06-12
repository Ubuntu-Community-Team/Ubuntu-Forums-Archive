---
title: "Windows 7 Theme Packs?"
date: 2011-12-29
forum: General Help
---

### Post by xyzzyman on 2011-12-29
Hi, I was wondering if anyone here would like to use the Windows 7 theme packs on Ubuntu?

[http://windows.microsoft.com/en-US/windows/downloads/personalize/themes](http://windows.microsoft.com/en-US/windows/downloads/personalize/themes)

At least just the wallpaper packs that rotate? I figured out how the rotating wallpaper works from the 11.10 contest, and have already made two wallpaper packs from Windows 7 show up additionally in the wallpaper box and they auto rotate. I thought about doing a PPA with deb's that would download the theme pack, extract and install it the same way that ttf-mscorefonts-installer does, but I'm still iffy on if that's considered redistribution.

So my question is would anyone be interested if I wrote a command that you would download the theme pack and at the CLI type:

```
sudo mstheme-installer catsanywhere.themepack
```

The attached screenshot is after having installed the first one. It shows the name of the theme pack and as you can see it auto rotates. I could also have the installer ask how many seconds you want it to be between rotations as it has to be written in up front. (Mine is set to show a new cat every 60 seconds. So every 10 minutes I loop back but still... They are cats so they're awesome) Each additional pack also only shows up once in the wallpaper window. I could show each wallpaper individually but then it would just become a mess.

If interested and would use it please reply, or if you like the idea but would prefer some other way (I don't have the skill to do a full GUI and I just want it to work and not have to be updated whenever they release new packs.)

---

### Post by 2F4U on 2011-12-29
Do you realize that these theme packs are copyright protected?

> These theme packs contain the intellectual property of Microsoft and  other third parties.  They are offered for download solely for your own  personal use.  Any other use, including the redistribution of the theme  packs, or any other conduct in contravention of the applicable Terms of  Use or End User License Agreement, is prohibited.

---

### Post by xyzzyman on 2011-12-29
> **2F4U said:**
> Do you realize that these theme packs are copyright protected?

It says they are for personal use. It seems to be the same as the Microsoft TTF Core fonts where you can't redistri bute or modify (See [http://www.microsoft.com/typography/faq/faq8.htm](http://www.microsoft.com/typography/faq/faq8.htm) which refers to the same End User License Agreement that seems to be written for everything). Ubuntu doesn't distribute them. It just downloads them for the user and extracts them and doesn't modify or rename the files, which is the same thing I would be doing.

---

### Post by 2F4U on 2011-12-29
I am not a legal person and anyways not interested in using these themes, but there seems to be a difference to me compared to the legal terms of the fonts. For the theme packs, the legal term reads as

> Any other use, including the redistribution of the theme  packs... is prohibited. 			 		

In my opinion, this means that you are not allowed to redistribute, and since you are planning to provide a ppa and deb packages, this could indeed be interpreted as redistribution.

---

### Post by LowSky on 2011-12-29
might be a better idea to package open source photos into similar packages.

---

### Post by xyzzyman on 2011-12-29
> **2F4U said:**
> I am not a legal person and anyways not interested in using these themes, but there seems to be a difference to me compared to the legal terms of the fonts. For the theme packs, the legal term reads as



In my opinion, this means that you are not allowed to redistribute, and since you are planning to provide a ppa and deb packages, this could indeed be interpreted as redistribution.

If you read what I wrote, I said I had thought about it but because that would probably be considered redestributing I decided to write a utility that only processes what the user downloads... So I don't know why you just said what you said...

---

