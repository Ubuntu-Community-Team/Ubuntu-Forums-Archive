---
title: "About to Give Up...Screen Glitches."
date: 2011-03-18
forum: General Help
---

### Post by loap on 2011-03-18
Augh, I'm completely new to Ubuntu and have run into the exact same problem twice now with 2 different hard drives. I love Ubuntu when it works, but with problems like this, I'm ready to give up on it.

First hard drive:
Installed Ubuntu alongside Windows 7 about 2 weeks ago. Works great until one day I log-in and I get a completely blank panel, however my background still shows along with any desktop icons I may have. I can't right click on the panel at all (by the way, I had TWO panels stacked on top of each other on top of the screen before this), but I can right click on the desktop itself. Next thing I know I get a hard drive error (I can't remember the exact phrasing). Also, upon log-in, the panel and icons keep moving constantly, as in they shift up and down rapidly about a pixel or so--it's really annoying.

Seconds hard drive:
Got a brand new, higher capacity hard drive. Install Ubuntu (and only Ubuntu) and everything runs swimmingly until today when I ran into THE EXACT SAME PROBLEM as before. I didn't mess with any advanced settings, the worst I did was install a few programs. Now I'm pissed, I haven't done anything to the OS that I haven't read about 1000 other people doing and most of the changes I made were done by clicking "install." But yet I get one blank panel instead of the two I set-up and the stupid shifting effect. I do what I can but I seem to be completely helpless. Running in Safe Mode doesn't make an ounce of difference for the problem and I fear that this is going to cause another hard drive error.

Any help you could supply would be great. What would cause this problem, how can I remedy it, and what should I (or shouldn't I) do so this doesn't happen again? I don't want to waste time downloading and burning Windows 7 onto this laptop, please.

---

### Post by gufide on 2011-03-18
what is your hardware? It's surely due to the video card. If you have an Nvidia, you can try to use the proprietary driver of nvidia. You can installing it with jokey-gtk. If you cot an ati, you can try this too. If you got an intel graphics, You can try to search in the internet. I can't do it for you now because I don't know the computer model/manifacturer and I don't know your hardware. You can try to make a cd check (press a key when you see human=keyboard in live cd) to see what happen. I your cd is correct, you can check your gconf-editor and try to check panel configuration. Else, you booting in recovery mode and repair broken package or make a new X configuration in safe mode X

---

### Post by loap on 2011-03-18
Thank you for your help so far.

I didn't know the graphics card off the top of my head, but I looked up my laptop model and found this:

"Intel GMA 4500MHD Dynamic Video Memory Technology"

Does that help?

EDIT:
The problem I have with the Live CD is that I used the alternative, BIOS-looking install because I was having issues with the standard one. So I don't think I have the ability to do a Live CD?

---

### Post by r-senior on 2011-03-18
> **loap said:**
> I didn't know the graphics card off the top of my head, but I looked up my laptop model and found this:

"Intel GMA 4500MHD Dynamic Video Memory Technology"
If you open up a terminal and type:

```

$ lspci

```

there will be an entry in there which gives information coming from your video card. Typically "VGA compatible controller". What does it say immediately after that?

For example, in my case:

```

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

```

---

### Post by loap on 2011-03-18
After the VGA compatible controller it says this:

```
Intel Corportation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

---

### Post by loap on 2011-03-18
Is there any way that I can upgrade a video card? Or is mine so crappy that I shouldn't be running Ubuntu in the first place? I just don't get how Ubuntu can be running fine one minute then spaz out like this after a simple restart.

---

