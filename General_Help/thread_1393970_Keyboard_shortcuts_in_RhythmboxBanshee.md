---
title: "Keyboard shortcuts in Rhythmbox/Banshee"
date: 2010-01-30
forum: General Help
---

### Post by Prodiga1 on 2010-01-30
I'm brand new to these forums and I'm hoping someone is able to help me here.

Lately I've been browsing through media players to use to listen to music and I really like the look and feel of both Rhythmbox and Banshee.  

Problem is, I'm used to the keyboard control scheme of iTunes, where the spacebar and left/right arrow keys control play, previous, and next song respectively.  This isn't the case in either of these programs.

I am aware of the gnome setting in System>Preferences>Appearance>Interface>Editable menu shortcuts.  But I can't get the menu shortcuts to use the left/right arrow keys.

My question is.. does anyone know of anyway to use the control scheme of iTunes as i described before in either of these two players?  Either by editing the menu shortcuts or editing a configuration file associated with one of the players?  Or at the very least a media program that uses such a control scheme.

Thanks in advance for your help.

---

### Post by Prodiga1 on 2010-01-30
bump

---

### Post by Prodiga1 on 2010-01-30
bump

---

### Post by Prodiga1 on 2010-01-30
bump

---

### Post by raktarok on 2010-01-30
Hi, 

Have a look at System >> Preferences >> Keyboard Shortcuts - it has entries like play, pause, etc.

If that doesn't work, look at the post here (even though its a bit unrelated to what you want to do) 
[http://ubuntuforums.org/showthread.php?t=1337120](http://ubuntuforums.org/showthread.php?t=1337120).
If you use remoot, you can definitely achieve that for both the players, at the same time.

---

### Post by Prodiga1 on 2010-01-30
So, I'm aware of the global keyboard shortcuts to play/pause, next, previous, etc..

What I'm seeking is a way to adjust the default keyboard shortcuts within the program itself.  I want to do this because I want, say Spacebar, to pause the song when I have one of the programs selected.

Any help on adjusting keyboard shortcuts of the program itself?  Again, I don't care about global shortcuts.

---

### Post by Prodiga1 on 2010-01-30
bump

---

### Post by Prodiga1 on 2010-01-30
bump

---

### Post by chewearn on 2010-01-30
> **Prodiga1 said:**
> So, I'm aware of the global keyboard shortcuts to play/pause, next, previous, etc..

What I'm seeking is a way to adjust the default keyboard shortcuts within the program itself.  I want to do this because I want, say Spacebar, to pause the song when I have one of the programs selected.

Any help on adjusting keyboard shortcuts of the program itself?  Again, I don't care about global shortcuts.

You don't care about global shortcuts, so what's the problem with changing them?  AFAIK Rythmbox uses the global shortcuts.  You change the global shortcuts, the change is propagated to Rythmbox.  Not sure about Banshee.

---

### Post by Prodiga1 on 2010-01-30
No, Rhythmbox does not use the global shortcuts, but that's neither here nor there.

My reasoning for nor being interested in global shortcuts is simple..

As I have said, I seek to modify the shortcuts of the program itself.  If I modified the global shortcut 'play' as spacebar, then anytime I typed spacebar globally-- the program would play/pause.  

Instead, I'm interested in the program keyboard shortcuts, as in Banshee where when you have Banshee selected, if you hit spacebar-- the music plays/pauses.  My problem with Banshee, is that I'd like the arrow keys while Banshee is selected to go to the previous or next song.

---

### Post by Prodiga1 on 2010-01-30
bump

---

### Post by dennymallow on 2010-03-06
> **chewearn said:**
>  AFAIK Rythmbox uses the global shortcuts. [...] Not sure about Banshee.

Yes, Banshee can use the global gnome keyboard shortcuts, but will not do it by default.
I'm so happy with Banshee, for me it's a little better than Rhythmbox, but this evening I was playing music and felt bored with clicking mouse over the tray icon to switch to the next song.

The global shortcuts **_*didn't work*_** in Banshee until that point, while _perfectly_ worked in Rhythmbox.

I found the solution to this problem absolutely unexpectedly: I opened the properties of the Banshee desktop launcher, and looked at which command was used there to start Banshee. It was:

```
dbus-launch banshee --redirect-log --play-enqueued %U
```

I changed it to:

```
banshee --redirect-log --play-enqueued %U
```

simply cutting away "dbus-launch".
And it worked! Now I'm listening Beethoven, and if something I don't like will come next, I'll use my global shortcut to switch to the next track.
Hope this will be useful to someone!!!

---

### Post by dennymallow on 2010-03-06
EDIT: **_not_** launching Banshee through dbus-launch ***breaks*** the volume control slide in Banshee itself. So I was able to use the global shortcut for switching tracks, but the slide of volume inside banhsee didn't control the volume, in effect.

So I tried launching Banshee through AOSS with:
```
aoss banshee --redirect-log --play-enqueued %U
```
And this worked, now I can control the volume using the Banshee slide, and control the track switching with global hotkeys even if Banshee is running in the background in another desktop of my wall.

---

