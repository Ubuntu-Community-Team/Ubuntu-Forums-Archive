---
title: "How to Change Inactive Window Border Color"
date: 2010-11-28
forum: General Help
---

### Post by fofo412 on 2010-11-28
I've been searching and have been unable to find a solution.

My current theme is rather dark, for reading at night, etc.  And with inactive windows on the screen, the border changes to white from black and makes it difficult on the eyes.

Is there a way to change this inactive color to another, such as black or dark gray?

I have looked all over, searched, and cannot find anything. . .

Thanks!!

---

### Post by howefield on 2010-11-29
You might try altering the metacity-theme-1.xml file. 

Open up a terminal and type

```
gksu nautilus
```

Navigate to the relevant theme eg ...

/usr/share/themes/Dust/metacity-1/metacity-theme-1.xml

Make a backup of metacity-theme-1.xml and open in gedit. Change the colour in line 54 as required and save your way back out. 

You might need to logout/back in to see the change take effect.

Other themes may be different on the lines that you are looking for, but hopefully you get the idea.

Remember, working with elevated rights in Nautilus means you need to take care, might be better to open the relevant file from terminal, eg.

```
gksudo gedit /usr/share/themes/Dust/metacity-1/metacity-theme-1.xml
```

---

### Post by fofo412 on 2010-11-30
> **howefield said:**
> You might try altering the metacity-theme-1.xml file. 

Open up a terminal and type

```
gksu nautilus
```

Navigate to the relevant theme eg ...

/usr/share/themes/Dust/metacity-1/metacity-theme-1.xml

Make a backup of metacity-theme-1.xml and open in gedit. Change the colour in line 54 as required and save your way back out. 

You might need to logout/back in to see the change take effect.

Other themes may be different on the lines that you are looking for, but hopefully you get the idea.

Remember, working with elevated rights in Nautilus means you need to take care, might be better to open the relevant file from terminal, eg.

```
gksudo gedit /usr/share/themes/Dust/metacity-1/metacity-theme-1.xml
```

Thanks for the reply!  I am trying your suggestion, and have found the lines of code, as per your instructions in the Dusty theme XML file, but am unable to do the same for the custom Ambiance theme that I am using. . .

For Ambiance, I created a pastebin file of the code, but am unable to locate any hex color code for "white".

```
http://pastebin.com/tdb1ANi9
```

Any further help is greatly appreciated!

---

