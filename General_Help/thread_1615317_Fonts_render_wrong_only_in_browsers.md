---
title: "Fonts render wrong only in browsers"
date: 2010-11-06
forum: General Help
---

### Post by CyberWasteland on 2010-11-06
Hey.

Out of seemingly nowhere both Chrome and Firefox started rendering all fonts wrong. 
Both on webpages as in the menu bars.

No other applications are doing this and I have most fonts installed. I have no clue what could have caused this since I didn't change any of the font settings lately.

Anyone have this happen and/or now how to solve it?

Screenshot is attached.

---

### Post by CyberWasteland on 2010-11-07
Anyone?

---

### Post by kerry_s on 2010-11-07
i can't tell from the screen shot, what exactly is wrong with the rendering?

---

### Post by ryadav on 2010-11-07
i don't see what's wrong? did the font size change??

if you hit [ctrl] and '-' minus this will reduce font size
if you hit [ctrl] and '+' it will increase font size

---

### Post by CyberWasteland on 2010-11-07
Yeah, you can't really see it from the screenshot. But the font looks like it does when you don't have subpixel smoothing turned on, which it didn't before and only is so in my browsers.
Also all fonts are the same, whether it's serif, sans, monochrome whatever it all reverts to the same font.

---

### Post by CyberWasteland on 2010-11-09
Ok, since it was kind of hard to see on it's own I took a screen shot of Arial rendered by OpenOffice writer and by chrome.

In the screenshot the top text is how Writer renders arial and the bottom how chrome does it. You can see the difference.

It kind of looks like chrome stretches out the letters height wise.

---

### Post by CyberWasteland on 2010-11-09
*sigh*

---

### Post by CyberWasteland on 2010-11-09
The problem is that chrome/firefox refuse to follow the global font configurations and don't do subpixel smoothing.
There has to be a way to make them do it.

---

### Post by CyberWasteland on 2010-11-09
I fixed the problem. Apparently Chrome and firefox use a different way to get their font configurations.

Most apps get them from the font.config file in the /etc/fonts folder, while chrome/firefox get them from the .font.config one in the home folder.

So I just replaced the one in the home folder by the one in the etc folder.

---

