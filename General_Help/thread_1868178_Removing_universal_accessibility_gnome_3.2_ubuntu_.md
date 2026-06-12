---
title: "Removing universal accessibility gnome 3.2 ubuntu 11.10"
date: 2011-10-23
forum: General Help
---

### Post by OneXero on 2011-10-23
Tried everything to remove that accessibility icon? (Or any other icon from gnome 3.2 panel?)

Some of the fixes around don't work because the menus have changed or updates from 11.10...Here is the solution I found:

[http://conjurecode.com/disable-the-universal-access-accessibility-menu-in-gnome-3/](http://conjurecode.com/disable-the-universal-access-accessibility-menu-in-gnome-3/)

"In the new gnome-shell, otherwise known as Gnome 3, there is an  accessibility menu called "Universal Access" that cannot be removed by  any apparent means. Fortunately it can easily be removed, hidden, or  disabled by editing a file and restarting the shell. This method works  for gnome-shell version 3.0 (this reportedly works in Gnome 3.2 as  well), it may or may not work in future versions. 

Edit the file /usr/share/gnome-shell/js/ui/panel.js

Look for the following line, (line 38 in my case):
  [FONT=monospace]'a11y': imports.ui.status.accessibility.ATIndicator,

[/FONT]Comment out this line like so:

[FONT=monospace]//'a11y': imports.ui.status.accessibility.ATIndicator,

[/FONT]Then restart gnome-shell by typing Alt-F2 to run command, enter "r"  without the quotes, and hit enter. This will quickly restart the shell  and you should find that the Universal Access menu no longer appears. If  you should find a use for it in the future, simply un-comment the lines  found in /usr/share/gnome-shell/js/ui/panel.js"


_**My Notes:**_

1. Fix the broken ALT+F2 by going to system settings -> keyboard -> shortcuts -> system; choose "show the run command prompt" and click to the right and make your shortcut ALT+F2 or whatever you'd like.

2. Use ALT+CTRL+T and open a terminal, use "sudo gedit /usr/share/gnome-shell/js/ui/panel.js" to open the file for editing. **Then do a search for "a11y" (Note: those are ONEs not Ls)** comment out the first one related to Universal Access (add // anywhere before the entry on the line). There is a second entry but you don't have to comment it out.

3. Now save and close that, use the fixed ALT+F2 and enter just r, hit enter...

4. You should be good to go!

---

### Post by strikeir13 on 2011-10-26
THANK YOU. 

I had tried many, many older methods, but none worked (maybe you had a similar experience). Finally, Google turned up this thread! Thanks for the heads up.

Edit: Would this method work for removing the bluetooth icon as well? Or would that break things?

---

### Post by stinkeye on 2011-10-26
> **strikeir13 said:**
> THANK YOU. 

I had tried many, many older methods, but none worked (maybe you had a similar experience). Finally, Google turned up this thread! Thanks for the heads up.

Edit: Would this method work for removing the bluetooth icon as well? Or would that break things?

You could probably just disable bluetooth in startup applications
if you don't use it.
You may  need to show all applications in startup applications because the defaults are now hidden.

If so just run in the terminal
```
cd /etc/xdg/autostart/
```
then
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

### Post by baronrouge on 2011-10-26
Great shout on removing that icon, thanks

---

### Post by Joshas on 2011-10-28
Simple, but not the best solution - you shouldn't mess with system files and they might be overwritten during next update. Aren't there any Gnome Shell settings in user home directory config?

---

### Post by gorostas on 2011-10-30
Good point from Joshas

I would like to know that too..

In home dir there is:

.local/share/gnome-shell/

can we put some config files inside to change layout?

---

### Post by mtron on 2011-10-30
there is a gnome-shell extension to hide the accessibility icon. 

```
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-noa11y
```

open gnome-tweaks, go to the 'Shell Extensions' tab and enable the noa11y extension.

---

### Post by JDog2pt0 on 2011-10-31
Thank you mtron. That is by far the best solution for everyone. A quick note, if you install it and it doesn't appear in the tweak tool, even after restarting gnome, just log out and back in.

---

### Post by sophistihip on 2011-11-04
> **mtron said:**
> there is a gnome-shell extension to hide the accessibility icon. 

```
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-noa11y
```

open gnome-tweaks, go to the 'Shell Extensions' tab and enable the noa11y extension.

Good to know mtron, I'll update my article as it is getting a lot of traffic.

---

