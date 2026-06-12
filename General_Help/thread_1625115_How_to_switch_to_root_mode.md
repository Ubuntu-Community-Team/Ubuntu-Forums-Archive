---
title: "How to switch to root mode?"
date: 2010-11-18
forum: General Help
---

### Post by Fracta on 2010-11-18
I am trying to put the System Tools option in the menu, but it deselects it whenever I click Show.
Just in case you don't realise what I'm talking about, its
System->Preferences->Main Menu

I assume its cos I'm not root. Is there a keyboard shortcut to turn everything into root mode or the current application? I don't know how to access the Main Menu thing from the terminal so I can't just go sudo.

---

### Post by WorMzy on 2010-11-18
That is your menu, it has nothing to do with root. If you can't change it, then something is probably wrong with your permissions. Can you run ```
ls -l ~/.local/share/applications
``` and post the output here. It may show what's gone wrong.

---

### Post by Fracta on 2010-11-18
This is the output I got. Thanks for quick reply!

total 4
-rw-r--r-- 1 fracta fracta 97 2010-11-18 10:36 mimeapps.list

---

### Post by WorMzy on 2010-11-18
That was considerably less output than I expected, but no matter. Do you get an error when you run the following:

```
touch ~/.local/share/applications/test
```

---

### Post by Fracta on 2010-11-18
nope. no error. I just want system tools in the menu. I need to change which side the close/minimize buttons are on. 
I know (this is a fresh install as of yesterday) (and yes I am quite new to linux but I learn quick) that I did it without any problems with my last install

---

### Post by WorMzy on 2010-11-18
Remove that file we just created then with: ```
rm ~/.local/share/applications/test
```

I think that the reason why you can't make that directory visible, is because it doesn't have anything in it. Open up alacarte (the menu editor) again and left-click on the System Tools item. If, when that item is selected, the right-box is empty, then the folder can't be made visible because it has nothing in it.

You can move the close/minimise/maximise buttons to the right pressing Alt+F2, running gconf-editor, browsing to /apps/metacity/general, and setting the button_layout to menu:minimize,maximize,close

---

### Post by Fracta on 2010-11-18
I figured out the problem. I was selecting the menu directory when (apparently) I should have been selecting System Tools on the left and clicking the entries on the right. I stupidly thought that just selecting System Tools on the right would add all the menu entries. 
Thanks for your help!

---

### Post by WorMzy on 2010-11-18
Ah. Well, hopefully I put you on the right track to find that out, despite not thinking of it myself. :)

Glad you got it sorted in any case.

---

