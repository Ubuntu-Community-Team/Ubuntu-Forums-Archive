---
title: "Compiz and Nautilus stopped working"
date: 2012-04-25
forum: General Help
---

### Post by colobix on 2012-04-25
Hello. I'm on version 11.4
For a day or two ago, Nautilus and compiz stopped booting up.
I tried to add commands for nautilus and compiz --replace to the startup session thing, but that doesn't work.
It works when I type it in to the terminal though.
This is strange.
Is there a way to fix this?

---

### Post by Frogs Hair on 2012-04-25
Hi, What do you mean by nautilus won't boot up ? Nautilus is the file browser so I don't understand the comment. What session are you selecting from the login screen ?

---

### Post by colobix on 2012-04-25
> **Frogs Hair said:**
> Hi, What do you mean by nautilus won't boot up ? Nautilus is the file browser so I don't understand the comment. What session are you selecting from the login screen ?
It's the file manager.
Basically the desktop doesn't start up.
The gnome-panel works though

---

### Post by Frogs Hair on 2012-04-25
I guessing in you are using Classic and not Unity because you said the gnome panel starts and that is not part of Unity . You could try the following for nautilus .  ```
nautilus -q
```

---

### Post by colobix on 2012-04-25
> **Frogs Hair said:**
> I guessing in you are using Classic and not Unity because you said the gnome panel starts and that is not part of Unity . You could try the following for nautilus .  ```
nautilus -q
```
I use gnome 2.
But not "nautilus -q" didn't do anything.

---

### Post by Frogs Hair on 2012-04-25
If your panel is visible but has no indicators try the following . The previous command was to restart nautilus. 

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

If that is not the problem Consider running ```
compiz --replce
``` from the recovery console. You get there from the session list below the greeter box on the bottom center of the login screen.

---

### Post by huggs on 2012-04-25
> **frogs hair said:**
> 
if that is not the problem consider running ```
compiz --repl[color="red"]a[/color]ce
``` from the recovery console..

---

### Post by colobix on 2012-04-26
As I said in my first message, doesn't work. I have to go to the terminal from the start menu, and manually type in compiz --replace and nautilus after every reboot.
And nothing is wrong with the panels, just to get that out of the way.

---

### Post by colobix on 2012-04-26
I'm sorry but I Need this to be fixed quicker than this.
Does ubuntu have a paid service or something where I can get instant support?

---

### Post by colobix on 2012-04-26
I did fix the compiz issue. Have no idea how.
So now, how do I make nautilus startup automatically?
Having no desktop icons is driving me nuts.

---

### Post by Frogs Hair on 2012-04-26
I am glad Compiz is working . You said you ran the compiz --replace command from the terminal which is different from the recovery console.

Missing desktop icons and Nautilus not starting are completely different problems . There have been many solutions previously posted on other threads to correct the missing icon problem. If that is the problem use the forum search tool .

---

