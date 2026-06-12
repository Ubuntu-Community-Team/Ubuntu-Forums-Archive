---
title: "panels"
date: 2009-11-19
forum: General Help
---

### Post by gilbertrios on 2009-11-19
i am fairly new to linux and i was wondering y my bottom panel just disappeared and i cannot find it anywhere. i have used a couple a methods that were posted here but was of no help it kept reading that program file does not exist can anyone help me?

---

### Post by Citizenpete on 2009-11-19
your LUCKY -- at least you have a panel ... LOL
same problem but worse...

I have NO MENUS -- i think the term is panels -- I still have zero panels -- notta -- no to no bottom -- just an empty desktop :cry:  

I can get the right click mouse menu up.

I was able to get Mozilla going through a right click menu for new backgrounds and then search for new backgrounds on line which launched mozilla firefox - thank god.  thats how I got here.

Is there a keyboard shortcut to turn panels on ...

When I ran UBUNTU from the DVD ISO image it ran fine
when I  brought it up the first time from the HD install UBUNTU udated and NO panels to or bottom

great UBUNTU deity .... help us  LOL

---

### Post by Citizenpete on 2009-11-19
This first cup of Ubuntu is bitter to swallow

no top or bottom panels  makes life a bit limited.   ](*,)

---

### Post by wojox on 2009-11-19
Do this in the terminal:

```
rm -r ~/.gconf/apps/panel
```

If you can't get a terminal press Alt+F2
Enter: gnome-terminal

Logout and back in or reboot.

---

### Post by Citizenpete on 2009-11-19
> **wojox said:**
> Do this in the terminal:

```
rm -r ~/.gconf/apps/panel
```

If you can't get a terminal press Alt+F2
Enter: gnome-terminal

Logout and back in or reboot.
rm: cannot remove `/home/pete/.gconf/apps/panel': No such file or directory

---

### Post by wojox on 2009-11-19
```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by Citizenpete on 2009-11-19
> **wojox said:**
> ```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
successfully entered and rebooted - however did not fix -- now I have no controls on mozilla windows --  resize delete etc.

---

### Post by Citizenpete on 2009-11-19
wow - I figured out  how to get my window controls back!  I lost abilty to change focus and lost my min/max/close controls, but when I right click on the desktop and select  the Change Desktop Background then select the Appearance preferences  then Visual Effects and select Normal or Extra options [only to have them error out) - my windows controls come back -- BUT still no panels on the top or bottom

---

### Post by Citizenpete on 2009-11-19
how are your panels doing

---

### Post by wojox on 2009-11-19
Maybe you need to reinstall gnome-panel:

```
sudo apt-get install gnome-panel
```

---

### Post by Citizenpete on 2009-11-19
> **wojox said:**
> Maybe you need to reinstall gnome-panel:

```
sudo apt-get install gnome-panel
```
hmmm...  

reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Citizenpete on 2009-11-19
> **wojox said:**
> Maybe you need to reinstall gnome-panel:

```
sudo apt-get install gnome-panel
```
Hey guru I'm gonna start a new thread on this panel issue because I inadvertently hijacked this thread from [gilbertrios]("http://ubuntuforums.org/member.php?u=959861") - his problem was slightly different from mine, however you input may have been of direct use to him as well.   Thanks for your attempts to get my first Ubuntu OS started.

pete

---

