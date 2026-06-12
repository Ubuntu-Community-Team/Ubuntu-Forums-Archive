---
title: "Add Times New Roman Font"
date: 2010-02-04
forum: General Help
---

### Post by PartsMan on 2010-02-04
Can I add Times New Roman to a Hardy/OpenOffice 2.4 install?

---

### Post by howefield on 2010-02-04
Have you installed the ttf-mscorefonts-installer package ?

Installable via Synaptic Package Manager.

[http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer](http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer)

---

### Post by PartsMan on 2010-02-04
No. I guess I should try that?

---

### Post by howefield on 2010-02-04
> **PartsMan said:**
> No. I guess I should try that?

Yes, I would.
It includes the font you are looking for.

The fonts it will install are

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

### Post by Enigmapond on 2010-02-04
Another way to add those and any others is to find whichever ones you want online, download them and throw them into /user/share/fonts or create a folder ".fonts" in your home directory then just run this command in your terminal to update the font cache..

```
sudo fc-cache -f -v
```Cheers!

---

### Post by PartsMan on 2010-02-05
Thanks for the help guys. Now I can use my laptop to type papers for Comp II.
Picky professor said "If it isn't Times New Roman 12 it's a zero".

I ended up checking the mscorefonts box in add/remove programs.

I guess that whole problem with 9.10 and my old computer was avoidable.](*,)

---

