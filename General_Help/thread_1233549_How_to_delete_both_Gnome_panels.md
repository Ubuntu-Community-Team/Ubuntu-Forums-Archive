---
title: "How to delete both Gnome panels ?"
date: 2009-08-06
forum: General Help
---

### Post by credobyte on 2009-08-06
Is there a way do delete both Gnome panels ?
 I can't seem to find a way to remove the top panel ( tough, all applets already removed from it ).

Ideas/suggestions always appreciated :)

---

### Post by ubudog on 2009-08-06
Right click on it and select "Delete This Panel"  Hope that helps. :)

---

### Post by credobyte on 2009-08-06
> **ubudog said:**
> Right click on it and select "Delete This Panel"  Hope that helps. :)

If it would be that easy ( option disabled ) ..

---

### Post by jaxxstorm on 2009-08-06
I'm not on my Linux box at the moment, but you can kill gnome-panel by typing
```

killall gnome-panel

```

Then go to Startup Manager in System and remove the option from there too. Sorry this isn't the best answer, but as I said, its hard remembering where stuff is without having it infront of you :D

---

### Post by credobyte on 2009-08-06
> **jaxxstorm said:**
> I'm not on my Linux box at the moment, but you can kill gnome-panel by typing
```

killall gnome-panel

```Then go to Startup Manager in System and remove the option from there too. Sorry this isn't the best answer, but as I said, its hard remembering where stuff is without having it infront of you :D

The problem is that .. Startup does not contain *gnome-panel* ( only *gnome-settings*, *gnome-daemon*, etc. ). *killall* doesn't help as well .. panel shows up again in a bout 2 seconds.

---

### Post by jaxxstorm on 2009-08-06
Try this from [here]("http://ubuntuforums.org/showthread.php?t=1118062")

> 
But you should be able to go to System > Preferences > Main Menu and if you click on System Tolls you can "tick" Configuration Editor.

Then go to System Tools > Configuration Editior and - well a picture is worth a thousand words:

