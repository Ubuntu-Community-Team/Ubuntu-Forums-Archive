---
title: "Default lid close behavior"
date: 2012-07-04
forum: General Help
---

### Post by nerratt on 2012-07-04
I am having an issue getting the behavior that I want with a laptop with 12.04.

The behavior I'm looking for is that when the lid is closed the default behavior is to turn off backlight and not suspend.  

This works fine as a user setting but when at the login screen it defaults back to sleeping so I must remained logged in.

Is there some way to change the default behavior of lid close to nothing?

---

### Post by Quackers on 2012-07-05
In my 12-04 I'm using Gnome-shell and it is an option to "do nothing" when laptop lid is closed. This option is in Settings > power settings.
Aren't you seeing such an option?

---

### Post by krustenBrot on 2012-07-05
Hi nerrat and welcome to the Forums. :)

Try it with the dconf editor as described here:
[http://askubuntu.com/questions/122856/dont-want-to-suspend-when-closing-lid](http://askubuntu.com/questions/122856/dont-want-to-suspend-when-closing-lid)

if you have not isntalled dconf editor yet type 
```
sudo apt-get install dconf-tools
```into a terminal.

after that open it up with dash or terminal by typing ***dconf-editor***

now follow the path to 
[B][I]org > gnome > settings-daemon > plugins > power

[/I][/B]and see if 
***lid-close-ac-action & lid-close-battery-action ***are set to "nothing".

):P

---

### Post by krustenBrot on 2012-07-05
> **Quackers said:**
> In my 12-04 I'm using Gnome-shell and it is an option to "do nothing" when laptop lid is closed. This option is in Settings > power settings.
Aren't you seeing such an option?

I reckon he already tried that -  > This works fine as a user setting 
My first guess was that he is referring to the  the power settings panel

---

### Post by nerratt on 2012-07-05
> **Quackers said:**
> In my 12-04 I'm using Gnome-shell and it is an option to "do nothing" when laptop lid is closed. This option is in Settings > power settings.
Aren't you seeing such an option?

Indeed, as krustenBrot mentions.  I have done this.  This is successful as long as the user who made this setting is logged in when the lid is closed.  If no user is logged in it will still sleep.

---

### Post by nerratt on 2012-07-05
> **krustenBrot said:**
> Hi nerrat and welcome to the Forums. :)

Try it with the dconf editor as described here:
[http://askubuntu.com/questions/122856/dont-want-to-suspend-when-closing-lid](http://askubuntu.com/questions/122856/dont-want-to-suspend-when-closing-lid)

if you have not isntalled dconf editor yet type 
```
sudo apt-get install dconf-tools
```into a terminal.

after that open it up with dash or terminal by typing ***dconf-editor***

now follow the path to 
[B][I]org > gnome > settings-daemon > plugins > power

[/I][/B]and see if 
***lid-close-ac-action & lid-close-battery-action ***are set to "nothing".

):P


This was something I had seen before.  My experience with this is that it either does nothing or does the same thing as the power settings as I saw no change in behavior.

Currently what I am doing is closing the lid while logged in, logging into the machine via ssh, issuing a reboot if I want that account to be logged out.

This is not a huge deal but this machine will often be used for server software and I don't want to have to be ultra careful to make sure I don't suspend it after using.

---

### Post by krustenBrot on 2012-07-05
Here something different you might want to give a shot - but **use it with caution i cannot guarantee that it'll do what you wanna do. **

open up a terminal and type
```
 gksu gedit /proc/acpi/wakeup
```in that file search for something like
```
 LID0        S3        *enabled  
```change the ***enabled** entry to ***disabled**.
I stumbled upon it while trying to get my machine to wake up from the lid opening event.
Once more **i do not know **if it affects the* go to sleep routine*, if you're lucky it just disables the lid button event.
Good luck ;)

):P

---

### Post by Youngst3r1 on 2012-07-06
Quick relevant questions to this topic:
1) How do I bring my Ubuntu 12.04 LTS back from suspend mode when I open the lid?
        - - My laptop suspends when I close the lid however it doesnt really wake up (or I don't have enough patience!).  I would like to know  shortcut keys if any that the kernel recognizes for waking up.

2) Is there a way to add "Power off" option in the "When the lid is closed" menu options? I currently see "Suspend", "Hibernate" (grayed out/Inactive), and "Do nothing".

Peace!

---

