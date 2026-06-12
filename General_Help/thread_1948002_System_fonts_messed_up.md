---
title: "System fonts messed up"
date: 2012-03-27
forum: General Help
---

### Post by Umunthu on 2012-03-27
I logged into my computer this morning to find that the normal system fonts used with Radiance had all been somehow changed. I tried logging out and back in, and finally restarting the computer a couple times. Nothing worked.
 
I've had the system display the wrong theme upon login before, but a restart always put everything back to normal. Now nothing seems to work, and I have the right theme but the wrong fonts. I didn't mess with system files, uninstall anything important, or recently change anything in the appearance.
 
In the screenshots you can see the font that has replaced the normal default.

---

### Post by PhantomTurtle on 2012-03-27
I have never seen this, but you can change the fonts using the gnome-tweak tool(this is for 11.10 and higher). You can get it by:
```
sudo apt-get install gnome-tweak-tool
```

It will come up as Advanced settings.

---

### Post by mikejonesey on 2012-03-27
are you sure it's the wrong font? maybe the setting you are looking for is the dpi? which will change the font size everywhere...

---

### Post by Umunthu on 2012-03-27
Thanks for the suggestion, PhantomTurtle. I was able to restore my main system font, which had somehow changed from 11-point Ubuntu to 12-point Cantarell (?). My web browsers are still not using their old fonts (or maybe they're not being rendered like before?). Is there anything else I can do?

---

### Post by PhantomTurtle on 2012-03-27
Changing Fonts for Firefox - [http://support.mozilla.org/en-US/kb/Changing%20fonts%20and%20colors]("http://support.mozilla.org/en-US/kb/Changing%20fonts%20and%20colors"). For Google Chrome or Chromium - [http://support.google.com/chrome/bin/answer.py?hl=en&answer=95416]("http://support.google.com/chrome/bin/answer.py?hl=en&answer=95416"). If you need help with any other browsers just post the name of the browser and I'll help find it.

---

### Post by Umunthu on 2012-03-27
I have Epiphany and Chromium. Epiphany is set to use system font settings, and Chromium displays the same fonts even though I have tweaked its font settings. So I think it's still a system font problem rather than a browser problem.

---

### Post by PhantomTurtle on 2012-03-27
Could you show me a screenshot from either Chromium or Epiphany. Also I have posted a screenshot of the default setting for fonts, make sure you have the exact same thing. Additionally if didn't already, try restarting after you change the settings.

---

