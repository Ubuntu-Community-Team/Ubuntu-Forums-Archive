---
title: "MS TT Fonts"
date: 2012-08-03
forum: General Help
---

### Post by rickm1945 on 2012-08-03
I am trying to get Ms Fonts installed. I have buntu 12.04 64 bit. I had the fonts installed but had to do a clean install again so I lost them. I installed Restricted extras again checked the Microsoft Fonts installer and proceeded to download the package.  I agreed to the EULA and after the download finished and installed there was an error message saying the fonts didn't install and to check my Internet connection. I removed restricted extras and tried to install everything again, but the fonts still don't install. 
Anyone have a solution to this problem. I have them in stalled on my desktop computer but I need them on this HP laptop as well.

---

### Post by howefield on 2012-08-03
What happens of you try from a terminal ?

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by rickm1945 on 2012-08-03
> **howefield said:**
> What happens of you try from a terminal ?

```
sudo apt-get install ttf-mscorefonts-installer
```

Here is the output ```
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

---

### Post by howefield on 2012-08-03
Looks like you have them.

If you fire up LibreOffice Writer do you have these fonts available ?

Andale Mono
Arial Black
Arial (Bold, Italic, Bold Italic)
Comic Sans MS (Bold)
Courier New (Bold, Italic, Bold Italic)
Georgia (Bold, Italic, Bold Italic)
Impact
Times New Roman (Bold, Italic, Bold Italic)
Trebuchet (Bold, Italic, Bold Italic)
Verdana (Bold, Italic, Bold Italic)
Webdings

---

### Post by rickm1945 on 2012-08-03
> **howefield said:**
> Looks like you have them.

If you fire up LibreOffice Writer do you have these fonts available ?

Andale Mono
Arial Black
Arial (Bold, Italic, Bold Italic)
Comic Sans MS (Bold)
Courier New (Bold, Italic, Bold Italic)
Georgia (Bold, Italic, Bold Italic)
Impact
Times New Roman (Bold, Italic, Bold Italic)
Trebuchet (Bold, Italic, Bold Italic)
Verdana (Bold, Italic, Bold Italic)
Webdings

No, I don't have any of them.

---

