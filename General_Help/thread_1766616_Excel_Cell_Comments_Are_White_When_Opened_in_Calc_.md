---
title: "Excel Cell Comments Are White When Opened in Calc / LibreOffice?"
date: 2011-05-24
forum: General Help
---

### Post by csharpplus on 2011-05-24
I have two boxes -- one running WindowsXP, and the other running Ubuntu 10.04 LTS.

On  the WindowsXP box, I created an Excel 2003 (.xls) spreadsheet. This  spreadsheet has some cells with comments in them. 

When I  open the same '.xls' spreadsheet in 'Calc' (on the Ubuntu box), it  appears that all the cell values / formatting is indeed there.

Yet, for some reason, all the comments that are in the cells appear to be **white text on yellow background** -- which makes them impossible to read.

Any hints how to fix this? This problem appear on both 10.04 & 11.04.

---

### Post by oldfred on 2011-05-24
It has been a long time agp for me, but I think I had white on white and thought I had lost the info. Then I just changed text to black and it worked. 

Not sure what the issue was and I only had a few spreadsheets with the issue. Have not recently used Excel as now I only use OO or soon LibreOffice.

---

### Post by csharpplus on 2011-05-24
Thanks. Is there anything that can be done to resolve this? I will be receiving many '.xls' files to my Ubuntu box, and need to find a way to open them & view the comments.

Any ideas?

---

### Post by linuxinstalledfromhdd on 2011-05-24
Did you add the LibreOffice PPA and upgrade?

---

### Post by csharpplus on 2011-05-24
I installed LibreOffice on 10.04 and it didn't help. I tried also a fresh install on 11.04 (which comes built-in with Libre) -- this also did not help.

I get the sense this is an Ubuntu bug, not OpenOffice / LibreOffice related.

Any ideas how to solve it?

---

### Post by AlphaLexman on 2011-05-24
Go to 'Tools -> Options -> OpenOffice.org -> Appearance -> [COLOR="Blue"]Notes Background[/COLOR]' **and** 'Tools -> Options -> OpenOffice.org -> Appearance -> [COLOR="blue"]Comment[/COLOR]' and change them to something that will work for you.

---

### Post by csharpplus on 2011-05-24
Thank you. This is definitely a big progress!

Yet, while the 'background' changes the [COLOR=Blue]Notes Background, [/COLOR]I am not successful changing the actual [COLOR=blue]Comment[/COLOR] font. [COLOR=Blue]

[/COLOR]Any ideas how to change the actual comment font, rather than change the background?

---

### Post by linuxinstalledfromhdd on 2011-05-24
Also you may want to remove your openoffice so you don't have conflicts later on..

[http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/](http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/)

---

### Post by csharpplus on 2011-05-25
linuxinstalledfromhdd: thank you. Unfortunately, it does not seem like 'libreOffice' solves this issue I am having (although, perhaps it's an Ubuntu issue).

If you have any ideas what should be done in order to solve it, I'd be happy to hear. Thanks.

---

### Post by rashmani on 2011-08-16
Hi everybody,

same problem here, running Ubuntu 10.4.
Tried to create a custom color scheme with OO 3.x first but then no way to load it at startup.
Tried to switch to LibreOffice then, but the problem stays the same.
Tried to modify my Ubuntu's theme, still no good.
I would LOVE to find a solution...

TIA
rash*

---

### Post by rashmani on 2011-08-17
Hi again,

yep, suggestions from AlphaLexman work but it's all manual.
I deal with a large number of .xls files everyday and changing every time manually it's a pain.
Isn't any way to automatically load a custom color scheme when opening a file?

TIA,
rash*

---

### Post by rashmani on 2011-08-17
Quick update: up to now, the only viable solution is to set Ubuntu's theme to Clearlooks (or a pale equivalent one).

rash*

---

### Post by octoamit on 2011-09-21
If you don't want to change your entire theme, I've found that you can achieve the same results by changing the background and text colors for Tooltips on the "Colors" tab of the "Customize Theme" window. 

This is under System -> Preferences -> Appearance, then click the "Customize..." button.

[IMG]https://lh3.googleusercontent.com/-AeP6xZY3bE8/TnogM_wJAnI/AAAAAAAAABY/JWPdQQR-DHQ/s1280/Screenshot.png[/IMG]

---

