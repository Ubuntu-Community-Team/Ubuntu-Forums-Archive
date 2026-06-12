---
title: "Pidging status as presently playing song"
date: 2009-08-15
forum: General Help
---

### Post by 7raTEYdCql on 2009-08-15
I want the presently playing song in totem, to appear as a status message in my pidgin messenger. Can someone mention the plugin which will help me do this. 

Thanking you, 
Mehrzad

---

### Post by tspan on 2009-08-15
There are plugins to do so for other players ([pidgin-musictracker supports many music players]("http://code.google.com/p/pidgin-musictracker/")) but I haven't found one that supports totem player.

---

### Post by coldReactive on 2009-08-15
> **tspan said:**
> There are plugins to do so for other players ([pidgin-musictracker supports many music players]("http://code.google.com/p/pidgin-musictracker/")) but I haven't found one that supports totem player.

Yeah, would be nice if the DEFAULT MUSIC PLAYER OF UBUNTU would be supported.

---

### Post by 7raTEYdCql on 2009-08-15
As far as i know, pidgin doesn't give direct support to Totem playing songs, yes it does support rhythymbox, but not Totem.

Can this be done.

---

### Post by ubudog on 2009-08-15
> **coldReactive said:**
> Yeah, would be nice if the DEFAULT MUSIC PLAYER OF UBUNTU would be supported.

Yeah that would be nice. :lolflag:

---

### Post by 7raTEYdCql on 2009-08-17
You can enable many music players in ubuntu by installing pidgin-musictracker, it is there in synaptic. Totem is suprisingle not a supported music player, rhythymbox is supported, therefore shouldn't be a problem.

---

### Post by coldReactive on 2009-08-18
> **i.mehrzad said:**
> You can enable many music players in ubuntu by installing pidgin-musictracker, it is there in synaptic. Totem is suprisingle not a supported music player, rhythymbox is supported, therefore shouldn't be a problem.

I'd rather have a player that replaces the current playlist with the music file I open rather than to add it to the current play list on top of any other files I am currently playing. Plus, I need the ability to loop one file over and over again forever.

---

### Post by mcduck on 2009-08-18
> **coldReactive said:**
> Yeah, would be nice if the DEFAULT MUSIC PLAYER OF UBUNTU would be supported.

It is, Rhythmbox is the default music application in Ubuntu and Gnome. :) Totem is the default *media* player, mainly targeted for video playing. That's why Totem appears in the menus as "Movie Player".

And no need for shouting.

Anyway, there are many music players actually made to be music players that are supported by that plugin. Sounds like you'd like Audacious, BMP or some similar player (as they are not library-based).

---

### Post by coldReactive on 2009-08-18
> **mcduck said:**
> It is, Rhythmbox is the default music application in Ubuntu and Gnome. :) Totem is the default *media* player, mainly targeted for video playing. That's why Totem appears in the menus as "Movie Player".

And no need for shouting.

Anyway, there are many music players actually made to be music players that are supported by that plugin. Sounds like you'd like Audacious, BMP or some similar player (as they are not library-based).


I'd rather have a player that replaces the current playlist with the music file I open rather than to add it to the current play list on top of any other files I am currently playing. Plus, I need the ability to loop one file over and over again forever.

---

### Post by mcduck on 2009-08-18
> **coldReactive said:**
> I'd rather have a player that replaces the current playlist with the music file I open rather than to add it to the current play list on top of any other files I am currently playing. Plus, I need the ability to loop one file over and over again forever.

Yes, that's what you said. And that's why I suggested Audacious, BMP or some similar player, which are all supported by the Pidgin plugin.

Anyway, my actual point as simply that it's pointless to complain that Ubuntu's default music player is not supported by some 3rd party Pidgin plugin, when in fact that 3rd party plugin supports Ubuntu's default player. It just happens to be that *you* prefer using Ubuntu's default movie player to play your music files.. ;)

---

### Post by coldReactive on 2009-08-18
> **mcduck said:**
> Yes, that's what you said. And that's why I suggested Audacious, BMP or some similar player, which are all supported by the Pidgin plugin.

Anyway, my actual point as simply that it's pointless to complain that Ubuntu's default music player is not supported by some 3rd party Pidgin plugin, when in fact that 3rd party plugin supports Ubuntu's default player. It just happens to be that *you* prefer using Ubuntu's default movie player to play your music files.. ;)

Is beep media player effected by compiz effects such as drag across workspaces? Because audacious sure isn't.

Besides, audacious will not play my MP3s, it just sits there, dong nothing.

---

### Post by frankob on 2009-10-22
In my case Audacious is effected by Compiz AND it plays ANY KIND of audio file, INCLUDING mp3, and even those odd tracker mod, nsf ecc. files.

Are you sure you have installed all the plugins?

---

### Post by coldReactive on 2009-10-22
> **frankob said:**
> In my case Audacious is effected by Compiz AND it plays ANY KIND of audio file, INCLUDING mp3, and even those odd tracker mod, nsf ecc. files.

Are you sure you have installed all the plugins?

You'd think it would take all the plugins totem has.

---

### Post by frankob on 2009-10-22
No... Totem uses GStreamer libs, or the xine ones. Audacious has nothing to do with neiter of them, it has its own playback engine. That's why you should install two more packages along with Audacious: audacious-plugins and audacious-plugins-extra. Then you should be completely set.

---

