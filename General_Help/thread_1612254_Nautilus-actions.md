---
title: "Nautilus-actions"
date: 2010-11-02
forum: General Help
---

### Post by Ntwiles on 2010-11-02
Hey guys, hopefully I'm in the right section. I'm brand new to the forums and to Ubuntu.

I've installed the nautilus-actions package and I'm trying to make additions to context menus. First I tried to make a set as desktop background option for right clicking images, but it didn't work. So I followed two different tutorials thinking I'd done something wrong, but those actions didn't pop up on my context menus either.

I'm hoping it's just because the tutorials were dated (I couldn't find any tutorials for Nautilus Actions Configuration 2.0 or later) I'll post the settings I used for the one that I most expected to work:

**Action**
Context Label: Add to Playlist
Tooltip: Enqueue in Audacious Playlist

**Command**
Label: Default Profile
Path: /usr/bin/audacious
-e %d%m

**Folders**
/

**Conditions**
Filenames: *.mp3; *.mid; 
Mimetype: audio/*
Appear if selection contains: Both

I left out some of the settings that didn't seem important. If you need anything else just ask.

I also noticed that the example showen other the Path textbox does something funny. Instead of replacing %d%m completely, I get the following example string:

*e.g. /usr/bin/audacious - /pathtodfile.txtm*

As you can see the "d" and "m" aren't removed. I'm not sure if that's my problem or not but that didn't look very good.

Again, I hope this is in the right section. Any help would be greatly appreciated.

---

### Post by Vaphell on 2010-11-02
i guess it's some kind of noncritical bug and it affects only the example line 
besides shouldn't you use %M instead of %d%m?

---

### Post by Ntwiles on 2010-11-02
Well like I said that's not my only problem. The actions simply don't work. When I right click - in this example - a midi file, nothing comes up.

---

### Post by Vaphell on 2010-11-03
have you tested it with %M?
i actually tried my version of Enqueue for totem with %M which is pretty much identical with yours in every other aspect - i temporarily replaced totem with audacious and it worked just fine.

checked 'display item in selection context menu'
action properties: enabled
totem
--enqueue %M
folders: /
*.mp3; *.ogg; *.avi; *.mp4; *.mov; *.wav
mime *
only files
appears for multiple selection
advanced conditions: 'file' checked

---

### Post by Ntwiles on 2010-11-03
Yeah I did. That did make the example less convoluted. Now it says 

*/path/to/file.txtM*

It didn't do anything for the context menu though. Could it be that the install didn't go through right? Or that there's something else I need to install? I installed it through the Terminal, would I be better off finding it in Ubuntu Software Center?

Edit: Yeah my settings match yours exactly.

---

### Post by Vaphell on 2010-11-03
my example string shows totem --enqueue /path/to/file1.txt /path/to/file2.txt

can you create ANY basic action without fancy filters that would show up in the context menu? something like command: gnome-terminal for any item, with no params?
have you restarted nautilus after creating the action (killall nautilus or logout/login)?

iirc sudo apt-get install nautilus-actions was all there was to it, it's a single package.

---

### Post by Ntwiles on 2010-11-03
Hey look at that, I'm an idiot. Killall did the trick. Thanks for the help.

---

### Post by Ntwiles on 2010-11-03
Sorry for the double post. I lied. The action does appear on the context menu, but the problem isn't solved. The actual option I was trying to perform was "Set image as background". Here is how I was doing it:

**Path:** /usr/bin/gconftool-2
**Command:** -t string -s /desktop/gnome/background/picture_filename %d%f

It works find when done through command line, so I can only assume that this must be related to the glitch with the % parameter variables mentioned in my first post. Does anyone know how to fix this?

---

### Post by mc4man on 2010-11-03
What version of aud. are you using - the current is audacious 2, so the command would be audacious2

There are 2 useful queue commands (3rd one isn't working right atm here as an action (audacious2 -e -p

audacious2 -e  (adds to a current list
audacious2 -E -p  (creates a new temp playlist plays

Both can be used on files and folders.

If you have audacious 2 then use one  the above as command, the parameter is simply %M (or create 2 actions

screens show the latter

---

