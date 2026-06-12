---
title: "No display, consoles only after update and driver activation"
date: 2011-04-24
forum: General Help
---

### Post by Sh4dounet on 2011-04-24
Hello,

I have a big issue that i can understand (and i didn't find any answers)

When i boot, i only have the fullscreen console (tty1 to tty6), which ask me to login... If a try a gedit it says that there is no display. Startx doesn't work neither.

Before this, i tried to update from 10.04 to 10.10, but I had some issues with the update manager. On looked on google for solutions and I tried a couple of those: I updated my source list with maverick ppa, I removed the nvida driver ... Finally I managed to update thanks to the synaptic manager... Then I tried to re-enable the nvidia driver ..

Since then i am stuck with absolutely no display ..

Thanks for your attention

---

### Post by nothingspecial on 2011-04-24
Get a wired connection

type ```
sudo jockey-text -l
```

if there are any restricted nvidia drivers listed type ```
sudo jockey-text -e <driver>
```

---

### Post by Sh4dounet on 2011-04-24
Thanks for your answer.

I don't know how to "get a wired connection", but I tried sudo jockey commands in the console, it say > GtKwarning: could not open display warnings.warn(srt(e), gtk.Warning)

Then  did ```
sudo jockey-text -e xorg:nvidia_current
```
(tried also with xorg:nvidia_173, nvidia_current or nvidia_173 say that the driver doesn't exist).

But then, it still "cannot open display" when i try something (gedit or jockey). Rebooting changes nothing, i am still having the console only.

---

### Post by nothingspecial on 2011-04-24
You need to be connected to the internet for jockey to download the driver.

So if you normally use wireless you need to plug your computer directly into your router.

Otherwise you will need to connect wirelessly from the console.

---

### Post by Sh4dounet on 2011-04-24
I am not using wireless connection. It's an ethernet cable.
I guess jockey warn me if it can't connect ...
Here it's just saying

> /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
     warnings.warn(str(e), _gtk.warning)
and the list of drivers. Btw the driver enabled with jockey-text -e is "Enabled" (and the two others are Disabled of course).

But then ?

I don't know what startx is supposed to do but i ve this when trying:

> exec: 3: /usr/bin/X: not found
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit; No such process (errno 3): Server error

---

### Post by nothingspecial on 2011-04-24
What happens if you try to install ubuntu-desktop

---

### Post by Sh4dounet on 2011-04-24
sorry ... how to ?

---

### Post by nothingspecial on 2011-04-24
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Sh4dounet on 2011-04-24
I tried a pdkg from recovery menu and then a  ```
sudo dpkg-reconfigure xserver-xorg
``` but i get ```
xserver-xorg is broken or not fully installed
```

---

### Post by Sh4dounet on 2011-04-25
Solved with ```
sudo apt-get install -f xserver-xorg
```

---

