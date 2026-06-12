---
title: "Tweaking BASS/TREBLE etc."
date: 2005-03-14
forum: General Help
---

### Post by Mark Marple on 2005-03-14
I was looking to see if there is a util for changing the bass, treble and such.
some of my mp3s seem to have to much bass.  I don't have anything for the default volume control.  I know its something I just need to install but not even sure what to type in to synaptic search, same here in the forums, so please forgive me if this is a repeat.

---

### Post by fackamato on 2005-03-14
[QUOTE=Mark Marple]I was looking to see if there is a util for changing the bass, treble and such.
some of my mp3s seem to have to much bass.  I don't have anything for the default volume control.  I know its something I just need to install but not even sure what to type in to synaptic search, same here in the forums, so please forgive me if this is a repeat.[/QUOTE]

If you're using xmms it has an equalizer.

---

### Post by Mark Marple on 2005-03-14
No I'm not using xmms.  I was looking to do it system wide.  Do I dare say this........like MS.  Right click on volume control in Taskbar area and going to a setting preference, moving a slider bar.  Something like this.

---

### Post by kassetra on 2005-03-14
[QUOTE=Mark Marple]No I'm not using xmms. I was looking to do it system wide. Do I dare say this........like MS. Right click on volume control in Taskbar area and going to a setting preference, moving a slider bar. Something like this.[/QUOTE]

There are a couple of different utilities you can use to change the base / treble, etc.  Most of us do it with our mp3 player such as xmms, bmp, rhythmbox, etc.

But if you want to control most of all the entire system, you'll probably want to install aumix-gtk.

It's a graphical interface that allows you to change the base/treble/etc.  (It's ugly, but it works.)

---

### Post by Mark Marple on 2005-03-15
[QUOTE=kassetra]There are a couple of different utilities you can use to change the base / treble, etc.  Most of us do it with our mp3 player such as xmms, bmp, rhythmbox, etc.

But if you want to control most of all the entire system, you'll probably want to install aumix-gtk.

It's a graphical interface that allows you to change the base/treble/etc.  (It's ugly, but it works.)[/QUOTE]

I'm using Rhythmbox............could you please help me find where this is?
I don't see anything that jumps out at me.

and you are right............aumix is VERY ugly.

---

### Post by electroglas on 2005-04-19
I don't see any equalizer or bass/treble controls with a default Hoary install. Am I missing something?

---

### Post by fackamato on 2005-04-20
[QUOTE=electroglas]I don't see any equalizer or bass/treble controls with a default Hoary install. Am I missing something?[/QUOTE]

No, because these adjustments are made on your amplifier. It's not Hoary's problem that you're listening to 96kbps mp3's ;). Not all soundcards support this feature either. Hrhr.

---

### Post by smoon on 2005-04-20
Try opening the Gnome Mixer (gnome-volume-control). Click on Edit->Preferences and if you're lucky there is a checkbox labeled with "Tone" in the list of available tracks. Switch it on. Turn on Bass and Treble there as well. After that you should be able to turn "Tone" on under the "Switches"-tab. Controlling "Bass" and "Treble" under "Playback" should change your bass and treble accordingly now.

For alsamixer this works similiar: Find "Tone", unmute (m) it and play with "Bass" and "Treble".

Note: This does not work with all soundcards AFAIK.

---

