---
title: "Cairo Dock Error!"
date: 2010-04-09
forum: General Help
---

### Post by Rytron on 2010-04-09
Hi.
I wanted to give Cairo Dock a try.

I did this:

```
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

Then in the terminal I enter cairo-dock but get this message:

```
:~$ cairo-dock
warning :  (cairo-dock.c:main:442)  
  couldn't create directory /home/rytron/.config/cairo-dock/themes
```

---

### Post by schwabdale on 2010-04-09
I am very new to Ubuntu, but I have installed Cairo dock on  a few machines. 
Maybe you should open Synaptics package manager, remove any cairo dock software you put on there,
reboot....Then, go back into Synaptics and add the repository (ppa:Cairo-team-dock/ppa) hit reload....
then, search for Cairo dock. 

It should be ver. 2.1.X. Just click to install Cairo Dock, it should install the dependencies including plugins.

Hope this helps

---

### Post by Rytron on 2010-04-09
Hi schwabdale.
I tried that. No joy.

---

### Post by schwabdale on 2010-04-09
Are you using 9.1?
Have you tried to install any themes?
Does it show as being installed in package manager?

Try this,,, hit alt+f2...then type...cairo-dock -c


Let me know

---

### Post by Rytron on 2010-04-09
> **schwabdale said:**
> Are you using 9.1?
Have you tried to install any themes?
Does it show as being installed in package manager?

Try this,,, hit alt+f2...then type...cairo-dock -c


Let me know

Yes, I am using 9.10

Here is the result:

---

### Post by lidex on 2010-04-09
I'm using glx-dock on lucid from the ppa. See the screen below. Do you have all those packages installed. Also you should run the command as either:
```
cairo-dock -c   (cairo backend)
or
cairo-dock -o   (glx)
```

---

### Post by lidex on 2010-04-09
> **Rytron said:**
> Yes, I am using 9.10

Here is the result:

Did you press the run button and what happened?

---

### Post by Rytron on 2010-04-10
Hi lidex.
Yes I have all those packages you mentioned. Nothing happens when I hit run. :confused:

It's no big deal. I prefer using panel icons over a dock but I just wanted to give Cairo Dock a go.

---

### Post by lidex on 2010-04-10
Try this:
```
chmod u+rwx -R ~/.config/cairo-dock/
```

---

### Post by Rytron on 2010-04-11
> **lidex said:**
> Try this:
```
chmod u+rwx -R ~/.config/cairo-dock/
```

:~$ chmod u+rwx -R ~/.config/cairo-dock/
chmod: changing permissions of `/home/rytron/.config/cairo-dock/': Operation not permitted
chmod: changing permissions of `/home/rytron/.config/cairo-dock/third-party': Operation not permitted
chmod: changing permissions of `/home/rytron/.config/cairo-dock/third-party/GnoMenu': Operation not permitted
chmod: changing permissions of `/home/rytron/.config/cairo-dock/third-party/GnoMenu/GnoMenu': Operation not permitted
chmod: changing permissions of `/home/rytron/.config/cairo-dock/third-party/GnoMenu/GnoMenu.conf': Operation not permitted
chmod: changing permissions of `/home/rytron/.config/cairo-dock/third-party/GnoMenu/icon': Operation not permitted

---

### Post by lidex on 2010-04-11
Try it with sudo:
```
sudo chmod u+rwx -R ~/.config/cairo-dock/
```

---

### Post by Rytron on 2010-04-11
> **lidex said:**
> Try it with sudo:
```
sudo chmod u+rwx -R ~/.config/cairo-dock/
```

Did the above line.

Output:
```
:~$ cairo-dock
warning :  (cairo-dock.c:main:459)  
  couldn't create directory /home/rytron/.config/cairo-dock/themes
```

---

### Post by fabounet on 2010-04-11
```
chmod -R 777 ~/.config/cairo-dock
```

---

### Post by lidex on 2010-04-11
> **fabounet said:**
> ```
chmod -R 777 ~/.config/cairo-dock
```
fabounet:
You may want to add that to the troubleshooting section on glx-dock.org
Thanks for your input.

---

### Post by Rytron on 2010-04-11
> **fabounet said:**
> ```
chmod -R 777 ~/.config/cairo-dock
```

Nice one fabounet. :P

---

