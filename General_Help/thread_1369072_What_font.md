---
title: "What font????"
date: 2009-12-31
forum: General Help
---

### Post by t1nm@n on 2009-12-31
hey guys it would be gr8 if anyone can point out which font is in this theme

[http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed](http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed)

---

### Post by m0o on 2009-12-31
Seems like [Zekton]("http://www.dafont.com/zekton.font")?

---

### Post by rcayea on 2009-12-31
I don't know if this will help, but there is a website to help figure out what font a person is using. 

the site is: [http://new.myfonts.com/WhatTheFont](http://new.myfonts.com/WhatTheFont)

---

### Post by Mahngiel on 2009-12-31
it's vibroceb.[[link]("http://www.deviantart.com/users/outgoing?http://www.dafont.com/vibrocentric.font")] i've got it installed as well

---

### Post by fcuk112 on 2009-12-31
how to install this font in karmic?

---

### Post by Mahngiel on 2009-12-31
i updated my post with the link. you'll need to create /.font in your /home folder if you don't already have it, and put the folder of the .ttf font styles in there. then when you customize your theme, it'll be in your font selection

---

### Post by fcuk112 on 2009-12-31
thanks, i have installed the link.  my menus are now using that font but i can't get my top panel to use it.  neither does nautilus use that font.  do i just go to appearance -> fonts and configure it there?  or do i need to change my theme?

thanks.

---

### Post by Mahngiel on 2009-12-31
From the appearance menu editor, select the font tab:

Application font refers to the fonts shown in tool bars and the gnome panel
Document font refers to the font within your browser or applications you use (ie. everything not associated with the structure of the application)
Desktop font refers to your desktop
Window title is you title bars for applications

---

### Post by fcuk112 on 2009-12-31
thanks, looks like i need to logout and log back in again for some of the fonts to take effect.  have everything set to vibrocentric 12 now, except the fixed width font which i kept on monospace.  will have to try it out for a while, the default sans does look a bit easier on the eyes.

---

### Post by Mahngiel on 2009-12-31
you shouldn't need to reboot. i keep the sans font for my documents. the vibocentri looks nice, but in smal tastes. did you set the fonts up right? i may have told you wrong. should look like this:

/home/*user*/.fonts/vibroce(b)(i)(u)(x).ttf [with each of the parenthesised being an individual file]

---

### Post by fcuk112 on 2009-12-31
yes, i think it is correctly setup - i followed the instructions on the ubuntu wiki:

> 
The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):


gksu nautilus /usr/share/fonts/truetype
Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Copy the fonts into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:


sudo fc-cache -f -v
 Note: After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs; however, some programs may require you to log out and log back in.


so you have document font set to sans 12?
everything else to vibrocentric 12?

btw i use ttf-inconsolata for my terminal.

---

### Post by Mahngiel on 2009-12-31
yes, that's my preference, all the title/menu bars are in vibro and regular, easy to reas sans in the documents. works for me. :)

---

### Post by t1nm@n on 2009-12-31
to install font in karmic ... copy the font file into this driectory

/usr/share/fonts/truetype

and then restart and change the font from system>preferences>appearance..

---

