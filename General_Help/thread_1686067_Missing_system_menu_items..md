---
title: "Missing system menu items."
date: 2011-02-11
forum: General Help
---

### Post by Anthony A on 2011-02-11
The shut down, log out, and lock screen menu items are missing from the system menu. They were there a few days ago. Why would they be missing?

---

### Post by DanneStrat on 2011-02-11
> **Anthony A said:**
> The shut down, log out, and lock screen menu items are missing from the system menu. They were there a few days ago. Why would they be missing?

Hi.

Panel items have a tendency to disappear every now and then and

sometimes the whole panel.

You can add the menu item back again by right-clicking

on the panel and then selecting "add to panel".

Drag the new menu item to where you want it and then lock it in place by

right-clicking and selecting "lock to panel".

---

### Post by Anthony A on 2011-02-11
> **DanneStrat said:**
> Hi.

Panel items have a tendency to disappear every now and then and

sometimes the whole panel.

You can add the menu item back again by right-clicking

on the panel and then selecting "add to panel".

Drag the new menu item to where you want it and then lock it in place by

right-clicking and selecting "lock to panel".

The shut down, log out, and lock screen menu items are not in the right click "add to panel" dialog. I tried adding the whole menu again and even it was missing the entries I mentioned were missing.

---

### Post by DanneStrat on 2011-02-11
> **Anthony A said:**
> The shut down, log out, and lock screen menu items are not in the right click "add to panel" dialog. I tried adding the whole menu again and even it was missing the entries I mentioned were missing.

Do the following instead.

This will recreate the panels and 

put the settings back to default.

Open a terminal and do this(one command at a time):

```
gconftool –-recursive-unset /apps/panel

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

---

### Post by Anthony A on 2011-02-11
> **DanneStrat said:**
> Do the following instead.

This will recreate the panels and 

put the settings back to default.

Open a terminal and do this(one command at a time):

```
gconftool –-recursive-unset /apps/panel

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

I must be doing something wrong. I open Terminal and copied the commands you gave one at a time but nothing is happening.

---

### Post by DanneStrat on 2011-02-12
> **Anthony A said:**
> I must be doing something wrong. I open Terminal and copied the commands you gave one at a time but nothing is happening.

You have to press enter after each command.

---

### Post by Anthony A on 2011-02-12
> **DanneStrat said:**
> You have to press enter after each command.

I did and the cursor goes to the next line and than I add the next command. After the last one is entered I press enter and the cursor just goes to a new line but nothing else happens. Is there a key I need to press to get the commands to run?

---

### Post by Frogs Hair on 2011-02-12
Try this one . run as a single command.```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by Anthony A on 2011-02-12
> **Frogs Hair said:**
> Try this one . run as a single command.```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

Well here's what happened when I tried that command.

I tried it on one of my computers running 10.10 to see if it would reset the main top panel and it did. It's now in the default state like it was when I first installed 10.10. The thing is this computer had the shut down, log out, and lock screen items in the system menu and now they have disappeared since running the command. 

I haven't run the command on the computer that I originally posted about.

So now that the menu items disappeared on a second machine my question is are those menu items supposed to be there or not in 10.10? If you click "system" on the top panel of 10.10 do you see shut down, log out, and lock screen in the menu?

Edit: Now they are back. Hmm strange. I will try that command on the  other computer I originally posted about when I get home in a few days  and see if it works. It should since it reset the panel on this  computer. Thanks everyone for the help.

Edit: Looks like when you remove the shut down icon on the far right of the top panel the system menu gets shut down, log out, and lock screen added to it. When you reset the panel the system menu items get removed and the shut down icon on the far right is added back. As soon as you remove the shut down icon on the far right the system menu gets the menu items back.

---

### Post by Spyderkid on 2011-02-12
the applet which has all the shutdown logg out etc. on is called Indicator Apllet Session by the way incase your looking for the wrong thing

---

### Post by Anthony A on 2011-02-12
> **Spyderkid said:**
> the applet which has all the shutdown logg out etc. on is called Indicator Apllet Session by the way incase your looking for the wrong thing

Yes thank you. I add that applet to the panel and the shut down, log out, and lock screen items are removed from the system menu. Remove that applet and the system menu gets those menu items back. That explains why they were missing on one computer and not the other.

---

