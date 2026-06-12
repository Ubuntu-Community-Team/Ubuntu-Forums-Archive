---
title: "I have installed but cannot find recordmydesktop!"
date: 2011-10-06
forum: General Help
---

### Post by JoshuaMiller0 on 2011-10-06
Bascially I needed a program to record games as I play them (minecraft) so I found and installed recordmydesktop onto my Ubuntu 10.04 successfully.

After installation I opened the Applications menu from the top panel and throughout all the menus I cannot find recordmydesktop anywhere.

In Synaptic Package Manager recordmydesktop is shown as being correctly installed and has the latest version.

To try and find recordmydesktop I have tried:
[LIST]
[*]Right-Clicking on Applications in the panel, clicking edit menus and searching through all the menus.
[*]Searching the whole system for recordmydesktop
[/LIST]

Please help me!

_**[COLOR="Red"][SIZE="8"][FONT="Comic Sans MS"][CENTER]HOW TO DO IT!!![/CENTER][/FONT][/SIZE][/COLOR]**_[CENTER]
[SIZE="3"]**> **jocko said:**
> **[COLOR="Navy"]
recordmydesktop is a command line application, but there's a graphical front-end named gtk-recordmydesktop.
Install it by:
```
sudo apt-get install gtk-recordmydesktop
```
It should appear in your menus as "Desktop Recorder" (or just run it by typing "gtk-recordmydesktop" in a terminal).[/COLOR][/SIZE] [COLOR="Blue"][SIZE="2"]I will also add that it should rock up in "Sound & Video" in your menu accessed by the upper panel.[/SIZE][/COLOR] [/CENTER]

---

### Post by amjjawad on 2011-10-06
> **JoshuaMiller0 said:**
> Bascially I needed a program to record games as I play them (minecraft) so I found and installed recordmydesktop onto my Ubuntu 10.04 successfully.

After installation I opened the Applications menu from the top panel and throughout all the menus I cannot find recordmydesktop anywhere.

In Synaptic Package Manager recordmydesktop is shown as being correctly installed and has the latest version.

To try and find recordmydesktop I have tried:
[LIST]
[*]Right-Clicking on Applications in the panel, clicking edit menus and searching through all the menus.
[*]Searching the whole system for recordmydesktop
[/LIST]

Please help me!

Hello,

What will happen if you type:
```
recordmydesktop

```In Terminal?

Sometimes, you may need to use "sudo" before that so it will be:

```
sudo recordmydesktop
```

---

### Post by jocko on 2011-10-06
> **amjjawad said:**
> 
Sometimes, you may need to use "sudo" before that so it will be:

**Don't.** Sudo should only be used when it's really needed (i.e when an applications needs to be able to write outside of your home directory). There is nothing in recordmydesktop that would require sudo.

recordmydesktop is a command line application, but there's a graphical front-end named gtk-recordmydesktop.
Install it by:
```
sudo apt-get install gtk-recordmydesktop
```
It should appear in your menus as "Desktop Recorder" (or just run it by typing "gtk-recordmydesktop" in a terminal).

---

### Post by amjjawad on 2011-10-06
> **jocko said:**
> **Don't.** Sudo should only be used when it's really needed (i.e when an applications needs to be able to write outside of your home directory). There is nothing in recordmydesktop that would require sudo.

That was "just in case" statement but thanks anyway :)

---

### Post by Elfy on 2011-10-06
Did you install gtk-recordmydesktop - it's the gui frontend for it.

---

### Post by JoshuaMiller0 on 2011-10-06
Thanks A LOT! I have it installed and working now!

---

### Post by Elfy on 2011-10-06
> **jocko said:**
> **Don't.** Sudo should only be used when it's really needed (i.e when an applications needs to be able to write outside of your home directory). There is nothing in recordmydesktop that would require sudo.

recordmydesktop is a command line application, but there's a graphical front-end named gtk-recordmydesktop.
Install it by:
```
sudo apt-get install gtk-recordmydesktop
```
It should appear in your menus as "Desktop Recorder" (or just run it by typing "gtk-recordmydesktop" in a terminal).I almost think I almost might edit your post so as not to appear to have been ninja'd :D 

> **JoshuaMiller0 said:**
> Thanks A LOT! I have it installed and working now!So what was it then? Other's might come here to find a quick fix - it would help them to know what it was you did :)

---

### Post by JoshuaMiller0 on 2011-10-06
> **forestpiskie said:**
> 
So what was it then? Other's might come here to find a quick fix - it would help them to know what it was you did :)

Done!

Thanks again everyone for the help! Even if you didn't help - Thanks for trying!

---

### Post by prosist on 2011-12-29
> **jocko said:**
> 
Install it by:
```
sudo apt-get install gtk-recordmydesktop
```
It should appear in your menus as "Desktop Recorder" (or just run it by typing "gtk-recordmydesktop" in a terminal).

thanks!

---

