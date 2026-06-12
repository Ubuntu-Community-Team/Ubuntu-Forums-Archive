---
title: "Simple solution for button positions in Ubuntu Lucid Lynx"
date: 2010-05-16
forum: General Help
---

### Post by EnergyEruption on 2010-05-16
Hey everyone,

       There's been a lot of talk about the button positions in Ubuntu Lucid Lynx 10.4 . I just upgraded from 9.10 Karmic to 10.4 Lucid a few minutes ago, and got confused with the window button positions in Lucid. So, I typed 

[B][COLOR=Black]how to put window buttons on right in ubuntu lucid
[/COLOR][/B]
in google. The first results is this page:
[B]
[http://www.baptiste-wicht.com/2010/05/ubuntu-lucid-lynx-buttons-right/](http://www.baptiste-wicht.com/2010/05/ubuntu-lucid-lynx-buttons-right/)[/B]

which basically offers this very simple solution:

[SIZE=3][B]1. Go to the Terminal.[COLOR=Red] (Applications>Accessories>Terminal)[/COLOR]

2. Type in:

[COLOR=Red] gconf-editor[/COLOR]

3. On the "Configuration Editor" window that appears, go to [COLOR=Red]apps>metacity>general[/COLOR]

4. On the right half of the Configuration Editor, you should see a [COLOR=Red]

button_layout

 [/COLOR]option, with 

[COLOR=Red]close,minimize,maximize:[/COLOR][/B]

[B]written to the right.

5. Double click it, and change the value to

[COLOR=Red] menu:minimize,maximize,close



[/COLOR][/B][COLOR=Red][COLOR=Black][SIZE=1]P.S. I've deliberately written the instruction in very simple format, so that even someone new to Linux can do this. Moderators, if you feel that this should be posted at another part of the forum, please let me know. 

Take care, 

Alex
[/SIZE][/COLOR][/COLOR][/SIZE]

---

### Post by philinux on 2010-05-16
I assume you've not seen the forum sticky. ;)

---

