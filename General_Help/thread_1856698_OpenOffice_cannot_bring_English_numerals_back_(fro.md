---
title: "OpenOffice: cannot bring English numerals back (from Arabic)"
date: 2011-10-08
forum: General Help
---

### Post by astrobob.tk on 2011-10-08
Hello,

I just wanted to use the Arabic numerals in ooffice -writer, so I used the Tools > Options > Language Settings > Languages > Enhanced Language support {checked: Enabled for complex text layout(CLT)}, to set the CTL to Arabic(Lebanon).

All my English documents that were normal now display the numerals in arabic, even though I have undone what I mentioned above.

Could you please help ?

thanks in advance

---

### Post by astrobob.tk on 2011-10-12
BUMP. anyone ?

I searched alot but the problem seems to have been solved in 2.x of OOo: [http://openoffice.org/bugzilla/show_bug.cgi?id=86811](http://openoffice.org/bugzilla/show_bug.cgi?id=86811)

---

### Post by astrobob.tk on 2011-10-12
the problem is solved :D

All i had to do is shutdown OOo.org, then remove the folder /home/user/.openoffice.org then start OOo. This will recreate the configuration folder (of course the user configuration would have been lost but thats the least of my problems).

Inspiration: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=12167&p=57958&hilit=arabic+numerals#p57818](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=12167&p=57958&hilit=arabic+numerals#p57818)

Hope this helps others ;)

Update: please see post #5 of this thread for another simple solution ;) (thanks to user **grahammechanical)**

---

### Post by grahammechanical on 2011-10-12
May I suggest another way of doing what you wanted to do in the first place? Install an Arabic language keyboard layout. There is a utility for doing that. In 11.10 it is called Keyboard Layout. In 11.04 I think that it is simply called Keyboard.

This will put a keyboard icon in the top panel from which you can select the language keyboard that you want and you can type in that language in Openoffice documents and other programs.

These are the numerals 0-9 using the Bengali keyboard layout that I installed recently:

&#2534; &#2535; &#2536; &#2537; &#2538; &#2539; &#2540; &#2541; &#2542; &#2543;

Two clicks and I am back to English.

Regards.

---

### Post by astrobob.tk on 2011-10-12
> **grahammechanical said:**
> May I suggest another way of doing what you wanted to do in the first place? Install an Arabic language keyboard layout. There is a utility for doing that. In 11.10 it is called Keyboard Layout. In 11.04 I think that it is simply called Keyboard.

This will put a keyboard icon in the top panel from which you can select the language keyboard that you want and you can type in that language in Openoffice documents and other programs.

These are the numerals 0-9 using the Bengali keyboard layout that I installed recently:

&#2534; &#2535; &#2536; &#2537; &#2538; &#2539; &#2540; &#2541; &#2542; &#2543;

Two clicks and I am back to English.


Thank you for the suggestion, but I already have this feature (or I think i do). I am on 10.04 LTS & from the Preferences > Keyboard > Layout, I installed the layout & it appears in the taskbar. The thing is, though, that when writing a document in Arabic, the right & left arrows become annoying (i.e.; to move the other way lol) + the numbers/numerals still remain in English (the layout that I am using is: Lebanon: Arabic, & the layout map shows English numerals; OH i just discovered the Arabic qwerty/digits & it replaces the English with the Arabic digits :D) .

thank U :D I guess this solved my problem :D

---

