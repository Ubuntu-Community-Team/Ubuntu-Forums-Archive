---
title: "HOW TO save power for a smarter planet"
date: 2009-08-17
forum: General Help
---

### Post by k.sangeeth on 2009-08-17
I usually lock my screen when I leave my cubicle for a tea-break etc.
With all the awareness for saving Energy etc. etc. I have disabled screen-savers on my system.
Still when I lock my screen I noticed that the LCD doesn't turn off completely.
Then I wanted to save even that little bit of light emitted i.e. wanted to switch off the LCD.

This command helps us do that :
xset dpms force off;

and this is the command invoked when I press "Alt+Ctrl+l" to lock the screen :
gnome-screensaver-command --lock;

Then, I wanted to associate the following command to a shortcut key:
gnome-screensaver-command --lock; xset dpms force off;

So that I can lock as well as power off my LCD screen with a keyboard shortcut.

So, I installed xbindkeys to add a custom shortcut key:
sudo apt-get install xbindkeys
#lock&blank
"gnome-screensaver-command --lock; sleep 1; xset dpms force off;"
alt+control+k

created the default config file :
xbindkeys --defaults > /home/your-user-name/.xbindkeysrc

Then to assign a shortkey, you can either edit this file manually or do it through xbindkeys-config(sudo apt-get install xbindkeys-config).
I removed the default enabled lines (somehow they interfered with my other shortcuts) from ~/.xbindkeysrc and appended the following lines :

#lock&blank
"gnome-screensaver-command --lock; sleep 1; xset dpms force off;"
alt+control+k

I was forced to give a "sleep 1" between the two commands; else it was not working ... maybe because of compiz animation time.

Now, when I press "alt+control+k" I save power as well as lock my screen.

Spread this word and let's save energy, so that our grand-children are not forced to lead a life in dark.

*Tested on Ubuntu 8.10 running on Lenovo T61p

Please feel free to post your comments/suggestions.

Sangeeth Keeriydath
[www.sangeek.com](www.sangeek.com)

---

