---
title: "How can I &quot;fix&quot; the red logout button?"
date: 2009-09-23
forum: General Help
---

### Post by Motorhead Kaze on 2009-09-23
Hiya. I am mainly a Hardy user, but just began using Jaunty a bit in another computer. There are a couple things I didn't like so am trying to change them:

After "fixing" the ctrl+alt+bskp shortcut to restart X, I now need to "fix" the red log-out button so restart and shutdown are back on the list of options. I would really appreciate it if someone could tell me how to do this.

Opinion time...
Well, there must already be a thread on this topic but I have not found it... A single red button with many options for restarting & shutdown, logout, etc. was logical. Red=hot,power,etc. and you don't push it unless you mean it. It was a good tool. But in Jaunty red means logout or switch users and there is an optional gray button for shutting down or restarting. Such a change is nonsensical. It is like changing the Firefox button to only show your bookmarks, and if you want to actually START it you need to use another button.

Thanks for the help guys. I hope the next upgrade finds the proper tools in the proper places.

---

### Post by kerry_s on 2009-09-24
i don't understand, what i think your saying is you removed the fast user switcher applet & put the logout applet, which doesn't have the shutdown,restart,suspend,hibernate, but you want to combine the 2 now seperate programs into 1.

why not just use the switcher applet, but use gconf-editor to turn off what you don't want?

here's what mine looks like.

---

### Post by Motorhead Kaze on 2009-09-24
> **kerry_s said:**
> i don't understand, what i think your saying is you removed the fast user switcher applet & put the logout applet, which doesn't have the shutdown,restart,suspend,hibernate, but you want to combine the 2 now separate programs into 1.

why not just use the switcher applet, but use gconf-editor to turn off what you don't want?

here's what mine looks like.

Sorry, I will try to be more clear. I didn't remove anything myself. I see that in your top corner you have a running green guy, as you probably know, default Ubuntu is a red button. In Hardy, this red button is used for logging out, suspend, hibernate, switching users, restarting or shutting down. But when I installed Jaunty, I see that pushing this button only gives me the option log out or switch users. There was no shutdown option, so I used the "add to panel" tool on my top panel to get another power button for shutting down (it was gray). I was bewildered as to why this had changed, but more than that I wanted to make the red button function the way it does in Hardy.

gconf-editor? I will give it a try, thanks.

---

### Post by wojox on 2009-09-24
Ctrl+Alt+Delete works as well.

---

### Post by kerry_s on 2009-09-24
sorry, i just got up & running, i changed to debian lenny.

> I see that in your top corner you have a running green guy, as you probably know, default Ubuntu is a red button. In Hardy, this red button is used for logging out, suspend, hibernate, switching users, restarting or shutting down.

yeah, the icon go's off the icon theme, i was using standard gnome.


> But when I installed Jaunty, I see that pushing this button only gives me the option log out or switch users. There was no shutdown option, so I used the "add to panel" tool on my top panel to get another power button for shutting down (it was gray). I was bewildered as to why this had changed, but more than that I wanted to make the red button function the way it does in Hardy.

what can i say, jaunty is using a newer gnome, there were a lot of changes since hardy.

---

### Post by unmole on 2009-09-24
LOL welcome to the club Kaze

