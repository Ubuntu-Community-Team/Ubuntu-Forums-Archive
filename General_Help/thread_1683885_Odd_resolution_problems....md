---
title: "Odd resolution problems..."
date: 2011-02-08
forum: General Help
---

### Post by Tsycho17 on 2011-02-08
mmk, so here's how it goes:
 
When I first installed ubuntu 10.10, the display was for some reason tinted green and shifted a few inches to the right. After experimenting with the resolution preferences, I eventually got it to a large resolution (1280x720 ... or something like that) yet is was quite blurry. I found out that the problem was with my monitor after I switched it to TV mode, then back to PC mode. It became perfectly clear! All I had to do then was adjust the screen positioning by shifting it left a bit. 
 
Even though I have made the resolution I figured out to be default, whenever I turn the PC on after shutting down, it goes back to the "green-and-to-the-side" mode. :/
Ain't really a big problem, until I tried to fiddle with the resolution preferences s'more. 
 
Somehow, I have set it to be twice as wide of the maximum my monitor can display, went back to being green tinted for some reason, and is completely shifted left (yet the right side is still visible) This means that I cannot see what is going on the left side, and cannot adjust the resolution preferences, nor can I click blindly cuz the border is only around my visible side of the screen. Now it is stuck like this.
 
I've researched many hours and eventually found the terminal command for the resolution preferences. Thankfully it popped up on the visible side. Although it was to no avail cuz I HAVE TRIED EVERY SETTING AND OPTION and absolutely nothing changed.
 
I assume a system restore would simply revert it back to the previous satisfactory settings, but the thing is I want to FIX it. I am new to this terminal stuff, so I want to learn it and all that. 
 
To put it simply, here's what I want:
• Learn how to manually adjust resolution without depending on a simple dialog box.
• Make the satisfactory resolution default and consistent through turning it on and off.
• Someone to hold me. :{
• Link that could teach me the essential commands, all this googling is stressful. D:

---

### Post by gordintoronto on 2011-02-08
Some specific information might be helpful. What video adapter is in your computer? The command lspci will display about 14 lines of information; the one which includes the word "VGA" will be about your video adapter. Also, what is the brand and model of your display? Is it a TV set? As well, did you install a proprietary driver?

---

### Post by Tsycho17 on 2011-02-08
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

The brand is Memorex. I'm not sure weather to call it a PC Monitor or a TV set. :/
Anyway, this thing can switch input modes; for game systems, television, monitors, and abuncha others.

... I have no idea what a proprietary driver is, but if more info is needed I have no problem looking it up.

---

### Post by Tsycho17 on 2011-02-10
ehhh nevermind i figured it out... sorta

---

