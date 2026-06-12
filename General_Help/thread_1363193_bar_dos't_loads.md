---
title: "bar dos't loads"
date: 2009-12-24
forum: General Help
---

### Post by imousavi on 2009-12-24
:KSwhen I login  into ubuntu I can't c the top & below bar I only can c the files on the desktop what should I do

---

### Post by dcstar on 2009-12-24
> **imousavi said:**
> :KSwhen I login  into ubuntu I can't c the top & below bar I only can c the files on the desktop what should I do

Reset your monitor or change the screen resolution.

---

### Post by imousavi on 2009-12-24
I dont have problem with the  resolution
there is a problem with the os maybe its from the source

---

### Post by imousavi on 2009-12-24
_[IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5410[/IMG]_
as u c no bar at top & bottom I checked the resolution & everything possible but problem remains  
I can't use my os any more the only thing possible is; I only can turn it on after that reset the pc nothing else I can do with my os

---

### Post by imousavi on 2009-12-24
help 
pleeeeeeeeeeeeeeeeeease?!
:confused:

---

### Post by lajevardi on 2009-12-24
Run the command:
```
ps -A | grep gnome-panel
```
If you get nothing, then run:
```
gnome-panel
```
else way (if you got something!) restart it:
```
killall gnome-panel
```
Even if that doesn't help, Kill 'em all:
```
killall gnome-settings-daemon && gnome-settings-daemon &
```

---

### Post by imousavi on 2009-12-25
can I reach Firefox with file manager I want to take backup from firefox with febe
I mean can i reach software without having top bar
somthing like this exp in windows C:\Program Files\Mozilla Firefox\firefox.exe

---

### Post by lajevardi on 2009-12-25
Of course you can! but getting backup from your firefox profile is not the problem at this stage, you have to get back the panels.
I guess you can not access the terminal, too since you've lost the gnome panels & so you're not able to run the mentioned commands in my previous post, if so please take a look:
Press **Ctrl+Alt+F1** you should see a black screen, type your username and your password afterward & you're in! It's terminal! run the commands you need to get the panels back (as I mentioned above), and then press **Ctrl+Alt+F7** to get back to the gui.
Also you can re-install the panels, and these all will hopefully solve the problem:
```
sudo aptitude install gnome-panel
```
Anyway if you want to run firefox via the command line you can simply use this:
```
firefox &
```
get back here & let us know what happened! wish you luck!

---

### Post by imousavi on 2009-12-25
[IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5419[/IMG][IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5418[/IMG][IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5417[/IMG]
[IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5420[/IMG]


no , no answer, nothing happened

---

### Post by lajevardi on 2009-12-25
Actually you did nothing!! you need to be more careful on reading posts & codes, having misspells in the terminal will not lead you to what you're goin' to do!
> 
**killall** not kill all
**gnome-panel** not gnome_panel
**gnome-settings-daemon** not gnome_settings_daemon
...

Also consider the order of the commands I mentioned, first of all you have to find out that the gnome-panels process is running or not! so: **ps -A | grep gnome-panel**
Well, let's begin again: go to the terminal and type this *exactly*: 
```
**sudo aptitude install gnome-panel**
```
And let me know the result.

---

### Post by imousavi on 2009-12-25
[B]ps -A | grep gnome-panel  
whats this    [/B][B] "| "
how do I type it ? 
[/B]

---

### Post by lajevardi on 2009-12-25
that's **Pipeline** character, **Shift+\** on most keyboards!
I think you need more interactive help, meet the folks at IRC **#ubuntu-ir** channel.

---

### Post by imousavi on 2009-12-25
[IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5421[/IMG]



so ,what 2 do?

---

### Post by lajevardi on 2009-12-25
Why don't you listen to me?!
```
**sudo aptitude install gnome-panel**
```
If you got a message saying that It's now installed on your system try to remove it and then re-install, the command for package removal is as follow:
```
**sudo aptitude remove gnome-panel**
```

---

### Post by WaveMyBlackFlag on 2010-01-13
too funny.

---

### Post by imousavi on 2010-01-13
can i ask what is the funny thing here

---

