---
title: "japanese characters in flash"
date: 2012-04-05
forum: General Help
---

### Post by Tehut on 2012-04-05
I've just noticed that japanese characters aren't displayed correctly for me in flash apps. Instead of the characters, only boxes that look approximately like this [X] are displayed. If I copy the text and paste it in, say, the browser's search bar, they are correctly displayed; so it seems to be a problem with just Flash.
Does anyone know how I can fix this?

---

### Post by Tehut on 2012-04-05
I've now tried setting the system locale and firefox itself to japanese. Still nothing. My whole system is japanese but for some reason flash player still won't display japanese script correctly.
I'm assuming it has something to do with whatever font flash is using here, but I haven't found a way to force it to use a different one.

---

### Post by whatthefunk on 2012-04-05
Which flash app are you trying to use?  Let me know and Ill mess around with it.

---

### Post by Tehut on 2012-04-05
It's a game: [http://sword.bg-time.jp/](http://sword.bg-time.jp/)
I've run into this problem before, though, so I'll try to dig up some other flash app that gives me the same issues but doesn't need you to register to use it.
Thanks a lot, in any case.

---

### Post by whatthefunk on 2012-04-08
Okay, got it to work!

It seems to be a web browser problem.  In firefox, go to Edit > Preferences > Content > Fonts and Colors Advanced

In that menu, select Japanese in the pull down "Fonts For:" menu.  Then choose Japanese fonts for the bottom three pull down menus.  Restart firefox and you should be ready to go.

Im guessing that for other browsers, you would have to alter the Japanese fonts in a similar manner.

---

### Post by Tehut on 2012-04-08
Thank you very much. =)

I've tried your solution, but so far still got the same problem.
What are your settings looking like exactly? I've currently got it set it like this:
(Fonts for: Japanese)
Proportional: Sans-Serif
Serif: Droid Sans Japanese
Sans-Serif: Droid Sans Japanese
Monospace: Droid Sans Japanese
Tried some other japanese fonts, too.
allow pages to choose their own fonts is currently set, also tried unselecting that.
Default Character Encoding is set to UTF-8, also tried Shift_JIS.
Restarted firefox each time and to make sure also restarted the computer.
Firefox version is 11.0, newest flash (64-bit version) from the repositories is installed.
I'm guessing that it's still due to some part of this. What fonts did you select here?

---

### Post by whatthefunk on 2012-04-08
I have Koichi Mincho selected for all fonts.  Also, on the main content page, I have Koichi Mincho selected as the Default font.  Does that do it?

---

### Post by Tehut on 2012-04-08
Wow, that did the trick. It's working now, all the japanese text is displayed like it should be. Thank you so much. =)

---

### Post by whatthefunk on 2012-04-08
Excellent!  Glad I could help.  Enjoy your games!

---

