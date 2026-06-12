---
title: "Complete removal of Evolution"
date: 2011-02-22
forum: General Help
---

### Post by OctaFish on 2011-02-22
Last night for some reason, maybe red wine related, I decided to remove Evolution, all traces of it, using Synaptic.:guitar:

And now I cant log on to my computer.

Are the two related?

Is there any hope of regaining access to my system?

Many thanx, A. Idiot (Hngvr)

---

### Post by Mariane on 2011-02-22
If you have a bootup menu with the option "recovery mode" try to boot into that and do: 

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge evolution
sudo apt-get install evolution

```

Tell us of any error messages. 

The bootup menu might not be shown by default, look for:

```

Grub loading, please wait...
Press ESC to enter the menu

```

And when that shows up hit the escape key immediately. You can put your finger over this key in advance. 

Mariane

---

### Post by Habitual on 2011-02-22
at the login screen... Ctrl+Alt+F1
login...and 
```
sudo apt-get install -y evolution-data-server-common
```

System doesn't like it when it's removed. Even w\out the other Evolution stuff, you should leave that one on the system.

---

### Post by OctaFish on 2011-02-22
Thanks you two, couple of avenues to explore after work tonight.

I will let you know how it goes.

---

### Post by OctaFish on 2011-02-22
Ok,
I have no recovery mode available to me as I do not use (or cannot see) Grub, so Mariane's post was of no help...

Habitual's Ctrl+Alt+f1 trick was new to me, and got me to a CLI where i could confirm my password. However his 
Code:

sudo apt-get install -y evolution-data-server-common


did nothing, nor did Mariane's

Code:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge evolution
sudo apt-get install evolution


no errors, but my password still will not let me past the login screen

thanks again guys may not have solved my problem but you both taught me

---

### Post by Habitual on 2011-02-22
OctaFish:

Well, you can login via tty, that's a good thing.

One more thing to try:

```
Ctrl+Alt+F1
login
mv ~/.gconf ~/.gconf.org
mv ~/.config ~/.config.org
exit

```
**NOTE: This will reset all your gnome panels.**

Ctrl+right Arrow to GUI and try the login

I am subscribed to this thread.

Please let me know...

---

