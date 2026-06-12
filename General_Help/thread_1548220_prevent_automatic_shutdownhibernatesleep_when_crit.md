---
title: "prevent automatic shutdown/hibernate/sleep when critical battery reached"
date: 2010-08-08
forum: General Help
---

### Post by alesserfate on 2010-08-08
hey folks

i'm trying to make the power manager NOT automatically shutdown / sleep / hibernate when battery power of my laptop reaches critical

i am surprised there isnt an 'NO ACTION' option for that in power manager

i've tried editing the acpi-supper in /etc/default bu couldn't find a solution in there nor in the /home/user/.gconf/apps/gnome-power-manager/ directory

someone must know this! rorr.. anybody ?

---

### Post by Lavahead on 2010-08-08
I am not certain if this will work or not. Using g-config editor, you can change a few options under apps > gnome-power-manager (specifically actions and threshholds).

---

### Post by alesserfate on 2010-08-08
> **Lavahead said:**
> I am not certain if this will work or not. Using g-config editor, you can change a few options under apps > gnome-power-manager (specifically actions and threshholds).

hmm.. i just tried but wasn't quite able to figure it out

---

### Post by halj32 on 2010-08-08
you could try using the power management preferences, it's in
system/preferences/power management
then go to the on Battery power options

---

### Post by Lavahead on 2010-08-08
If "Configuration Editor" is not listed in the "System Tools" option from "Applications," then open the command line terminal (under "Accessories"). Then, type in:
```
gconf-editor
```
The Configuration Editor should appear. Click on the triangle next to "Apps." A list of applications appears. Look for "gnome-power-manager." Click on the triangle next to it. "Actions" and "Threshholds" should appear.

When clicking on either, you should see Name/Value pairs appear in the right pane. You can manually set the values by double-clicking on the name. The long description should assist you. By the way, most of these peoperties are not available in Power Management preferences.

From your description, it looks as though the options in "Actions" is what you're looking for.

---

### Post by frogo on 2010-08-08
> **alesserfate said:**
> hey folks

i'm trying to make the power manager NOT automatically shutdown / sleep / hibernate when battery power of my laptop reaches critical

i am surprised there isnt an 'NO ACTION' option for that in power manager

i've tried editing the acpi-supper in /etc/default bu couldn't find a solution in there nor in the /home/user/.gconf/apps/gnome-power-manager/ directory

someone must know this! rorr.. anybody ?


Hi, 

I can't help with tweaking things at command lines. I do the sort of things you're talking about through an applet in the panel. 

There's two ways, I think... 

A. The first to directly access the settings is by doing:
1. System -> Preferences -> Power Management
2. goto C below

B. The other ties to the battery/power status which is in the notification area. It's another way of accessing the same control, but in addition, having it allows to keep track of your battery status. 

Make sure you have it in the panel.

1. rightclik on panel area (black bar on top)
2. Add to panel... 
3. find 'Notification area' in the list and highlight it by single left click
4. Add button

On the top right I have an indicator for battery. If you see this: 

1. left click on the battery icon, this will display a menu
2. Preferences (second item)

C. Once you got to the power management preferences by one of the above routes, you have three tabs. 

Main Power
Battery Power
General

they are pretty much self-explanatory or else I wouldn't know better than you... 

You can fiddle with settings there. For example, my machine can't resume from suspend or hibernate. So I set action for 'when laptop lid is close' to blank screen. 

In the general tab, you can set the notification regime, I ask it to always display an icon, so I have the confort of having the system pinging me every other minute when the battery is 20% charged as it regards it as critical... I usually have 15 minutes left to find a plug. Makes me wonder whether I really have a laptop but that's another story.

---

### Post by alesserfate on 2010-08-09
thanks for all the input guys

the graphical user interface did not offer an option of 'nothing' when critical battery

the file

i found the file

/home/'user'/.gconf/apps/gnome-power-manager/actions/%gconf.xml

has a 

```
<?xml version="1.0"?>
<gconf>
	<entry name="critical_battery" mtime="1281243126" type="string">
		<stringvalue>suspend</stringvalue>
	</entry>

```

you can change that to 'nothing' and it will override the GUI options

...

also, you can do this the same way with the gconf-editor like LAVAHEAD described

you can go to terminal, type in sudo gconf-editor

and head to the power-manager options and set the 'nothing' in there as well

thanks for all the input and this has been SOLVED!

---

### Post by Adem Stival on 2010-08-09
start > run > type in: mmc, add the event viewer as LOCAL, click  add, then click ok. View the event viewer in the applcations area.  should give you an explanation of what is going on.

---

