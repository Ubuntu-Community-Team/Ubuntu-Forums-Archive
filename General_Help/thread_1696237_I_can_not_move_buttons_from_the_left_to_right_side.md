---
title: "I can not move buttons from the left to right side in the window border"
date: 2011-02-27
forum: General Help
---

### Post by pavelexpertov on 2011-02-27
I usually used ubuntu tweak to move the buttons to another side, but when i customized one theme, i could not change the button positions by using ubuntu tweak. So is there any other way i could change the button positions?

---

### Post by rvchari on 2011-02-27
> **pavelexpertov said:**
> I usually used ubuntu tweak to move the buttons to another side, but when i customized one theme, i could not change the button positions by using ubuntu tweak. So is there any other way i could change the button positions?

type gconf-editor in terminal
it will open gconf-editor
go to app > metacity > general
on right side window you will get window button lay out
right clink and edit the keys to menu:minimize,maximize,close
close the editor.

you can set this as mandatory so that whatever scheme you select, your window buttons will be on top right.

---

### Post by pavelexpertov on 2011-02-27
Yeah thanx, but i can not understand why i can not do that anymore in ubuntu tweak..... Recently i installed kubuntu desktop environment, so i have two desktop environments. Does it affect ubuntu tweak?
ps how can i make it "mandatary"?

---

### Post by stinkeye on 2011-02-27
> **pavelexpertov said:**
> 
ps how can i make it "mandatary"?

In gconf-editor right click on the entry in the right panel and select
**set as mandatory**.

If you ever need to set them back 
```
gksudo gconf-editor
```
go to 
File > New Mandatory Window

This window only lists keys you have made mandatory, so it is
easy to find the relevant entries,
and Right click and select Unset Key.

---

### Post by pavelexpertov on 2011-02-27
Also, titles in window borders are not centered, can i do anything to the titles that they become centered?

---

### Post by rvchari on 2011-02-27
> **pavelexpertov said:**
> Yeah thanx, but i can not understand why i can not do that anymore in ubuntu tweak..... Recently i installed kubuntu desktop environment, so i have two desktop environments. Does it affect ubuntu tweak?
ps how can i make it "mandatary"?

after you edit the keys, right click again and you should get set as mandatory option.
once you do this then reverting is another process. but thats managable, you can go ahead and enjoy !!!

---

### Post by rvchari on 2011-02-27
> **pavelexpertov said:**
> Also, titles in window borders are not centered, can i do anything to the titles that they become centered?

not sure if centering the titles can also be shifted positions as it is theme specific. (though i am not sure and havent fiddled with that)

one option is as follows.
go to ~/.themes/YOUR-THEME
select folder metacity and have a back up of the xml file (metacity-theme-1.xml or something like that)
read it carefully and notice the positions of window title and tweak if you can.

i asked you for back up coz if everything is messed up, you can replace that messed up file with the back up to get back what you had.

---

