---
title: "The turn off icon has disappeared"
date: 2011-03-03
forum: General Help
---

### Post by newcolt on 2011-03-03
Hi

I am a newbie. Occasionally, my username superimposes the turn off button on the menu bar. Now on the top-right corner of the screen, I have my username displayed twice, consecutively. I am unable to turn off or logout as the icon itself is missing. How do I rectify this?

---

### Post by vivek.pandey on 2011-03-03
to get a new shutdown applet right click at a suitable point in your panel then add to panel and you will see in the list a shutdown applet... similarly to remove one of the usernames right click on one of them and remove

---

### Post by MARP1961 on 2011-03-03
Sometimes the icons/applets on the panels stop displaying correctly, get broken and will not work. I do not know why this happens but I have always solved it by typing the following code :

killall gnome-panel

---

### Post by howefield on 2011-03-03
Pressing Ctrl-Alt-Del should bring up a shutdown dialogue if needs be.

---

### Post by vivek.pandey on 2011-03-03
> **howefield said:**
> Pressing Ctrl-Alt-Del should bring up a shutdown dialogue if needs be.

well i have seen many a times that ctrl+alt+del doesnt bring a shutdown window ..mostly wubi install.. i couldnt find the reason though

---

### Post by leviathan8 on 2011-03-03
You can also use the command line to shut down or restart your computer, using these commands:

```
sudo shutdown -h now
```

for shutting down and

```
sudo shutdown -r now
```

for restarting.

---

### Post by newcolt on 2011-03-03
Thanks, but I am unable to remove the duplicate copy of my username. Also it doesn't appear fully. I am unable to do anything to it.

---

### Post by leviathan8 on 2011-03-03
> **newcolt said:**
> Thanks, but I am unable to remove the duplicate copy of my username. Also it doesn't appear fully. I am unable to do anything to it.

You can try reseting the panels by executing the following commands in a terminal:

```
gconftool --recursive-unset /apps/panel
```

Now we remove the settings:

```
rm -rf ~/.gconf/apps/panel
```

Kill it:

```
pkill gnome-panel
```

And then start it again:

```
gnome-panel &
```

Note that if you will close the terminal the panels will disappear - that's normal. Once you reboot everything will be back to default and you can customize your panels again.

---

### Post by newcolt on 2011-03-03
Should I do this only when I face the problem again?

---

### Post by leviathan8 on 2011-03-04
> **newcolt said:**
> Should I do this only when I face the problem again?

If it ain't broke, then don't try to fix it. In other words, you only do that when the problem persists.

---

### Post by newcolt on 2011-03-04
> **leviathan8 said:**
> If it ain't broke, then don't try to fix it. In other words, you only do that when the problem persists.

Thanks :)

---

