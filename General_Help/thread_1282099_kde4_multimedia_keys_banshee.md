---
title: "kde4 multimedia keys banshee"
date: 2009-10-03
forum: General Help
---

### Post by Strongman332 on 2009-10-03
i am trying to use banshee in kde4 (i think amarok is to slow)(and ugly!) but i cant get multimedia keys or notifications to work. can any one help with this

---

### Post by coolen on 2009-10-12
I agree. I'm liking KDE4, but some of the applications are quite horrible...

Anyway, partly due to a desire to answer this post, I've just figured this out. Go to System Setting -> Input Actions.

Down the bottom, go to Edit > New Group, name it Banshee. Make sure you select Banshee, then go Edit > New > Global Shortcut > D-Bus Command. Make a total of three of these commands, and name then Play/Pause, Next, and Previous (or whatever else you feel like calling them).

On each one, go to the trigger tab and give it the appropriate shortcut. Make sure you apply them. Then, under action, fill out the fields as below:

_Play/Pause_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlayerEngine
Function: org.bansheeproject.Banshee.PlayerEngine.TogglePlaying
Arguments:

_Next_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlaybackController
Function: org.bansheeproject.Banshee.PlaybackController.Next
Arguments: false


_Previous_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlaybackController
Function: org.bansheeproject.Banshee.PlaybackController.Previous     (I don't know about you, but in my browser, there's a space there that shouldn't be. Take care when copy and pasting)
Arguments: false

If I missed any, go [here]("http://banshee-project.org/contribute/write-code/dbus-interfaces/") for a list of interfaces. The pattern's pretty easy once you get used to it.

I'll have to learn how to use the mouse gestures and window events another time. That could be very interesting.

---

### Post by treris on 2010-01-30
Thanks so much! 

Banshee is my preferred music player by far, but not being able to use the media buttons on my keyboard was bugging me, a little, about it.

---

### Post by arch0njw on 2010-12-28
Coolen:  Thanks!  I normally use Amarok but started using Ubuntu on one computer and discovered Banshee.  I like that Banshee has an ability to randomize by album and build smart playlists by the same logic (e.g., least played albums).  Very nice.  Having media key control is nice.

I would like to setup a shortcut for vol-up, vol-down.  I found the interfaces for doing so, but am unsure what to pass in for arguments.  Can you help clarify that?

[http://git.gnome.org/browse/banshee/tree/src/Core/Banshee.Services/Banshee.MediaEngine/IPlayerEngineService.cs](http://git.gnome.org/browse/banshee/tree/src/Core/Banshee.Services/Banshee.MediaEngine/IPlayerEngineService.cs)

There is a "get" and "set" parameter.  I'm not sure what to provide there for values.

---

### Post by HendyIrawan on 2011-04-05
> **coolen said:**
> I agree. I'm liking KDE4, but some of the applications are quite horrible...

Anyway, partly due to a desire to answer this post, I've just figured this out. Go to System Setting -> Input Actions.

Down the bottom, go to Edit > New Group, name it Banshee. Make sure you select Banshee, then go Edit > New > Global Shortcut > D-Bus Command. Make a total of three of these commands, and name then Play/Pause, Next, and Previous (or whatever else you feel like calling them).

On each one, go to the trigger tab and give it the appropriate shortcut. Make sure you apply them. Then, under action, fill out the fields as below:

```
_Play/Pause_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlayerEngine
Function: org.bansheeproject.Banshee.PlayerEngine.TogglePlaying
Arguments:

_Next_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlaybackController
Function: org.bansheeproject.Banshee.PlaybackController.Next
Arguments: false

_Previous_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlaybackController
Function: org.bansheeproject.Banshee.PlaybackController.Previous
Arguments: false
```If I missed any, go [here]("http://banshee-project.org/contribute/write-code/dbus-interfaces/") for a list of interfaces. The pattern's pretty easy once you get used to it.

I'll have to learn how to use the mouse gestures and window events another time. That could be very interesting.
This post is amazing !!!

Thanks a LOT ! :)

Another one for Stop :

```
_Stop_
Remote application: org.bansheeproject.Banshee
Remote object: /org/bansheeproject/Banshee/PlayerEngine
Function: org.bansheeproject.Banshee.PlayerEngine.Close
Arguments:
```

---

### Post by danwizard208 on 2011-11-28
Thanks guys, you just made my life a whole lot nicer!

Cheers!

---

### Post by mescobal on 2012-07-27
Thank you!!!!!!!!! 
Hay can I "mod you up"?

---

