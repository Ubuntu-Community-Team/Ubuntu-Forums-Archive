---
title: "where is system monitor? I want to see how data is transefered(intenet) from my PC."
date: 2011-07-12
forum: General Help
---

### Post by vikash_chandola on 2011-07-12
It should probably in system->system monitor but it is not there. There is another thing name task manager but i need system monitor that also give information about how many data out and in via Internet. and many more but task manager not give this facility.

---

### Post by Surendil on 2011-07-12
Same as windows

CRTL+ALT+DEL

---

### Post by vikash_chandola on 2011-07-12
> **Surendil said:**
> Same as windows

CRTL+ALT+DEL
this is not system monitor if press **CRTL+ALT+DEL** then a screen appear ask password input password and press **enter** nothing happen i come back to main screen. If does not press enter then their is screen showing a thing moving round and round. :confused:

---

### Post by Surendil on 2011-07-12
> **vikash_chandola said:**
> this is not system monitor if press **CRTL+ALT+DEL** then a screen appear ask password input password and press **enter** nothing happen i come back to main screen. If does not press enter then their is screen showing a thing moving round and round. :confused:

Ok, there two other ways then.

If you want to enable Ctrl+Alt+Del to open System Monitor you have to do this:

Go to System->Preferences->Keyboard Shortcuts and search for “Logout” action (that is under Desktop actions) and you will see that Ctrl+Alt+Del combination is associated to Logout shortcut.
You have to click on that shortcut and press Backspace if you want to disable it or choose another combination.
Close this and open the Configuration Editor (if you have installed it you will find it under Applications->System Tools; or just run gconf-editor).
- On left tree select: apps->metacity
- Select “Global_keybindings” and search for a “run_command_X” value where X is between 1 and 12 and it is not used
- Add this value: <Control><Alt>Delete
- Now select “Keybindings_commands” on left tree. Goto “command_X” where X is the same number selected in run_command_X option.
Add this value: gnome-system-monitor

Alternative solution (I prefer this one):
Run in terminal: 
```
 gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_1 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_1 "gnome-system-monitor" 
```

---

### Post by vikash_chandola on 2011-07-12
> **Surendil said:**
> Ok, there two other ways then.

If you want to enable Ctrl+Alt+Del to open System Monitor you have to do this:

Go to System->Preferences->Keyboard Shortcuts and search for “Logout” action (that is under Desktop actions) and you will see that Ctrl+Alt+Del combination is associated to Logout shortcut.
You have to click on that shortcut and press Backspace if you want to disable it or choose another combination.
Close this and open the Configuration Editor (if you have installed it you will find it under Applications->System Tools; or just run gconf-editor).
- On left tree select: apps->metacity
- Select “Global_keybindings” and search for a “run_command_X” value where X is between 1 and 12 and it is not used
- Add this value: <Control><Alt>Delete
- Now select “Keybindings_commands” on left tree. Goto “command_X” where X is the same number selected in run_command_X option.
Add this value: gnome-system-monitor

Alternative solution (I prefer this one):
Run in terminal: 
```
 gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_1 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_1 "gnome-system-monitor" 
```

It is seeming that i will change system setting here. 

And their is nothing like preferences in system there are these options **additional driver, giglo language support,log in screen,printing, start up disk creator,synaptic package manager,tak manager, time and date,update manager , user and groups**. Except these their is no option. I try this setting->setting manager->keyboard->application shortcuts  there is a screen like in attachment1.
How i change that to get system monitor.:confused:

OR

I should try terminal command that will work.:)

---

### Post by Surendil on 2011-07-12
Try terminal command!!!
if not, your screenshot is telling CTRL+ALT+DEL locks the screen, change the value like it says in the guide

---

### Post by vikash_chandola on 2011-07-12
> **Surendil said:**
> Try terminal command!!!
if not, your screenshot is telling CTRL+ALT+DEL locks the screen, change the value like it says in the guide
nothing happens.
see this screen shot. (i am using xubuntu 11.04)

---

### Post by mali2297 on 2011-07-12
The thread is marked xubuntu. If that is what you use Vikash, then Surendil's instructions won't work since they are gnome-specific.

---

### Post by vikash_chandola on 2011-07-12
> **mali2297 said:**
> The thread is marked xubuntu. If that is what you use Surendil, then Vikash' instructions won't work since they are gnome-specific.
**Surendil** try to give me those commands and instructions which are not gnome specific because i am using [color=red]xubuntu 11.04[/color].

---

### Post by mali2297 on 2011-07-12
> **vikash_chandola said:**
> **Surendil** try to give me those commands and instructions which are not gnome specific because i am using [color=red]xubuntu 11.04[/color].

I am sorry for the mix-up. Still, the commands given are for gnome (gconf, metacity etc are gnome components).

---

### Post by vikash_chandola on 2011-07-12
> **mali2297 said:**
> I am sorry for the mix-up. Still, the commands given are for gnome (gconf, metacity etc are gnome components).
then what i do where is system monitor in xubunu. Does it exist or not(in my OS).

---

### Post by Toz on 2011-07-12
See: [http://ubuntuforums.org/showpost.php?p=11029768&postcount=3]("http://ubuntuforums.org/showpost.php?p=11029768&postcount=3")

Either install gnome-system-monitor or use a curses based tool such as bmon. Conky will also work.

---

### Post by Surendil on 2011-07-12
I apologize for giving the wrong command.
My bad.

---

### Post by vikash_chandola on 2011-07-12
> **Surendil said:**
> I apologize for giving the wrong command.
My bad.
I am happy that you try to help but next time when you try to help any person then see what distro is he/she using. In my post i write in my first post that i am using xubuntu even then you answer in gnome. 
> 
See: [http://ubuntuforums.org/showpost.php...68&postcount=3]("http://ubuntuforums.org/showpost.php?p=11029768&postcount=3")

Either install gnome-system-monitor or use a curses based tool such as bmon. Conky will also work.     
Now i am installing system monitor from software canter as advised by toz

EDIT:
I have installed  system monitor. This is the thing i want. THANKS TOZ
linux require greater system processor(10% to 20% in normal) than windows(2% to 7% in normal).

---

