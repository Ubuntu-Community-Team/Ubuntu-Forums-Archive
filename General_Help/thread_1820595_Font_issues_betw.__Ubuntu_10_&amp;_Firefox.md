---
title: "Font issues betw.  Ubuntu 10 &amp; Firefox"
date: 2011-08-07
forum: General Help
---

### Post by captain_mills on 2011-08-07
Hello all...

Linux newbie here...

I have installed a set of about 250 fonts that I am bringing over from my old PC (planning to convert over completely).  I created a .fonts folder in my /home/<username> and moved fonts over to it.  After a restart, there were some web pages I'd created using different fonts that were still not displaying with the required fonts.

After this, I did an install using the Terminal to create a folder inside /usr/shared/fonts/truetype/ and moved the fonts over there.  After a restart, still no change in the font appearance on Firefox.

In Komodo Edit, I changed the native font to be displayed to one I knew was already installed in this Linux version (Ubuntu 10.04), which was 'URW Chancery L', in the CSS, and there was STILL no change in the way the page was displayed.

I am looking for some help.  I know I should use a font that will display easily on each machine, but if I include a line:

font-family:* 'Monotype Corsiva'*, 'Apple Chancery', 'URW Chancery L';

in my CSS, then it should render similarly no matter what OS is being used by the website visitor.  However, this is not the case.  Please help, and thanks in advance for any and all help given!

CMills

---