[http://ubuntuforums.org/attachment.php?attachmentid=108909&d=1239054483](http://ubuntuforums.org/attachment.php?attachmentid=108909&d=1239054483)

You can see that I expanded Desktop, then Gnome, then Session. From there you can deselect panel from "required components".



Not sure if it'll work.
A

Also, an EXTREMELY last resort is this

```

sudo chmod -x /usr/bin/gnome-panel

```

It'll prevent gnome-panel from being executed.

---

### Post by Brandon Williams on 2009-08-06
It's not recommended to delete the last panel, because if you don't run gnome-panel, then AltF2 doesn't work to open the 'Run Application' dialog. For some reason, that functionality is provided by gnome-panel.I recommend that you auto-hide the panel instead.

If you really want it to be disabled, then one way to do it is to remove "panel" from the gconf key /desktop/gnome/session/required_components_list using gconf-editor. This should work in jaunty, I think. It doesn't appear to work in hardy, though, and my jaunty machine is at the office so I can't test it now to verify.

---

### Post by credobyte on 2009-08-06
> **jaxxstorm said:**
> Try this from [here]("http://ubuntuforums.org/showthread.php?t=1118062")



Not sure if it'll work.
A

Also, an EXTREMELY last resort is this

```

sudo chmod -x /usr/bin/gnome-panel

```It'll prevent gnome-panel from being executed.

Ah, thank you - *last resort* works like a charm ( tough, I hope I'll not get any errors tomorrow :D ).

---

### Post by jaxxstorm on 2009-08-06
If you're worried about losing the run facility from Alt+f2 like Brandon said, install gmrun and map it to alt+f2. Some quick Google-fu will help you work out how I'm sure, but I use gmrun under Openbox and its awesome :D

---

### Post by samden on 2009-08-06
If you don't want the gnome panel, maybe you don't need gnome? I have no idea what you are doing, but there is a possiblity you might be better off ditching gnome completely for fluxbox or something like that rather than trying to trim down gnome.

---

### Post by greenmoss on 2009-08-06
> **samden said:**
> If you don't want the gnome panel, maybe you don't need gnome? I have no idea what you are doing, but there is a possiblity you might be better off ditching gnome completely for fluxbox or something like that rather than trying to trim down gnome.

God. Who in the Gnome project decided that if you want alt-f2, you *have* to have a panel? That is, frankly, ridiculous. There is nothing that would logically dictate that a panel should be linked to keyboard macros!

They won't even let you auto-hide the thing all the way out of view anymore (it used to be do-able); you are *forced* to see at least a small portion peeking out at you, at all times. It's like they went out of their way to ignore any possible protest you might have with the panel, and force you to have it anyway!

So, in my case I had previously set up Gnome with auto-login, and kept the panel out of the way for mythtv. Now I either have to resort to some ugly hack, or go way out of my way with a new window manager. Sometimes, these open-source projects just go all brain-dead; it's like they hate their users and want to see us suffer.

---

### Post by credobyte on 2009-08-07
> **samden said:**
> If you don't want the gnome panel, maybe you don't need gnome? I have no idea what you are doing, but there is a possiblity you might be better off ditching gnome completely for fluxbox or something like that rather than trying to trim down gnome.
 
As you can see it in my second post, I want to remove both panels to make my Desktop *cleaner*. I've installed AWN and added amlost everything I had on my panels ( so .. I don't need them anymore ).
For the Gnome thingy - this was just an experiment ( the whole AWN and gnome panel stuff ), which kind of failed .. I wasn't able to remove both panels without breaking the whole panel system ( by removing execution permissions ).
 
> **greenmoss said:**
> God. Who in the Gnome project decided that if you want alt-f2, you *have* to have a panel? That is, frankly, ridiculous. There is nothing that would logically dictate that a panel should be linked to keyboard macros!
 
They won't even let you auto-hide the thing all the way out of view anymore (it used to be do-able); you are *forced* to see at least a small portion peeking out at you, at all times. It's like they went out of their way to ignore any possible protest you might have with the panel, and force you to have it anyway!
 
So, in my case I had previously set up Gnome with auto-login, and kept the panel out of the way for mythtv. Now I either have to resort to some ugly hack, or go way out of my way with a new window manager. Sometimes, these open-source projects just go all brain-dead; it's like they hate their users and want to see us suffer.
 
That's exactly why I can't hide it .. Even if it's transparent, I still see some part of it on the top ( like 2-3mm ). Regarding panels and Alt-F2 - I've never used this shortcut :D

---

### Post by greenmoss on 2009-08-07
> **credobyte said:**
> As you can see it in my second post, I want to remove both panels to make my Desktop *cleaner*. I've installed AWN and added amlost everything I had on my panels ( so .. I don't need them anymore ).
For the Gnome thingy - this was just an experiment ( the whole AWN and gnome panel stuff ), which kind of failed .. I wasn't able to remove both panels without breaking the whole panel system ( by removing execution permissions ).


So, I took the advice of using a different Window Manager (XFCE4), as one of the previous posters suggested. It works OK for my setup. It still has an un-hideable panel, but that panel doesn't insist on covering every other window on my desktop. Given what you've said, this solution probably won't work for you, of course.

---

### Post by tarps87 on 2009-08-07
> **jaxxstorm said:**
> Try this from [here]("http://ubuntuforums.org/showthread.php?t=1118062")



Not sure if it'll work.
A

Also, an EXTREMELY last resort is this

```

sudo chmod -x /usr/bin/gnome-panel

```

It'll prevent gnome-panel from being executed.

My solution was to hide it by renaming it to gnome-panel2, it'll never find it there :)

A better solution is open up gconf-editor under / -> desktop -> gnome -> session -> required_components there is a entry called panel change this to awn

or

gconftool -s /desktop/gnome/session/required_components/panel awn -t string

This is assuming awn still launches the panel

---

