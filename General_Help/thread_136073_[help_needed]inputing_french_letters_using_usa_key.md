---
title: "[help needed]inputing french letters using usa keyboard"
date: 2006-02-25
forum: General Help
---

### Post by jasonli on 2006-02-25
Salut!

J'apprends le français.

However, I can't figure out how to input the accented french letters, especially letters like ê. I am using a DELL Latitude D600 and have set Fra for my keyboard. I know normally you can just hit the [ key in normal 101 usa keyboard and then hit e, but when I do that, I get nothing for hitting [ and only the normal e when hitting e.

Please help me. I really don't want to do the tiring copy and paste work when typing French.

Merci beaucoup!!!

You can also refer to the post below on the French ubuntu forum to see how Pabix gave out a useful solution for using the composing key setting, which I do not prefer to use. Any advice or suggestions are welcome!
[http://forum.ubuntu-fr.org/viewtopic.php?id=29800](http://forum.ubuntu-fr.org/viewtopic.php?id=29800)

---

### Post by hajk on 2006-02-25
You should open the System --> Preferences --> Keyboard menu, and under Layout Options choose the right Win-key (for example) as the "compose" (dead-letter) key. With this setting, hitting the compose-key puts the keyboard in dead-letter mode, meaning that you can first type the accent followed by the letter, which produces the accented letter.... but only for common combinations. Your letter "e-circonflex" is typed by hitting 

right Win-key, ^, and e (sequentially) ==> ê

and similar for é and à (or even Ñ, ö, etc).

Is there a Euro-sign on your keyboard, say next to the "5"? Then you could also add the Euro-sign to the 5-key, followed by choosing the right Alt-key (Alt-Gr) as the third-level key. Now you produce the Euro-sign by pressing the Alt-Gr key together with the 5-key (at the same time), to produce &#8364;. Of course, you could also choose the e-key instead of the 5-key.

You'll find that these changes work in all Gnome terminals and windows.

---

### Post by jasonli on 2006-02-26
Hi hajk,

I tried to setup a compose key, and typed in the address bar of firefox, it worked. Then I opened gedit and typed there, it sucked.

I restarted and then even in firefox, it sucked. A compose key + > + e gave out simply the ".e". Did I get anything wrong?

Jason

---

### Post by hajk on 2006-02-26
In my own setup -- Dell US keyboard, en_US.UTF-8 locale, Euro-sign added to the 5-key -- the compose key works both in the Firefox address bar and in gedit (and in a terminal session as well). You could try to change the locale. Just to be sure, you should use the caret ^ to get the e-circonflexe ê, not the > sign listed in your last message. Also, pressing the compose-key only works for the immediately following accent plus letter, and then only for certain allowable combinations of them, all entered sequentially.

---

