---
title: "Ubuntu Fonts on Windows?"
date: 2010-10-17
forum: General Help
---

### Post by leon_chame on 2010-10-17
Hello,

I have been using Ubuntu at home for over a year now and just love it..by far because of the way it looks..but unfortunately I have to use XP for my one work computer and have wondered for a long time if there is a way to install a font in XP that will give me the Ubuntu font look on windows?

Does anyone have any advice?

Sorry for posting here but I have failed for a long time on this issue via google..and btw...I am not interested in making my computer look like anything else than 10.04.  I know there are ways to make XP look like older versions of Ubuntu..which I am not interested in (or cant install tons of win dll overides because its a work pc)...and its the font I want really nothing more...?

Thanks in advance!

leon

---

### Post by kotaro535 on 2010-10-17
> **leon_chame said:**
> Hello,

I have been using Ubuntu at home for over a year now and just love it..by far because of the way it looks..I still am saying to myself how great it looks (Im sticking with 10.04 btw)...but unfortunately I have to use XP for my one work computer and have wondered for a long time if there is a way to install a font in XP that will give me the Ubuntu font look on windows?

Does anyone have any advice?

Sorry for posting here but I have failed for a long time on this issue via google..and btw...I am not interested in making my computer look like anything else than 10.04.  I know there are ways to make XP look like older versions of Ubuntu..which I am not interested in (or cant install tons of win dll overides because its a work pc)...and its the font I want really nothing more...?

Thanks in advance!

leon

Go to to terminal and type this.
$sudo apt-get install msttcorefonts

or else go to software center and search msttcorefonts.

it should do.

---

### Post by Vaphell on 2010-10-17
lol, read more carefully :-)
OP wants to move ubuntu DejaVu font to his XP so it gives a more familiar look

---

### Post by sendblink23 on 2010-10-18
> **kotaro535 said:**
> Go to to terminal and type this.
$sudo apt-get install msttcorefonts

or else go to software center and search msttcorefonts.

it should do.

learn to read before posting :P

---

### Post by mike555 on 2010-10-18
You could use the "Trebuchet MS "font in Windows , it looks very much like the new Ubuntu font ...

---

### Post by coffeecat on 2010-10-18
@leon_chame, if you mean the new Ubuntu font family, you can find the ttf files for these in /usr/share/fonts/truetype/ubuntu-font-family/ . Try copying the four .ttf files in there and installing them the usual way in Windows XP. "The usual way" = I can't remember how you install ttf fonts in Windows. :p

However, I doubt they'll look anything like they should do in Windows. Even Verdana (a Microsoft font) doesn't get rendered properly in XP.

The other thing to consider is that, as far as I remember, XP doesn't give you any way of changing the desktop font. I'm sure there's a hack for this, but you'd have to google unless anyone else knows.

---

### Post by coffeecat on 2010-10-18
For what it's worth, here is how the Ubuntu font appears in Word Pad in Windows 7.

---

### Post by Dans564 on 2010-10-18
that picture gives me heart pains...... :(
jk, wow windows is so customizable, installing ur own fonts......CRAZY!

---

### Post by Vaphell on 2010-10-18
i've changed the desktop font in windows (in fact i've changed the font of everything in OS) but it required regedit - i don't remember which key i had to modify, i'd have to google for it. Things became distorted here and there but it worked.

---

### Post by diablo75 on 2010-10-18
[http://font.ubuntu.com/](http://font.ubuntu.com/)

(Thanks, Google!)

Download the ttf file.

I think you just double-click on it, use the file menu to install it in the system.  Or you drag it into c:/windows/fonts, right-click on the file and hit Install.

---

### Post by leon_chame on 2010-10-18
Thanks for the replies...got it...yes..not quite the same look but at least it is a much better improvement!

Thanks again!!!

PS - Oh why does google work so differently from country to country???? :)

---

