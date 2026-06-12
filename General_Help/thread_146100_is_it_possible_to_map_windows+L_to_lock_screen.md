---
title: "is it possible to map windows+L to lock screen?"
date: 2006-03-17
forum: General Help
---

### Post by namregzepol on 2006-03-17
where can i map the windows+'L' key to lock session?

---

### Post by aysiu on 2006-03-17
First you have to make the Windows key function "properly."
Go to System > Preferences > Keyboard and one of the tabs has some extra options where you can make the Windows key behave differently (I'm not on my Ubuntu box right now, so I forget what the exact option is).

Then go to Applications > System Tools > Configuration Editor > Apps > Metacity and select Global Keybindings and put in Win + L and then go Keybinding Commands and put the command to lock the screen.

Win + L may not be the exact syntax. If you want to know for sure, go to System > Preferences > Keyboard Shortcuts and select a shortcut you don't normally use and select Windows + L and see what it says. After you jot that down, hit Backspace to disable that shortcut.

---

### Post by eyebrowman92 on 2006-03-17
alright how can i do this in xfce?

---

### Post by namregzepol on 2006-03-17
mmm, when i press win+L in keyboard shotcuts mapped to lock session, it shows 'Super_L' and after pressing only the windows key it locks the session. But i've got no way of mapping win+L

another relative question, which is the default key, if any, to lock the session?

---

### Post by bender unit on 2006-03-17
Same for me, I'm not able to set "Win + L" or some other key plus the windows key as a shortcut. Wenn I press the Win Key it just takes "Super_L" as shortcut (for the left win key). 
However, for setting a shortcut to lock the screen, it's not necessary to use the Configuration Editor. Under System->Preferences->Shortcuts, on my system, the 4th entry reads "lock screen".

---

### Post by Barrakketh on 2006-03-17
Open the keyboard applet, switch to the layout options tab, and expand Alt/Win key behavior.  Switch it to "Meta is mapped to the Win-keys".

Now when you try to set the lock shortcut to WIn+L, it say <Mod4>+l.

---

### Post by namregzepol on 2006-03-17
but i like to lock it with a key. Is faster than the mouse.

---

### Post by namregzepol on 2006-03-17
yes, it says <mode4>+L but when press win+L the session doesn't lock

---

### Post by eyebrowman92 on 2006-03-17
anyone know how to do it in xfce?

---

### Post by bender unit on 2006-03-18
[QUOTE=Barrakketh]Open the keyboard applet, switch to the layout options tab, and expand Alt/Win key behavior.  Switch it to "Meta is mapped to the Win-keys".

Now when you try to set the lock shortcut to WIn+L, it say <Mod4>+l.[/QUOTE]

Doesn't work for me. Not even a complete restart seems to change the Win key behaviour. It still says "Super_L" when I try to use the Win key in a hotkey combination. What's wrong?

---

### Post by namregzepol on 2006-03-18
First of all thank you very much for the help, honestly, it's very apreciated for a newbie like me

Second, i'm trying hard to do this. It's some kind of little personal challenge. I can't map win+'L' to lock screen yet. Why win+'L'? because it's the same in XP. I like to have a rest and lock the session quickly. Please if there is anyone who know why, even changing the setting in the keyboard layout to 'Meta is mapped to the Win-keys', doen't work to lock the session, let me know.

---

### Post by firecat53 on 2006-03-18
I suppose I'm not directly answering your question, but when using Enlightenment (e17), there is a keyboard activated screen lock Ctrl-Alt 'l' (little l). There is a keyboard binding utility there as well, but I can't say I've used it yet. 

Scott

---

### Post by Barrakketh on 2006-03-18
[QUOTE=firecat53]I suppose I'm not directly answering your question, but when using Enlightenment (e17), there is a keyboard activated screen lock Ctrl-Alt 'l' (little l). There is a keyboard binding utility there as well, but I can't say I've used it yet. 

Scott[/QUOTE]
The default in Gnome is Ctrl+Alt+l.  The problem is, it doesn't seem to be recognizing the Win key in all cases.  I'm a KDE guy (but will give Gnome a shot in a few Flights), but I launched Gnome and configured the keys...Win+t (once configured) will launch my terminal (which is what I want), but Win+l (once configured) won't lock the workstation.  They both show up the same way in the configuration panel (<Mod4>t and <Mod4>l respectively), but only the terminal shortcut works.

I'm thinking it might be wise to file a bug report, and hopefully a Dapper user will comment on whether this is broken in 2.14 as well.  I have every application I frequently use bound to a hotkey (I was spoiled during by Fluxbox days :D), and I a deskop environment is useless to me if I can't do the same with it.  Then again, Gnome 2.12 doesn't seem to let you define custom shortcuts for any application, so unless 2.14 changes that I won't both trying to switch.

---

### Post by rakhesh on 2006-04-24
Just checking -- has anyone managed to get this working? I am on Dapper Beta1 and facing the same problem. (Sorry if this is the wrong place to post to since I am on Dapper, but I was searching the forum and found this thread. Thought its better to continue the discussion rather than start a new one). 

Thanks,
Rakhesh

---

### Post by Copter on 2006-05-07
hi!

ive got similar question. how to run session lock from command line? xscreensaver-command -lock doesnt work fine on my box. 

copter :]

---

### Post by BitTorrentBuddha on 2006-05-07
I just got it working, follow these steps:

1. Set "Meta is mapped to the Win-keys." selected for System -> Preferences -> Keyboard -> Layout Options -> Alt/Win key behaviour

2. Get xbindkeys and xbindkeys-config (apt can get both of those, they're in the universe repositories)

3. Start xbindkeys and then xbindkeys-config, that will bring up a GUI and you can add a new one or modify the pre-existing ones. Set a name (what you pick, doesn't matter), the Key to "Mod4 + L", and the Action to "xscreensaver-command -lock" then click "Save & Apply & Exit" and voila, the elusive windows+L screen lock is attained.

Copter, perhaps there's something else used in KDE other than xscreensaver, but I'm probably wrong.

PS I'm fairly sure this won't work in dapper since I believe they changed to gnome-screensaver instead of xscreensaver

---

### Post by jester805 on 2006-09-15
Is there any update to this??  I'm new to Linux and I have Dapper installed.  I'm still trying to figure out how to map the Win + L keys.

---