[http://ubuntuforums.org/showthread.php?t=1165036](http://ubuntuforums.org/showthread.php?t=1165036)

---

### Post by Motorhead Kaze on 2009-09-24
AH HA! I KNEW there was a club out there! Hahaha. Thanks. Is membership free, and is the emblem a red square with a white circle in it?

---

### Post by unmole on 2009-09-24
LOL. For now I'm using the grey button though.....

---

### Post by Chronon on 2009-09-24
I'm using Jaunty and my user switcher applet displays a red button.

---

### Post by kerry_s on 2009-09-24
i just did a zenity script for mine, it was simple & you can easily add what ever you want to serve your needs.

it requires that you add some nopasswd lines to visudo:
**you  ALL=NOPASSWD:  /sbin/shutdown, /usr/sbin/pm-suspend**

```
#!/bin/sh
read=`zenity --height=250 --list --title='Shutdown' --column=Action Logout Suspend Restart Shutdown`

if [ $read = "Logout" ]; then
	gnome-session-save --kill 
fi

if [ $read = "Suspend" ]; then
	sudo pm-suspend
fi

if [ $read = "Restart" ]; then
	sudo shutdown -r now
fi

if [ $read = "Shutdown" ]; then
	sudo shutdown -h now
fi

```


mind you it's not fancy, but it works & its fast on this old 450mhz 256mb ram piece of junk. :lolflag:

---

### Post by kerry_s on 2009-09-24
i decided to do 1 with xmessage, cause zenity does not have a setting for placement & i want it right under the icon.

```
#!/bin/sh
read=`xmessage -fn 9x15 -g -5+10 "Shutdown Options" -buttons Logout,Suspend,Restart,Shutdown,Cancel -print`

if [ $read = "Logout" ]; then
	gnome-session-save --kill 
fi

if [ $read = "Suspend" ]; then
	sudo pm-suspend
fi

if [ $read = "Restart" ]; then
	sudo shutdown -r now
fi

if [ $read = "Shutdown" ]; then
	sudo shutdown -h now
fi

if [ $read = "Cancel" ]; then
	exit 0
fi


```

---

### Post by Motorhead Kaze on 2009-09-27
Thanks! I will try this script thingy. I oddly enjoy them...makes me feel like I am learning something.

Funny how I assumed that ctrl+alt+del was only a Windows thing.

Oh, and I hope that the people in charge of setting up the desktop buttons will read this and put the beautiful shiny button...the jolly candy-like button...back the way it was/is in Hardly Herring. Before we all get Space Madness.

---

### Post by oboedad55 on 2009-09-27
Here's another scripty thing you can try if you don't like the other one. This will restore both panels to the way the were when the install was new, before customization. I had to use it the other night... It took five minutes to put things back the way I had them.

mv $HOME/.gconf/apps/panel $HOME/.gconf/apps/panel-old 
sudo /etc/init.d/dbus restart

---

### Post by Motorhead Kaze on 2009-09-29
Wow. You guys have all sorts of scripty codey things! Thanks.
But to tell the truth, after I found out about the ctrl+alt+del combo, I have just been using that. Has that shortcut always been like that? Ha! Right under my nose too!

Peace

---

### Post by Motorhead Kaze on 2009-09-29
OH, and Kerry S? "WTF?" under the coffee is awesome.

---

### Post by kerry_s on 2009-09-29
> **Motorhead Kaze said:**
> OH, and Kerry S? "WTF?" under the coffee is awesome.

i chose that cause i actually say that a lot. :lolflag:

i been using the zenity 1, the xmessage feels slower to me.
i'm using debian lenny, the ctrl+alt+delete does the same as ctrl+alt+backspace so that don't help me. :(

---

### Post by kerry_s on 2009-10-01
here's 1 using gmessage.

```

#!/bin/sh
read=`gmessage -center "Shutdown Options" -buttons Logout,Suspend,Restart,Shutdown,Cancel -print`

if [ $read = "Logout" ]; then
	gnome-session-save --kill 
fi

if [ $read = "Suspend" ]; then
	sudo pm-suspend
fi

if [ $read = "Restart" ]; then
	sudo shutdown -r now
fi

if [ $read = "Shutdown" ]; then
	sudo shutdown -h now
fi

if [ $read = "Cancel" ]; then
	exit 0
fi


```

---

### Post by NinjaNumberNine on 2009-10-02
> **kerry_s said:**
> i chose that cause i actually say that a lot. :lolflag:
-tsk, tsk, tsk. :-$

---

### Post by bonkey on 2009-10-07
This doesn't seem to happen consistently. I have 4 systems running ubuntu, all on the latest version. Only 2 of them are missing the shutdown option on the red button.

The other 2 work normally. This must be configurable somehow, but I haven't found it.

---

