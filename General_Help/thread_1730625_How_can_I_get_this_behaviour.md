---
title: "How can I get this behaviour?"
date: 2011-04-16
forum: General Help
---

### Post by camaron1 on 2011-04-16
Does anyone know how to get the following behaviour?

-**When I open a new app. I want all the other already open apps. to minimize.**

Any ideas?

Thanks in advance

---

### Post by TeoBigusGeekus on 2011-04-16
Install wmctrl and replace the command of your app from
```
appname
```
to 
```
wmctrl -k on && appname
```
Create a script if the app launcher doesn't accept it
```
#!/bin/bash
wmctrl -k on
appname
```

---

### Post by camaron1 on 2011-04-16
> **TeoBigusGeekus said:**
> Install wmctrl and replace the command of your app from
```
appname
```to 
```
wmctrl -k on && appname
```Create a script if the app launcher doesn't accept it
```
#!/bin/bash
wmctrl -k on
appname
```


That sounds very good, thanks teobigusgeekus...what a name eh?:)

Is it possible to make this default for ALL apps?

---

### Post by TeoBigusGeekus on 2011-04-16
> **camaron1 said:**
> That sounds very good, thanks teobigusgeekus...what a name eh?:)

Is it possible to make this default for ALL apps?

I don't think so... Can't think of one anyway...
You'll have to create launchers for all your apps.

---

### Post by camaron1 on 2011-04-16
Thanks, 

Just to be clear. If I want Nautilus to behave like that.

```
#!/bin/bash wmctrl -k on nautilus
```

I make the above executable and where do I place it?

---

### Post by TeoBigusGeekus on 2011-04-16
Not all in one line. 
Open gedit (geany, kate, vim, emacs, whatever you like).
Create a new file and put these lines in it
```
#!/bin/bash 
wmctrl -k on 
nautilus
```
Save as, say, nautilus_launch in your home folder.
Make the script executable
```
chmod +x ~/nautilus_launch
```
Now right click your menus>edit menus.
Find the nautilus entry (could be called file manager, can't remember).
Click edit; change its command from 
```
nautilus
```
to 
```
bash ~/nautilus_launch
```
For all the above to work, you have to install wmctrl first
```
sudo apt-get install wmctrl
```

---

### Post by camaron1 on 2011-04-16
Thanks very much. I'm nearly there but not quite

When I execute the script it produces the right result
Changing the command in the menu editor doesn't seem to do anything
I should've said that i'm on Natty and I want to get the launcher in the bar. It doensn't accept the script as a launcher, although I've done something very similar (with wmctrl) to get the "show desktop" icon working from the bar.

---

### Post by TeoBigusGeekus on 2011-04-16
Are we talking about Unity here?

---

### Post by camaron1 on 2011-04-16
> **TeoBigusGeekus said:**
> Are we talking about Unity here?

Yes, we are now :)

Your script works when launched from the file itself but can't mange to include it as a launcher in Unity bar....

---

### Post by TeoBigusGeekus on 2011-04-16
I can't help you, sorry... I don't use it (and never will)...
Anyone else?

---

### Post by camaron1 on 2011-04-16
> **TeoBigusGeekus said:**
> I can't help you, sorry... I don't use it (and never will)...
Anyone else?

Thanks very much for your attention

---

