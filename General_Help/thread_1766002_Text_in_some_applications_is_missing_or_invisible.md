---
title: "Text in some applications is missing or invisible"
date: 2011-05-23
forum: General Help
---

### Post by lechuza05 on 2011-05-23
Hi everyone.

First, the issue:
I'm finding that some applications (2 thus far) are not properly displaying text.  I first noticed it in Firefox, where it appears that NO text is being rendered because the search and "feeling lucky" buttons are both about 1.5 characters wide and blank inside.  I'll include screen-caps below to exemplify what I mean.  In addition to Firefox, I just tonight noticed that my PDF reader is apparently rendering all text in white (even though the same PDF opens up fine with black text on my Windows desktop computer).  For the PDF's, I can see that there is text there because I can do a Ctrl+A and copy, and then when I paste it into gedit I can see all the text.

Some background: 
I'm running Ubuntu 11.04 32-bit w/gnome.  The first thing I did after installing Ubuntu was to install the BlackBuntu theme by copying appropriate files from /usr/share/ from the BlackBuntu live USB.

What I've tried:
I've uninstalled and reinstalled Firefox a couple of times, but ultimately I just installed Chromium which is working fine and is not experiencing the same issue that Firefox is.  I've tried changing my theme back to default, changing all the fonts (under Appearance Preferences), and nothing is fixing this.  I'm about to just do a full reinstall of the OS, paying careful attention to at exactly what point in my process everything gets screwed up, but I'm hoping that someone has an idea that I can try before I have to reinstall the system.

Screen shots:
[IMG]http://dcdworld.com/imagehost/ScreenCap-Ubuntu-Firefox-Google.png[/IMG]
[IMG]http://dcdworld.com/imagehost/ScreenCap-Ubuntu-Firefox-GoogleSearchResults.png[/IMG]
[IMG]http://dcdworld.com/imagehost/ScreenCap-Ubuntu-PDFReader.png[/IMG]

---

### Post by wildmanne39 on 2011-05-23
> **lechuza05 said:**
> Hi everyone.

First, the issue:
I'm finding that some applications (2 thus far) are not properly displaying text.  I first noticed it in Firefox, where it appears that NO text is being rendered because the search and "feeling lucky" buttons are both about 1.5 characters wide and blank inside.  I'll include screen-caps below to exemplify what I mean.  In addition to Firefox, I just tonight noticed that my PDF reader is apparently rendering all text in white (even though the same PDF opens up fine with black text on my Windows desktop computer).  For the PDF's, I can see that there is text there because I can do a Ctrl+A and copy, and then when I paste it into gedit I can see all the text.

Some background: 
I'm running Ubuntu 11.04 32-bit w/gnome.  The first thing I did after installing Ubuntu was to install the BlackBuntu theme by copying appropriate files from /usr/share/ from the BlackBuntu live USB.

What I've tried:
I've uninstalled and reinstalled Firefox a couple of times, but ultimately I just installed Chromium which is working fine and is not experiencing the same issue that Firefox is.  I've tried changing my theme back to default, changing all the fonts (under Appearance Preferences), and nothing is fixing this.  I'm about to just do a full reinstall of the OS, paying careful attention to at exactly what point in my process everything gets screwed up, but I'm hoping that someone has an idea that I can try before I have to reinstall the system.

Screen shots:
[IMG]http://dcdworld.com/imagehost/ScreenCap-Ubuntu-Firefox-Google.png[/IMG]
[IMG]http://dcdworld.com/imagehost/ScreenCap-Ubuntu-Firefox-GoogleSearchResults.png[/IMG]
[IMG]http://dcdworld.com/imagehost/ScreenCap-Ubuntu-PDFReader.png[/IMG]
Hi, I have had that happen to me it was caused by the theme I was using, if you change your theme it might fix it.:)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Reverse the steps you made to make this happen.

---

### Post by lechuza05 on 2011-05-23
I've tried changing my theme back, but to no avail; the theme successfully changes, but the issues above persist.  The steps I took to make this change included adding (not overwriting, removing) files from the /usr/share/backgrounds; /usr/share/themes; /usr/share/fonts of BlackBuntu to Ubuntu.  Looks like I should just suck it up and reinstall again.

---

### Post by wildmanne39 on 2011-05-23
> **lechuza05 said:**
> I've tried changing my theme back, but to no avail; the theme successfully changes, but the issues above persist.  The steps I took to make this change included adding (not overwriting, removing) files from the /usr/share/backgrounds; /usr/share/themes; /usr/share/fonts of BlackBuntu to Ubuntu.  Looks like I should just suck it up and reinstall again.Hi, if you know the names of the fonts and themes you can get rid of them use this command in terminal.```
sudo apt-get --purge remove <package>
```without the brackets.:D

---

